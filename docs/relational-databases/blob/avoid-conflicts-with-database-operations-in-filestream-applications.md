---
title: "Evitare conflitti con le operazioni del database nelle applicazioni di FILESTREAM | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FILESTREAM [SQL Server], conflitti tra Win32 e Transact-SQL"
ms.assetid: 8b1ee196-69af-4f9b-9bf5-63d8ac2bc39b
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 16
---
# Evitare conflitti con le operazioni del database nelle applicazioni di FILESTREAM
  Le applicazioni che usano SqlOpenFilestream() per aprire gli handle di file Win32 per la lettura o la scrittura di dati BLOB FILESTREAM possono entrare in conflitto con le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] gestite in una transazione comune. Sono incluse le query [!INCLUDE[tsql](../../includes/tsql-md.md)] o MARS la cui esecuzione richiede molto tempo. È necessario progettare con attenzione le applicazioni per evitare questi tipi di conflitti.  
  
 Quando il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] o le applicazioni provano ad aprire dati BLOB FILESTREAM, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] controlla il contesto di transazione associato. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] consente o nega la richiesta a seconda che l'operazione di apertura funzioni o meno con le istruzioni DDL, le istruzioni DML, il recupero dei dati o la gestione delle transazioni. Nella tabella seguente viene illustrato il modo in cui il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina se un 'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] verrà consentita o negata in base al tipo di file aperti nella transazione.  
  
|istruzioni Transact-SQL|Aperte per l'accesso in lettura|Aperte per l'accesso in scrittura|  
|------------------------------|---------------------|----------------------|  
|Istruzioni DDL che funzionano con i metadati del database, ad esempio CREATE TABLE, CREATE INDEX, DROP TABLE e ALTER TABLE.|Allowed|Bloccate ed errore di timeout.|  
|Istruzioni DML che funzionano con i dati archiviati nel database, ad esempio UPDATE, DELETE e INSERT.|Allowed|Negate|  
|SELECT|Allowed|Allowed|  
|COMMIT TRANSACTION|Negate*|Negate*|  
|SAVE TRANSACTION|Negate*|Negate*|  
|ROLLBACK|Consentite*|Consentite*|  
  
 \* La transazione viene annullata e gli handle aperti per il contesto di transazione vengono invalidati. L'applicazione deve chiudere tutti gli handle aperti.  
  
## Esempi  
 Gli esempi seguenti illustrano come le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] e l'accesso Win32 FILESTREAM possano creare conflitti.  
  
### A. Apertura di dati BLOB FILESTREAM per l'accesso in scrittura  
 Nell'esempio seguente viene mostrato l'effetto dell'apertura di un file per il solo accesso in scrittura.  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//Write some date to the FILESTREAM BLOB.  
WriteFile(dstHandle, updateData, …);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed. The FILESTREAM BLOB is  
//returned without the modifications that are made by  
//WriteFile(dstHandle, updateData, …).  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed. The FILESTREAM BLOB  
//is returned with the updateData applied.  
```  
  
### B. Apertura di dati BLOB FILESTREAM per l'accesso in lettura  
 Nell'esempio seguente viene mostrato l'effetto dell'apertura di un file per il solo accesso in lettura.  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed. Any changes that are  
//made to the FILESTREAM BLOB will not be returned until  
//the dstHandle is closed.  
//SELECT statements will be allowed.  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### C. Apertura e chiusura di più file BLOB FILESTREAM  
 Se sono aperti più file, viene utilizzata la regola più restrittiva. Nell'esempio seguente vengono aperti due file. Il primo file è aperto in lettura, il secondo in scrittura. Le istruzioni DML rimarranno negate finché non viene aperto il secondo file.  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
  
dstHandle1 =  OpenSqlFilestream(dstFilePath1, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
//Close the read handle. The write handle is still open.  
CloseHandle(dstHandle);  
//DML statements are still denied because the write handle is open.  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
CloseHandle(dstHandle1);  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### D. Chiusura non riuscita di un cursore  
 Nell'esempio seguente viene illustrato come un cursore dell'istruzione non chiuso possa impedire a `OpenSqlFilestream()` di aprire i dati BLOB per l'accesso in scrittura.  
  
```  
TCHAR *sqlDBQuery =  
TEXT("SELECT GET_FILESTREAM_TRANSACTION_CONTEXT(),")  
TEXT("Chart.PathName() FROM Archive.dbo.Records");  
  
//Execute a long-running Transact-SQL statement. Do not allow  
//the statement to complete before trying to  
//open the file.  
  
SQLExecDirect(hstmt, sqlDBQuery, SQL_NTS);  
  
//Before you call OpenSqlFilestream() any open files  
//that the Cursor the Transact-SQL statement is using  
// must be closed. In this example,  
//SQLCloseCursor(hstmt) is not called so that  
//the transaction will indicate that there is a file  
//open for reading. This will cause the call to  
//OpenSqlFilestream() to fail because the file is  
//still open.  
  
HANDLE srcHandle =  OpenSqlFilestream(srcFilePath,  
     Write, 0,  transactionToken,  cbTransactionToken,  0);  
  
//srcHandle will == INVALID_HANDLE_VALUE because the  
//cursor is still open.  
```  
  
## Vedere anche  
 [Accesso ai dati FILESTREAM con OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)   
 [Uso di MARS &#40;Multiple Active Result Set&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)  
  
  