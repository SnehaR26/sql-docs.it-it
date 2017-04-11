---
title: "Categoria di eventi Blocchi | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Blocchi - categoria di eventi [SQL Server]"
  - "classi di evento SQL Server, categoria di eventi Blocchi"
  - "classi di evento [SQL Server], categoria di eventi Blocchi"
  - "escalation blocchi [SQL Server], categoria di eventi Blocchi"
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# Categoria di eventi Blocchi
  Le classi di evento della categoria di eventi **Locks** consentono di monitorare l'attività di blocco in un'istanza del [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Queste classi di evento possono contribuire a esaminare problemi di blocco provocati dalla lettura e modifica dei dati da parte di più utenti simultaneamente.  
  
 Poiché nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] vengono spesso elaborati più blocchi, l'acquisizione delle classi di evento **Locks** durante una traccia può provocare un overhead significativo e comportare la creazione di file o tabelle di traccia di grandi dimensioni.  
  
## Argomenti della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Classe di evento Deadlock Graph](../../relational-databases/event-classes/deadlock-graph-event-class.md)|Include una descrizione XML di un deadlock.|  
|[Classe Lock:Acquired Event](../../relational-databases/event-classes/lock-acquired-event-class.md)|Indica l'acquisizione di un blocco su una risorsa, ad esempio una riga in una tabella.|  
|[Classe di evento Lock:Cancel](../../relational-databases/event-classes/lock-cancel-event-class.md)|Tiene traccia delle richieste di blocchi annullate prima dell'acquisizione del blocco, ad esempio per evitare un deadlock.|  
|[Classe di evento Lock:Deadlock Chain](../../relational-databases/event-classes/lock-deadlock-chain-event-class.md)|Esegue il monitoraggio di condizioni di deadlock e degli oggetti coinvolti.|  
|[Classe di evento Lock:Deadlock](../../relational-databases/event-classes/lock-deadlock-event-class.md)|Tiene traccia di una richiesta di blocco da parte di una transazione su una risorsa già bloccata da un'altra transazione e del deadlock risultante.|  
|[Classe di evento Lock:Escalation](../../relational-databases/event-classes/lock-escalation-event-class.md)|Indica la conversione di un blocco con granularità fine in un blocco con granularità grossolana.|  
|[Classe di evento Lock:Released](../../relational-databases/event-classes/lock-released-event-class.md)|Tiene traccia del rilascio di un blocco.|  
|[Lock:Timeout &#40;timeout &#62; 0&#41; Event Class](../../relational-databases/event-classes/lock-timeout-timeout-0-event-class.md)|Tiene traccia dell'impossibilità di completare richieste di blocco a causa del blocco della risorsa richiesta da parte di un'altra transazione. Questo evento viene generato solo nei casi in cui il valore specificato per il timeout del blocco è superiore a zero.|  
|[Classe di evento Lock:Timeout](../../relational-databases/event-classes/lock-timeout-event-class.md)|Tiene traccia dell'impossibilità di completare richieste di blocco a causa del blocco della risorsa richiesta da parte di un'altra transazione.|  
  
  