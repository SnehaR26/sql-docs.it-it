---
title: "Utilizzare la modalit&#224; PATH con FOR XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PATH FOR XML - modalità"
  - "caratteri [SQL Server], XML"
  - "alias [SQL Server], XML"
  - "clausola FOR XML, modalità PATH"
  - "FOR XML PATH - modalità"
  - "nomi di colonne [SQL Server]"
  - "query XPath [SQL Server]"
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Utilizzare la modalit&#224; PATH con FOR XML
  Come descritto nell'argomento [Costruzione di codice XML tramite la clausola FOR XML](../../relational-databases/xml/for-xml-sql-server.md), la modalità PATH consente di combinare in modo più semplice elementi e attributi. e di introdurre nidificazione aggiuntiva per la rappresentazione di proprietà complesse. È possibile utilizzare query in modalità FOR XML EXPLICIT per la costruzione di questo tipo di strutture XML da un set di righe, ma la modalità PATH costituisce un'alternativa più semplice alla formulazione di query in modalità EXPLICIT, che può essere un'operazione complessa. La modalità PATH, insieme alla possibilità di scrivere query FOR XML annidate e alla direttiva TYPE per restituire istanze di tipo **xml**, consente di formulare più facilmente le query.  
  
 In modalità PATH i nomi e gli alias di colonna vengono gestiti come espressioni XPath. Queste espressioni indicano il modo in cui viene eseguito il mapping tra i valori e il codice XML. Ogni espressione XPath è un XPath relativo che specifica il tipo dell'elemento, ad esempio attributo, elemento e valore scalare, nonché il nome e la gerarchia del nodo che verrà generato in relazione all'elemento riga.  
  
 In questa sezione viene descritto il mapping delle colonne in un set di righe in varie condizioni e vengono forniti alcuni esempi.  
  
## Argomenti della sezione  
  
-   [Colonne senza nome](../../relational-databases/xml/columns-without-a-name.md)  
  
-   [Colonne provviste di un nome](../../relational-databases/xml/columns-with-a-name.md)  
  
-   [Colonne con nome specificato come carattere jolly](../../relational-databases/xml/columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [Colonne con il nome di un test di nodo XPath](../../relational-databases/xml/columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [Nomi di colonna con il percorso specificato come data&#40;&#41;](../../relational-databases/xml/column-names-with-the-path-specified-as-data.md)  
  
-   [Colonne contenenti un valore NULL per impostazione predefinita](../../relational-databases/xml/columns-that-contain-a-null-value-by-default.md)  
  
-   [Supporto dello spazio dei nomi in modalità di PATH](../../relational-databases/xml/namespace-support-in-path-mode.md)  
  
-   [Esempi di utilizzo della modalità PATH](../../relational-databases/xml/examples-using-path-mode.md)  
  
## Vedere anche  
 [Aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML &#40;SQL Server&#41;](../../relational-databases/xml/for-xml-sql-server.md)  
  
  