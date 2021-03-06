---
title: Ricerca full-Text e semantica (Transact-SQL) di viste del catalogo | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- catalog views [SQL Server], full-text search
- full-text search [SQL Server], catalog views
- full-text indexes [SQL Server], catalog views
ms.assetid: b08ad2fd-e3d8-458f-96f1-678217e0f419
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9a6785c198bedb99ea0fd5b42f54cab431535527
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735029"
---
# <a name="full-text-search-and-semantic-search-catalog-views-transact-sql"></a>Viste del catalogo per ricerca full-text e ricerca semantica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questa sezione vengono descritte le viste del catalogo che forniscono informazioni sugli indici full-text e semantici.  
  
## <a name="full-text-search-catalog-views"></a>Viste del catalogo di ricerca full-text  
 [sys.fulltext_catalogs](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)  
 Contiene una riga per ogni catalogo full-text.  
  
 [sys.fulltext_document_types](../../relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql.md)  
 Restituisce una riga per ogni tipo di documento disponibile per operazioni di indicizzazione full-text. Ogni riga rappresenta il **IFilter** interfaccia che viene registrato nell'istanza di SQL Server.  
  
 [sys.fulltext_index_catalog_usages](../../relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql.md)  
 Restituisce una riga per ogni catalogo full-text in riferimento all'indice full-text.  
  
 [sys.fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)  
 Contiene una riga per ogni colonna che fa parte di un indice full-text.  
  
 [sys.fulltext_index_fragments](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)  
 Contiene una riga per ogni frammento di indice full-text presente in ogni tabella contenente un indice full-text.  
  
 [sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
 Contiene una riga per indice full-text di un oggetto in formato di tabella.  
  
 [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)  
 Contiene una riga per ogni lingua i cui word breaker sono registrati con SQL Server. In ogni riga è visualizzato l'identificatore LCID e il nome della lingua.  
  
 [sys.fulltext_stoplists](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)  
 Contiene una riga per ogni elenco di parole non significative full-text del database.  
  
 [sys.fulltext_stopwords](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
 Contiene una riga per ogni parola non significativa per tutti gli elenchi di parole non significative nel database.  
  
 [sys.fulltext_system_stopwords](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)  
 Consente di accedere all'elenco di parole non significative del sistema.  
  
 [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)  
 Contiene una riga per ogni proprietà di ricerca contenuta in qualsiasi elenco delle proprietà di ricerca nel database corrente.  
  
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
 Contiene una riga per ogni elenco delle proprietà di ricerca nel database corrente.  
  
## <a name="semantic-search-catalog-views"></a>Viste del catalogo di ricerca semantica  
 [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)  
 Restituisce una riga sul database di statistiche lingua semantica installato nell'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md)  
 Restituisce una riga per ogni lingua il cui modello delle statistiche è registrato con l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quando un modello di lingua è registrato, la lingua è abilitata per l'indicizzazione semantica.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Funzioni e viste a gestione dinamica la ricerca semantica e ricerca full-Text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
