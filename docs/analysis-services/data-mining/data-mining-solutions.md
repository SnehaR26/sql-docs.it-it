---
title: "Soluzioni di data mining | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data mining [Analysis Services], informazioni sul data mining"
  - "data mining [Analysis Services], sviluppo"
ms.assetid: 84f6548d-ebb0-4e10-9b29-66253fa0a04a
caps.latest.revision: 64
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 64
---
# Soluzioni di data mining
  Una soluzione di data mining è una soluzione di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che contiene uno o più progetti di data mining.  
  
 Negli argomenti di questa sezione vengono fornite informazioni sulla progettazione e l'implementazione di una soluzione di data mining integrata utilizzando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per una panoramica sul processo di progettazione dei modelli di data mining e sugli strumenti correlati, vedere [Concetti di data mining](../../analysis-services/data-mining/data-mining-concepts.md).  
  
 Per altre informazioni su ulteriori tipi di progetti utili per il data mining, vedere [Progetti correlati per soluzioni di data mining](../../analysis-services/data-mining/related-projects-for-data-mining-solutions.md).  
  
 [Modelli di data mining relazionali e multidimensionali](#bkmk_RelMD)  
  
 [Distribuzione di soluzioni di data mining](#bkmk_Deploy)  
  
 [Procedure dettagliate sulla soluzione](#bkmk_Walkthru)  
  
##  <a name="bkmk_RelMD"></a> Modelli di data mining relazionali e multidimensionali  
 Una soluzione di data mining può essere basata su dati multidimensionali, ovvero un cubo esistente, o su dati puramente relazionali, ad esempio tabelle e viste in un data warehouse, o su file di testo, cartelle di lavoro di Excel o altre origini dati esterne.  
  
-   È possibile creare oggetti di data mining all'interno di una soluzione di database multidimensionale esistente.  
  
     In genere una soluzione come questa verrebbe creata se è già stato creato un cubo e si desidera eseguire il data mining utilizzando il cubo come origine dati. Quando si sposta e si esegue il backup dei modelli in base a un cubo, è necessario spostare o copiare anche il cubo.  
  
-   È possibile creare una soluzione di data mining che contiene solo oggetti di data mining, incluse le origini dati e le viste origine dati di supporto, e che utilizza solo origini dati relazionali.  
  
     Si tratta del metodo preferito per la creazione di modelli di data mining, in quanto l'elaborazione e l'esecuzione di query è generalmente più veloce rispetto alle origini dati relazionali. È inoltre facile spostare ed eseguire il backup dei modelli tra i server tramite i comandi EXPORT e IMPORT.  
  
##  <a name="bkmk_Deploy"></a> Distribuzione di soluzioni di data mining  
 L'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a cui si distribuisce la soluzione deve essere in esecuzione in una modalità che supporta oggetti multidimensionali e oggetti di data mining; non è infatti possibile distribuire oggetti di data mining a un'istanza che ospita modelli tabulari o dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 Pertanto, quando si crea una soluzione di data mining in Visual Studio, assicurarsi di utilizzare il modello **Progetto multidimensionale e di data mining di Analysis Services**.  
  
 Quando si distribuisce la soluzione, gli oggetti utilizzati per il data mining vengono creati nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] specificata, in un database con lo stesso nome del file della soluzione.  
  
 Per altre informazioni sulla modalità di distribuzione delle soluzioni relazionali e multidimensionali, vedere [Distribuzione di soluzioni di data mining](../../analysis-services/data-mining/deployment-of-data-mining-solutions.md).  
  
##  <a name="bkmk_Walkthru"></a> Procedura dettagliata sulla soluzione  
 Vengono forniti cenni preliminari relativi alla creazione di soluzioni di data mining tramite Creazione guidata modello di data mining.  
  
 [Creare una struttura di data mining relazionale](../../analysis-services/data-mining/create-a-relational-mining-structure.md)  
 Creare una struttura di data mining da dati relazionali, file di testo e altre origini che è possibile combinare in una vista origine dati.  
  
 [Create an OLAP Mining Structure](../../analysis-services/data-mining/create-an-olap-mining-structure.md)  
 Creare una struttura di data mining basata sui dati di un cubo OLAP. È possibile salvare i modelli creati dai dati OLAP come dimensione di data mining oppure salvare il set di dati e i modelli come nuovo cubo.  
  
## Contenuto della sezione  
 [Progetti di data mining](../../analysis-services/data-mining/data-mining-projects.md)  
  
 [Elaborazione di oggetti di data mining](../../analysis-services/data-mining/processing-data-mining-objects.md)  
  
 [Progetti correlati per soluzioni di data mining](../../analysis-services/data-mining/related-projects-for-data-mining-solutions.md)  
  
 [Distribuzione di soluzioni di data mining](../../analysis-services/data-mining/deployment-of-data-mining-solutions.md)  
  
## Attività e argomenti correlati  
 Dopo avere creato una soluzione di data mining di base, che include origini dati e una struttura di data mining, è possibile ampliarla aggiungendo nuovi modelli, eseguendo test e confrontando i modelli, creando stime e sperimentando l'utilizzo di subset di dati.  
  
 Per ulteriori informazioni, vedere i seguenti collegamenti:  
  
|Attività|Argomento|  
|-----------|------------|  
|Eseguire test sui modelli creati, convalidare la qualità dei dati di training e creare grafici che rappresentano l'accuratezza dei modelli di data mining.|[Test e convalida &#40;Data mining&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)|  
|Eseguire il training del modello popolando la struttura e i modelli correlati con i dati. Aggiornare ed estendere i modelli con nuovi dati.|[Elaborazione di oggetti di data mining](../../analysis-services/data-mining/processing-data-mining-objects.md)|  
|Personalizzare un modello di data mining applicando filtri ai dati di training, scegliendo un algoritmo diverso o impostando parametri avanzati dell'algoritmo.|[Personalizzare struttura e modelli di data mining](../../analysis-services/data-mining/customize-mining-models-and-structure.md)|  
|Personalizzare un modello di data mining applicando filtri ai dati utilizzati per il training del modello.|[Aggiungere modelli di data mining a una struttura &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|Aggiornare e gestire soluzioni di data mining.|Collegamento|  
  
## Vedere anche  
 [Esercitazioni sul data mining &#40;Analysis Services&#41;](../../analysis-services/data-mining-tutorials-analysis-services.md)  
  
  