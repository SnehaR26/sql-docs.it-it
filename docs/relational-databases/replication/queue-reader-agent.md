---
title: Agente di lettura coda | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.queuereaderagent.f1
helpviewer_keywords:
- Queue Reader Agent dialog box
ms.assetid: f02d24b6-dcb5-4126-b56e-fab41cfe4337
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 496ba72f12598157a6cf864538944a96f049e3c8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636169"
---
# <a name="queue-reader-agent"></a>Agente di lettura coda
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Nella finestra di dialogo **Agente di lettura coda** vengono visualizzate informazioni dettagliate sull'agente di lettura coda, tra cui lo stato, la cronologia, i messaggi informativi ed eventuali messaggi di errore.  
  
## <a name="options"></a>Opzioni  
 Scegliere le sessioni dell'agente di lettura coda da visualizzare nel menu **Visualizza** e quindi selezionare una sessione specifica nella griglia con etichetta **Sessioni dell'agente di lettura coda**. Nella griglia con etichetta **Azioni nella sessione selezionata**verranno visualizzate informazioni dettagliate sulla sessione selezionata. Se la sessione selezionata è terminata con un errore, verrà inoltre visualizzata l'area di testo con etichetta **Messaggio o dettagli errore della sessione selezionata** .  
  
 **Visualizza**  
 Consente di selezionare le sessioni dell'agente di lettura coda da visualizzare. L'agente di lettura coda in genere viene eseguito in modo continuo, pertanto potrebbe essere disponibile una sola sessione da visualizzare.  
  
 **Stato**  
 Stato dell'agente di lettura coda. Nell'elenco seguente vengono indicati i valori di stato possibili:  
  
-   Errore  
  
-   Ripetizione comando non riuscito  
  
-   Non in esecuzione  
  
-   In esecuzione  
  
 **Start Time**  
 Ora di inizio della sessione.  
  
 **Ora fine**  
 Ora di fine della sessione. Se l'agente non è arrestato, questo campo è vuoto.  
  
 **Durata**  
 Periodo di tempo durante il quale l'agente di lettura coda è stato eseguito in questa sessione. Il valore di durata rappresenta il tempo trascorso se l'agente è ancora in esecuzione e la durata totale della sessione se la sessione dell'agente è terminata.  
  
 **Messaggio di errore**  
 Se una sessione è terminata con un errore, in questo campo viene visualizzato l'ultimo messaggio di errore registrato dall'agente di lettura coda. Se una sessione non è terminata con un errore, questo campo è vuoto.  
  
 **Messaggio azione**  
 Tutti i messaggi informativi e i messaggi di errore registrati dall'agente di lettura coda durante la sessione selezionata.  
  
 **Ora azione**  
 Ora di esecuzione dell'azione descritta nella colonna **Messaggio azione** .  
  
 **Messaggio o dettagli errore della sessione selezionata**  
 Area visualizzata solo se per la sessione selezionata è visualizzato il valore **Errore** nella colonna **Stato** . In questa area di testo vengono visualizzate informazioni dettagliate sull'errore e viene indicato il comando di cui è stata tentata l'esecuzione quando si è verificato l'errore. Sono inoltre disponibili collegamenti a contenuto aggiuntivo correlato all'errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una pubblicazione &#40;Monitoraggio replica&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
