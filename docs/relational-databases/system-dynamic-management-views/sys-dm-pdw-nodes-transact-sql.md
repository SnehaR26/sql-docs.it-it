---
title: sys.dm_pdw_nodes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ff3f6c31389622dc424c42e06bfa78477c70cde2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769369"
---
# <a name="sysdmpdwnodes-transact-sql"></a>sys.dm_pdw_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutti i nodi in [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]. Elenca una riga per ogni nodo nell'appliance.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Id numerico univoco associato al nodo.<br /><br /> Chiave per questa visualizzazione.|Deve essere univoco nell'intera appliance, indipendentemente dal tipo.|  
|Tipo|**nvarchar(32)**|Tipo del nodo.|'GESTIONE DI CALCOLO', 'CONTROL',' '|  
|NAME|**nvarchar(32)**|Nome logico del nodo.|Qualsiasi stringa di lunghezza appropriato.|  
|address|**nvarchar(32)**|Indirizzo IP del nodo.|Nel formato [0-255]. [0-255]. [0-255]. [0-255].|  
|is_passive|**int**|Indica se la macchina virtuale che esegue il nodo è in esecuzione sul server assegnato o ha eseguito il failover al server di riserva.|0 – nodo della macchina virtuale è in esecuzione nel server originale.<br /><br /> 1: nodo della macchina virtuale è in esecuzione nel server di riserva.|  
|regione|**nvarchar(32)**|L'area in cui il nodo è in esecuzione.|'PDW', 'HDINSIGHT'|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
