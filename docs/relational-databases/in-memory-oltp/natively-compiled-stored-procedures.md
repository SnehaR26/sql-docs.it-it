---
title: "Stored procedure compilate in modo nativo | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "stored procedure compilate in modo nativo"
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
caps.latest.revision: 54
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 54
---
# Stored procedure compilate in modo nativo
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Le stored procedure compilate in modo nativo sono stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] compilate nel codice nativo che accedono a tabelle con ottimizzazione per la memoria. Le stored procedure compilate in modo nativo consentono un'esecuzione efficiente delle query e della logica di business nella stored procedure. Per altri dettagli sul processo di compilazione nativa, vedere [Compilazione nativa di tabelle e stored procedure](../../relational-databases/in-memory-oltp/native-compilation-of-tables-and-stored-procedures.md). Per altre informazioni sulla migrazione delle stored procedure basate su disco alle stored procedure compilate in modo nativo, vedere [Problemi di migrazione relativi alle stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md).  
  
> [!NOTE]  
>  Una differenza tra le stored procedure interpretate (basate su disco) e le stored procedure compilate in modo nativo è che una stored procedure interpretata viene compilata alla prima esecuzione, mentre una stored procedure compilata in modo nativo viene compilata quando viene creata. Con le stored procedure compilate in modo nativo, molte condizioni di errore (overflow aritmetico, conversione dei tipi e alcune condizioni di divisione per zero) possono essere rilevate in fase di creazione e impediscono la creazione della stored procedure compilata in modo nativo. Con le stored procedure interpretate, queste condizioni di errore in genere non causano un errore durante la creazione della stored procedure, ma tutte le esecuzioni non riescono.  
  
 Contenuto della sezione:  
  
-   [Creazione di stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md)  
  
-   [Blocchi atomici](../../relational-databases/in-memory-oltp/blocchi-atomici-nelle-procedure-native.md)  
  
-   [Funzionalità supportate per i moduli T-SQL compilati in modo nativo](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [Costrutti DDL supportati per i moduli T-SQL compilati in modo nativo](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [Stored procedure compilate in modo nativo e opzioni SET di esecuzione](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [Procedure consigliate per chiamare stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [Monitoraggio delle prestazioni di stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [Chiamata di stored procedure compilate in modo nativo da applicazioni di accesso ai dati](../../relational-databases/in-memory-oltp/calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## Vedere anche  
 [Tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  