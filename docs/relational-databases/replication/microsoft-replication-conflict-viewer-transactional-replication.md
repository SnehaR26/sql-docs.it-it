---
title: "Visualizzatore conflitti di replica Microsoft (replica transazionale) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.replconflictviewer.cvqueued.f1"
ms.assetid: eec59d8e-cadb-4623-a31f-9f42ec09c97f
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Visualizzatore conflitti di replica Microsoft (replica transazionale)
  Il Visualizzatore conflitti di replica consente di visualizzare conflitti che si sono verificati durante la sincronizzazione per la replica transazionale peer-to-peer e la replica transazionale con sottoscrizioni ad aggiornamento in coda. Per ulteriori informazioni, vedere [Visualizza conflitti di dati per le pubblicazioni transazionali e 40 #; SQL Server Management Studio & #41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md).  
  
> [!NOTE]  
>  Il Visualizzatore conflitti di replica consente di visualizzare i conflitti che si verificano nella replica di tipo merge e nella replica transazionale. Per la replica transazionale, è possibile utilizzare il Visualizzatore conflitti di replica per visualizzare i dati in conflitto, ma non è possibile scegliere una diversa risoluzione del conflitto.  
  
## Opzioni  
 Il Visualizzatore conflitti di replica è suddiviso in due sezioni. Nella sezione superiore della finestra di dialogo vengono elencati i conflitti relativi alla tabella selezionata. Quando si fa clic su un elemento incluso nell'elenco dei conflitti, nella sezione inferiore della finestra di dialogo vengono visualizzati i dettagli del conflitto.  
  
 I dati dei conflitti nella sezione inferiore vengono visualizzati in due colonne corrispondenti (**prioritaria** e **perdente**). Se il conflitto si verifica tra dati aggiornati e dati eliminati, questi ultimi potrebbero non venire visualizzati. In questo caso, in una delle due colonne verrà visualizzato un messaggio per segnalare che la riga è stata eliminata in una posizione e aggiornata nell'altra. Verrà inoltre indicata la risoluzione suggerita.  
  
 **Database**  
 Consente di scegliere un database contenente pubblicazioni con conflitti.  
  
 **Pubblicazione**  
 Consente di scegliere una pubblicazione contenente tabelle con conflitti.  
  
 **Tabella**  
 Consente di scegliere una tabella contenente conflitti.  
  
 **Definisci filtro**  
 Fare clic per aprire la **definire filtri** la finestra di dialogo.  
  
 **Applica o rimuovi filtro**  
 Fare clic per applicare o rimuovere un filtro che è stato definito nel **Definisci filtri** la finestra di dialogo.  
  
 **Seleziona tutto**  
 Fare clic su questo pulsante per selezionare tutti i conflitti elencati nella griglia.  
  
 **Deseleziona tutto**  
 Fare clic su questo pulsante per deselezionare tutti i conflitti elencati nella griglia.  
  
 **Rimuovi**  
 Fare clic su questo pulsante per rimuovere i conflitti selezionati dal visualizzatore e i relativi metadati associati dalle tabelle del sistema di replica.  
  
 **Mostra tutte le colonne**  
 Selezionare questa opzione per visualizzare tutte le colonne della tabella.  
  
 **Mostra le prime cinque colonne e le altre colonne con dati in conflitto**  
 Selezionare questa opzione per visualizzare le prime cinque colonne e tutte le colonne contenenti conflitti. Questa opzione risulta utile quando nella tabella sono presenti numerose colonne, ma si desidera visualizzare solo le colonne più significative per la risoluzione dei conflitti. Le prime cinque colonne vengono sempre visualizzate perché i campi di identificazione di una riga, ad esempio i campi del nome o della chiave primaria, sono solitamente inclusi tra le prime colonne della tabella.  
  
 **Visualizza informazioni sulla colonna** (**...**)  
 Fare clic per visualizzare informazioni sulla colonna: **nome della tabella**, **nome della colonna**, **tipo di dati**, e **valore della colonna**.  
  
 **Registra informazioni dettagliate sul conflitto**  
 Selezionare questa casella per registrare le informazioni dettagliate sul conflitto in un file. Per specificare un percorso per il file, scegliere il **visualizzazione** menu e fare clic su **Opzioni**. Immettere un valore o fare clic su Sfoglia (**...**) e passare al file appropriato. Fare clic su **OK** per chiudere la **Opzioni** la finestra di dialogo.  
  
## Vedere anche  
 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md)   
 [Visualizza conflitti di dati per le pubblicazioni transazionali e 40 #; SQL Server Management Studio & #41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
  