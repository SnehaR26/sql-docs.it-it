---
title: Configurare le opzioni avanzate per il backup gestito di SQL Server in Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: ffd28159-8de8-4d40-87da-1586bfef3315
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 044e52311bbdb21f1a7f144a2b6f25809ea33ade
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610179"
---
# <a name="configure-advanced-options-for-sql-server-managed-backup-to-microsoft-azure"></a>Configurare le opzioni avanzate per il backup gestito di SQL Server in Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'esercitazione seguente descrive come impostare le opzioni avanzate per [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Queste procedure sono necessarie solo se servono le funzionalità offerte. In caso contrario, è possibile abilitare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] e affidarsi al comportamento predefinito.  
  
 In ogni scenario, il backup viene specificato con il parametro `database_name` . Quando `database_name` è NULL o *, le modifiche interessano le impostazioni predefinite a livello di istanza. Le impostazioni a livello di istanza influiscono anche sui nuovi database creati dopo la modifica.  
  
 Dopo aver specificato queste impostazioni, è possibile abilitare il backup gestito per il database o l'istanza usando la stored procedure di sistema [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md). Per altre informazioni, vedere [Abilitare il backup gestito di SQL Server in Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md).  
  
> [!WARNING]  
>  È sempre opportuno configurare le opzioni avanzate e le opzioni di pianificazione personalizzate prima di abilitare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] con [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md). In caso contrario, è possibile che si verifichino operazioni di backup indesiderate durante il periodo di tempo che intercorre tra l'abilitazione di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] e la configurazione di queste impostazioni.  
  
## <a name="configure-encryption"></a>Configurare la crittografia  
 I passaggi seguenti descrivono come specificare le impostazioni di crittografia usando la stored procedure [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md).  
  
1.  **Determinare l'algoritmo di crittografia**: stabilire prima di tutto il nome dell'algoritmo di crittografia da usare. Selezionare uno degli algoritmi seguenti:  
  
    -   AES_128  
  
    -   AES_192  
  
    -   AES_256  
  
    -   TRIPLE_DES_3KEY  
  
    -   NO_ENCRYPTION  
  
2.  **Creare una chiave master del database:** scegliere una password per crittografare la copia della chiave master che verrà archiviata nel database.  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
       CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
    ```  
  
3.  **Creare un certificato o una chiave asimmetrica per il backup:** è possibile usare un certificato o una chiave asimmetrica da usare con la crittografia. L'esempio seguente crea un certificato di backup da usare per la crittografia.  
  
    ```sql  
    USE Master;  
    GO  
       CREATE CERTIFICATE MyTestDBBackupEncryptCert  
          WITH SUBJECT = 'MyTestDBBackupEncryptCert';  
    GO  
    ```  
  
4.  **Impostare la crittografia per il backup gestito:** chiamare la stored procedure **managed_backup.sp_backup_config_advanced** con i valori corrispondenti. L'esempio seguente configura ad esempio il database `MyDB` per la crittografia con un certificato denominato `MyTestDBBackupEncryptCert` e l'algoritmo di crittografia `AES_128` .  
  
    ```  
    USE msdb;  
    GO  
       EXEC managed_backup.sp_backup_config_advanced  
          @database_name = 'MyDB'                
          ,@encryption_algorithm ='AES_128'  
          ,@encryptor_type = 'CERTIFICATE'  
          ,@encryptor_name = 'MyTestDBBackupEncryptCert';  
    GO  
    ```  
  
    > [!WARNING]  
    >  Se `@database_name` è NULL nell'esempio precedente, le impostazioni vengono applicate all'istanza di SQL Server.  
  
## <a name="configure-a-custom-backup-schedule"></a>Configurare una pianificazione di backup personalizzata  
 I passaggi seguenti descrivono come impostare una pianificazione personalizzata usando la stored procedure [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md).  
  
1.  **Determinare la frequenza per i backup completi:** stabilire con quale frequenza eseguire backup completi del database. È possibile scegliere tra 'Daily' e 'Weekly' per i backup completi.  
  
2.  **Determinare la frequenza per i backup del log:** stabilire con quale frequenza eseguire un backup del log. Il valore è espresso in minuti o ore.  
  
3.  **Determinare il giorno della settimana per i backup settimanali:** se il backup è settimanale, scegliere un giorno della settimana per il backup completo.  
  
4.  **Determinare l'ora di inizio per il backup:** scegliere l'ora di inizio del backup usando il formato 24 ore.  
  
5.  **Determinare la durata consentita per il backup:** specificare il periodo di tempo entro il quale deve essere completato un backup.  
  
6.  **Impostare una pianificazione personalizzata per il backup:** la stored procedure seguente definisce una pianificazione personalizzata per il database `MyDB` . I backup completi vengono eseguiti settimanalmente il giorno `Monday` alle `17:30`. I backup del log vengono eseguiti ogni `5` minuti. Per il completamento del backup sono previste due ore.  
  
    ```  
    USE msdb;  
    GO  
    EXEC managed_backup.sp_backup_config_schedule   
         @database_name =  'MyDB'  
        ,@scheduling_option = 'Custom'  
        ,@full_backup_freq_type = 'Weekly'  
        ,@days_of_week = 'Monday'  
        ,@backup_begin_time =  '17:30'  
        ,@backup_duration = '02:00'  
        ,@log_backup_freq = '00:05'  
    GO  
  
    ```  
  
## <a name="next-steps"></a>Next Steps  
 Dopo aver configurato le opzioni avanzate e le pianificazioni personalizzate, è necessario abilitare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nel database di destinazione o nell'istanza di SQL Server. Per altre informazioni, vedere [Abilitare il backup gestito di SQL Server in Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Backup gestito di SQL Server in Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
