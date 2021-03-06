---
title: Sys. system_sql_modules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- system_sql_modules_TSQL
- sys.system_sql_modules
- sys.system_sql_modules_TSQL
- system_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_sql_modules catalog view
ms.assetid: ad3548bc-4780-4821-b962-b421d52daed9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 349abe5ccc5fb36ee6c3568e97163e6eb665f633
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47594674"
---
# <a name="syssystemsqlmodules-transact-sql"></a>sys.system_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per oggetto di sistema contenente un modulo definito tramite il linguaggio SQL. Gli oggetti di sistema di tipo FN, IF, P, PC, TF, V sono associati a un modulo SQL. Per identificare l'oggetto contenitore, è possibile unire questa vista alla [Sys. system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Numero di identificazione dell'oggetto contenitore, univoco all'interno di un database.|  
|**Definizione**|**nvarchar(max)**|Testo SQL che definisce il modulo.|  
|**uses_ansi_nulls**|**bit**|1 = Il modulo è stato creato con l'opzione di database SET ANSI_NULLS impostata su ON.<br /><br /> Restituisce sempre 1.|  
|**uses_quoted_identifier**|**bit**|1= Il modulo è stato creato con SET QUOTED_IDENTIFIER ON.<br /><br /> Restituisce sempre 1.|  
|**is_schema_bound**|**bit**|0 = Il modulo non è stato creato con l'opzione SCHEMABINDING.<br /><br /> Restituisce sempre 0.|  
|**uses_database_collation**|**bit**|0 = Il modulo non dipende dalle regole di confronto predefinite del database.<br /><br /> Restituisce sempre 0.|  
|**is_recompiled**|**bit**|0 = La procedura non è stata creata tramite l'opzione WITH RECOMPILE.<br /><br /> Restituisce sempre 0.|  
|**null_on_null_input**|**bit**|0 = Il modulo è stato creato in modo da produrre un output NULL per ogni input NULL.<br /><br /> Restituisce sempre 0.|  
|**execute_as_principal_id**|**int**|Restituisce sempre NULL.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Sys.all_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
