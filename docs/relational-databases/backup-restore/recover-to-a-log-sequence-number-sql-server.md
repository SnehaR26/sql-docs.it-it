---
title: "Recupero fino a un numero di sequenza del file di log (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "numeri di sequenza del file di log [SQL Server]"
  - "STOPBEFOREMARK - opzione [istruzione RESTORE]"
  - "STOPATMARK - opzione [istruzione RESTORE]"
  - "recupero temporizzato [SQL Server]"
  - "ripristino dei database [SQL Server], temporizzazione"
  - "recupero [SQL Server], database"
  - "ripristino [SQL Server], temporizzazione"
  - "LSN"
  - "recupero del database [SQL Server]"
  - "ripristini di database [SQL Server], temporizzazione"
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
caps.latest.revision: 38
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 37
---
# Recupero fino a un numero di sequenza del file di log (SQL Server)
  Le informazioni contenute in questo argomento sono rilevanti solo per i database che utilizzano il modello di recupero con registrazione completa o con registrazione minima delle operazioni bulk.  
  
 È possibile utilizzare un numero di sequenza del file di log (LSN) per definire il punto di recupero per un'operazione di ripristino. Si tratta tuttavia di una funzionalità specializzata progettata per i fornitori di strumenti e viene utilizzata solo in rari casi.  
  
##  <a name="LSNs"></a> Panoramica dei numeri di sequenza del file di log  
 Gli LSN sono utilizzati internamente durante una sequenza RESTORE per tenere traccia del momento specifico rispetto al quale i dati sono stati ripristinati. Quando un backup viene ripristinato, i dati vengono ripristinati sull'LSN corrispondente al momento specifico di esecuzione del backup. Backup dei log e differenziali spostano il database ripristinato a un momento successivo, corrispondente a un LSN maggiore.  
  
 Ogni record presente nel log delle transazioni è identificato in modo univoco da un numero di sequenza dei file di log (LSN). Gli LSN sono ordinati in modo tale che se LSN è maggiore di LSN1, la modifica descritta dal record di log cui fa riferimento LSN2 si verifica dopo la modifica descritta dall'LSN del record di log.  
  
 L'LSN di un record di log in corrispondenza del quale si è verificato un evento significativo può essere utile per creare sequenze di ripristino corrette. Essendo ordinati, gli LSN possono essere confrontati in termini di uguaglianza e disuguaglianza, ovvero **\<**, **>**, **=**, **\<=**, **>=**. Questi confronti sono utili nella creazione di sequenze di ripristino.  
  
> [!NOTE]  
>  Gli LSN sono valori di tipo di dati **numerici**(25,0). Gli operatori matematici, ad esempio addizione o sottrazione, non sono significativi e non devono essere utilizzati con gli LSN.  
  
 [&#91;Torna all'inizio&#93;](#Top)  
  
## Visualizzazione degli LSN utilizzati tramite backup e ripristino  
 L'LSN di un record di log in corrispondenza del quale si è verificato un determinato evento di backup e di ripristino è visibile utilizzando una o più delle istruzioni seguenti:  
  
-   [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md); [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
-   [RESTORE HEADERONLY](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)  
  
-   [RESTORE FILELISTONLY](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)  
  
> [!NOTE]  
>  Gli LSN sono inoltre visualizzati nel testo di alcuni messaggi.  
  
## Sintassi Transact-SQL per il ripristino fino a un numero di sequenza del file di log (LSN)  
 Un'istruzione [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) consente di arrestare il processo esattamente in corrispondenza dell'LSN o immediatamente prima, come illustrato di seguito:  
  
-   Usare la clausola WITH STOPATMARK **='**lsn:*<numero_lsn>***'**, dove lsn:*\<Numerolsn>* è una stringa che specifica che il punto di recupero corrisponde al record di log contenente l'LSN specificato.  
  
     STOPATMARK esegue il rollforward al numero di sequenza del file di log (LSN) includendo anche tale record del log.  
  
-   Usare la clausola WITH STOPBEFOREMARK **='**lsn:*<numero_lsn>***'**, dove lsn:*\<Numerolsn>* è una stringa che specifica che il punto di recupero corrisponde al record di log immediatamente precedente a quello contenente l'LSN specificato.  
  
     Tramite STOPBEFOREMARK viene eseguito il rollforward fino all'LSN escludendo tale record di log.  
  
 In genere, viene selezionata una transazione specifica da includere o escludere. Sebbene non sia necessario, il record di log specificato è in pratica un record di commit delle transazioni.  
  
## Esempi  
 Nell'esempio seguente si presuppone che il database `AdventureWorks` sia stato modificato in modo da utilizzare il modello di recupero con registrazione completa.  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Ripristinare un backup del database tramite SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [Backup di un log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [Ripristinare un backup del log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [Ripristinare un database al punto di errore nel modello di recupero con registrazione completa &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore database to point of failure - full recovery.md)  
  
-   [Ripristinare un database fino a una transazione contrassegnata &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [Ripristinare un database di SQL Server fino a un punto specifico &#40;Modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## Vedere anche  
 [Applicare backup log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  