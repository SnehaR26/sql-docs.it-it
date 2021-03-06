---
title: sys.fn_get_sql (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_get_sql
- sys.fn_get_sql_TSQL
- fn_get_sql_TSQL
- sys.fn_get_sql
dev_langs:
- TSQL
helpviewer_keywords:
- fn_get_sql function
- text [SQL Server], SQL handles
- sys.fn_get_sql function
- valid SQL handles [SQL Server]
- SQL handles
ms.assetid: d5fe49b5-0813-48f2-9efb-9187716b2fd4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: db1c1d36bb3cb831a2f744a77529939894fff27a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842059"
---
# <a name="sysfngetsql-transact-sql"></a>sys.fn_get_sql (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il testo dell'istruzione SQL per l'handle SQL specificato.  
  
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa a partire da una delle prossime versioni di Microsoft SQL Server. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Utilizzare sys.dm_exec_sql_text. Per altre informazioni, vedere [DM exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md).  
  
 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_get_sql ( SqlHandle )  
```  
  
## <a name="arguments"></a>Argomenti  
 *SqlHandle*  
 Valore dell'handle. *SqlHandle* viene **varbinary(64)** non prevede alcun valore predefinito.  
  
## <a name="tables-returned"></a>Tabelle restituite  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|dbid|**smallint**|ID del database. Per istruzioni SQL ad hoc e preparate, l'ID del database in cui sono state compilate le istruzioni.|  
|objectid|**int**|ID dell'oggetto di database. Per istruzioni SQL ad hoc viene restituito NULL.|  
|number|**smallint**|Specifica il numero del gruppo, se le procedure sono raggruppate.<br /><br /> 0 = Le voci immesse non sono procedure.<br /><br /> NULL = Istruzioni SQL ad hoc.|  
|encrypted|**bit**|Specifica se l'oggetto è crittografato.<br /><br /> 0 = Non crittografato<br /><br /> 1 = Crittografato|  
|text|**text**|Testo dell'istruzione SQL. Per gli oggetti crittografati viene restituito NULL.|  
  
## <a name="remarks"></a>Note  
 È possibile ottenere un handle SQL valido dalla colonna sql_handle della [exec_requests &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) vista a gestione dinamica.  
  
 Se non si passa un handle che non è più presente nella cache, fn_get_sq**l** restituisce un set di risultati vuoto. Se si passa un handle non valido, il batch viene arrestato e viene visualizzato un messaggio di errore.  
  
 Il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] non è possibile memorizzare nella cache alcuni [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni, ad esempio istruzioni per la copia bulk e istruzioni con valori letterali di stringa superiori a 8 KB. Gli handle relativi a tali istruzioni non possono essere recuperati tramite fn_get_sql.  
  
 Il **testo** colonna del set di risultati viene filtrata per il testo che potrebbe includere password. Per altre informazioni sulla sicurezza relativa stored procedure che non vengono monitorate, vedere [filtrare una traccia](../../relational-databases/sql-trace/filter-a-trace.md).  
  
 La funzione fn_get_sql restituisce informazioni simili per il [DBCC INPUTBUFFER](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md) comando. Di seguito sono riportati due esempi di situazioni in cui è possibile utilizzare fn_get_sql e non DBCC INPUTBUFFER:  
  
-   Quando gli eventi includono più di 255 caratteri.  
  
-   Quando è necessario ottenere il livello di nidificazione massimo corrente di una stored procedure. Si supponga, ad esempio, che esistano due stored procedure denominate sp_1 e sp_2. Se sp_1 chiama sp_2 e si ottiene l'handle dalla vista a gestione dinamica sys.dm_exec_requests mentre sp_2 è in esecuzione, la funzione fn_get_sql restituirà informazioni su sp_2. Inoltre, la funzione fn_get_sql restituisce il testo completo della stored procedure al livello di nidificazione massimo corrente.  
  
## <a name="permissions"></a>Permissions  
 L'utente deve disporre dell'autorizzazione VIEW SERVER STATE nel server.  
  
## <a name="examples"></a>Esempi  
 Gli amministratori del database possono utilizzare la funzione fn_get_sql, come illustrato nell'esempio seguente, per individuare processi che causano problemi. Dopo avere identificato un ID di sessione che causa problemi, l'amministratore può recuperare l'handle SQL di tale sessione, chiamare la funzione fn_get_sql con tale handle e quindi utilizzare l'offset iniziale e quello finale per determinare il testo SQL dell'ID di sessione che crea problemi.  
  
```  
DECLARE @Handle varbinary(64);  
SELECT @Handle = sql_handle   
FROM sys.dm_exec_requests   
WHERE session_id = 52 and request_id = 0;  
SELECT * FROM sys.fn_get_sql(@Handle);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DBCC INPUTBUFFER &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)   
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
