---
title: "Modificare le propriet&#224; in una vista origine dati (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nomi descrittivi [Analysis Services]"
  - "nomi [Analysis Services], viste origine dati"
  - "visualizzazione di tabelle"
  - "visualizzazione di tabelle"
  - "viste origine dati [Analysis Services], tabelle"
  - "tabelle [Analysis Services], viste origine dati"
ms.assetid: 4ccdabea-9c4d-460d-ba78-d23068143696
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# Modificare le propriet&#224; in una vista origine dati (Analysis Services)
  Dopo aver definito una vista origine dati mediante la Creazione guidata vista origine dati e aver aggiunto tabelle, viste, calcoli denominati e query denominate alla vista origine dati, può rivelarsi utile modificare le proprietà relative a:  
  
-   Criteri di corrispondenza della vista origine dati  
  
-   Opzioni avanzate della vista origine dati  
  
-   Nomi degli oggetti  
  
-   Metadati degli oggetti  
  
 È inoltre possibile visualizzare metadati degli oggetti che vengono recuperati dall'origine dei dati e non possono essere modificati.  
  
## Visualizzazione o modifica delle proprietà di una vista origine dati  
 Le proprietà di una vista origine dati diverse dalla relativa descrizione vengono impostate nella Creazione guidata vista origine dati quando viene inizialmente definita la vista origine dati. Nella tabella seguente vengono elencate e descritte le proprietà di una vista origine dati.  
  
> [!NOTE]  
>  Nel riquadro Proprietà vengono mostrate le proprietà per il file con estensione dsv nonché per l'oggetto vista origine dati. Per visualizzare le proprietà dell'oggetto, fare doppio clic su di esso in Esplora soluzioni. Le proprietà verranno aggiornate per riflettere quelle visualizzate nella tabella seguente.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|Origine dati|Specifica l'origine dei dati all'interno della vista origine dati di cui vengono visualizzate le proprietà.|  
|Description|Specifica una descrizione della vista origine dati.|  
|Nome|Specifica il nome della vista origine dati visualizzato in Esplora soluzioni o nel database di Analysis Services. Il nome della vista origine dati può essere modificato in questo contesto o in Esplora soluzioni.|  
|NameMatchingCriteria|Criteri di corrispondenza nomi per l'origine dei dati. Se nella Creazione guidata vista origine dati sono state rilevate relazioni tra chiave primaria e chiave esterna, l'impostazione predefinita è (nessuno). È possibile specificare un valore indipendentemente dall'eventuale impostazione di questa proprietà nella Creazione guidata vista origine dati. Se esistono relazioni di database e si specificano criteri di corrispondenza nomi, entrambi verranno utilizzati per derivare le relazioni tra le tabelle esistenti e le nuove tabelle aggiunte.|  
|RetrieveRelationships|Specifica se vengono recuperate relazioni dal database. Il valore predefinito è True.|  
|SchemaRestriction|Specifica le eventuali restrizioni relative agli schemi recuperati da un'origine dei dati. Per impostazione predefinita, non esistono restrizioni dello schema.|  
  
## Visualizzazione o modifica delle proprietà di DataTable  
 Le proprietà di **DataTable** sono le proprietà di tabelle, viste e query denominate di una vista origine dati. Queste proprietà vengono impostate quando uno di questi oggetti viene aggiunto alla vista origine dati. La tabella seguente elenca e descrive le proprietà degli oggetti **DataTable** di una vista origine dati.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|AllowChangesDuringGeneration|Specifica se la Generazione guidata schema dispone delle autorizzazioni necessarie per sovrascrivere una tabella della vista origine dati durante la rigenerazione. Questa proprietà è disponibile soltanto per tabelle inizialmente generate mediante la Generazione guidata schema. Per altre informazioni, vedere [Informazioni sulla generazione incrementale](../../analysis-services/multidimensional-models/understanding-incremental-generation.md).|  
