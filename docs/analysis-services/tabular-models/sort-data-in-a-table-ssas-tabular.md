---
title: "Ordinare i dati di una tabella (SSAS tabulare) | Microsoft Docs"
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
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Ordinare i dati di una tabella (SSAS tabulare)
  È possibile ordinare i dati per testo (da A a Z o da Z ad A) e numeri (dal più piccolo al più grande o dal più grande al più piccolo) in una o più colonne.  
  
### Per ordinare i dati in una tabella basata su una colonna di testo  
  
1.  In Progettazione modelli selezionare una colonna di dati alfanumerici, un intervallo di celle in una colonna oppure assicurarsi che la cella attiva si trovi in una colonna di una tabella contenente dati alfanumerici, quindi fare clic sulla freccia nell'intestazione della colonna in base alla quale filtrare i dati.  
  
2.  Nel menu Filtro automatico effettuare uno dei passaggi seguenti:  
  
    -   Per ordinare in ordine alfanumerico crescente, fare clic su **Ordina da A a Z**.  
  
    -   Per ordinare in ordine alfanumerico decrescente, fare clic su **Ordina da Z a A**.  
  
    > [!NOTE]  
    >  In alcuni casi, dati importati da un'altra applicazione potrebbero presentare spazi iniziali inseriti prima dei dati stessi. È necessario rimuovere gli spazi iniziali per ordinare correttamente i dati.  
  
### Per ordinare i dati in una tabella basata su una colonna numerica  
  
1.  In Progettazione modelli selezionare una colonna di dati alfanumerici, un intervallo di celle in una colonna oppure assicurarsi che la cella attiva si trovi in una colonna di una tabella contenente dati alfanumerici, quindi fare clic sulla freccia nell'intestazione della colonna in base alla quale filtrare i dati.  
  
2.  Nel menu Filtro automatico effettuare uno dei passaggi seguenti:  
  
    -   Per l'ordinamento ascendente fare clic su **Ordina dal più piccolo al più grande**.  
  
    -   Per l'ordinamento discendente fare clic su **Ordina dal più grande al più piccolo**.  
  
    > [!NOTE]  
    >  Se i risultati non sono quelli previsti, la colonna potrebbe contenere numeri archiviati come testo e non come numeri. Ad esempio numeri negativi importati da alcuni sistemi di contabilità o un numero immesso con carattere apostrofo (') iniziale, vengono archiviati come testo.  
  
## Vedere anche  
 [Filtrare e ordinare dati &#40;SSAS tabulare&#41;](../Topic/Filter%20and%20Sort%20Data%20\(SSAS%20Tabular\).md)   
 [Prospettive &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Ruoli &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  