---
title: "Esempio: Ripristino a fasi di filegroup selezionati (modello di recupero con registrazione minima) | Microsoft Docs"
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
  - "ripristino a fasi [SQL Server], modello di recupero con registrazione minima"
  - "sequenze di ripristino [SQL Server], ripristino a fasi"
  - "modello di recupero con registrazione minima [SQL Server], esempi RESTORE"
ms.assetid: d7ad026c-5355-4308-9560-0dc843940d4f
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Esempio: Ripristino a fasi di filegroup selezionati (modello di recupero con registrazione minima)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Le informazioni in questo argomento sono rilevanti per i database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che utilizzano il modello di recupero con registrazione minima e che contengono un filegroup di sola lettura.  
  
 Con una sequenza di ripristino a fasi, il database viene ripristinato e recuperato in varie fasi a livello di filegroup, partendo dal filegroup primario e da tutti i filegroup secondari in lettura/scrittura.  
  
 In questo esempio, un database denominato `adb`, che utilizza il modello di recupero con registrazione minima, contiene tre filegroup. Il filegroup `A` è in lettura/scrittura, mentre i filegroup `B` e `C` sono di sola lettura. Inizialmente, tutti i filegroup sono online.  
  
 Il filegroup primario e il filegroup `B` del database `adb` risultano danneggiati. L'amministrazione del database decide pertanto di ripristinarli con una sequenza di ripristino a fasi. Nel modello di recupero con registrazione minima, tutti i filegroup in lettura/scrittura devono essere ripristinati dallo stesso backup parziale. Sebbene sia intatto, il filegroup `A` deve essere ripristinato con il filegroup primario per assicurarne la consistenza. Il database verrà ripristinato fino al punto nel tempo corrispondente alla fine dell'ultimo backup parziale. Il filegroup `C` è intatto, ma è necessario recuperarlo per attivare la modalità online. Nel filegroup `B`, sebbene sia danneggiato, sono inclusi dati meno critici rispetto al filegroup `C`. Il filegroup `B`, pertanto, verrà ripristinato per ultimo.  
  
## Sequenze di ripristino  
  
> [!NOTE]  
>  La sintassi di una sequenza di ripristino online è la stessa di una sequenza di ripristino offline.  
  
1.  Ripristino parziale del filegroup primario e del filegroup `A` da un backup parziale.  
  
    ```  
    RESTORE DATABASE adb READ_WRITE_FILEGROUPS FROM partial_backup   
    WITH PARTIAL, RECOVERY  
    ```  
  
     A questo punto il filegroup primario e il filegroup `A` sono online. I file nei filegroup `B` e `C` sono in attesa di recupero e i filegroup sono offline.  
  
2.  Recupero online del filegroup `C`.  
  
     Il filegroup `C` è consistente poiché il backup parziale ripristinato in precedenza è stato creato dopo l'impostazione del filegroup `C` in modalità di sola lettura, anche se il ripristino ha portato il database in un momento anteriore nel tempo. L'amministratore del database recupera il filegroup `C`, senza ripristinarlo, per attivare la modalità online.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' WITH RECOVERY  
    ```  
  
     A questo punto il filegroup primario e i filegroup `A` e `C` sono online. I file del filegroupB restano in attesa di recupero, con il filegroup offline.  
  
3.  Ripristino online del filegroup `B.`  
  
     I file nel filegroup `B` devono essere ripristinati. L'amministratore del database ripristina il backup del filegroup `B` eseguito dopo l'impostazione del filegroup `B` in modalità di sola lettura e prima del backup parziale.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup   
    WITH RECOVERY  
    ```  
  
     In questa fase tutti i filegroup sono online.  
  
## Esempi aggiuntivi  
  
-   [Esempio: Ripristino a fasi di un database &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Esempio: Ripristino online di un file di sola lettura &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di un database &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di un numero limitato di filegroup &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Esempio: Ripristino online di un file di lettura/scrittura &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Esempio: Ripristino online di un file di sola lettura &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## Vedere anche  
 [Ripristino online &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Ripristini a fasi &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  