---
title: "Scollegamento e collegamento di database DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 830e33bc-dd15-4f8e-a4ac-d8634b78fe45
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Scollegamento e collegamento di database DQS
  In questo argomento viene descritto come scollegare e collegare i database DQS.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Limitations"></a> Limitazioni e restrizioni  
 Per un elenco delle limitazioni e restrizioni, vedere [scollegare il Database e Allega & #40; SQL Server & #41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   Assicurarsi che non vi siano attività o processi in esecuzione in DQS. È possibile verificare utilizzando la schermata **Monitoraggio attività** . Per informazioni dettagliate su funzionamento di questa schermata, vedere [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md).  
  
-   Assicurarsi che non vi siano utenti connessi al [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
  
-   È necessario che l'account utente di Windows sia membro del ruolo predefinito del server db_owner nell'istanza di SQL Server per scollegare i database DQS.  
  
-   L'account utente di Windows deve disporre dell'autorizzazione CREATE DATABASE, CREATE ANY DATABASE o ALTER ANY DATABASE per collegare un database.  
  
-   È necessario disporre del ruolo dqs_administrator sul database DQS_MAIN per interrompere qualsiasi attività in esecuzione o arrestare processi in corso in DQS.  
  
##  <a name="Detach"></a> Scollegare i database DQS  
 Quando si scollega un database DQS utilizzando SQL Server Management Studio, i file scollegati non vengono eliminati dal computer e possono essere ricollegati alla stessa istanza di SQL Server o possono essere spostati in un altro server dove vengono collegati. I file di database DQS sono in genere disponibili nel seguente percorso sul computer Data Quality Services: C:\Program Files\Microsoft SQL Server\MSSQL13.*\< Instance_Name >*\MSSQL\DATA.  
  
1.  Avviare Microsoft SQL Server Management Studio e connettersi all'istanza di SQL Server appropriata.  
  
2.  In Esplora oggetti espandere il nodo **Database** .  
  
3.  Fare doppio clic sul **DQS_MAIN** database, scegliere **attività**, quindi fare clic su **scollegamento**. Verrà visualizzata la finestra di dialogo **Scollega database** .  
  
4.  Selezionare la casella di controllo sotto la **Drop** colonna e fare clic su **OK** per scollegare il database DQS_MAIN.  
  
5.  Ripetere i passaggi 3 e 4 con i database DQS_PROJECTS e DQS_STAGING_DATA per scollegarli.  
  
 È inoltre possibile scollegare i database DQS tramite le istruzioni Transact-SQL utilizzando la stored procedure sp_detach_db. Per ulteriori informazioni sullo scollegamento di database tramite istruzioni Transact-SQL, vedere [tramite Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) in [scollegare un Database](../relational-databases/databases/detach-a-database.md).  
  
##  <a name="Attach"></a> Collegare i database DQS  
 Utilizzare le istruzioni seguenti per collegare un database DQS alla stessa istanza di SQL Server, da cui è stato scollegato, o a un'istanza di SQL Server diversa in cui è installato [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
1.  Avviare Microsoft SQL Server Management Studio e connettersi all'istanza di SQL Server appropriata.  
  
2.  In Esplora oggetti, fare doppio clic su **database**, quindi fare clic su **Attach**. Verrà visualizzata la finestra di dialogo **Collega database** .  
  
3.  Per specificare il database da collegare, fare clic su **Aggiungi**. Verrà visualizzata la finestra di dialogo **Individua file di database** .  
  
4.  Selezionare l'unità disco in cui si trova il database ed espandere l'albero di directory per individuare e selezionare il file con estensione mdf del database. Ad esempio, per il database DQS_MAIN:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\DQS_MAIN.mdf  
    ```  
  
5.  Il **Dettagli database** (in basso) Visualizza i nomi dei file da allegare. Per verificare o modificare il percorso di un file, fare clic sui **Sfoglia** pulsante (...).  
  
6.  Fare clic su **OK** per collegare il database DQS_MAIN.  
  
7.  Ripetere i passaggi da 2 a 6 per il collegamento dei database DQS_PROJECTS e DQS_STAGING_DATA.  
  
8.  È inoltre necessario eseguire le istruzioni Transact-SQL nel passaggio successivo al ripristino del database DQS_MAIN; in caso contrario, viene visualizzato un messaggio di errore quando si tenta una connessione al server Data Quality tramite l'applicazione client Data Quality e la connessione non può essere stabilita. Tuttavia, non è necessario effettuare i passaggi 9 e 10 se è stato aggiunto solo il database DQS_STAGING_DATA o DQS_PROJECTS e non DQS_MAIN.  
  
     Per eseguire le istruzioni Transact-SQL, in Esplora oggetti, fare doppio clic su server e quindi fare clic su **Nuova Query**.  
  
9. Nella finestra dell'editor di query copiare le istruzioni SQL seguenti:  
  
    ```  
    ALTER DATABASE [DQS_MAIN] SET TRUSTWORTHY ON;  
    EXEC sp_configure 'clr enabled', 1;  
    RECONFIGURE WITH OVERRIDE  
    ALTER DATABASE [DQS_MAIN] SET ENABLE_BROKER  
    ALTER AUTHORIZATION ON DATABASE::[DQS_MAIN] TO [##MS_dqs_db_owner_login##]  
    ALTER AUTHORIZATION ON DATABASE::[DQS_PROJECTS] TO [##MS_dqs_db_owner_login##]  
  
    ```  
  
10. Premere F5 per eseguire le istruzioni. Esaminare il riquadro dei risultati per verificare che le istruzioni siano state eseguite correttamente. Viene visualizzato il messaggio seguente: `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`  
  
11. Connettersi al server Data Quality utilizzando il client Data Quality per verificare se è possibile stabilire correttamente la connessione.  
  
 È inoltre possibile collegare i database DQS utilizzando le istruzioni Transact-SQL. Per ulteriori informazioni sulla connessione di database tramite istruzioni Transact-SQL, vedere [tramite Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) in [collegare un Database](../relational-databases/databases/attach-a-database.md).  
  
## Vedere anche  
 [Gestire i database DQS](../data-quality-services/manage-dqs-databases.md)  
  
  