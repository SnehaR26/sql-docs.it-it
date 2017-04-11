---
title: "Definizione di un articolo | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "articles [SQL Server replication], defining"
  - "sp_addmergearticle"
  - "adding articles"
  - "sp_addarticle"
  - "articoli [replica di SQL Server], aggiunta"
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Definizione di un articolo
  In questo argomento viene descritto come definire un articolo in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per definire un articolo tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   I nomi di articolo non possono includere i caratteri seguenti: %, *, [,], |: ?" , ' , \ , / , \< , >. Se si desidera replicare oggetti del database che includono uno qualsiasi di questi caratteri, è necessario specificare un nome di articolo diverso dal nome dell'oggetto.  
  
##  <a name="Security"></a> Sicurezza  
 Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](http://go.microsoft.com/fwlink/?LinkId=34733) offerti da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Creare le pubblicazioni e definire gli articoli utilizzando la Creazione guidata nuova pubblicazione. Dopo aver creata una pubblicazione, visualizzare e modificare le proprietà di pubblicazione nel **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per informazioni sulla creazione di una pubblicazione da un database Oracle, vedere [creare una pubblicazione da un Database Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
#### Per creare una pubblicazione e definire articoli  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere il **replica** cartella e quindi fare di **pubblicazioni locali** cartella.  
  
3.  Fare clic su **Nuova pubblicazione**.  
  
4.  Eseguire i vari passaggi della Creazione guidata nuova pubblicazione per:  
  
    -   Specificare un server di distribuzione se la distribuzione non è stata configurata sul server. Per ulteriori informazioni sulla configurazione della distribuzione, vedere [Configura pubblicazione e distribuzione](../../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
         Se si specifica per il **distributore** pagina che il server di pubblicazione fungerà da server di distribuzione (un server di distribuzione locale) e il server non è configurato come server di distribuzione, la creazione guidata nuova pubblicazione verrà configurato il server. Nella pagina **Cartella snapshot** è necessario specificare una cartella snapshot predefinita per il server di distribuzione. La cartella snapshot è semplicemente una directory designata come condivisione. Gli agenti che eseguono letture e scritture in questa cartella devono disporre di autorizzazioni sufficienti per accedervi. Per ulteriori informazioni sulla protezione della cartella in modo appropriato, vedere [sicurezza della cartella Snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
         Se si specifica che un altro server deve agire come server di distribuzione, è necessario immettere una password nella pagina **Password amministrativa** per le connessioni effettuate dal server di pubblicazione a quello di distribuzione. Questa password deve corrispondere a quella specificata quando il server di pubblicazione è stato attivato nel server di distribuzione remoto.  
  
         Per ulteriori informazioni, vedere [Configura distribuzione](../../../relational-databases/replication/configure-distribution.md).  
  
    -   Scegliere un database di pubblicazione.  
  
    -   Selezionare un tipo di pubblicazione. Per ulteriori informazioni, vedere [tipi di replica](../../../relational-databases/replication/types-of-replication.md).  
  
    -   Specificare i dati e gli oggetti di database da pubblicare; facoltativamente, filtrare le colonne dagli articoli di tabelle e impostare le proprietà degli articoli.  
  
    -   Facoltativamente, filtrate le righe dagli articoli di tabelle. Per ulteriori informazioni, vedere [filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md).  
  
    -   Impostare la pianificazione dell'agente snapshot.  
  
    -   Specificare le credenziali con cui gli agenti di replica seguenti vengono eseguiti e stabiliscono le connessioni:  
  
         \- Agente snapshot per tutte le pubblicazioni.  
  
         \- Agente di lettura log per tutte le pubblicazioni transazionali.  
  
         \- Agente di lettura coda per le pubblicazioni transazionali che consentono sottoscrizioni aggiornabili.  
  
         Per ulteriori informazioni, vedere [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) e [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
    -   Facoltativamente, creare lo script della pubblicazione. Per altre informazioni, vedere [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
    -   Specificare un nome per la pubblicazione.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Dopo aver creato una pubblicazione, è possibile creare gli articoli a livello di programmazione tramite le codice stored procedure di replica. Le stored procedure utilizzate per creare un articolo dipendono dal tipo di pubblicazione per il quale viene definito l'articolo. Per altre informazioni, vedere [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Per definire un articolo per una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare il nome della pubblicazione a cui appartiene l'articolo per **@publication**, un nome per l'articolo per **@article**, l'oggetto di database da pubblicare per **@source_object**, e gli altri parametri facoltativi. Utilizzare **@source_owner** per specificare la proprietà dello schema dell'oggetto, se non **dbo**. Se l'articolo non è un articolo di tabella basato su log, specificare il tipo di articolo per **@type**; Per ulteriori informazioni, vedere [specificare tipi di articolo & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md).  
  
2.  Per visualizzare un articolo in senso orizzontale filtrare le righe in una tabella oppure utilizzare [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) per definire la clausola di filtro. Per altre informazioni, vedere [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Per filtrare le colonne in una tabella o visualizzare un articolo verticalmente, utilizzare [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md). Per altre informazioni, vedere [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
4.  Eseguire [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) Se l'articolo è filtrato.  
  
5.  Se la pubblicazione include sottoscrizioni esistenti e [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) restituisce un valore di **0** nel **immediate_sync** colonna, è necessario chiamare [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) per aggiungere l'articolo per ogni sottoscrizione esistente.  
  
6.  Se la pubblicazione esistono sottoscrizioni pull, eseguire [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) nel server di pubblicazione per creare un nuovo snapshot per le sottoscrizioni pull esistenti contenente solo il nuovo articolo.  
  
    > [!NOTE]  
    >  Per le sottoscrizioni non inizializzate utilizzando uno snapshot, non è necessario eseguire [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) come questa procedura viene eseguita da [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
#### Per definire un articolo per una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare il nome della pubblicazione per **@publication**, un nome per il nome dell'articolo per **@article**, e l'oggetto da pubblicare per **@source_object**. Per filtrare in senso orizzontale le righe della tabella, specificare un valore per **@subset_filterclause**. Per ulteriori informazioni, vedere [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) e [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md). Se l'articolo non è un articolo di tabella, specificare il tipo di articolo per **@type**. Per ulteriori informazioni, vedere [specificare tipi di articolo & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md).  
  
2.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) per definire un filtro di join tra due articoli. Per altre informazioni, vedere [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
3.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) per filtrare le colonne di tabella. Per altre informazioni, vedere [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio si definisce un articolo basato sulla tabella `Product` per una pubblicazione transazionale, in cui l'articolo è filtrato in senso orizzontale e verticale.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_1.sql)]  
  
 In questo esempio si definiscono gli articoli per una pubblicazione di tipo merge, in cui l'articolo `SalesOrderHeader` è filtrato in modo statico in base a **SalesPersonID**e l'articolo `SalesOrderDetail` è filtrato con filtro di join in base a `SalesOrderHeader`.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile definire articoli a livello di programmazione tramite gli oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per la definizione di un articolo dipendono dal tipo di pubblicazione per la quale l'articolo viene definito.  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 Nell'esempio seguente un articolo con filtri di riga e di colonna viene aggiunto a una pubblicazione transazionale.  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 Nell'esempio seguente tre articoli vengono aggiunti a una pubblicazione di tipo merge. Gli articoli contengono filtri di colonna e vengono utilizzati due filtri join per propagare un filtro di riga con parametri negli altri articoli.  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Aggiunta ed eliminazione di articoli a e da pubblicazioni esistenti](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Filtro dei dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  