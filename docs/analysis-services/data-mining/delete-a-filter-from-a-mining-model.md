---
title: "Eliminare un filtro da un modello di data mining | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtri [Analysis Services]"
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 13
---
# Eliminare un filtro da un modello di data mining
  Quando si crea un filtro in un modello di data mining, è possibile creare modelli in un subset dei dati nella vista origine dati. I filtri sono anche utili per il test dell'accuratezza del modello su un subset dei dati originali.  
  
 Tuttavia, è necessario eliminare il filtro se si desidera visualizzare nuovamente il set completo dei case. In questa procedura viene descritto come rimuovere le condizioni su un filtro o eliminare completamente il filtro.  
  
### Per eliminare una condizione da un filtro su un modello di data mining  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Esplora soluzioni, fare clic sulla struttura di data mining che contiene il modello di data mining da filtrare.  
  
2.  Fare clic sulla scheda **Modelli di data mining** .  
  
3.  Selezionare il modello, quindi fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida.  
  
     -oppure-  
  
     Selezionare il modello. Scegliere **Imposta filtro modello** dal menu **Modello di data mining**.  
  
4.  Nella finestra di dialogo **Filtro modello** fare clic con il pulsante destro del mouse sulla riga della griglia che contiene la condizione da eliminare.  
  
5.  Selezionare **Elimina**.  
  
### Per cancellare il filtro su un modello di data mining nella finestra di dialogo Editor filtri  
  
-   Nella finestra di dialogo **Editor filtri** fare clic con il pulsante destro del mouse su una riga della griglia e quindi scegliere **Elimina tutto**.  
  
## Utilizzo dei filtri di modelli con la finestra Proprietà  
 Se si desidera eliminare l'intero filtro, non è necessario aprire le finestre di dialogo Editor filtri. Le condizioni di filtro create sono disponibili nella proprietà **Filter** del modello di data mining.  
  
> [!NOTE]  
>  È possibile visualizzare le proprietà di un modello di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ma non in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Per cancellare il filtro su un modello di data mining in Esplora soluzioni  
  
1.  In Esplora soluzioni fare clic sul modello di data mining che contiene il filtro.  
  
2.  Nella finestra **Proprietà** fare clic con il pulsante destro del mouse sul testo del filtro nella proprietà **Filter** e quindi scegliere **Seleziona tutto**.  
  
3.  Premere il tasto BACKSPACE o CANC.  
  
## Vedere anche  
 [Eseguire il drill-through sui dati del case da un modello di data mining](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)   
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Filtri per i modelli di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  