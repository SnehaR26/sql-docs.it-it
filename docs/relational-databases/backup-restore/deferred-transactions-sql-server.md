---
title: "Transazioni posticipate (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "I/O [SQL Server], recupero del database"
  - "ripristino di pagine [SQL Server]"
  - "transazioni posticipate"
  - "modifica dello stato di transazione posticipata"
ms.assetid: 6fc0f9b6-d3ea-4971-9f27-d0195d1ff718
caps.latest.revision: 45
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 45
---
# Transazioni posticipate (SQL Server)
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise una transazione danneggiata può diventare posticipata se i dati necessari per il rollback (annullamento) sono offline durante l'avvio del database. Una *transazione posticipata* è una transazione di cui non è stato eseguito il commit al termine della fase di rollforward e per la quale si è verificato un errore che ne impedisce il rollback. Non essendo possibile eseguire il rollback, la transazione viene posticipata.  
  
> [!NOTE]  
>  Le transazioni danneggiate vengono posticipate solo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise. Nelle altre edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] una transazione danneggiata causa un errore di avvio.  
  
 In genere, una transazione posticipata si verifica perché durante il rollforward del database un errore di I/O ha impedito la lettura di una pagina necessaria per la transazione. Anche un errore a livello di file può tuttavia determinare transazioni posticipate. Una transazione posticipata si può verificare anche quando una sequenza di ripristino parziale si arresta in un punto in cui è necessario eseguire il rollback della transazione e i dati richiesti dalla transazione sono offline.  
  
 Se si verifica un errore di I/O durante il rollback delle transazioni utente, verrà attivata la modalità offline per l'intero database. Quando viene riattivata la modalità online per il database, il rollforward riacquisisce tutti i blocchi precedenti e tenta di eseguire il rollback delle transazioni di cui non è stato eseguito il commit. Tutti i dati modificati da una transazione rimangono bloccati nel modo appropriato fino a quando non è possibile eseguire il rollback della transazione. Le transazioni di cui non è possibile eseguire il rollback rilasciano i relativi blocchi quando il problema di danneggiamento viene risolto e il database viene riavviato oppure, dopo un ripristino online, quando le transazioni posticipate vengono risolte mentre il database rimane online. Fino a quel momento, una transazione posticipata può mantenere attivi blocchi che impediscono l'esecuzione di determinate operazioni sull'intero database. Ad esempio, se una transazione posticipata contiene un'istruzione CREATE TABLE, verrà impedito agli utenti di creare una tabella fino alla risoluzione della transazione posticipata.  
  
 Una transazione posticipata si può anche verificare quando un ripristino a fasi recupera un database fino a un punto in cui una o più transazioni attive influiscono su un filegroup che non è ancora stato ripristinato ed è offline. Non essendo possibile eseguire il rollback, le transazioni diventano posticipate.  
  
 Nella tabella seguente sono illustrate le azioni che determinano l'esecuzione di un recupero in un database e il risultato ottenuto nel caso si verifichi un errore di I/O.  
  
|Azione|Risoluzione (se si verificano problemi di I/O oppure i dati necessari sono offline)|  
|------------|-----------------------------------------------------------------------|  
|Avvio del server|Transazione posticipata|  
|Restore|Transazione posticipata|  
|Collega|Il collegamento ha esito negativo|  
|Riavvio automatico|Transazione posticipata|  
|Creazione di database o di snapshot del database|La creazione ha esito negativo|  
|Rollforward nel mirroring del database|Transazione posticipata|  
|Filegroup offline|Transazione posticipata|  
  
## Annullamento dello stato di transazione posticipata  
  
> [!IMPORTANT]  
>  Le transazioni posticipate mantengono attivo il log delle transazioni. Un file di log virtuale contenente transazioni posticipate non può essere troncato fino a quando lo stato di transazione posticipata non viene annullato. Per altre informazioni sul troncamento del log, vedere [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
 Per annullare lo stato di transazione posticipata, è necessario che durante l'avvio del database non si verifichino errori di I/O. Se sono presenti transazioni posticipate, è necessario correggere l'origine degli errori di I/O. Di seguito sono riportate le soluzioni possibili, elencate nell'ordine in cui solitamente vengono tentate:  
  
-   Riavviare il database. Se il problema era temporaneo, il database verrà avviato senza transazioni posticipate.  
  
-   Se le transazioni sono state posticipate a causa di un filegroup offline, attivare di nuovo la modalità online per il filegroup.  
  
     Per attivare di nuovo la modalità online per un filegroup, utilizzare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente:  
  
    ```  
    RESTORE DATABASE database_name FILEGROUP=<filegroup_name>  
    ```  
  
-   Ripristinare il database. Dopo un ripristino online, eventuali transazioni posticipate vengono risolte.  
  
     In base al modello di recupero con registrazione completa o con registrazione minima delle operazioni bulk, se le transazioni posticipate sono causate da un numero ridotto di pagine danneggiate, un ripristino delle pagine online può risolvere gli errori (se supportato).  
  
-   Se non è più necessario un filegroup offline che causa transazioni posticipate, è possibile renderlo inattivo. Quando il filegroup in questione diventa offline, lo stato di transazione posticipata viene annullato.  
  
    > [!IMPORTANT]  
    >  Un filegroup inattivo non può in alcun modo essere recuperato.  
  
     Per altre informazioni, vedere [Rimuovere filegroup inattivi &#40;SQL Server&#41;](../../relational-databases/backup-restore/remove-defunct-filegroups-sql-server.md).  
  
-   Se le transazioni sono state posticipate a causa di una pagina danneggiata e non è disponibile un backup valido del database, eseguire le operazioni seguenti per correggere gli errori del database:  
  
    -   Attivare innanzitutto la modalità di emergenza del database eseguendo l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente:  
  
        ```  
        ALTER DATABASE <database_name> SET EMERGENCY  
        ```  
  
         Per informazioni sulla modalità di emergenza, vedere [Stati del database](../../relational-databases/databases/database-states.md).  
  
    -   Correggere quindi gli errori del database usando l'opzione DBCC REPAIR_ALLOW_DATA_LOSS in una delle istruzioni DBCC seguenti: [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md), [DBCC CHECKALLOC](../../t-sql/database-console-commands/dbcc-checkalloc-transact-sql.md) o [DBCC CHECKTABLE](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md).  
  
         Quando rileva la pagina danneggiata, DBCC ne esegue la deallocazione e corregge gli eventuali errori correlati. Questo approccio consente di attivare di nuovo la modalità online per il database in uno stato fisicamente consistente. È tuttavia possibile che vengano persi dati aggiuntivi. Utilizzare pertanto questo approccio solo se strettamente necessario.  
  
## Vedere anche  
 [Panoramica del ripristino e del recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [Rimuovere filegroup inattivi &#40;SQL Server&#41;](../../relational-databases/backup-restore/remove-defunct-filegroups-sql-server.md)   
 [Ripristini di file &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [Ripristini di file &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)   
 [Ripristinare pagine &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-pages-sql-server.md)   
 [Ripristini a fasi &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  