---
title: log_shipping_secondary (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary
- log_shipping_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary system table
ms.assetid: 69723419-4544-49c6-a517-adb30ffa5741
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c65e57f65311a01a337594b702cc4dc19d35f321
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815171"
---
# <a name="logshippingsecondary-transact-sql"></a>log_shipping_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia un record per ogni ID secondario. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**secondary_id**|**uniqueidentifier**|ID del server secondario nella configurazione per il log shipping.|  
|**primary_server**|**sysname**|Nome dell'istanza primaria del Motore di database di SQL Server nella configurazione di log shipping.|  
|**primary_database**|**sysname**|Nome del database primario nella configurazione di log shipping.|  
|**backup_source_directory**|**nvarchar(500)**|Directory in cui vengono archiviati i file di backup del log delle transazioni dal server primario.|  
|**backup_destination_directory**|**nvarchar(500)**|Directory nel server secondario in cui vengono copiati i file di backup.|  
|**file_retention_period**|**int**|Durata di tempo, in minuti, durante la quale un file di backup viene mantenuto nel server secondario prima di essere eliminato.|  
|**copy_job_id**|**uniqueidentifier**|ID associato al processo di copia nel server secondario.|  
|**restore_job_id**|**uniqueidentifier**|ID associato al processo di ripristino nel server secondario.|  
|**monitor_server**|**sysname**|Il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utilizzato come server di monitoraggio nella configurazione di log shipping.|  
|**monitor_server_security_mode**|**bit**|Modalità di sicurezza utilizzata per connettersi al server di monitoraggio.<br /><br /> 1 = Autenticazione di Windows.<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione.|  
|**last_copied_file**|**nvarchar(500)**|Nome dell'ultimo file di backup copiato nel server secondario.|  
|**last_copied_date**|**datetime**|Data e ora dell'ultima operazione di copia nel server secondario.|  
  
## <a name="remarks"></a>Note  
 Più database secondari nello stesso server secondario per un determinato database primario condividono alcune impostazioni nella **log_shipping_secondary** tabella. Se una impostazione condivisa viene modificata per uno dei database, l'impostazione viene modificata per tutti i database.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [Tabelle di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
