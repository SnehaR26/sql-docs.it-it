---
title: sp_dbmmonitorchangemonitoring (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorchangemonitoring
- sp_dbmmonitorchangemonitoring_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_dbmmonitorchangemonitoring
- database mirroring [SQL Server], monitoring
ms.assetid: 17be755b-673d-4cd4-9544-6ecb4220bed3
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c640f9306d8fe4a484d453bd3846da2e58a25e62
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="spdbmmonitorchangemonitoring-transact-sql"></a>sp_dbmmonitorchangemonitoring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cambia il valore di un parametro del monitoraggio di mirroring del database.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dbmmonitorchangemonitoring parameter  
    , value   
```  
  
## <a name="arguments"></a>Argomenti  
 *parametro*  
 Specifica l'identificatore del parametro da modificare. È attualmente disponibile solo il parametro seguente:  
  
 1 = Periodo di aggiornamento  
  
 Numero di minuti tra gli aggiornamenti della tabella di stato di mirroring del database. L'intervallo predefinito è 1 minuto.  
  
 *Valore*  
 Specifica il nuovo valore per il parametro da modificare.  
  
|Parametro|Descrizione del valore|  
|---------------|--------------------------|  
|1|Valore intero compreso nell'intervallo da 1 a 120 che specifica un nuovo periodo di aggiornamento in minuti.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il periodo di aggiornamento viene modificato in 5 minuti.  
  
```  
EXEC sp_dbmmonitorchangemonitoring 1, 5 ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitoraddmonitoring &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  