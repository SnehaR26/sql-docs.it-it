---
title: SQL Server funzionalità deprecate in SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a90c1387a609ee59dec93b67e0a48bd2af7baf77
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129771"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>Funzionalità di SQL Server deprecate in SQL Server 2014
  In questo argomento vengono descritte le funzionalità deprecate ancora disponibili in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Tali funzionalità verranno rimosse a partire da una delle prossime versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. È consigliabile non usare le funzionalità deprecate nelle nuove applicazioni.  
  
## <a name="features-not-supported-in-the-next-version-of-includessnoversionincludesssnoversion-mdmd"></a>Funzionalità non supportate nella prossima versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
 Le funzionalità riportate di seguito di [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] non saranno supportate nella prossima versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Non usare queste funzionalità in un nuovo progetto di sviluppo e modificare non appena possibile le applicazioni in cui sono attualmente implementate. La colonna Nome funzionalità viene visualizzata negli eventi di traccia come nome dell'oggetto, mentre nei contatori delle prestazioni e in sys.dm_os_performance_counters viene visualizzata come nome dell'istanza. L'ID della funzionalità viene visualizzato negli eventi di traccia come ObjectId.  
  
|Category|Funzionalità deprecata|Sostituzione|Nome funzionalità|ID funzionalità|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Programmabilità dei dati|[Sys. soap_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Windows Communications Foundation (WCF) o ASP.NET|Servizi Web XML nativi|22|  
|Programmabilità dei dati|[Sys. endpoint_webmethods &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Windows Communications Foundation (WCF) o ASP.NET|Servizi Web XML nativi|23|  
  
### <a name="slipstream-functionality"></a>Funzionalità di integrazione  
 La funzionalità Aggiornamento prodotto sostituisce la funzionalità di integrazione disponibile in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1. I parametri della riga di comando /*PCUSource* e /*CUSource*associati a tale funzionalità non devono pertanto essere più utilizzati. Tali parametri continuano a funzionare, ma potrebbero essere rimossi nelle versioni future del programma di installazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il parametro /*UpdateSource* combina la funzionalità dei parametri di integrazione /*PCUSource* e /*CUSource*.  
  
 Per altre informazioni sulla funzionalità di integrazione disponibile in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1, vedere [integrare un aggiornamento di SQL Server](http://go.microsoft.com/fwlink/?LinkId=219945) (http://go.microsoft.com/fwlink/?LinkId=219945).  
  
## <a name="see-also"></a>Vedere anche  
 [Compatibilità con le versioni precedenti](../../2014/getting-started/backward-compatibility.md)  
  
  
