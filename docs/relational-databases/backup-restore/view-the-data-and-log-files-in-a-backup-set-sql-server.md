---
title: Visualizzare i file di dati e i file di log in un set di backup (SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database backups [SQL Server], viewing backup sets
- viewing backup set information
- backup sets [SQL Server], viewing files in
- displaying backup set information
- transaction log backups [SQL Server], viewing backup sets
- backing up [SQL Server], viewing backup sets
ms.assetid: abb6420c-f809-426e-aeb4-d0a74989cf39
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b315b0bc0d56cf0e618869f1eef69278fc0d6988
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="view-the-data-and-log-files-in-a-backup-set-sql-server"></a>Visualizzare i file di dati e i file di log in un set di backup (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In questo argomento viene descritto come visualizzare i file di log e di dati in un set di backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzare i file di dati e i file di log in un set di backup utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni sulla sicurezza, vedere [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md).  
  
####  <a name="Permissions"></a> Autorizzazioni  
 In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive, per ottenere informazioni su un set o un dispositivo di backup è necessario disporre dell'autorizzazione CREATE DATABASE. Per altre informazioni, vedere [GRANT - autorizzazioni per database &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a>Per visualizzare i file di dati e i file di log in un set di backup  
  
1.  Dopo aver stabilito la connessione all'istanza appropriata del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Esplora oggetti fare clic sul nome del server per espandere l'albero del server.  
  
2.  Espandere **Database**e, a seconda del database, selezionare un database utente o espandere **Database di sistema** e selezionare un database di sistema.  
  
3.  Fare clic con il pulsante destro del mouse sul database e quindi scegliere **Proprietà**per visualizzare la finestra di dialogo **Proprietà database** .  
  
4.  Nel riquadro **Selezione pagina** fare clic su **File**.  
  
5.  Nella griglia **File di database** è visualizzato un elenco dei file di dati e dei file di log e delle relative proprietà.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a>Per visualizzare i file di dati e i file di log in un set di backup  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Utilizzare l'istruzione [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md) . In questo esempio vengono restituite informazioni sul secondo set di backup (`FILE=2`) nel dispositivo di backup `AdventureWorksBackups` .  
  
```tsql  
USE AdventureWorks2012 ;  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [Dispositivi di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
  