|DataSource|Specifica l'origine dei dati per l'oggetto. Questa proprietà non è modificabile.|  
|Description|Specifica la descrizione della tabella, della vista o della query denominata. Se per la vista o la tabella di database sottostante è stata archiviata una descrizione come proprietà estesa, verrà visualizzato tale valore. Questa proprietà è modificabile.|  
|FriendlyName|Specifica un nome per la tabella o la vista più facilmente comprensibile per gli utenti o più pertinente per l'area di interesse. Per impostazione predefinita, la proprietà **FriendlyName** di una tabella o una vista corrisponde alla proprietà **Name** della tabella o della vista. La proprietà **FriendlyName** viene usata dagli oggetti di data mining e OLAP durante la definizione dei nomi degli oggetti in base a tabelle o viste. Questa proprietà è modificabile.|  
|Nome|Specifica il nome della vista o della tabella sottostante oppure il nome della query denominata. La proprietà **Name** viene usata dagli oggetti di data mining e OLAP durante la definizione dei nomi degli oggetti in base a query denominate. Questa proprietà è modificabile soltanto per query denominate.|  
|QueryDefinition|Specifica la definizione della query denominata. Questa proprietà è applicabile soltanto a query denominate e non è direttamente modificabile. Per modificare questa proprietà, è necessario modificare la query denominata.|  
|Schema|Specifica lo schema di database applicabile alla tabella, alla vista o alla query denominata. Questa proprietà non è modificabile.|  
|TableType|Specifica il tipo di tabella per la tabella, la vista o la query denominata. Questa proprietà non è modificabile.|  
  
## Visualizzazione o modifica delle proprietà di DataColumn  
 Le proprietà di **DataColumn** sono le proprietà delle colonne di tabelle, viste e query denominate di una vista origine dati. Queste proprietà vengono impostate quando uno di questi oggetti viene aggiunto alla vista origine dati, dalla vista o dalla tabella sottostante, da una query denominata o in base alle definizione di un calcolo denominato. La tabella seguente elenca e descrive le proprietà degli oggetti **DataColumn** di una vista origine dati.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|AllowNull|Specifica la proprietà di supporto di valori Null della colonna in base alla colonna della query denominata, della vista o della tabella sottostante. Questa proprietà non è modificabile.|  
|DataType|Specifica il tipo di dati della colonna in base alla colonna della query denominata, della vista o della tabella sottostante. Questa proprietà non è direttamente modificabile. Se è tuttavia necessario modificare il tipo di dati di una colonna di una tabella o una vista, sostituire la tabella con una query denominata in grado di convertire la colonna nel tipo di dati desiderato.|  
|DateTimeMode|Specifica il formato di serializzazione della data per le colonne **DateTime**. Il valore predefinito è **UnspecifiedLocal**. Questa proprietà è modificabile.|  
|Description|Specifica la descrizione della colonna. Se per la colonna di database sottostante è stata archiviata una descrizione come proprietà estesa, verrà visualizzato tale valore. Questa proprietà è modificabile.|  
|FriendlyName|Specifica un nome per una colonna di una tabella o una vista più facilmente comprensibile per gli utenti o più pertinente per l'area di interesse. Per impostazione predefinita, la proprietà **FriendlyName** di una colonna di una tabella o una vista corrisponde alla proprietà **Name** della colonna. La proprietà **FriendlyName** viene usata dagli oggetti di data mining e OLAP durante la definizione degli attributi in base a colonne di tabelle o viste. Questa proprietà è modificabile.|  
|Length|Specifica la lunghezza massima della colonna, in base ai dati nella colonna della vista o della tabella sottostante.|  
|Nome|Specifica il nome della colonna sottostante oppure il nome del calcolo denominato. La proprietà **Name** viene usata dagli oggetti di data mining e OLAP durante la definizione degli attributi in base a calcoli denominati. Questa proprietà è modificabile soltanto per calcoli denominati.|  
  
## Vedere anche  
 [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Usare diagrammi in Progettazione vista origine dati &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  