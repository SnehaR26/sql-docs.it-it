---
title: sp_help_targetserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_targetserver_TSQL
- sp_help_targetserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_targetserver
ms.assetid: f841d3bd-901a-4980-ad0b-1c6eeba3f717
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aacb30e4c809f965635b9d8640d8fcd690cd340f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747429"
---
# <a name="sphelptargetserver-transact-sql"></a>sp_help_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza un elenco di tutti i server di destinazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_targetserver   
     [ [ @server_name = ] 'server_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@server_name=** ] **'***nome_server***'**  
 Nome della colonna per cui restituire informazioni. *nome_server* viene **nvarchar(30)**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Se *nome_server* non viene specificato, **sp_help_targetserver** restituisce questo set di risultati.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Numero di identificazione del server.|  
|**server_name**|**nvarchar(30)**|Nome del server.|  
|**Posizione**|**nvarchar(200)**|Posizione del server specificato.|  
|**time_zone_adjustment**|**int**|Regolazione del fuso orario, in ore, rispetto all'ora di Greenwich (GMT).|  
|**enlist_date**|**datetime**|Data di integrazione del server specificato.|  
|**last_poll_date**|**datetime**|Data dell'ultimo polling del server per l'individuazione dei processi.|  
|**status**|**int**|Stato del server specificato.|  
|**unread_instructions**|**int**|Indica se il server include istruzioni non lette. Se tutte le righe sono state scaricate, questa colonna viene **0**.|  
|**local_time**|**datetime**|Data e ora locali del server di destinazione, basata sull'ora locale del server di destinazione rilevata durante l'ultimo polling del server master.|  
|**enlisted_by_nt_user**|**Nvarchar(100)**|Utente di Microsoft Windows che ha eseguito l'integrazione del server di destinazione.|  
|**poll_interval**|**int**|Frequenza espressa in secondi con cui il server di destinazione esegue il polling del servizio SQLServerAgent principale per il download dei processi e il caricamento dello stato dei processi.|  
  
## <a name="permissions"></a>Permissions  
 Per eseguire questa stored procedure, è necessario che gli utenti siano membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-information-for-all-registered-target-servers"></a>A. Visualizzazione dell'elenco delle informazioni per tutti i server di destinazione registrati  
 Nell'esempio seguente vengono visualizzate le informazioni relative a tutti i server di destinazione registrati.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-target-server"></a>B. Visualizzazione dell'elenco delle informazioni per un server di destinazione specifico  
 Nell'esempio seguente vengono visualizzate le informazioni relative al server di destinazione `SEATTLE2`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_delete_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [dbo.sysdownloadlist &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysdownloadlist-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
