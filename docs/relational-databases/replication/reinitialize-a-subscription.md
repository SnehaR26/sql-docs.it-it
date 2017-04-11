---
title: "Reinizializzare una sottoscrizione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "inizializzazione della sottoscrizioni [replica di SQL Server], reinizializzazione"
  - "sottoscrizioni [replica di SQL Server], reinizializzazione"
  - "reinizializzazione di sottoscrizioni"
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Reinizializzare una sottoscrizione
  In questo argomento viene descritto come reinizializzare una sottoscrizione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o RMO (Replication Management Objects). È possibile contrassegnare singole sottoscrizioni per la reinizializzazione in modo che nel corso della successiva sincronizzazione venga applicato un nuovo snapshot.  
  
 **Contenuto dell'argomento**  
  
-   **Per reinizializzare una sottoscrizione, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Il processo di reinizializzazione di una sottoscrizione è articolato in due parti.  
  
1.  Una singola sottoscrizione o tutte le sottoscrizioni di una pubblicazione vengono *contrassegnate* per la reinizializzazione. Contrassegnare le sottoscrizioni per la reinizializzazione nel **Reinizializza sottoscrizioni** la finestra di dialogo, disponibile tramite il **pubblicazioni locali** cartella e il **sottoscrizioni locali** cartella [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. È inoltre possibile contrassegnare le sottoscrizioni nella scheda **Tutte le sottoscrizioni** e nel nodo delle pubblicazioni in Monitoraggio replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md). Quando si contrassegna una sottoscrizione per la reinizializzazione, sono disponibili le opzioni seguenti:  
  
     **Usa lo snapshot corrente**  
     Selezionare questa opzione per applicare lo snapshot corrente al Sottoscrittore alla successiva esecuzione dell'agente di distribuzione o dell'agente di merge. Se non sono disponibili snapshot validi, questa opzione non può essere selezionata.  
  
     **Usa un nuovo snapshot**  
     Selezionare questa opzione per reinizializzare la sottoscrizione con un nuovo snapshot. Lo snapshot può essere applicato al Sottoscrittore solo dopo essere stato generato dall'agente snapshot. Se l'agente snapshot è impostato in modo da essere eseguito in base a una pianificazione, la sottoscrizione verrà reinizializzata soltanto dopo la successiva esecuzione pianificata dell'agente snapshot. Per avviare l'agente snapshot immediatamente, selezionare **Genera il nuovo snapshot ora** .  
  
     **Carica le modifiche non sincronizzate prima della reinizializzazione**  
     Solo per la replica di tipo merge. Selezionare questa opzione per caricare le eventuali modifiche in sospeso dal database della sottoscrizione prima che i dati nel Sottoscrittore vengano sovrascritti con uno snapshot.  
  
     Se si aggiunge, elimina o modifica un filtro con parametri, le modifiche in sospeso nel Sottoscrittore non possono essere caricate nel server di pubblicazione durante la reinizializzazione. Per caricare le modifiche in sospeso, sincronizzare tutte le sottoscrizioni prima di modificare il filtro.  
  
2.  Una sottoscrizione viene reinizializzata alla successiva sincronizzazione. L'agente di distribuzione (per la replica transazionale) o l'agente di merge (per la replica di tipo merge) applica lo snapshot più recente a ogni Sottoscrittore dotato di una sottoscrizione contrassegnata per la reinizializzazione. Per ulteriori informazioni sulla sincronizzazione delle sottoscrizioni, vedere [sincronizzare una sottoscrizione Push](../../relational-databases/replication/synchronize-a-push-subscription.md) e [sincronizzare una sottoscrizione Pull](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Per contrassegnare una singola sottoscrizione push o pull per la reinizializzazione in Management Studio (nel server di pubblicazione)  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Espandere la pubblicazione di cui si desidera reinizializzare la sottoscrizione.  
  
4.  Fare doppio clic su sottoscrizione e quindi fare clic su **reinizializzare**.  
  
5.  Nel **Reinizializza sottoscrizioni** la finestra di dialogo, selezionare le opzioni e quindi fare clic su **contrassegnare per la reinizializzazione**.  
  
#### Per contrassegnare una singola sottoscrizione pull per la reinizializzazione in Management Studio (nel Sottoscrittore)  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Sottoscrizioni locali** .  
  
3.  Fare doppio clic su sottoscrizione e quindi fare clic su **reinizializzare**.  
  
4.  Nella finestra di dialogo di conferma che viene visualizzata, fare clic su **Sì**.  
  
#### Per contrassegnare tutte le sottoscrizioni per la reinizializzazione in Management Studio  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Pulsante destro del mouse la pubblicazione con sottoscrizioni che si desidera reinizializzare e quindi fare clic su **reinizializzare tutte le sottoscrizioni**.  
  
4.  Nel **Reinizializza sottoscrizioni** la finestra di dialogo, selezionare le opzioni e quindi fare clic su **contrassegnare per la reinizializzazione**.  
  
#### Per contrassegnare una singola sottoscrizione push o pull per la reinizializzazione in Monitoraggio replica  
  
1.  In Monitoraggio replica espandere un gruppo di server di pubblicazione nel riquadro di sinistra, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic sulla scheda **Tutte le sottoscrizioni** .  
  
3.  Fare doppio clic su sottoscrizione si desidera reinizializzare e quindi fare clic su **Reinizializza sottoscrizione**.  
  
4.  Nel **Reinizializza sottoscrizioni** la finestra di dialogo, selezionare le opzioni e quindi fare clic su **contrassegnare per la reinizializzazione**.  
  
#### Per contrassegnare tutte le sottoscrizioni per la reinizializzazione in Monitoraggio replica  
  
1.  In Monitoraggio replica espandere un gruppo di server di pubblicazione nel riquadro di sinistra e quindi espandere un server di pubblicazione.  
  
2.  Pulsante destro del mouse la pubblicazione con sottoscrizioni che si desidera reinizializzare e quindi fare clic su **reinizializzare tutte le sottoscrizioni**.  
  
3.  Nel **Reinizializza sottoscrizioni** la finestra di dialogo, selezionare le opzioni e quindi fare clic su **contrassegnare per la reinizializzazione**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile reinizializzare le sottoscrizioni a livello di programmazione tramite le stored procedure di replica. La stored procedure utilizzata dipende dal tipo di sottoscrizione, ovvero push o pull, nonché dal tipo di pubblicazione a cui appartiene la sottoscrizione.  
  
#### Per reinizializzare una sottoscrizione pull in una pubblicazione transazionale  
  
1.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_reinitpullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql.md). Specificare **@publisher**, **@publisher_db**, e **@publication**. La sottoscrizione verrà contrassegnata per la reinizializzazione alla successiva esecuzione dell'agente di distribuzione.  
  
