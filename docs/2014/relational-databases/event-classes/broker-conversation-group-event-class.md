---
title: Classe di evento Broker:Conversation Group | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Conversation Group event class
ms.assetid: 6595bef6-9d40-42eb-a934-735622dd23fb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d42b2183cb2927ad9c7c477810f1a7fddfbcbb46
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079381"
---
# <a name="brokerconversation-group-event-class"></a>Broker:Conversation Group  - classe di evento
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un evento **Broker:Conversation Group** .  
  
## <a name="brokerconversation-group-event-class-data-columns"></a>Colonne di dati della classe di evento Broker:Conversation Group  
  
|Colonna di dati|Tipo|Description|Numero colonna|Filtrabile|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|`nvarchar`|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|**ClientProcessID**|`int`|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se l'ID del processo client viene fornito dal client.|9|Sì|  
|**DatabaseID**|`int`|ID del database specificato nell'istruzione USE *database* oppure ID del database predefinito, se per una determinata istanza non viene eseguita un'istruzione USE *database* . [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**EventClass**|`int`|Tipo di classe di evento acquisita. Per **Broker:Conversation Group** è sempre **136**.|27|no|  
|**EventSequence**|`int`|Numero di sequenza dell'evento.|51|no|  
|**EventSubClass**|`nvarchar`|Tipo di sottoclasse di evento in cui sono disponibili informazioni aggiuntive su ogni classe di evento. Questa colonna può contenere i valori seguenti:<br /><br /> **Crea**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha creato un nuovo gruppo di conversazioni.<br /><br /> **Elimina**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha eliminato un gruppo di conversazioni.|21|Sì|  
|**GUID**|`uniqueidentifier`|Identificatore del gruppo di conversazioni descritto dall'evento.|54|no|  
|**HostName**|`nvarchar`|Nome del computer in cui è in esecuzione il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|**IsSystem**|`int`|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|no|  
|**LoginSid**|`image`|ID di sicurezza (SID) dell'utente connesso. Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|**NTDomainName**|`nvarchar`|Dominio di Windows a cui appartiene l'utente.|7|Sì|  
|**NTUserName**|`nvarchar`|Nome dell'utente proprietario della connessione che ha generato questo evento.|6|Sì|  
|**ServerName**|`nvarchar`|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|no|  
|**SPID**|`int`|ID del processo server assegnato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al processo associato al client.|12|Sì|  
|**StartTime**|`datetime`|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**TransactionID**|`bigint`|ID della transazione assegnato dal sistema.|4|no|  
  
  
