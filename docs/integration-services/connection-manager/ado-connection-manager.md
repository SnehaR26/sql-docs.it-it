---
title: "Gestione connessione ADO | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connessioni [Integration Services], ADO"
  - "gestioni connessioni [Integration Services], ADO"
  - "gestioni connessioni ADO [Integration Services]"
ms.assetid: 490418bc-5ef1-41b8-a9c8-de38aa96e0f6
caps.latest.revision: 54
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 54
---
# Gestione connessione ADO
  Una gestione connessione ADO consente la connessione di un pacchetto a oggetti ADO (ActiveX Data Objects), ad esempio un recordset. Questa gestione connessione viene in genere usata nelle attività personalizzate create con versioni precedenti di un linguaggio, ad esempio Microsoft Visual Basic 6.0, o in attività personalizzate che fanno parte di un'applicazione esistente che usa ADO per connettersi a un'origine dei dati.  
  
 Quando si aggiunge una gestione connessione ADO a un pacchetto, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene creata una gestione connessione che in fase di esecuzione verrà risolta in una connessione ADO, vengono impostate le proprietà della gestione connessione, dopodiché la gestione connessione viene aggiunta alla raccolta **Connections** del pacchetto. La proprietà **ConnectionManagerType** della gestione connessione viene impostata su **ADO**.  
  
## Risoluzione dei problemi relativi alla gestione connessione ADO  
 Durante la lettura da parte di una gestione connessione ADO, alcuni tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relativi alle date genereranno i risultati mostrati nella tabella seguente.  
  
|Tipo di dati di SQL Server|Risultato|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|L'esecuzione del pacchetto non viene completata correttamente, a meno che non vengano utilizzati comandi SQL con parametri. È necessario servirsi dell'attività Esegui SQL nel pacchetto per utilizzare i comandi SQL con parametri. Per altre informazioni, vedere [Attività Esegui SQL](../../integration-services/control-flow/execute-sql-task.md) e [Parametri e codici restituiti nell'attività Esegui SQL](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md).|  
|**datetime2**|La gestione connessione ADO tronca il valore relativo ai millisecondi.|  
  
> [!NOTE]  
>  Per altre informazioni sui tipi di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e sul relativo mapping nei tipi di dati [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vedere [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md) e [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Configurazione della gestione connessione ADO  
 Per configurare una gestione connessione ADO, procedere nel modo seguente:  
  
-   Specificare una stringa di connessione configurata in modo da soddisfare i requisiti del provider selezionato.  
  
-   Se richiesto dal provider, includere il nome dell'origine dei dati a cui connettersi.  
  
-   Specificare le credenziali di sicurezza come previsto dal provider selezionato.  
  
-   Indicare se la connessione creata dalla gestione connessione deve essere mantenuta in fase di esecuzione.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Configura gestione connessione OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## Vedere anche  
 [Connessioni in Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  