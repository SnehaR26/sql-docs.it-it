---
title: Monitorare e risolvere i problemi relativi alla migrazione dei dati (Estensione database) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 06/14/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, monitoring
- monitoring Stretch Database
ms.assetid: 06950858-8c02-4ec6-9c59-42b787316a2d
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 91c10b51a3fec9ccc96c3aa23100abdf2a60ba81
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="monitor-and-troubleshoot-data-migration-stretch-database"></a>Monitorare e risolvere i problemi relativi alla migrazione dei dati (Estensione database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Per monitorare la migrazione dei dati in Monitoraggio dell'estensione database, selezionare **Attività | Estensione | Monitoraggio** per un database in SQL Server Management Studio.  
  
## <a name="check-the-status-of-data-migration-in-the-stretch-database-monitor"></a>Controllare lo stato della migrazione dei dati in Stretch Database Monitor  
 Selezionare **Attività | Estensione | Monitoraggio** per un database in SQL Server Management Studio per aprire Monitoraggio dell'estensione database e monitorare la migrazione dei dati.  
  
-   Nella parte superiore della finestra di monitoraggio vengono visualizzate informazioni generali sul database SQL Server abilitato per l'estensione e sul database Azure remoto.  
  
-   Nella parte inferiore viene visualizzato lo stato della migrazione dei dati per ogni tabella abilitata per l'estensione nel database.  
  
 ![Monitoraggio di Estensione database](../../sql-server/stretch-database/media/stretch-monitor.PNG "Monitoraggio di Estensione database")  
  
##  <a name="Migration"></a> Controllare lo stato della migrazione dei dati in una DMV  
 Aprire la DMV **sys.dm_db_rda_migration_status** per visualizzare il numero di batch e righe di dati di cui è stata eseguita la migrazione. Per altre informazioni, vedere [sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md).  
  
##  <a name="Firewall"></a> Risolvere i problemi relativi alla migrazione dei dati  
 **Non viene eseguita la migrazione in Azure delle righe dalla tabella abilitata per l'estensione. Qual è il problema?**  
 Esistono diversi problemi che possono influire sulla migrazione. Verificare quanto segue.  
  
-   Verificare la connettività di rete per il computer SQL Server.  
  
-   Verificare che il firewall di Azure non impedisca a SQL Server di connettersi all'endpoint remoto.  
  
-   Verificare lo stato dell'ultimo batch nella DMV **sys.dm_db_rda_migration_status** . Se si è verificato un errore, controllare i valori error_number, error_state, ed error_severity per il batch.  
  
    -   Per altre informazioni sulla vista, vedere [sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md).  
  
    -   Per altre informazioni sul contenuto di un messaggio di errore di SQL Server, vedere [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md).  
  
 **Il firewall di Azure blocca le connessioni dal server locale.**  
 Può essere necessario aggiungere una regola nelle impostazioni del firewall di Azure del server di Azure per consentire a SQL Server di comunicare con il server remoto di Azure.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione e risoluzione dei problemi di Estensione database](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
  
