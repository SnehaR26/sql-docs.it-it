---
title: Visualizzare la Formula per una serie temporale (Data Mining) modello | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c9225b2eb95d267c78caaf7521a8dee0b436db08
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164001"
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a>Visualizzare la formula per un modello Time Series (Data Mining)
  Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] inData Visualizzatore Time Series progettazione Data Mining fornisce il modo più semplice per visualizzare i dettagli dell'equazione di regressione utilizzata in un modello time series.  
  
 È possibile estrarre la formula di regressione per un modello Time Series eseguendo una query sul contenuto del modello. Tuttavia, per visualizzare la formula ARTXP o ARIMA completa, è consigliabile usare la **legenda Data Mining** del [visualizzatore Microsoft Time Series](browse-a-model-using-the-microsoft-time-series-viewer.md), che consente di elencare tutte le costanti in un formato leggibile.  
  
 Se si crea un modello misto, le analisi ARIMA e ARTXP vengono create in alberi separati e unite in join al nodo radice che rappresenta il modello. Le strutture degli alberi ARIMA e ARTXP sono molto diverse. Ad esempio, l'albero ARTXP è di fatto un albero, come un albero delle decisioni, mentre l'albero ARIMA rappresenta una serie di medie mobili. Pertanto, anche se le due rappresentazioni vengono presentate per praticità in un solo modello, devono essere considerate come due modelli indipendenti. Anche le equazioni sono completamente diverse e non possono essere combinate né confrontate.  
  
 È anche possibile visualizzare i modelli time series utilizzando la [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md). Per altre informazioni sul contenuto di un modello time series, vedere [contenuto del modello di Data Mining per i modelli Time Series &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a>Per visualizzare la formula di regressione ARTXP per un modello Time Series  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]selezionare il modello Time Series da visualizzare e fare clic su **Sfoglia**.  
  
     -oppure-  
  
     In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]selezionare il modello Time Series e fare clic sulla scheda **Visualizzatore modello di data mining** .  
  
2.  Fare clic sulla scheda **Modello** .  
  
3.  Se il modello contiene più alberi, selezionare un solo albero nell'elenco a discesa **Albero** .  
  
    > [!NOTE]  
    >  In presenza di più serie di dati un modello presenta sempre più alberi. Tuttavia, il numero di alberi visualizzati nel **Visualizzatore Time Series** non sarà uguale a quello degli alberi visualizzati in [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md), in quanto nel primo caso le informazioni ARIMA e ARTXP di ogni serie di dati vengono combinate in una sola rappresentazione.  
  
4.  Fare clic su un nodo foglia dell'albero.  
  
     I nodi identificati come **Serie di dati** sono sempre nodi foglia e possono contenere un'equazione. Se un nodo **(Tutto)** non presenta nodi figlio, può contenere anch'esso un'equazione.  
  
5.  Se **Legenda data mining** non è disponibile, fare clic con il pulsante destro del mouse sul nodo e scegliere **Mostra legenda**.  
  
     La formula ARTXP viene visualizzata nella prima metà di **Legenda data mining**come **Equazione nodo dell'albero**.  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a>Per visualizzare la formula ARIMA per un modello Time Series  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]selezionare il modello Time Series da visualizzare e fare clic su **Sfoglia**.  
  
     -oppure-  
  
     In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]selezionare il modello Time Series e fare clic sulla scheda **Visualizzatore modello di data mining** .  
  
2.  Fare clic sulla scheda **Modello** .  
  
3.  Se il modello contiene più alberi, selezionare un solo albero nell'elenco a discesa **Albero** .  
  
    > [!NOTE]  
    >  Se vengono incluse più serie di dati, il modello presenta sempre più alberi.  
  
4.  Fare clic su un nodo dell'albero.  
  
     La formula ARIMA viene visualizzata nella seconda metà di **Legenda data mining**come **Equazione ARIMA**.  
  
5.  Se **Legenda data mining** non è disponibile, fare clic con il pulsante destro del mouse sul nodo e scegliere **Mostra legenda**.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività del Visualizzatore modelli e procedure dettagliate di data mining](mining-model-viewer-tasks-and-how-tos.md)   
 [Visualizzare un modello usando il visualizzatore Microsoft Time Series](browse-a-model-using-the-microsoft-time-series-viewer.md)   
 [Esempi di query sui modelli Time Series](time-series-model-query-examples.md)  
  
  
