---
title: "Disabilitare il backup gestito di SQL Server in Microsoft Azure | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e02187f-363f-4e69-a82f-583953592544
caps.latest.revision: 8
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 6
---
# Disabilitare il backup gestito di SQL Server in Microsoft Azure
  Questo argomento descrive come disabilitare o sospendere [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] a livello di database e di istanza.  
  
##  <a name="DatabaseDisable"></a> Disabilitare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per un database  
 È possibile disabilitare le impostazioni di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] usando la stored procedure di sistema [managed_backup.sp_backup_config_basic &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md). Il parametro *@enable_backup* consente di abilitare e disabilitare le configurazioni di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per un database specifico. Il valore 1 abilita e il valore 0 disabilita le impostazioni di configurazione.  
  
#### Per disabilitare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per un database specifico:  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
```  
EXEC msdb.managed_backup.sp_backup_config_basic  
                @database_name = 'TestDB'   
                ,@enable_backup = 0;  
GO  
  
```  
  
##  <a name="DatabaseAllDisable"></a> Disabilitare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per tutti i database dell'istanza  
 La procedura seguente viene utilizzata quando si desidera disabilitare le impostazioni di configurazione di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] da tutti i database con [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] abilitato attualmente nell'istanza.  Le impostazioni di configurazione come l'URL di archiviazione, la memorizzazione e le credenziali SQL rimarranno nei metadati ed è possibile usarle se si abilita [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per il database in un secondo momento. Se si vuole sospendere solo temporaneamente i servizi [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], è possibile usare l'opzione master descritta nelle sezioni successive di questo argomento.  
  
#### Per disabilitare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per tutti i database:  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. L'esempio seguente determina se [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è configurato a livello di istanza e tutti i database abilitati da [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nell'istanza ed esegue la stored procedure di sistema **sp_backup_config_basic** per disabilitare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
```  
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM   
  
       msdb.managed_backup.fn_backup_db_config (NULL)  
       WHERE is_managed_backup_enabled = 1  
  
       --Select DBName from @DBNames  
  
       select @rowid = min(RowID)  
       FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin  
  
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC msdb.managed_backup.sp_backup_config_basic    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END  
```  
  
 Per verificare le impostazioni di configurazione per tutti i database nell'istanza, utilizzare la query seguente:  
  
```  
Use msdb;  
GO  
SELECT * FROM managed_backup.fn_backup_db_config (NULL);  
GO  
  
```  
  
##  <a name="InstanceDisable"></a> Disabilitare le impostazioni predefinite di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per l'istanza  
 Le impostazioni predefinite a livello di istanza vengono applicate a tutti i nuovi database creati nell'istanza in questione.  Se le impostazioni predefinite non sono più necessarie o richieste, è possibile disabilitare questa configurazione usando la stored procedure di sistema **managed_backup.sp_backup_config_basic** con il parametro *@database_name* impostato su NULL. La disabilitazione non comporta la rimozione delle altre impostazioni di configurazione come l'URL di archiviazione, l'impostazione di memorizzazione o il nome delle credenziali SQL. Queste impostazioni verranno utilizzate se [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] viene abilitato per l'istanza in un secondo momento.  
  
#### Per disabilitare le impostazioni di configurazione predefinite di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    EXEC msdb.managed_backup.sp_backup_config_basic  
                    @database_name = 'TestDB'   
                    ,@enable_backup = 0;  
    GO  
  
    ```  
  
##  <a name="InstancePause"></a> Sospendere [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] a livello di istanza  
 In alcuni casi è possibile che sia necessario sospendere temporaneamente i servizi [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per un breve periodo.  La stored procedure di sistema **managed_backup.sp_backup_master_switch** consente di disabilitare il servizio [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] a livello di istanza.  La stessa stored procedure viene utilizzata per riprendere [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Il parametro @state viene utilizzato per definire se [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] deve essere disabilitato o abilitato.  
  
#### Per sospendere i servizi [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] tramite Transact-SQL:  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### Per riprendere [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] tramite Transact-SQL  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
```  
Use msdb;  
Go  
EXEC managed_backup. sp_backup_master_switch @new_state=1;  
GO  
  
```  
  
## Vedere anche  
 [Abilitare il backup gestito di SQL Server in Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md)  
  
  