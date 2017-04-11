---
title: "Editor trasformazione Ricerca (pagina Generale) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.lookuptransformation.general.f1"
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Editor trasformazione Ricerca (pagina Generale)
  Utilizzare la pagina **Generale** della finestra di dialogo Editor trasformazione Ricerca per selezionare la modalità di cache, selezionare il tipo di connessione e specificare la modalità di gestione delle righe senza voci corrispondenti.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca, vedere [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
## Opzioni  
 **Full Cache**  
 Generare e caricare il set di dati di riferimento nella cache prima dell'esecuzione della trasformazione Ricerca.  
  
 **Partial Cache**  
 Generare il set di dati di riferimento durante l'esecuzione della trasformazione Ricerca. Caricare le righe con le voci corrispondenti nel set di dati di riferimento e le righe senza voci corrispondenti nel set di dati nella cache.  
  
 **No Cache**  
 Generare il set di dati di riferimento durante l'esecuzione della trasformazione Ricerca. Non sono stati caricati dati in cache.  
  
 **gestione connessione della cache**  
 Configurare la trasformazione Ricerca per l'utilizzo della gestione connessione della cache. L'opzione è disponibile solo se è stata selezionata anche l'opzione Full Cache.  
  
 **gestione connessione OLE DB**  
 Configurare la trasformazione Ricerca per l'utilizzo della gestione connessione OLE DB.  
  
 **Specificare come gestire le righe senza voci corrispondenti**  
 Selezionare un'opzione per la gestione delle righe che non dispongono di almeno una voce corrispondente nel set di dati di riferimento.  
  
 Quando si seleziona **Reindirizza righe all'output nessuna corrispondenza**, le righe vengono reindirizzate a un output senza corrispondenze e non vengono gestite come errori. L'opzione **Errore** nella pagina **Output errori** della finestra di dialogo **Editor trasformazione Ricerca** non è disponibile.  
  
 Quando si seleziona un'altra opzione nella casella di riepilogo **Specificare come gestire le righe senza voci corrispondenti** , le righe vengono gestite come errori. L'opzione **Errore** nella pagina **Output errori** è disponibile.  
  
## Risorse esterne  
 Intervento nel blog sulle [modalità cache di ricerca](http://go.microsoft.com/fwlink/?LinkId=219518) su blogs.msdn.com  
  
## Vedere anche  
 [Gestione connessione della cache](../../../integration-services/data-flow/transformations/cache-connection-manager.md)   
 [Editor trasformazione Ricerca &#40;pagina Connessione&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-connection-page.md)   
 [Editor trasformazione Ricerca &#40;pagina Colonne&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-columns-page.md)   
 [Editor trasformazione Ricerca &#40;pagina Avanzate&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-advanced-page.md)   
 [Editor trasformazione Ricerca &#40;pagina Output degli errori&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-error-output-page.md)  
  
  