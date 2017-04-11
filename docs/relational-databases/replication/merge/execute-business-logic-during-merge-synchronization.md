---
title: "Esecuzione di logiche di business durante la sincronizzazione di tipo merge | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "risoluzione personalizzata di errori [replica di SQL Server]"
  - "gestione personalizzata delle modifiche [replica di SQL Server]"
  - "errori [replica di SQL Server], gestori della logica di business"
  - "gestori della logica di business per la replica di tipo merge [replica di SQL Server]"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
  - "gestori della logica di business [replica di SQL Server]"
ms.assetid: 9d4da2ef-c17f-4a31-a1f6-5c3b7ca85f71
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Esecuzione di logiche di business durante la sincronizzazione di tipo merge
  Il framework di gestione della logica di business consente di scrivere un assembly di codice gestito che viene chiamato durante il processo di sincronizzazione di tipo merge. L'assembly include la logica di business che consente di rispondere a diverse situazioni durante la sincronizzazione, ad esempio modifiche ai dati, conflitti ed errori. Il framework di gestione della logica di business offre un semplice modello di programmazione e i dati forniti all'assembly dal processo di merge sono sotto forma di set di dati ADO.NET. In questo modo, è possibile approfondire la propria conoscenza di ADO.NET anziché apprendere un'interfaccia specifica. Per ulteriori informazioni sulla programmazione dei gestori della logica di business, vedere:  
  
-   Il riferimento all'API di programmazione delle applicazioni: <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>  
  
-   Istruzioni su come implementare un gestore della logica di business: [implementare un gestore della logica di Business per un articolo di Merge](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
## Utilizzi dei gestori della logica di business  
 Il processo di sincronizzazione di tipo merge consente di richiamare i gestori della logica di business per eseguire le operazioni seguenti:  
  
-   Gestione personalizzata delle modifiche  
  
-   Risoluzione personalizzata dei conflitti  
  
-   Risoluzione personalizzata degli errori  
  
> [!NOTE]  
>  Il gestore della logica di business specificato viene eseguito per ogni riga sincronizzata. La complessità della logica e le chiamate ad altre applicazioni o servizi di rete possono ridurre le prestazioni.  
  
### Gestione personalizzata delle modifiche  
 Il gestore della logica di business può essere richiamato durante l'elaborazione di modifiche ai dati non in conflitto e consente di eseguire una delle tre azioni seguenti:  
  
-   Rifiutare i dati  
  
     Operazione utile per le applicazioni di cui non si desidera propagare le modifiche a o da un Sottoscrittore specifico. Un amministratore, ad esempio, potrebbe escludere tramite un filtro gli inserimenti che non appartengono alla partizione del Sottoscrittore oppure eventualmente rifiutare le eliminazioni eseguite in un Sottoscrittore. Un'applicazione potrebbe inoltre rifiutare un ordine immesso in un Sottoscrittore perché le scorte non sono più disponibili.  
  
-   Accettare i dati  
  
     Operazione utile per le applicazioni in cui è necessario esaminare le modifiche ai dati apportate nel server di pubblicazione o nel Sottoscrittore prima di consentirne la propagazione. Un'applicazione di livello intermedio, ad esempio, consentirebbe di esaminare i nuovi ordini provenienti dal campo e di integrarli con un processo del flusso di lavoro relativo all'approvvigionamento nel livello intermedio.  
  
-   Applicare dati personalizzati  
  
     Operazione utile per le applicazioni in cui è necessario sostituire operazioni o valori di dati specifici. Ad esempio, un'applicazione può trasformare una riga eliminata in un aggiornamento speciale che imposta una **stato** colonna nella riga a un valore di "deleted" e quindi rileva l'identità del client che ha eseguito l'eliminazione. Questa operazione potrebbe risultare utile per effettuare controlli e monitorare il flusso di lavoro.  
  
### Risoluzione personalizzata dei conflitti  
 La replica di tipo merge consente di rilevare e risolvere i conflitti, permettendo di accettare una strategia di risoluzione predefinita o di scegliere la risoluzione personalizzata per i conflitti. Per altre informazioni, vedere [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md). Il gestore della logica di business può essere richiamato durante l'elaborazione di modifiche ai dati in conflitto e consente di eseguire una delle due azioni seguenti:  
  
-   Accettare la risoluzione predefinita  
  
     Operazione utile per le applicazioni per cui può essere necessario esaminare il conflitto, eseguire altre azioni ed eventualmente registrare un messaggio personalizzato del log dei conflitti.  
  
-   Eseguire la risoluzione personalizzata  
  
     Operazione utile per le applicazioni per cui può essere necessario selezionare valori di dati specifici della logica di business e fornire al processo di sincronizzazione questo set di dati personalizzato. Un'applicazione, ad esempio, potrebbe rendere disponibile una nuova versione della riga confermata combinando i valori dei set di dati del server di pubblicazione e del Sottoscrittore.  
  
### Risoluzione personalizzata degli errori  
 È possibile richiamare la logica personalizzata durante la propagazione delle modifiche che restituiscono errori. La logica consente di eseguire una delle due azioni seguenti:  
  
-   Accettare la risoluzione predefinita degli errori  
  
     Operazione utile per le applicazioni per cui può essere necessario esaminare l'errore ed eseguire l'altra azione ed eventualmente registrare un messaggio personalizzato del log degli errori.  
  
-   Accettare la risoluzione personalizzata degli errori  
  
     Operazione utile per le applicazioni per cui può essere necessario selezionare valori di dati specifici della logica di business e fornire al processo di sincronizzazione questo set di dati personalizzato. Se, ad esempio, durante il processo di replica viene rilevata una violazione di chiave duplicata, il gestore della logica di business potrebbe specificare una nuova versione della modifica ai dati in cui la chiave non risulta più in conflitto. Le modifiche apportate nel server di pubblicazione e nel Sottoscrittore possono essere mantenute nel database e il processo di replica non deve compensare l'inserimento non riuscito con un'eliminazione.  
  
## Scenari di distribuzione per gestori della logica di business  
 È possibile distribuire gestori della logica di business nei sistemi seguenti:  
  
-   Server di distribuzione. Utilizzare una sottoscrizione push per eseguire la logica di business nel server di distribuzione.  
  
-   Sottoscrittore. Utilizzare una sottoscrizione pull per eseguire la logica di business nel Sottoscrittore.  
  
-   Server IIS (Internet Information Services), se si utilizza la sincronizzazione tramite il Web. Utilizzare una sottoscrizione pull sincronizzata tramite il Web per eseguire il gestore della logica di business nel server IIS.  
  
## Vedere anche  
 [Replica di tipo merge](../../../relational-databases/replication/merge/merge-replication.md)   
 [Sottoscrizione delle pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md)   
 [Sincronizzare i dati](../../../relational-databases/replication/synchronize-data.md)   
 [Sincronizzazione Web per la replica di tipo merge](../../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  