---
title: "Elemento Column per Index (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "Column - elemento"
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Elemento Column per Index (DTA)
  Specifica le colonne sulle quali viene creato l'indice per una configurazione specificata dall'utente.  
  
## Sintassi  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## Attributi elemento  
  
 **Type**: facoltativo. Specifica il tipo di colonna dell'indice. Usare un tipo di dati **string** per specificare questo attributo con uno dei valori consentiti seguenti:  
  
-   **KeyColumn**  
  
     Specifica che alla colonna viene fatto riferimento mediante una chiave di indice. Per impostare questo attributo, utilizzare la sintassi seguente:  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     Per altre informazioni sulle colonne chiave, vedere [Descrizione di indici cluster e non cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).  
  
-   **IncludedColumn**  
  
     Specifica che la colonna è una colonna inclusa, anziché una colonna chiave. Per impostare questo attributo, utilizzare la sintassi seguente:  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     Per altre informazioni sulle colonne incluse, vedere [Creare indici con colonne incluse](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
 **SortOrder**: facoltativo. Specifica l'ordinamento della colonna. Usare un tipo di dati **string** per specificare un ordinamento **"Ascending"** o **"Descending"** come segue:  
  
```  
<Column SortOrder="Ascending">  
```  
  
## Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuno|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|È possibile specificare un massimo di 1024 colonne per l'elemento **Index**.|  
  
## Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Index &#40;DTA&#41;](../../tools/dta/index-element-dta.md)|  
|**Elementi figlio**|[Elemento Name per Column &#40;DTA&#41;](../../tools/dta/name-element-for-column-dta.md)|  
  
## Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  