2.  (Facoltativo) Avviare l'agente di distribuzione nel Sottoscrittore per sincronizzare la sottoscrizione. Per altre informazioni, vedere [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Per reinizializzare una sottoscrizione push in una pubblicazione transazionale  
  
1.  Server di pubblicazione, eseguire [sp_reinitsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql.md). Specificare **@publication**, **@subscriber**, e **@destination_db**. La sottoscrizione verrà contrassegnata per la reinizializzazione alla successiva esecuzione dell'agente di distribuzione.  
  
2.  (Facoltativo) Avviare l'agente di distribuzione nel server di distribuzione per sincronizzare la sottoscrizione. Per altre informazioni, vedere [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Per reinizializzare una sottoscrizione pull in una pubblicazione di tipo merge  
  
1.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_reinitmergepullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md). Specificare **@publisher**, **@publisher_db**, e **@publication**. Per caricare le modifiche dal sottoscrittore prima della reinizializzazione, specificare un valore di **true** per **@upload_first**. La sottoscrizione verrà contrassegnata per la reinizializzazione alla successiva esecuzione dell'agente di merge.  
  
    > [!IMPORTANT]  
    >  Se si aggiunge, elimina o modifica un filtro con parametri, le modifiche in sospeso nel Sottoscrittore non possono essere caricate nel server di pubblicazione durante la reinizializzazione. Per caricare le modifiche in sospeso, sincronizzare tutte le sottoscrizioni prima di modificare il filtro.  
  
2.  (Facoltativo) Avviare l'agente di merge nel Sottoscrittore per sincronizzare la sottoscrizione. Per altre informazioni, vedere [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Per reinizializzare una sottoscrizione push in una pubblicazione di tipo merge  
  
1.  Server di pubblicazione, eseguire [sp_reinitmergesubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql.md). Specificare **@publication**, **@subscriber**, e **@subscriber_db**. Per caricare le modifiche dal sottoscrittore prima della reinizializzazione, specificare un valore di **true** per **@upload_first**. La sottoscrizione verrà contrassegnata per la reinizializzazione alla successiva esecuzione dell'agente di distribuzione.  
  
    > [!IMPORTANT]  
    >  Se si aggiunge, elimina o modifica un filtro con parametri, le modifiche in sospeso nel Sottoscrittore non possono essere caricate nel server di pubblicazione durante la reinizializzazione. Per caricare le modifiche in sospeso, sincronizzare tutte le sottoscrizioni prima di modificare il filtro.  
  
