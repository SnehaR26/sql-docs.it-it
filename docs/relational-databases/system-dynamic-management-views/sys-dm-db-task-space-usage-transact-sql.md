---
title: sys.dm_db_task_space_usage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_task_space_usage_TSQL
- sys.dm_db_task_space_usage_TSQL
- dm_db_task_space_usage
- sys.dm_db_task_space_usage
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_task_space_usage dynamic management view
ms.assetid: fb0c87e5-43b9-466a-a8df-11b3851dc6d0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7ab12b9a0c042b96803e44c479a68a110a3c560b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806739"
---
# <a name="sysdmdbtaskspaceusage-transact-sql"></a>sys.dm_db_task_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce informazioni sulle allocazioni e deallocazioni delle pagine per ogni attività per il database.  
  
> [!NOTE]  
>  Questa vista è applicabile solo per i [database tempdb](../../relational-databases/databases/tempdb-database.md).  
  
> [!NOTE]  
>  Per chiamare questo elemento dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oppure [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], usare il nome **sys.dm_pdw_nodes_db_task_space_usage**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|ID di sessione.|  
|**request_id**|**int**|ID di richiesta all'interno della sessione.<br /><br /> Una richiesta è anche chiamata batch e può contenere una o più query. Una sessione può contenere più richieste attive contemporaneamente. Ogni query nella richiesta può avviare più thread (attività), se si utilizza un piano di esecuzioni parallele.|  
|**exec_context_id**|**int**|ID del contesto di esecuzione dell'attività. Per altre informazioni, vedere [DM os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md).|  
|**database_id**|**smallint**|ID del database.|  
|**user_objects_alloc_page_count**|**bigint**|Numero di pagine riservate o allocate per gli oggetti utente dall'attività.|  
|**user_objects_dealloc_page_count**|**bigint**|Numero di pagine deallocate e non più riservate per gli oggetti utente dall'attività.|  
|**internal_objects_alloc_page_count**|**bigint**|Numero di pagine riservate o allocate per gli oggetti interni dall'attività.|  
|**internal_objects_dealloc_page_count**|**bigint**|Numero di pagine deallocate e non più riservate per gli oggetti interni dall'attività.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo in questa distribuzione.|  
  
## <a name="permissions"></a>Permissions

Sul [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è necessario `VIEW SERVER STATE` autorizzazione.   
Sul [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], è necessario il `VIEW DATABASE STATE` autorizzazione nel database.   

## <a name="remarks"></a>Note  
 Le pagine IAM non sono incluse nei conteggi di pagine restituiti da questa vista.  
  
 I contatori di pagine vengono inizializzati a zero (0) all'inizio di una richiesta. Questi valori vengono aggregati a livello di sessione quando la richiesta viene completata. Per altre informazioni, vedere [sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md).  
  
 La memorizzazione nella cache delle tabelle di lavoro e delle tabelle temporanee nonché le operazioni di rimozione posticipata influiscono sul numero di pagine allocate e deallocate in una determinata attività.  
  
## <a name="user-objects"></a>Oggetti utente  
 Gli oggetti seguenti vengono inclusi nei contatori di pagine degli oggetti utente:  
  
-   Tabelle e indici definiti dall'utente  
  
-   Tabelle e indici di sistema  
  
-   Tabelle e indici temporanei globali  
  
-   Tabelle e indici temporanei locali  
  
-   Variabili di tabella  
  
-   Tabelle restituite nelle funzioni con valori di tabella  
  
## <a name="internal-objects"></a>Oggetti interni  
 Gli oggetti interni sono solo in **tempdb**. Gli oggetti seguenti vengono inclusi nei contatori di pagine degli oggetti interni:  
  
-   Tabelle di lavoro per le operazioni di spooling o di cursore e l'archiviazione di LOB (Large Object) temporanei.  
  
-   File di lavoro per le operazioni quali un hash join  
  
-   Operazioni di ordinamento  
  
## <a name="physical-joins"></a>Join fisici  
 ![Join fisici per sys.dm_db_session_task_usage](../../relational-databases/system-dynamic-management-views/media/join-dm-db-task-space-usage-1.gif "join fisici per sys.dm_db_session_task_usage")  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|dm_db_task_space_usage.request_id|dm_exec_requests.request_id|Uno-a-uno|  
|dm_db_task_space_usage.session_id|dm_exec_requests.session_id|Uno-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)   
 [sys.dm_db_file_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  


