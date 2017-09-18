---
title: Modelli di SQL Server Profiler e autorizzazioni | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d55a2aaf43865897995dea95fd900bf9f6eee422
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-profiler-templates-and-permissions"></a>Modelli e autorizzazioni di SQL Server Profiler
  In [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] è possibile verificare come [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risolve le query internamente. In questo modo gli amministratori possono verificare quali istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] o espressioni multidimensionali vengono inviate al server e in quale modo il server accede al database o al cubo per restituire i set di risultati.  
  
 Tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], è possibile eseguire una delle operazioni seguenti:  
  
-   Creazione di una traccia basata su un modello riutilizzabile  
  
-   Monitoraggio dei risultati della traccia durante l'esecuzione della traccia  
  
-   Archiviazione dei risultati della traccia in una tabella  
  
-   Avvio, arresto e modifica dei risultati della traccia in base alle specifiche esigenze  
  
-   Riproduzione dei risultati della traccia  
  
 Utilizzare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per eseguire unicamente il monitoraggio degli eventi di interesse. Se le dimensioni delle tracce diventano troppo grandi, è possibile filtrarle in base ai criteri desiderati, in modo da raccogliere solo un subset dei dati degli eventi. Il monitoraggio di un numero troppo elevato di eventi comporta un overhead aggiuntivo per il server e il processo di monitoraggio e pertanto potrebbe aumentare in modo considerevole le dimensioni del file o della tabella di traccia, in particolare se il processo di monitoraggio viene prolungato nel tempo.  
  
> [!NOTE]  
>  I valori della colonna di traccia maggiori di 1 GB restituiscono un errore e vengono troncati nell'output di traccia.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Modelli di SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates.md)|Presenta informazioni sui modelli di traccia predefiniti disponibili in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Autorizzazioni necessarie per eseguire SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)|Presenta informazioni sulle autorizzazioni necessarie per l'esecuzione di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Salvare tracce e modelli di traccia](../../tools/sql-server-profiler/save-traces-and-trace-templates.md)|Presenta informazioni sul salvataggio di un output di traccia e sul salvataggio delle definizioni di traccia in un modello.|  
|[Modificare modelli di traccia](../../tools/sql-server-profiler/modify-trace-templates.md)|Presenta informazioni sulla modifica dei modelli di traccia tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|[Avviare una traccia](../../tools/sql-server-profiler/start-a-trace.md)|Presenta informazioni sugli effetti dell'avvio, della sospensione o dell'arresto di una traccia.|  
|[Correlare una traccia con i dati di Log delle prestazioni di Windows](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)|Presenta informazioni sulla correlazione dei dati del registro prestazioni di Windows con una traccia tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.|  
|[Visualizzare e analizzare le tracce con SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)|Presenta informazioni sull'utilizzo delle tracce per la risoluzione di problemi relativi ai dati, sulla visualizzazione dei nomi degli oggetti in una traccia e sulla ricerca di eventi in una traccia.|  
|[Analizzare deadlock con SQL Server Profiler](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)|Presenta informazioni sull'utilizzo di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per identificare la causa di un deadlock.|  
|[Analizzare query con risultati SHOWPLAN in SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)|Presenta informazioni sull'utilizzo di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per raccogliere e visualizzare i risultati di Showplan e Showplan Statistics.|  
|[Filtrare le tracce con SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md)|Presenta informazioni sull'impostazione di filtri per le colonne di dati allo scopo di filtrare l'output di traccia tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Riprodurre le tracce](../../tools/sql-server-profiler/replay-traces.md)|Presenta informazioni relative alla riproduzione di una traccia e ai relativi requisiti.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Avviare SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)  
  
  