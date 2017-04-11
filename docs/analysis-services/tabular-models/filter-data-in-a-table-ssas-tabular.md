---
title: "Filtrare i dati di una tabella (SSAS tabulare) | Microsoft Docs"
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
f1_keywords: 
  - "sql13.asvs.bidtoolset.notallitemsshowing.f1"
  - "sql13.asvs.bidtoolset.autofiltermenu.f1"
  - "sql13.asvs.bidtoolset.customfilterdb.f1"
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# Filtrare i dati di una tabella (SSAS tabulare)
  È possibile applicare filtri quando si importano dati per controllare le righe caricate in una tabella. Dopo aver importato i dati, non è possibile eliminare righe singole. Tuttavia, è possibile applicare filtri personalizzati per controllare la modalità in cui visualizzare tali righe. Le righe che non soddisfano i criteri di filtro sono nascoste. È possibile filtrare i dati in base a una o più colonne. I filtri sono additivi, pertanto ciascun filtro aggiuntivo è basato sul filtro corrente e consente di ridurre ulteriormente il subset di dati.  
  
> [!NOTE]  
>  La finestra di anteprima del filtro consente di limitare il numero di valori diversi visualizzati. Se il limite viene superato, viene visualizzato un messaggio.  
  
### Per filtrare dati in base ai valori della colonna  
  
1.  In Progettazione modelli selezionare una tabella, quindi fare clic sulla freccia nell'intestazione della colonna in base alla quale filtrare i dati.  
  
2.  Nel menu Filtro automatico effettuare uno dei passaggi seguenti:  
  
    -   Nell'elenco di valori delle colonne selezionare o deselezionare uno o più valori da utilizzare come filtri, quindi fare clic su **OK**.  
  
         Se il numero di valori è estremamente elevato, singoli elementi potrebbero non essere visualizzati nell'elenco. Verrà invece visualizzato il messaggio, "Troppi elementi da visualizzare".  
  
    -   Fare clic su **Filtri per numeri** o su **Filtri per testo** (a seconda del tipo di colonna) e quindi fare clic su uno dei comandi di operatore di confronto (ad esempio **Uguale a**) o su **Filtro personalizzato**. Nella finestra di dialogo **Filtro personalizzato** creare il filtro, quindi fare clic su **OK**.  
  
### Per cancellare un filtro per una colonna  
  
1.  Fare clic sulla freccia nell'intestazione della colonna per la quale si desidera cancellare un filtro.  
  
2.  Fare clic su **Cancella filtro da \<Nome colonna>**.  
  
### Per cancellare tutti i filtri per una tabella  
  
1.  In Progettazione modelli selezionare la tabella per la quale si desidera cancellare i filtri.  
  
2.  Fare clic sul menu **Colonna** , quindi scegliere **Cancella tutti i filtri**.  
  
## Vedere anche  
 [Filtrare e ordinare dati &#40;SSAS tabulare&#41;](../Topic/Filter%20and%20Sort%20Data%20\(SSAS%20Tabular\).md)   
 [Prospettive &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Ruoli &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  