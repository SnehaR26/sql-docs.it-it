---
title: "Aggiornamento di Monitoraggio attivit&#224; processi | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.jobactivitymon.refresh.f1"
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Aggiornamento di Monitoraggio attivit&#224; processi
  Utilizzare la finestra di dialogo **Impostazioni aggiornamento** per configurare la frequenza di acquisizione di nuove informazioni sull'attività del server da parte di Monitoraggio attività processi. Monitoraggio attività processi deve eseguire query sul server monitorato per ottenere informazioni per la griglia Monitoraggio attività processi. Quando l'intervallo di aggiornamento automatico è impostato su un valore inferiore a 30 secondi, il tempo impiegato per eseguire queste query può ridurre le prestazioni del server.  
  
 Per aprire questa finestra di dialogo fare clic su **Visualizza impostazioni di aggiornamento**nella sezione **Stato** di Monitoraggio attività processi.  
  
## Opzioni  
 **Aggiorna automaticamente ogni**  
 Selezionare questa opzione per iniziare l'aggiornamento automatico delle informazioni di Monitoraggio attività. Questa opzione è deselezionata per impostazione predefinita.  
  
 **secondi**  
 Il numero di secondi che intercorrono tra i tentativi di aggiornamento automatici. Il valore predefinito è 60 secondi. Quando questa opzione è impostata su un valore uguale o inferiore a 5 l'aggiornamento viene eseguito comunque ogni 5 secondi.  
  
## Vedere anche  
 [Monitoraggio delle attività del processo](../../ssms/agent/monitor-job-activity.md)  
  
  