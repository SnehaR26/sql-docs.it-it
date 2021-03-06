---
title: Sys.external_tables (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: fac4720c-b679-4ab2-864b-ff7810a9b559
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 58c86f9eed16b83d9cc63c54f907f50dda1aab4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702719"
---
# <a name="sysexternaltables-transact-sql"></a>sys.external_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Contiene una riga per ogni tabella esterna nel database corrente.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|\<colonne ereditate >||Per un elenco delle colonne ereditate da questa vista, vedere [Sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).||  
|max_column_id_used|**int**|ID di colonna massimo utilizzato per questa tabella.||  
|uses_ansi_nulls|**bit**|La tabella è stata creata con l'opzione di database SET ANSI_NULLS impostata su ON.||  
|data_source_id|**int**|ID oggetto per l'origine dati esterna.||  
|file_format_id|**int**|Per le tabelle esterne su un'origine dati esterna HADOOP, questo è l'ID oggetto per il formato di file esterno.||  
|posizione|**nvarchar(4000)**|Per le tabelle esterne su un'origine dati esterna HADOOP, questo è il percorso dei dati esterni in HDFS.||  
|reject_type|**tinyint**|Per le tabelle esterne su un'origine dati esterna HADOOP, questo è il modo per eseguire query sui dati esterni vengono contate righe rifiutate.|VALORE: il numero di righe rifiutate.<br /><br /> Percentuale: la percentuale di righe rifiutate.|  
|reject_value|**float**|Per le tabelle esterne su un'origine dati esterna HADOOP:<br /><br /> Per la *reject_type =* valore, questo è il numero di rifiuti delle righe per consentire prima di aver eseguito la query.<br /><br /> Per la *reject_type* = percentage, questa è la percentuale di rifiuti delle righe per consentire prima di aver eseguito la query.||  
|reject_sample_value|**int**|Per la *reject_type* = percentage, il numero di righe da caricare, esito positivo o negativo, prima di calcolare la percentuale di righe rifiutate.|NULL se reject_type = VALUE.|  
|distribution_type|**int**|Per le tabelle esterne su un'origine dati esterne SHARD_MAP_MANAGER, questa è la distribuzione dei dati delle righe in tabelle di base sottostanti.|0 – Sharded<br /><br /> 1 – replicati<br /><br /> 2-Round robin|  
|distribution_desc|**nvarchar(120)**|Per le tabelle esterne su un'origine dati esterne SHARD_MAP_MANAGER, si tratta del tipo di distribuzione visualizzato sotto forma di stringa.||  
|sharding_column_id|**int**|Per le tabelle esterne su un'origine dati esterne SHARD_MAP_MANAGER e una distribuzione con partizionamento orizzontale, questo è l'ID di colonna della colonna che contiene i valori di chiave di partizionamento orizzontale.||  
|remote_schema_name|**sysname**|Per le tabelle esterne su un'origine dati esterne SHARD_MAP_MANAGER, questo è lo schema in cui si trova la tabella di base sui database remoti (se diverso dallo schema in cui è definita la tabella esterna).||  
|remote_object_name|**sysname**|Per le tabelle esterne su un'origine dati esterne SHARD_MAP_MANAGER, si tratta del nome della tabella di base sui database remoti (se diverso dal nome della tabella esterna).||  
  
## <a name="permissions"></a>Permissions  
 La visibilità dei metadati nelle viste del catalogo è limitata alle entità a protezione diretta di cui l'utente è proprietario o per le quali dispone di autorizzazioni. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
