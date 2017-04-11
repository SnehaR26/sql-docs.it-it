---
title: "Visualizzazione delle intestazioni durante lo scorrimento di un report (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
caps.latest.revision: 10
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 10
---
# Visualizzazione delle intestazioni durante lo scorrimento di un report (Generatore report e SSRS)
  Per evitare che le etichette di riga e di colonna scorrano oltre l'area di visualizzazione dopo il rendering di un report, è possibile bloccare le intestazioni di riga o di colonna.  
  
 La modalità di controllo delle righe e delle colonne varia a seconda che si tratta di una tabella o di una matrice. Se si dispone di una tabella, configurare i membri statici (intestazioni di riga e di colonna) in modo che rimangano visibili. Se si dispone di una matrice, configurare le intestazioni di gruppi di riga e di colonna in modo che rimangano visibili.  
  
 Se si esporta il report in Excel, l'intestazione non verrà bloccata automaticamente. È possibile bloccare il riquadro in Excel. Per altre informazioni vedere la sezione **Intestazioni di pagina e piè di pagina** di [Esportazione in Microsoft Excel &#40;Generatore report e SSRS&#41;](../../reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Anche se una tabella include gruppi di righe e colonne, non è possibile mantenere visibili le intestazioni di gruppo durante lo scorrimento  
  
 Nell'immagine seguente viene illustrata una tabella.  
  
 ![Tabella](../../reporting-services/report-design/media/table.png "Tabella")  
  
 Nell'immagine seguente viene illustrata una matrice.  
  
 ![Matrice](../../reporting-services/report-design/media/matrix.png "Matrice")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Per mantenere visibili le intestazioni di gruppo di matrice durante lo scorrimento  
  
1.  Fare clic con il pulsante destro del mouse sulla riga o sulla colonna oppure sull'handle d'angolo di un'area dati Tablix, quindi scegliere **Proprietà Tablix**.  
  
2.  Nella scheda **Generale** sotto **Intestazioni riga** o **Intestazioni colonna**selezionare **Mantieni intestazione visibile durante lo scorrimento**.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Per mantenere visibile un membro Tablix statico (riga o colonna) durante lo scorrimento  
  
1.  Nell'area di progettazione fare clic in un punto qualsiasi della tabella per visualizzare i membri statici e i gruppi, nel riquadro di raggruppamento.  
  
     ![riquadro di raggruppamento](../../reporting-services/report-design/media/grouppane-updated.png "riquadro di raggruppamento")  
  
     Nel riquadro Gruppi di righe vengono visualizzati i membri statici e dinamici gerarchici per la gerarchia di gruppi di righe, mentre nel riquadro Gruppi di colonne è riportata una visualizzazione simile per la gerarchia di gruppi di colonne.  
  
2.  Sul lato destro del riquadro di raggruppamento fare clic sulla freccia rivolta verso il basso, quindi fare clic su **Modalità avanzata**.  
  
3.  Fare clic sul membro statico (riga o colonna) che si desidera mantenere visibile durante lo scorrimento. Nel riquadro Proprietà verranno visualizzate le proprietà dei membri Tablix **** .  
  
     ![Proprietà del membro Tablix](../../reporting-services/report-design/media/grouppane-tablixmember-updated.png "Proprietà del membro Tablix")  
  
4.  Nel riquadro Proprietà impostare **FixedData** su **True**.  
  
5.  Ripetere questo passaggio per tutti i membri adiacenti che si desidera mantenere visibili durante lo scorrimento.  
  
6.  Visualizzare l'anteprima del report.  
  
 Durante lo scorrimento verticale o orizzontale del report, i membri Tablix statici resteranno visibili.  
  
## Vedere anche  
 [Area dati Tablix &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Ricerca, visualizzazione e gestione dei report &#40;Generatore report SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Esportare report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [Visualizzare intestazioni e piè di pagina con un gruppo &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)   
 [Visualizzare le intestazioni di riga e colonna in più pagine &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)   
 [Riquadro di raggruppamento &#40;Generatore report&#41;](../../reporting-services/report-design/grouping-pane-report-builder.md)  
  
  