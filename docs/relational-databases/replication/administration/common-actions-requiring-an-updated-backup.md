---
title: "Operazioni comuni che richiedono il backup del database | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "recupero [replica di SQL Server], azioni che richiedono un backup"
  - "ripristino [replica di SQL Server], azioni che richiedono un backup"
  - "backup [replica di SQL Server], azioni che richiedono un backup"
ms.assetid: a5975bf4-183e-42e3-b7d1-ad02f89d2e1d
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Operazioni comuni che richiedono il backup del database
  Se si eseguono backup regolari del log, le eventuali modifiche correlate alla replica dovrebbero essere incluse nei backup del log. Se non si eseguono i backup del log, eseguire un backup della pubblicazione, distribuzione, sottoscrizione, **msdb**, e **master** database dopo aver apportato modifiche alla topologia o schema di replica.  
  
## Database di pubblicazione  
 È necessario eseguire il backup del database di pubblicazione in seguito al completamento delle operazioni seguenti:  
  
-   Creazione di nuove pubblicazioni.  
  
-   Modifica delle proprietà di una pubblicazione, inclusa l'applicazione di filtri.  
  
-   Aggiunta di articoli a una pubblicazione esistente.  
  
-   Reinizializzazione delle sottoscrizioni nell'intera pubblicazione.  
  
-   Modifica dello schema in una tabella pubblicata.  
  
-   Esecuzione di esecuzione degli script su richiesta con [sp_addscriptexec & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md).  
  
-   Modifica delle proprietà di un articolo.  
  
-   Eliminazione di pubblicazioni.  
  
-   Eliminazione di articoli.  
  
-   Disabilitazione della replica.  
  
## Database di distribuzione  
 È necessario eseguire il backup del database di distribuzione in seguito al completamento delle operazioni seguenti:  
  
-   Creazione o modifica dei profili agenti di replica.  
  
-   Modifica dei parametri dei profili agenti di replica.  
  
-   Modifica delle proprietà degli agenti di replica (incluse le pianificazioni) per qualsiasi sottoscrizione push.  
  
-   Un nuovo intervallo di valori Identity viene assegnato dalla caratteristica di gestione automatica degli intervalli di valori Identity.  
  
## Database di sottoscrizione  
 È necessario eseguire il backup del database di sottoscrizione in seguito al completamento delle operazioni seguenti:  
  
-   Modifica delle proprietà di una sottoscrizione.  
  
-   Modifica della priorità di una sottoscrizione di tipo merge nel server di pubblicazione.  
  
-   Eliminazione di sottoscrizioni.  
  
-   Disabilitazione della replica.  
  
## Database msdb  
 Backup di **msdb** database di sistema nel nodo appropriato dopo:  
  
-   Attivazione o disabilitazione della replica.  
  
-   Aggiunta o eliminazione di un database di distribuzione (nel server di distribuzione).  
  
-   Attivazione o disabilitazione di un database per la pubblicazione (nel server di pubblicazione).  
  
-   Creazione o modifica dei profili agenti di replica (nel server di distribuzione).  
  
-   Modifica dei parametri dei profili agenti di replica (nel server di distribuzione).  
  
-   Modifica delle proprietà degli agenti di replica (incluse le pianificazioni) per qualsiasi sottoscrizione push (nel server di distribuzione).  
  
-   Modifica delle proprietà degli agenti di replica (incluse le pianificazioni) per qualsiasi sottoscrizione pull (nel Sottoscrittore).  
  
-   Creazione di un pacchetto DTS associato a una pubblicazione transazionale che utilizza sottoscrizioni trasformabili (nel server di distribuzione e nel Sottoscrittore).  
  
-   Aggiunta o eliminazione di una sottoscrizione trasformabile (nel server di distribuzione e nel Sottoscrittore).  
  
## Database master  
 Backup di **master** database di sistema nel nodo appropriato dopo:  
  
-   Attivazione o disabilitazione della replica.  
  
-   Aggiunta o eliminazione di un database di distribuzione (nel server di distribuzione).  
  
-   Attivazione o disabilitazione di un database per la pubblicazione (nel server di pubblicazione).  
  
-   Aggiunta della prima pubblicazione o eliminazione dell'ultima pubblicazione in qualsiasi database (nel server di pubblicazione).  
  
-   Aggiunta della prima sottoscrizione o eliminazione dell'ultima sottoscrizione in qualsiasi database (nel Sottoscrittore).  
  
-   Attivazione o disabilitazione di un server di pubblicazione nel server di pubblicazione di distribuzione (nel server di pubblicazione e nel server di distribuzione).  
  
## Vedere anche  
 [Backup e ripristino di database SQL Server](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Backup e ripristino di database replicati](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)  
  
  