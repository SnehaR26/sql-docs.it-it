---
title: sp_refresh_log_shipping_monitor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refresh_log_shipping_monitor
- sp_refresh_log_shipping_monitor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refresh_log_shipping_monitor
ms.assetid: edefb912-31c5-4d99-9aba-06629afd0171
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4382dc4de4010944e60cb37640759e91a0fc2727
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851559"
---
# <a name="sprefreshlogshippingmonitor-transact-sql"></a>sp_refresh_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa stored procedure aggiorna le tabelle di monitoraggio remote in base alle informazioni più recenti recuperate da un server primario o secondario specificato per l'agente di log shipping specificato. La procedura viene richiamata dal server primario o secondario.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_refresh_log_shipping_monitor  
[ @agent_id = ] 'agent_id',  
[ @agent_type = ] 'agent_type'  
[ @database = ] 'database'  
[ @mode ] n  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@agent_id=** ] **'***agent_id***'**  
 ID primario per il backup o ID secondario per la copia o il ripristino. *agent_id* viene **uniqueidentifier** e non può essere NULL.  
  
 [  **@agent_type=** ] **'***agent_type***'**  
 Tipo di processo di log shipping.  
  
 0 = backup.  
  
 1 = copia.  
  
 2 = ripristino.  
  
 *agent_type* viene **tinyint** e non può essere NULL.  
  
 [  **@database=** ] **'***database***'**  
 Database primario o secondario utilizzato dagli agenti di registrazione in base al backup o di ripristino.  
  
 [ **@mode** ] *n*  
 Specifica se aggiornare i dati di monitoraggio oppure eliminarli. Il tipo di dati *m* è tinyint e i valori supportati sono:  
  
 1 = aggiornamento (valore predefinito)  
  
 2 = delete  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuna.  
  
## <a name="remarks"></a>Note  
 **sp_refresh_log_shipping_monitor** consente di aggiornare il **log_shipping_monitor_primary**, **log_shipping_monitor_secondary**, **log_shipping_monitor_history_detail** , e **log_shipping_monitor_error_detail** tabelle con le informazioni sulla sessione che non è già stata trasferita. Ciò consente di sincronizzare il server di monitoraggio con il server primario o secondario nel caso in cui il server di monitoraggio non sia più in sincronia. Consente inoltre di eliminare le informazioni di monitoraggio nel server di monitoraggio, se necessario.  
  
 **sp_refresh_log_shipping_monitor** deve essere eseguita la **master** database nel server primario o secondario.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server può eseguire questa procedura.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
