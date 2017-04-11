---
title: "Set di righe dello schema di data mining (SSAS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "set di righe dello schema [Analysis Services], data mining"
  - "data mining [Analysis Services], query"
  - "contenuto di modelli di data mining"
  - "data mining [Analysis Services], set di righe dello schema"
  - "set di righe dello schema [Analysis Services], recupero"
  - "data mining [Analysis Services], risoluzione dei problemi"
ms.assetid: 442d8c29-07c7-45de-9a15-d556059f68d7
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 14
---
# Set di righe dello schema di data mining (SSAS)
  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] molti dei set di righe esistenti dello schema di data mining OLE DB sono esposti come set di tabelle di sistema su cui è possibile eseguire query tramite istruzioni DMX (Data Mining Extensions). Mediante la creazione di query sul set di righe dello schema di data mining, è possibile identificare i servizi disponibili, ottenere aggiornamenti sullo stato dei modelli e delle strutture e trovare dettagli sul contenuto del modello o sui parametri. Per una descrizione dei set di righe dello schema di data mining, vedere [Data Mining Schema Rowsets](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md).  
  
> [!NOTE]  
>  È anche possibile eseguire una query sul set di righe dello schema di data mining utilizzando l'analisi XMLA. Per altre informazioni sull'esecuzione di questa operazione in SQL Server Management Studio, vedere [Creare una query di data mining utilizzando XMLA](../../analysis-services/data-mining/create-a-data-mining-query-by-using-xmla.md).  
  
## Elenco di set di righe dello schema di data mining  
 Nella tabella seguente sono elencati i set di righe dello schema di data mining che possono essere utili per l'esecuzione delle query e il monitoraggio.  
  
|Nome del set di righe|Description|  
|-----------------|-----------------|  
|DMSCHEMA_MINING_MODELS|Elenca tutti i modelli di data mining nel contesto corrente.<br /><br /> Include informazioni quali la data di creazione, i parametri utilizzati per creare il modello e la dimensione del set di training.|  
|DMSCHEMA_MINING_COLUMNS|Elenca tutte le colonne utilizzate nei modelli di data mining nel contesto corrente.<br /><br /> Le informazioni specificano il mapping a una colonna di origine della struttura di data mining, il tipo di dati, la precisione e le funzioni di stima che possono essere utilizzate con la colonna.|  
|DMSCHEMA_MINING_STRUCTURES|Elenca tutte le strutture di data mining nel contesto corrente.<br /><br /> Le informazioni specificano se la struttura viene popolata, la data dell'ultima elaborazione della struttura e la definizione del set di dati di controllo per la struttura, se disponibile.|  
|DMSCHEMA_MINING_STRUCTURE_COLUMNS|Elenca tutte le colonne utilizzate nelle strutture di data mining nel contesto corrente.<br /><br /> Le informazioni specificano il tipo di contenuto e il tipo di dati, l'eventuale supporto dei valori Null e la presenza o meno di dati di tabella nidificati nella colonna.|  
|DMSCHEMA_MINING_SERVICES|Elenca tutti i servizi di data mining, o algoritmi, disponibili sul server specificato.<br /><br /> Le informazioni specificano i flag di modellazione supportati, i tipi di input e i tipi di origine dati supportati.|  
|DMSCHEMA_MINING_SERVICE_PARAMETERS|Elenca tutti i parametri per i servizi di data mining disponibili nell'istanza corrente.<br /><br /> Le informazioni includono il tipo di dati per ogni parametro, i valori predefiniti e i limiti superiore e inferiore.|  
|DMSCHEMA_MODEL_CONTENT|Restituisce il contenuto del modello se il modello è stato elaborato.<br /><br /> Per altre informazioni, vedere [Contenuto del modello di data mining &#40;Analysis Services - Data Mining&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).|  
|DBSCHEMA_CATALOGS|Elenca tutti i database (cataloghi) nell'istanza corrente di Analysis Services.|  
|MDSCHEMA_INPUT_DATASOURCES|Elenca tutte le origini dati nell'istanza corrente di Analysis Services.|  
  
> [!NOTE]  
>  L'elenco nella tabella non è completo in quanto contiene solo i set di righe che possono essere utili per la risoluzione dei problemi.  
  
## Esempi  
 Nella sezione seguente sono riportati alcuni esempi di query sui set di righe dello schema di data mining.  
  
### Esempio 1: Elenco di servizi di data mining  
 Nella query seguente viene restituito un elenco di servizi di data mining disponibili sul server corrente, che indica gli algoritmi abilitati. Le colonne specificate per ogni servizio di data mining includono i flag di modellazione e i tipi di contenuto che possono essere utilizzati con ogni algoritmo, il GUID di ogni servizio e gli eventuali limiti di stima che potrebbero essere stati specificati per ogni servizio.  
  
```  
SELECT *  
FROM $system.DMSCHEMA_MINING_SERVICES  
```  
  
### Esempio 2: Elenco di parametri del modello di data mining  
 Nell'esempio seguente vengono restituiti i parametri utilizzati per creare uno specifico modello di data mining:  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
### Esempio 3: Elenco di tutti i set di righe  
 Nell'esempio seguente viene restituito un elenco completo di set di righe disponibili nel server corrente:  
  
```  
SELECT *   
FROM $system.DBSCHEMA_TABLES  
```  
  
  