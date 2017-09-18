---
title: Tipo di dati sinonimi (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], synonyms
- alternate names [SQL Server]
- synonyms [SQL Server], data types
ms.assetid: 390eef67-1a49-4185-a971-e07765be9717
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1d9b1da2bdc7084268740cd7de2580e64ee9698b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="data-type-synonyms-transact-sql"></a>Sinonimi dei tipi di dati (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

I sinonimi dei tipi di dati sono disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per compatibilità con ISO. Nella tabella seguente vengono elencati i sinonimi e i tipi di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui viene eseguito il mapping.
  
|Sinonimo|Tipo di dati di sistema di SQL Server|  
|---|---|
|**La variabile binario**|**varbinary**|  
|**Char (variabile)**|**varchar**|  
|**carattere**|**char**|  
|**carattere**|**Char (1)**|  
|**carattere (**  *n*  **)**|**char(n)**|  
|**variabile di tipo carattere (**  *n*  **)**|**varchar(n)**|  
|**DEC**|**decimal**|  
|**Valore a precisione doppia**|**float**|  
|**float**[**(***n***)**] per  *n*  = 1-7|**real**|  
|**float**[**(***n***)**] per  *n*  = 8-15|**float**|  
|**integer**|**int**|  
|**caratteri nazionali (**  *n*  **)**|**nchar (n)**|  
|**National char (**  *n*  **)**|**nchar (n)**|  
|**variabile di caratteri nazionali (**  *n*  **)**|**nvarchar (n)**|  
|**char National varying (**  *n*  **)**|**nvarchar (n)**|  
|**testo nazionale**|**ntext**|  
|**timestamp**|rowversion|  
  
Sinonimi dei tipi di dati può essere utilizzati anziché il nome di tipo di dati di base corrispondente in istruzioni data definition language (DDL), ad esempio CREATE TABLE, CREATE PROCEDURE o dichiarare  *@variable* . I sinonimi non sono tuttavia visibili dopo la creazione dell'oggetto. In fase di creazione infatti all'oggetto viene assegnato il tipo di dati di base associato al sinonimo e la presenza del sinonimo nell'istruzione con cui è stato creato l'oggetto non viene registrata.
  
Agli oggetti che derivano dall'oggetto originale, ad esempio colonne del set di risultati o espressioni, viene assegnato il tipo di dati di base. Le successive funzioni per i metadati eseguite sull'oggetto originale e sugli oggetti derivati visualizzano il tipo di dati di base, non il sinonimo. Questo comportamento si verifica con operazioni sui metadati, ad esempio **sp_help** e l'altro sistema stored procedure, le viste degli schemi di informazioni o le varie operazioni di metadati di API di accesso ai dati che fanno riferimento i tipi di dati della tabella o set di risultati colonne.
  
È possibile, ad esempio, creare una tabella specificando `national character varying`:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, VarCharCol national character varying(10))  
```  
  
`VarCharCol`viene assegnato un **nvarchar (10)** tipo di dati, e tutte le funzioni successive metadati visualizzeranno la colonna come un **nvarchar (10)** colonna. Le funzioni per metadati mai visualizzate come un **varying(10) caratteri nazionali** colonna.
  
## <a name="see-also"></a>Vedere anche
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
