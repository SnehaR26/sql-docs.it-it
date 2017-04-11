---
title: "Risolvere i problemi relativi a un log delle transazioni completo (Errore di SQL Server 9002) | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-transaction-log"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "log [SQL Server], completi"
  - "risoluzione dei problemi [SQL Server], log delle transazioni completo"
  - "9002 (errore del motore di database)"
  - "log delle transazioni [SQL Server], troncamento"
  - "backup dei log delle transazioni [SQL Server], log completi"
  - "log delle transazioni [SQL Server], log completo"
  - "log delle transazioni completi [SQL Server]"
ms.assetid: 0f23aa84-475d-40df-bed3-c923f8c1b520
caps.latest.revision: 59
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 59
---
# Risolvere i problemi relativi a un log delle transazioni completo (Errore di SQL Server 9002)
  In questo argomento vengono illustrate le risposte possibili a un log delle transazioni pieno e viene spiegato come evitare tale situazione in futuro. 
  
  Quando il log delle transazioni è pieno,[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] genera un **errore 9002**. Il log può riempirsi quando il database è online o in stato di recupero. Se il log si riempie quando il database è online, quest'ultimo rimane online anche se potrà soltanto essere letto, non aggiornato. Se il log si riempie durante il recupero, in [!INCLUDE[ssDE](../../includes/ssde-md.md)] il database viene contrassegnato come RESOURCE PENDING. In entrambi i casi, è richiesto che l'utente intervenga per liberare spazio nel log.  
  
