---
title: "Backup di sola copia (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "08/10/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backup di sola copia [SQL Server]"
  - "COPY_ONLY - opzione [istruzione BACKUP]"
  - "backup [SQL Server], sola copia"
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
caps.latest.revision: 48
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 47
---
# Backup di sola copia (SQL Server)
  Un *backup di sola copia* è un backup di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indipendente dalla sequenza di backup convenzionali di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In genere, l'esecuzione di un backup comporta la modifica del database e influisce sulla modalità di ripristino dei backup successivi. In alcuni casi, tuttavia, è utile eseguire un backup per uno scopo speciale senza influire sulle procedure generali di backup e ripristino del database. I backup di sola copia hanno questo scopo.  
  
 I tipi di backup di sola copia sono i seguenti:  
  
-   Backup completi di sola copia (tutti i modelli di recupero)  
  
     Un backup di sola copia non può essere utilizzato come base differenziale o come backup differenziale e non influisce sulla base differenziale.  
  
     Ripristinare un backup completo di sola copia equivale al ripristino di un qualsiasi altro backup completo.  
  
-   Backup del log di sola copia (solo modello di recupero con registrazione completa e modello di recupero con registrazione minima delle operazioni bulk)  
  
     Un backup del log di sola copia mantiene il punto di archiviazione del log esistente e pertanto non influisce sulla sequenza dei backup del log regolari. I backup del log di sola copia in genere non sono necessari. È invece possibile creare un nuovo backup del log di routine (con WITH NORECOVERY) e quindi utilizzare il backup in questione insieme a tutti i backup del log precedenti necessari per la sequenza di ripristino. Tuttavia, un backup del log di sola copia può talvolta essere utile per eseguire un ripristino in linea. Per un esempio di questo, vedere [Esempio: Ripristino online di un file di lettura/scrittura &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md).  
  
     Il log delle transazioni non viene mai troncato dopo un backup di sola copia.  
  
 I backup di sola copia vengono registrati nella colonna **is_copy_only** della tabella [backupset](../../relational-databases/system-tables/backupset-transact-sql.md).  
  
## Per creare un backup di sola copia  
 È possibile creare un backup di sola copia utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o PowerShell.  

### Esempi  
###  <a name="SSMSProcedure"></a> A.  Utilizzo di SQL Server Management Studio  
In questo esempio verrà eseguito il backup di sola copia su disco del database `Sales` nel percorso di backup predefinito.

1.  In **Esplora oggetti**connettersi a un'istanza del motore di database di SQL Server e, successivamente, espanderla.

2.  Espandere i **database**, fare clic con il pulsante destro del mouse su `Sales`, scegliere **Attività**, quindi fare clic su **Backup...**.

3.  Nella pagina **Generale** della sezione **Origine** selezionare la casella di controllo **Backup di sola copia**.

4.  Scegliere **OK**.

  
###  <a name="TsqlProcedure"></a>B.  Utilizzo di Transact-SQL  
Questo esempio crea un backup di sola copia per il database `Sales` usando il parametro COPY_ONLY.  Viene eseguito anche un backup di sola copia del log delle transazioni.

```tsql
BACKUP DATABASE Sales
TO DISK = 'E:\BAK\Sales_Copy.bak'
WITH COPY_ONLY;

BACKUP LOG Sales
TO DISK = 'E:\BAK\Sales_LogCopy.trn'
WITH COPY_ONLY;
```
  
> [!NOTE]  
> L'opzione COPY_ONLY non ha alcun effetto quando specificata con l'opzione DIFFERENTIAL.  

  
###  <a name="PowerShellProcedure"></a>C.  Utilizzo di PowerShell  
Questo esempio crea un backup di sola copia per il database `Sales` usando il parametro CopyOnly.  
```powershell
Backup-SqlDatabase -ServerInstance 'SalesServer' -Database 'Sales' -BackupFile 'E:\BAK\Sales_Copy.bak' -CopyOnly
```  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per creare un backup completo o del log**  
  
-   [Creazione di un backup completo del database &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [Backup di un log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 **Per visualizzare backup di sola copia**  
  
-   [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
 [&#91;Torna all'inizio&#93;](#Top)  
  
## Vedere anche  
 [Panoramica del backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [Copiare database tramite backup e ripristino](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Panoramica del ripristino e del recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)  
[BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
[Backup-SqlDatabase](https://technet.microsoft.com/library/mt683378.aspx)

  