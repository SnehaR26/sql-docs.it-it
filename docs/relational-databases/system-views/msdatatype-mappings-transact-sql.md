---
title: MSdatatype_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00df6d73813fea7efebb3fa4db3c5e65187f2109
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636699"
---
# <a name="msdatatypemappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSdatatype_mappings** vista esegue il mapping di tipi di dati di SQL Server ai tipi di dati usati per i sistemi di gestione di database (DBMS) non SQL Server. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|È il nome del sistema DBMS. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> **MSSQLSERVER**: la destinazione è un database di SQL Server.<br />**ORACLE**: la destinazione è un database Oracle.<br />**DB2**: la destinazione è un database IBM DB2.<br />**SYBASE**: la destinazione è un database di Sybase.|  
|**sql_type**|**nvarchar(128)**|È il tipo di dati di SQL Server.|  
|**dest_type**|**nvarchar(128)**|È il nome del tipo di dati non SQL Server.|  
|**dest_prec**|**bigint**|È la precisione del tipo di dati non SQL Server.|  
|**dest_create_params**|**int**|Solo per uso interno.|  
|**dest_nullable**|**bit**|Indica se il tipo di dati non SQL Server supporta un valore NULL.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Specificare i mapping dei tipi di dati per un server di pubblicazione Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
