---
title: "Dati nei flussi di dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conversione di tipi di dati [Integration Services]"
  - "confronto di dati"
  - "tipi di dati [Integration Services], flusso di dati"
  - "analisi [Integration Services]"
  - "confronti di stringhe"
  - "flusso di dati [Integration Services], opzioni relative ai dati"
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Dati nei flussi di dati
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è disponibile un set di tipi di dati che è possibile usare nei flussi di dati.  
  
## Conversione tipo di dati  
 L'origine aggiunta a un flusso di dati converte i dati di origine nei tipi di dati di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Le trasformazioni successive possono convertire i dati in tipi di dati di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] diversi e, a seconda del tipo di archivio dati in cui vengono caricati i dati, le destinazioni possono convertire il tipo di dati finale di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel tipo di dati richiesto dall'archivio dati di destinazione. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Per essere convertivi nei tipi di dati di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], i dati vengono analizzati da un componente del flusso di dati. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono disponibili due tipi di analisi dei dati: analisi veloce e analisi standard. La maggior parte dei componenti dei flussi di dati è in grado di eseguire solo l'analisi standard. L'origine file flat e la trasformazione Conversione dati sono tuttavia in grado di utilizzare sia l'analisi veloce che l'analisi standard. Per altre informazioni, vedere [Analisi dei dati](../../integration-services/data-flow/parsing-data.md).  
  
## Conversione dei tipi di dati  
 Molte trasformazioni confrontano i valori dei dati. La trasformazione Aggregazione, ad esempio, confronta i valori al fine di eseguirne l'aggregazione su un set di righe di dati, la trasformazione Ordinamento confronta i valori allo scopo di ordinarli e la trasformazione Ricerca confronta i valori con quelli contenuti in una tabella di riferimento separata. Per specificare la modalità di confronto delle stringhe, la trasformazione include un set di opzioni di confronto che consentono ad esempio di ignorare la distinzione tra maiuscole e minuscole, gestire i caratteri Katakana e Hiragana nel testo giapponese e ignorare i caratteri spazio nelle stringhe. Per altre informazioni, vedere [Comparing String Data](../../integration-services/data-flow/comparing-string-data.md).  
  
 Anche l'analizzatore di espressioni confronta i valori dei dati durante la valutazione delle espressioni utilizzate da variabili, vincoli di precedenza e trasformazioni.  
  
## Risoluzione dei problemi del flusso di dati  
 Dopo avere distribuito un pacchetto nel catalogo [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è possibile analizzare il flusso di dati nel pacchetto durante l'esecuzione per verificarne le prestazioni o per verificare la presenza di altri problemi. Sono disponibili alcuni report standard che consentono di visualizzare lo stato e la cronologia dei pacchetti ed è possibile eseguire una query sulle viste del database per ottenere informazioni dettagliate sull'esecuzione dei pacchetti. È inoltre possibile aggiungere e rimuovere dinamicamente i data tap durante l'esecuzione per individuare specifici componenti del pacchetto. Per altre informazioni, vedere [Analisi del flusso di dati](../../integration-services/performance/analysis-of-data-flow.md).  
  
  