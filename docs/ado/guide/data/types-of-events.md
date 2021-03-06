---
title: Tipi di eventi | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- EventComplete event [ADO]
- events [ADO], types
- Will events [ADO]
- complete events [ADO]
- WillEvent event [ADO]
ms.assetid: f3327ea0-635a-43d4-bd78-c1674f62f1a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b324857816df774486716978425d1332a695952a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708469"
---
# <a name="types-of-events"></a>Tipi di eventi
Esistono due tipi di base degli eventi. "Verrà eventi," che vengono chiamati prima dell'avvio di un'operazione, in genere includono "Sarà" nei relativi nomi, ad esempio, **WillChangeRecordset** oppure **WillConnect**. Gli eventi che vengono chiamati dopo che un evento è stato completato in genere includono "Completa" nei relativi nomi, ad esempio, **RecordChangeComplete** oppure **ConnectComplete**. Esistono eccezioni, ad esempio **InfoMessage** , ma queste si verificano dopo l'operazione associata è stata completata.  
  
## <a name="will-events"></a>Verrà eventi  
 Gestori eventi chiamati prima dell'avvio dell'operazione offerta l'opportunità per esaminare o modificare i parametri dell'operazione e quindi annullare l'operazione o consentire il completamento. Queste routine del gestore eventi hanno in genere nomi nel formato **verranno*evento * * *.  
  
## <a name="complete-events"></a>Eventi completati  
 I gestori di eventi viene chiamati dopo che viene completata un'operazione possono inviare una notifica all'applicazione che un'operazione è conclusa. Il gestore eventi è anche una notifica quando un gestore dell'evento verrà Annulla un'operazione in sospeso. Queste routine del gestore eventi hanno in genere nomi nel formato ***evento * completa**.  
  
 Eventi completati e sarà in genere vengono utilizzati insieme.  
  
## <a name="other-events"></a>Altri eventi  
 Altri gestori di eventi, vale a dire, gli eventi i cui nomi non sono nel formato **verranno * evento*** o ***evento * completa** , ovvero vengono chiamati solo dopo che viene completata un'operazione. Questi eventi riguardano **Disconnect**, **EndOfRecordset**, e **InfoMessage**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Creazione di istanze evento ADO per linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Parametri di evento](../../../ado/guide/data/event-parameters.md)   
 [Interazione tra i gestori eventi](../../../ado/guide/data/how-event-handlers-work-together.md)
