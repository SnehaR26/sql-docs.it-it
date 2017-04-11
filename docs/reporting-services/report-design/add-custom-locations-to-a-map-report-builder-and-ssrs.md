---
title: "Aggiungere percorsi personalizzati a una mappa (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE"
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
caps.latest.revision: 10
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 10
---
# Aggiungere percorsi personalizzati a una mappa (Generatore report e SSRS)
  Dopo avere aggiunto una mappa a un report impaginato di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)], è possibile aggiungere percorsi punto personalizzati.  
  
 Le proprietà di visualizzazione per tutti i punti su un livello vengono controllate impostando le opzioni per le proprietà punto per il livello. Per un punto incorporato selezionato, è possibile ignorare le proprietà di visualizzazione.  
  
> [!NOTE]  
>  Quando si ignorano le proprietà di visualizzazione del livello per il punto incorporato, le modifiche apportate non sono reversibili.  
  
 Per altre informazioni, vedere [Variare la visualizzazione di poligoni, linee e punti in base a regole e dati analitici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/vary polygon, line, and point display by rules and analytical data.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Per aggiungere un livello punto  
  
1.  Nell'area di progettazione del report fare clic sulla mappa per selezionarla e visualizzare il riquadro mappa.  
  
2.  Sulla barra degli strumenti fare clic su **Aggiungi livello**.  
  
3.  Nell'elenco a discesa fare clic su **Aggiungi livello punto**. Alla mappa viene aggiunto un livello punto senza alcun punto. Per impostazione predefinita, il livello punto è pronto per i punti incorporati.  
  
## Per aggiungere un punto personalizzato  
  
1.  Nell'area di progettazione del report fare clic sulla mappa per selezionarla e visualizzare il riquadro mappa.  
  
2.  Nel riquadro mappa fare clic con il pulsante destro del mouse su un livello punto con il tipo **Incorporato**, quindi scegliere **Aggiungi punto**. Il cursore passa alla selezione di precisione.  
  
3.  Per aggiungere un punto fare clic su una posizione sulla mappa. Un punto incorporato viene aggiunto al livello selezionato nella posizione scelta.  
  
## Per personalizzare la visualizzazione per un punto incorporato  
  
1.  Fare clic con il pulsante destro del mouse sul punto, quindi scegliere **Proprietà punto**. Viene visualizzata la finestra di dialogo **Proprietà punto incorporato nella mappa**.  
  
2.  Fare clic su **Ignora opzioni punto per questo livello**. Nel riquadro sinistro vengono visualizzate più pagine delle proprietà.  
  
3.  Fare clic sulle pagine e impostare le proprietà di visualizzazione che si desidera applicare a questo punto.  
  
## Vedere anche  
 [Mappe &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/maps-report-builder-and-ssrs.md)   
 [Variare la visualizzazione di poligoni, linee e punti in base a regole e dati analitici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/vary polygon, line, and point display by rules and analytical data.md)  
  
  