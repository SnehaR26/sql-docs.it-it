---
title: Gestione degli eventi ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
- event handlers [ADO]
ms.assetid: e9003457-0762-48b3-942f-0820266b158f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1738c7432dce6538fe15c4b23f15f5ab7fe6f219
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606505"
---
# <a name="handling-ado-events"></a>Gestione degli eventi ADO
Il modello di eventi ADO supporta determinate operazioni ADO sincroni e asincroni che rilasciano *eventi*, o le notifiche, prima dell'avvio dell'operazione o dopo il completamento. Un evento è effettivamente una chiamata a una routine del gestore eventi definiti nell'applicazione.  
  
 Se si fornisce funzioni di gestione o le procedure per il gruppo di eventi che si verificano prima dell'avvio dell'operazione, è possibile esaminare o modificare i parametri passati all'operazione. Poiché non è stata eseguita ancora, è possibile annullare l'operazione o consentire il completamento.  
  
 Gli eventi che si verificano dopo il completamento di un'operazione sono particolarmente importanti se si utilizza ADO in modo asincrono. Ad esempio, un'applicazione che avvia un'operazione [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) operazione riceve una notifica tramite un evento di completamento dell'esecuzione quando l'operazione è terminata.  
  
 Usando il modello di eventi ADO aggiunge un sovraccarico all'applicazione, ma fornisce flessibilità decisamente maggiore rispetto ad altri metodi di gestione delle operazioni asincrone, ad esempio il monitoraggio di [stato](../../../ado/reference/ado-api/state-property-ado.md) proprietà di un oggetto con un ciclo.  
  
> [!NOTE]
>  Per gestire gli eventi, ADO deve avere un message pump o essere utilizzati in un modello di apartment a thread singolo (STA). Eventi ADO vengono gestiti internamente tramite la creazione di una finestra nascosta. ADO invia messaggi a questa finestra quando gli eventi devono essere attivati. Questa operazione viene eseguita per garantire che gli eventi vengono inviati al thread che ha chiamato **IConnectionPoint::** nel punto di connessione. Questa architettura può causare problemi quando il thread che deve ricevere le notifiche non che distribuisca i messaggi della finestra. Problemi che possono includono eventi ADO non vengono recapitati ai thread e trasmissioni finestra globale scadere e possibilmente rallentando l'intero sistema perché le finestre nascoste non elaborano i messaggi. Thread STA hanno in genere un message pump in esecuzione in modo che questo problema non manifestarsi su thread STA. Thread MTA, tuttavia, tipicamente non hanno un message pump in modo che il problema si manifesta in genere su thread MTA.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)  
  
-   [Tipi di eventi](../../../ado/guide/data/types-of-events.md)  
  
-   [Parametri evento](../../../ado/guide/data/event-parameters.md)  
  
-   [Interazione tra i gestori eventi](../../../ado/guide/data/how-event-handlers-work-together.md)  
  
-   [Creazione di istanze evento ADO per linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Creazione di istanze evento ADO per linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Eventi ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Parametri di evento](../../../ado/guide/data/event-parameters.md)   
 [Tipi di eventi](../../../ado/guide/data/types-of-events.md)
