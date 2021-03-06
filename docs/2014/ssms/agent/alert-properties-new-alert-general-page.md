---
title: Avviso di proprietà-nuovo avviso (pagina generale) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c0a3abb807efffd757c7f56e447c888ea4febef4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206351"
---
# <a name="alert-properties-new-alert-general-page"></a>Avviso proprietà-nuovo avviso (pagina generale)
  Usare questa pagina per visualizzare e modificare le proprietà generali degli avvisi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di modificare il nome dell'avviso.  
  
 **Abilita**  
 Consente di abilitare l'avviso. Se l'avviso non è abilitato, le azioni specificate nell'avviso non verranno eseguite.  
  
 **Tipo**  
 Consente di selezionare il tipo di avviso:  
  
-   **Avviso per evento di SQL Server** risponde ai messaggi nel registro degli eventi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
-   **Avviso relativo alle prestazioni di SQL Server** risponde a una specifica condizione in un contatore delle prestazioni.  
  
-   **Avviso per evento WMI** risponde a un evento del servizio Strumentazione gestione Windows (WMI, Windows Management Instrumentation).  
  
## <a name="sql-server-event-alert-options"></a>Opzioni di Avviso per evento di SQL Server  
 **Nome database**  
 Consente di specificare un database per l'evento o **tutti i database** per rispondere a un messaggio indipendentemente dal database in cui si verifica l'evento.  
  
 **Numero di errore**  
 Consente di specificare che l'evento risponde a un errore e di indicare il numero dell'errore.  
  
 **Severity**  
 Consente di specificare che l'evento risponde a tutti messaggi con uno specifico livello di gravità e di indicare tale livello.  
  
 **Genera avviso quando il messaggio contiene**  
 Consente di applicare un filtro agli eventi in base a una stringa specifica. Se questa opzione è selezionata, l'avviso risponde solo agli eventi contenenti la stringa specificata.  
  
 **Testo del messaggio**  
 Consente di specificare la stringa da utilizzare come filtro per gli eventi.  
  
## <a name="sql-server-performance-condition-alerts"></a>Opzioni di Avviso relativo alle prestazioni di SQL Server  
 **Oggetto**  
 Consente di specificare l'oggetto prestazioni da monitorare.  
  
 **Contatore**  
 Consente di specificare il contatore all'interno dell'oggetto prestazioni da monitorare.  
  
 **Istanza**  
 Consente di specificare l'istanza del contatore da monitorare.  
  
 **Avvisa se il contatore**  
 Consente di specificare il comportamento del contatore a cui risponde l'evento. È ad esempio possibile impostare questa opzione in modo che l'avviso risponda a una condizione in cui il valore del contatore **Spazio disponibile in tempdb (KB)** scende al di sotto di un determinata soglia o il valore di **Compilazioni SQL/sec** supera un determinato livello.  
  
 **Valore**  
 Consente di specificare un valore per il contatore.  
  
## <a name="wmi-event-alert-options"></a>Opzioni di Avviso per evento WMI  
 **Spazio dei nomi**  
 Consente di specificare lo spazio dei nomi da utilizzare per l'istruzione WQL (WMI Query Language). Sono supportati solo gli spazi dei nomi sul computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Query**  
 Consente di specificare l'istruzione WQL che identifica l'evento al quale risponde l'avviso.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi](alerts.md)   
 [Utilizzo di WQL con il Provider WMI per eventi del Server](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)   
 [Creare un avviso utilizzando un numero di errore](create-an-alert-using-an-error-number.md)   
 [Create an Alert Using Severity Level](create-an-alert-using-severity-level.md)  
  
  
