---
title: Classe di evento Deprecation Announcement | Microsoft Docs
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
- deprecation [SQL Server], events announced stage
- Deprecation Announcement event class
ms.assetid: 46fc578f-3c97-477f-879c-8a1b2cfd9d58
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f937e252123265ac28d215a751fc6419b5fe8dcc
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="deprecation-announcement-event-class"></a>Deprecation Announcement - classe di evento
  La classe di evento **Deprecation Announcement** viene generata quando si usa una caratteristica che verrà eliminata da una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma non dalla successiva versione principale. Per garantire la massima durata delle applicazioni, evitare di usare caratteristiche da cui viene generata la classe di evento **Deprecation Announcement** o **Deprecation Final Support** .  
  
## <a name="deprecation-announcement-event-class-data-columns"></a>Colonne di dati della classe di evento Deprecation Announcement  
  
|Nome colonna di dati|Tipo di dati|Descrizione|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|ClientProcessID|**int**|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se tramite il client viene indicato l'ID del processo client.|9|Sì|  
|DatabaseID|**int**|ID del database specificato nell'istruzione di *database* USE oppure il database predefinito se per un'istanza specifica l'istruzione di *database* USE non è stata eseguita. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|DatabaseName|**nvarchar**|Nome del database nel quale viene eseguita l'istruzione dell'utente.|35|Sì|  
|EventClass|**int**|Tipo di evento = 125.|27|No|  
|EventSequence|**int**|Sequenza di un determinato evento all'interno della richiesta.|51|No|  
|HostName|**nvarchar**|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il client fornisce il nome host. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|IntegerData2|**int**|Offset finale (in byte) dell'istruzione in esecuzione.|55|Sì|  
|IsSystem|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Sì|  
|LoginName|**nvarchar**|Nome dell'account di accesso dell'utente (account di accesso di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows nel formato DOMINIO\nomeutente).|11|Sì|  
|LoginSid|**image**|ID di sicurezza (SID) dell'utente connesso. Queste informazioni sono disponibili nella vista del catalogo sys.server_principals. Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|NTDomainName|**nvarchar**|Dominio Windows di appartenenza dell'utente.|7|Sì|  
|NTUserName|**nvarchar**|Nome utente di Windows.|6|Sì|  
|ObjectID|**int**|Numero ID della caratteristica deprecata.|22|Sì|  
|ObjectName|**nvarchar**|Nome della caratteristica deprecata.|34|Sì|  
|Offset|**Int**|Offset iniziale dell'istruzione nella stored procedure o nel batch.|61|Sì|  
|RequestID|**int**|ID della richiesta contenente l'istruzione.|49|Sì|  
|ServerName|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|SessionLoginName|**nvarchar**|Nome dell'account di accesso dell'utente che ha avviato la sessione. Ad esempio, se si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName**  indica Login1 e **LoginName** indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|SPID|**int**|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|SqlHandle|**image**|Handle binario che è possibile utilizzare per identificare batch o stored procedure SQL.|63|Sì|  
|StartTime|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|TextData|**ntext**|Valore di testo che dipende dalla classe di evento acquisita nella traccia.|1|Sì|  
|TransactionID|**bigint**|ID della transazione assegnato dal sistema.|4|Sì|  
|XactSequence|**bigint**|Token utilizzato per descrivere la transazione corrente.|50|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Classe di evento Deprecation Final Support](../../relational-databases/event-classes/deprecation-final-support-event-class.md)   
 [Funzionalità del Motore di database deprecate in SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  