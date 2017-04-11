---
title: "Stati di mirroring (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "stati [SQL Server], mirroring del database"
  - "PENDING_FAILOVER - stato"
  - "stati di mirroring [SQL Server]"
  - "DISCONNECTED - stato"
  - "SYNCHRONIZING - stato"
  - "SYNCHRONIZED - stato"
  - "SUSPENDED - stato"
  - "mirroring del database [SQL Server], stati"
ms.assetid: 90062917-74f9-471b-b49e-bc153ae1a468
caps.latest.revision: 39
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 39
---
# Stati di mirroring (SQL Server)
  Durante una sessione di mirroring del database, il database con mirroring si trova sempre in uno stato specifico, ovvero lo *stato di mirroring*. Lo stato del database riflette lo stato delle comunicazioni, il flusso di dati e la differenza nei dati tra i partner. La sessione di mirroring del database adotta lo stesso stato del database principale.  
  
 Nel corso della sessione di mirroring del database viene eseguito il monitoraggio reciproco delle istanze del server. Per eseguire il monitoraggio del database, i partner utilizzano lo stato di mirroring. Ad eccezione dello stato PENDING_FAILOVER, lo stato del database principale è sempre identico a quello del database mirror. Se per la sessione è impostato un server di controllo del mirroring, per eseguire il monitoraggio di tale server ciascun partner utilizza il relativo stato della connessione (CONNECTED o DISCONNECTED).  
  
 Gli stati di mirroring possibili del database sono i seguenti:  
  
|Stato mirroring|Descrizione|  
|---------------------|-----------------|  
|SYNCHRONIZING|Il contenuto del database mirror è in ritardo rispetto a quello del database principale. Il server principale invia i record del log al server mirror, che applica le modifiche al database mirror ai fini del rollforward.<br /><br /> All'inizio di una sessione di mirroring, lo stato del database è SYNCHRONIZING. Il server principale soddisfa le richieste del database e il mirror tenta di aggiornarsi.|  
|SYNCHRONIZED|Quando il server mirror è sufficientemente aggiornato rispetto al server principale, lo stato di mirroring diventa SYNCHRONIZED. Il database resta in questo stato fino a quando il server principale continua a inviare modifiche al server mirror e quest'ultimo continua ad applicare le modifiche al database mirror.<br /><br /> Se la protezione delle transazioni è impostata su FULL, il failover automatico e quello manuale sono supportati nello stato SYNCHRONIZED, quindi non può verificarsi una perdita di dati dopo un failover.<br /><br /> Se la protezione delle transazioni è disattivata, è possibile che si verifichi la perdita di dati anche in stato SYNCHRONIZED.|  
|SUSPENDED|La copia mirror del database non è disponibile. Il database principale viene eseguito senza inviare log al server mirror. Tale condizione è nota come *esecuzione senza mirroring*. Si tratta dello stato attivo dopo un failover.<br /><br /> Una sessione può diventare SUSPENDED anche in seguito a errori di rollforward oppure se viene sospesa dall'amministratore.<br /><br /> Lo stato SUSPENDED è persistente in quanto non viene modificato in seguito a operazioni di chiusura e avvio dei partner.|  
|PENDING_FAILOVER|Questo stato viene applicato solo sul server principale dopo l'avvio di un failover, quando il server non è ancora passato al ruolo di mirror.<br /><br /> Quando il failover viene avviato, lo stato del database principale diventa PENDING_FAILOVER, vengono rapidamente interrotte eventuali connessioni utente e subito dopo il database assume il ruolo di mirror.|  
|DISCONNECTED|Le comunicazioni tra un partner e l'altro sono state interrotte.|  
  
## Vedere anche  
 [Monitoraggio del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
  