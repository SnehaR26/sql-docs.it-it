---
title: Configura log degli errori di SQL Server Agent (pagina Generale) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fc4741f03b147904d1c6010bcb4d1f0621d21cf3
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="configure-sql-server-agent-error-logs-general-page"></a>Configura log degli errori di SQL Server Agent (pagina Generale)
Utilizzare questa schermata per visualizzare e aggiornare le impostazioni relative alla registrazione degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**File di log degli errori**  
Consente di specificare il file in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dovrà scrivere i log degli errori.  
  
**...**  
Consente di individuare i file di log degli errori.  
  
**Scrivi log degli errori OEM**  
Consente di scrivere il file di log degli errori come file non Unicode. In questo modo, è possibile ridurre la quantità di spazio su disco utilizzata dal file di log. Quando questa opzione è selezionata, è tuttavia possibile che i messaggi contenenti dati Unicode siano più difficili da leggere.  
  
**errori**  
Nel file di log vengono scritti soltanto gli errori e i messaggi informativi.  
  
**Avvisi**  
Nel file di log vengono scritti gli avvisi e i messaggi informativi.  
  
**Informazioni**  
Nel file di log vengono scritti soltanto i messaggi informativi.  
  
## <a name="see-also"></a>Vedere anche  
[Log degli errori di SQL Server Agent](../../ssms/agent/sql-server-agent-error-log.md)  
  
