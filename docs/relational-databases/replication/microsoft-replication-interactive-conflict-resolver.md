---
title: "Sistema di risoluzione dei conflitti di replica interattivo Microsoft | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.replconflictviewer.interactiveresolver.f1"
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Sistema di risoluzione dei conflitti di replica interattivo Microsoft
  Il sistema di risoluzione dei conflitti interattivo può essere utilizzato per le sottoscrizioni di tipo merge sincronizzate tramite Gestione sincronizzazione Microsoft Windows e consente di visualizzare, confrontare, modificare e selezionare i risultati dei conflitti di dati. È inoltre disponibile il Visualizzatore conflitti, che consente di visualizzare e modificare i risultati dei conflitti dopo il commit. Con il sistema di risoluzione dei conflitti interattivo è possibile selezionare il risultato durante la sincronizzazione.  
  
> [!NOTE]  
>  I conflitti a livello di record logici non vengono visualizzati nel sistema di risoluzione interattivo. Per visualizzare informazioni relative a questi conflitti, utilizzare le stored procedure di replica. Per ulteriori informazioni, vedere [visualizzare informazioni sul conflitto per le pubblicazioni di tipo Merge & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/view conflict information for merge publications.md).  
  
## Opzioni  
 **Nome colonna**  
 Nome di tutte le colonne nella tabella. È possibile che una o più colonne contengano dati in conflitto. Indipendentemente da quali siano le colonne in conflitto, l'intera riga confermata sovrascriverà l'intera riga non confermata.  
  
 **Risoluzione suggerita**  
 Risoluzione suggerita indicata dal sistema di risoluzione dei conflitti per l'articolo.  
  
 **Server di pubblicazione**  
 Il valore di dati nel server di pubblicazione.  
  
 **Sottoscrittore**  
 Il valore di dati nel Sottoscrittore.  
  
 **Accetta soluzione proposta**, **Accetta server di pubblicazione**, e **Accetta Sottoscrittore**  
 Fare clic su questo pulsante per accettare la riga che verrà applicata al server di pubblicazione o al Sottoscrittore, a seconda della riga che prevale nel conflitto. Se la riga del server di pubblicazione non viene confermata, tutti gli altri Sottoscrittori riceveranno la riga confermata durante la successiva sincronizzazione con il server di pubblicazione.  
  
 **Risoluzione automatica conflitti rimanenti**  
 Risolve tutti i conflitti rimanenti utilizzando la risoluzione suggerita indicata dal sistema di risoluzione dei conflitti per l'articolo.  
  
 **Registra informazioni dettagliate sul conflitto per riferimenti futuri**  
 Registra informazioni dettagliate sul conflitto nelle tabelle di sistema.  
  
## Vedere anche  
 [Risoluzione dei conflitti interattiva](../../relational-databases/replication/merge/interactive-conflict-resolution.md)   
 [Visualizzare e risolvere i conflitti di dati per pubblicazioni di tipo Merge & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/view and resolve data conflicts for merge publications.md)   
 [Sincronizzare una sottoscrizione tramite Gestione sincronizzazione Microsoft Windows & #40; Gestione sincronizzazione Microsoft Windows & #41;](../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md)   
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  