2.  (Facoltativo) Avviare l'agente di merge nel server di distribuzione per sincronizzare la sottoscrizione. Per altre informazioni, vedere [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Per impostare i criteri di reinizializzazione durante la creazione di una nuova pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), specificando uno dei seguenti valori per **@automatic_reinitialization_policy**:  
  
    -   **1** -le modifiche vengono caricate dal sottoscrittore prima di una sottoscrizione viene reinizializzata automaticamente come richiesto da una modifica della pubblicazione.  
  
    -   **0** -le modifiche nel Sottoscrittore vengono eliminate quando una sottoscrizione viene reinizializzata automaticamente come richiesto da una modifica della pubblicazione.  
  
    > [!IMPORTANT]  
    >  Se si aggiunge, elimina o modifica un filtro con parametri, le modifiche in sospeso nel Sottoscrittore non possono essere caricate nel server di pubblicazione durante la reinizializzazione. Per caricare le modifiche in sospeso, sincronizzare tutte le sottoscrizioni prima di modificare il filtro.  
  
     Per altre informazioni, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Per modificare i criteri di reinizializzazione per una pubblicazione di tipo merge esistente  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), specificando **automatic_reinitialization_policy** per **@property** e uno dei seguenti valori per **@value**:  
  
    -   **1** -le modifiche vengono caricate dal sottoscrittore prima di una sottoscrizione viene reinizializzata automaticamente come richiesto da una modifica della pubblicazione.  
  
    -   **0** -le modifiche nel Sottoscrittore vengono eliminate quando una sottoscrizione viene reinizializzata automaticamente come richiesto da una modifica della pubblicazione.  
  
    > [!IMPORTANT]  
    >  Se si aggiunge, elimina o modifica un filtro con parametri, le modifiche in sospeso nel Sottoscrittore non possono essere caricate nel server di pubblicazione durante la reinizializzazione. Per caricare le modifiche in sospeso, sincronizzare tutte le sottoscrizioni prima di modificare il filtro.  
  
     Per altre informazioni, vedere [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile contrassegnare singole sottoscrizioni per la reinizializzazione in modo che nel corso della successiva sincronizzazione venga applicato un nuovo snapshot. Le sottoscrizioni possono essere reinizializzate a livello di programmazione tramite gli oggetti RMO (Replication Management Objects). Le classi utilizzate dipendono dal tipo di pubblicazione a cui appartiene la sottoscrizione e dal tipo di sottoscrizione, ovvero push o pull.  
  
#### Per reinizializzare una sottoscrizione pull in una pubblicazione transazionale  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPullSubscription> e impostare <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, e la connessione dal passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto.  
  
    > [!NOTE]  
    >  Se questo metodo restituisce **false**, le proprietà della sottoscrizione nel passaggio 2 sono state definite in modo non corretto o la sottoscrizione pull non esiste.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> metodo. Questo metodo contrassegna la sottoscrizione per la reinizializzazione.  
  
5.  Sincronizzare la sottoscrizione pull. Per altre informazioni, vedere [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Per reinizializzare una sottoscrizione push in una pubblicazione transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransSubscription> e impostare <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, e la connessione dal passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto.  
  
    > [!NOTE]  
    >  Se questo metodo restituisce **false**, le proprietà della sottoscrizione nel passaggio 2 sono state definite in modo non corretto o la sottoscrizione push non esiste.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> metodo. Questo metodo contrassegna la sottoscrizione per la reinizializzazione.  
  
5.  Sincronizzare la sottoscrizione push. Per altre informazioni, vedere [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Per reinizializzare una sottoscrizione pull in una pubblicazione di tipo merge  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePullSubscription> e impostare <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, e la connessione dal passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto.  
  
    > [!NOTE]  
    >  Se questo metodo restituisce **false**, le proprietà della sottoscrizione nel passaggio 2 sono state definite in modo non corretto o la sottoscrizione pull non esiste.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> metodo. Passare il valore **true** per caricare le modifiche nel Sottoscrittore prima della reinizializzazione oppure il valore **false** per eseguire la reinizializzazione e perdere eventuali modifiche in sospeso nel Sottoscrittore. Questo metodo contrassegna la sottoscrizione per la reinizializzazione.  
  
    > [!NOTE]  
    >  Se la sottoscrizione è scaduta, non sarà possibile caricare le modifiche. Per altre informazioni, vedere [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Sincronizzare la sottoscrizione pull. Per altre informazioni, vedere [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Per reinizializzare una sottoscrizione push in una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeSubscription> e impostare <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, e la connessione dal passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto.  
  
    > [!NOTE]  
    >  Se questo metodo restituisce **false**, le proprietà della sottoscrizione nel passaggio 2 sono state definite in modo non corretto o la sottoscrizione push non esiste.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> metodo. Passare il valore **true** per caricare le modifiche nel Sottoscrittore prima della reinizializzazione oppure il valore **false** per eseguire la reinizializzazione e perdere eventuali modifiche in sospeso nel Sottoscrittore. Questo metodo contrassegna la sottoscrizione per la reinizializzazione.  
  
    > [!NOTE]  
    >  Se la sottoscrizione è scaduta, non sarà possibile caricare le modifiche. Per altre informazioni, vedere [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Sincronizzare la sottoscrizione push. Per altre informazioni, vedere [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio viene eseguita la reinizializzazione di una sottoscrizione pull in una pubblicazione transazionale.  
  
 [!code-csharp[HowTo#rmo_ReinitTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 In questo esempio viene eseguita la reinizializzazione di una sottoscrizione pull in una pubblicazione di tipo merge dopo aver prima caricato le modifiche in sospeso nel Sottoscrittore.  
  
 [!code-csharp[HowTo#rmo_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## Vedere anche  
 [Reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Concetti di base relativi a RMO (Replication Management Objects)](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  