## Risposta a un log delle transazioni completo  
 La risposta appropriata a un log delle transazioni pieno dipende in parte dalla condizione o dalle condizioni che hanno causato il riempimento del log. 
 
 Per individuare la condizione che impedisce il troncamento del log in un caso specifico, usare le colonne **log_reuse_wait** e **log_reuse_wait_desc** della vista del catalogo **sys.database**. Per altre informazioni, vedere [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md). Per le descrizioni dei fattori che possono ritardare il troncamento del log, vedere [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
> **IMPORTANTE**  
>  Se l'errore 9002 si è verificato durante il recupero del database, risolvere il problema, quindi recuperare il database tramite [ALTER DATABASE *nome_database* SET ONLINE.](https://msdn.microsoft.com/library/bb522682.aspx)  
  
 Per gestire un log delle transazioni pieno sono disponibili le soluzioni alternative seguenti:  
  
-   Esecuzione del backup del log  
  
-   Aumento dello spazio libero su disco in modo che le dimensioni del log possano aumentare automaticamente  
  
-   Spostamento del file di log in un'unità disco con spazio sufficiente  
  
-   Aumento delle dimensioni di un file di log  
  
-   Aggiunta di un file di log in un altro disco  
  
-   Completamento o termine di una transazione con esecuzione prolungata.  
  
 Queste soluzioni alternative verranno illustrate nelle sezioni successive. Scegliere la risposta più appropriata a seconda della situazione.  
  
## Eseguire il backup del log  
 Nel modello di recupero con registrazione completa o nel modello di recupero con registrazione minima delle operazioni bulk, se non è stato eseguito il backup del log delle transazioni di recente, è possibile che sia il backup a impedire il troncamento del log. Se il backup del log non è mai stato eseguito, è **necessario creare due backup del log** per consentire a [!INCLUDE[ssDE](../../includes/ssde-md.md)] di troncare il log in corrispondenza del punto dell'ultimo backup. Il troncamento del log consente di rendere disponibile spazio per nuovi record del log. Per evitare che il log si riempia di nuovo, eseguire backup del log frequenti.  
  
 **Per creare un backup del log delle transazioni**  
  
> **IMPORTANTE**  
>  Se il database è danneggiato, vedere [Backup della parte finale del log &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).  
  
-   [Backup di un log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)  
  
### Aumento dello spazio disponibile su disco  
 Potrebbe essere possibile liberare spazio sull'unità disco contenente il file del log delle transazioni per il database, eliminando o spostando altri file. L'aumento dello spazio disponibile su disco consente al sistema di recupero di ingrandire automaticamente il file di log.  
  
### Spostare il file di log in un altro disco  
 Se non é possibile liberare spazio su disco sufficiente nell'unità che attualmente contiene il file di log, prendere in considerazione lo spostamento del file in un'altra unità con spazio adeguato.  
  
> **IMPORTANTE** È consigliabile non memorizzare mai file di log in file system compressi.  
  
 **Spostare un file di log**  
  
-   [Spostare file del database](../../relational-databases/databases/move-database-files.md)  
  
### Aumentare le dimensioni del file di log  
 Se nel disco del log è disponibile spazio, è possibile aumentare le dimensioni del file di log. La dimensione massima per i file di log è due terabyte per file di log.  
  
 **Aumentare le dimensioni del file**  
  
 Se l'aumento automatico dimensioni è disabilitato, il database è online ed è disponibile spazio sufficiente sul disco, eseguire una delle operazioni seguenti:  
  
-   Aumentare manualmente le dimensioni del file per produrre un incremento di crescita singolo.  
  
-   Abilitare l'aumento automatico dimensioni utilizzando l'istruzione ALTER DATABASE per impostare un incremento di crescita diverso da zero per l'opzione FILEGROWTH.  
  
> **NOTA:** in entrambi i casi, se sono state raggiunte le dimensioni massime consentite correnti, aumentare il valore MAXSIZE.  
  
### Aggiungere un file di log a un altro disco  
 Aggiungere un nuovo file di log al database in un altro disco contenente spazio sufficiente utilizzando ALTER DATABASE <database_name> ADD LOG FILE.  
  
 **Aggiungere un file di log**  
  
-   [Aggiungere file di dati o file di log a un database](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)  
## Completare o terminare una transazione a esecuzione prolungata
### Individuare le transazioni a esecuzione prolungata
Una transazione a esecuzione molto prolungata può comportare il riempimento del log delle transazioni. Per individuare le transazioni con esecuzione prolungata, utilizzare una delle alternative seguenti:
 - **[sys.dm_tran_database_transactions](https://msdn.microsoft.com/library/ms186957.aspx).**
Questa vista a gestione dinamica restituisce informazioni sulle transazioni a livello di database. Per una transazione a esecuzione prolungata, le colonne particolarmente rilevanti sono quelle che indicano l'ora del primo record di log [(database_transaction_begin_time)](https://msdn.microsoft.com/library/ms186957.aspx), lo stato corrente della transazione [(database_transaction_state)](https://msdn.microsoft.com/library/ms186957.aspx) e il [numero di sequenza del file di log (LSN)](https://msdn.microsoft.com/library/ms191459.aspx) del record iniziale nel log delle transazioni [(database_transaction_begin_lsn)](https://msdn.microsoft.com/library/ms186957.aspx).

 - **[DBCC OPENTRAN](https://msdn.microsoft.com/library/ms182792.aspx).**
Questa istruzione consente di identificare l'ID utente del proprietario della transazione, in modo da risalire, se lo si desidera, all'origine della transazione per terminarla in modo più appropriato, ovvero tramite il commit invece del rollback.

### Terminare una transazione
In alcuni casi è necessario terminare il processo usando l'istruzione [KILL](https://msdn.microsoft.com/library/ms173730.aspx). Usare l'istruzione con cautela, soprattutto quando sono in esecuzione processi importanti che non vanno terminati. Per altre informazioni, vedere [KILL (Transact-SQL)](https://msdn.microsoft.com/library/ms173730.aspx)

## Vedere anche  
[Articolo di supporto della Knowledge Base - Il log delle transazioni aumenta in modo imprevisto o diventa pieno in SQL Server](https://support.microsoft.com/en-us/kb/317375)
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Gestione delle dimensioni del file di log delle transazioni](../../relational-databases/logs/manage-the-size-of-the-transaction-log-file.md)   
 [Backup di log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)   
 [sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql.md)  
  
  