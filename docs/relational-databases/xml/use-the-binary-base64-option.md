---
title: "Utilizzo dell&#39;opzione BINARY BASE64 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "AUTO FOR XML - modalità, opzione BINARY BASE64"
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Utilizzo dell&#39;opzione BINARY BASE64
  Se nella query è specificata l'opzione BINARY BASE64, i dati binari verranno restituiti con la codifica Base64. Per impostazione predefinita, se l'opzione BINARY BASE64 non viene specificata la modalità AUTO supporta la codifica URL dei dati binari, ovvero, al posto dei dati binari viene restituito un riferimento a un URL relativo alla radice virtuale del database in cui è stata eseguita la query. Tale riferimento può essere utilizzato per accedere ai dati binari effettivi nelle operazioni successive, tramite la query SQLXML ISAPI dbobject. La query deve restituire una quantità di informazioni sufficiente per l'identificazione dell'immagine, ad esempio le colonne chiave primarie.  
  
 Quando si specifica una query, se per la colonna di dati binari della vista viene utilizzato un alias, tale alias verrà restituito nella codifica URL dei dati binari. Nelle operazioni successive l'alias non è importante e non sarà possibile utilizzare la codifica URL per recuperare l'immagine. Non utilizzare pertanto gli alias per l'esecuzione di query su una vista utilizzando la modalità AUTO della clausola FOR XML.  
  
 In una query SELECT, il cast di una colonna qualsiasi a una colonna BLOB (Binary Large Object) rende tale query un'entità temporanea, ovvero i relativi nomi di tabella e colonna associati verranno persi. La query in modalità AUTO genererà pertanto un errore in quanto non sarà in grado di determinare la posizione in cui inserire questo valore nella gerarchia XML. Esempio:  
  
```  
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)  
INSERT INTO MyTable VALUES (1, 0x7);  
```  
  
 Questa query genera un errore a causa del cast a un tipo BLOB:  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO;  
```  
  
 Per risolvere il problema, è possibile aggiungere l'opzione BINARY BASE64 alla clausola FOR XML. Se si rimuove il casting, la query darà i risultati previsti:  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO, BINARY BASE64;  
```  
  
 Risultato:  
  
```  
<MyTable Col1="1" Col2="Bw==" />  
```  
  
## Vedere anche  
 [Utilizzo della modalità AUTO con FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)  
  
  