---
title: "Individuare i colli di bottiglia | Microsoft Docs"
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
  - "colli di bottiglia delle risorse [SQL Server]"
  - "monitoraggio di database [SQL Server], colli di bottiglia"
  - "prestazioni [SQL Server], colli di bottiglia"
  - "ottimizzazione dei database [SQL Server], colli di bottiglia"
  - "monitoraggio delle prestazioni del server [SQL Server], colli di bottiglia"
  - "monitoraggio delle prestazioni [SQL Server], colli di bottiglia"
  - "monitoraggio del database [SQL Server], colli di bottiglia"
  - "prestazioni del server [SQL Server], colli di bottiglia"
  - "colli di bottiglia [SQL Server]"
  - "identificazione di colli di bottiglia [SQL Server]"
ms.assetid: db079e65-ee80-4105-aec9-f8230d0d6635
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# Individuare i colli di bottiglia
  In seguito all'accesso simultaneo alle risorse condivise si possono verificare colli di bottiglia. I colli di bottiglia in genere sono inevitabili e presenti in qualsiasi sistema software. È tuttavia necessario identificare e ottimizzare le situazioni di eccesso di domanda, in quanto una domanda eccessiva delle risorse condivise comporta un rallentamento dei tempi di risposta.  
  
 Le possibili cause dei colli di bottiglia sono:  
  
-   Risorse insufficienti che rendono necessari l'aggiunta di componenti o l'aggiornamento dei componenti disponibili.  
  
-   Carichi di lavoro non distribuiti equamente tra risorse dello stesso tipo, ad esempio monopolizzazione di un disco.  
  
-   Funzionamento non corretto delle risorse.  
  
-   Configurazione non corretta delle risorse.  
  
## Analisi dei colli di bottiglia  
 La durata eccessiva di alcuni eventi segnala la presenza di colli di bottiglia che è possibile ottimizzare.  
  
 Esempio:  
  
-   È possibile che un altro componente impedisca che il processo di caricamento raggiunga il componente in uso, con un conseguente incremento dei tempi necessari per completare il caricamento.  
  
-   Le richieste client potrebbero richiedere tempi più lunghi a causa di traffico di rete intenso.  
  
 Per la valutazione delle prestazioni del server allo scopo di individuare eventuali colli di bottiglia, è necessario eseguire il monitoraggio delle cinque aree fondamentali descritte nella tabella seguente.  
  
|Possibile area in cui è presente un collo di bottiglia|Effetti sul server|  
|------------------------------|---------------------------|  
|Utilizzo della memoria|Se la memoria allocata per Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o disponibile per il sistema non è sufficiente, le prestazioni risultano inferiori. I dati infatti devono essere letti nel disco anziché direttamente nella cache dei dati. Microsoft Windows NT esegue un paging eccessivo con uno swapping dei dati da e nel disco in base alle pagine richieste.|  
|Utilizzo della CPU|Se la frequenza di utilizzo della CPU risulta costantemente elevata, potrebbe essere necessario ottimizzare le query [!INCLUDE[tsql](../../includes/tsql-md.md)] o aggiornare la CPU.|  
|Input/output (I/O) del disco|[!INCLUDE[tsql](../../includes/tsql-md.md)] le query possono essere ottimizzate per ridurre le operazioni di I/O del disco non necessarie, ad esempio tramite l'uso di indici.|  
|Connessioni utente|Se il numero di utenti che accede al server simultaneamente è molto elevato, le prestazioni potrebbe risultare inferiori.|  
|Blocchi di blocco|L'utilizzo di applicazioni progettate in modo non corretto può causare blocchi e ostacolare la concorrenza, con un conseguente rallentamento dei tempi di risposta e una diminuzione della velocità effettiva.|  
  
## Vedere anche  
 [Monitorare l'utilizzo della CPU](../../relational-databases/performance-monitor/monitor-cpu-usage.md)   
 [Monitoraggio dell'utilizzo del disco](../../relational-databases/performance-monitor/monitor-disk-usage.md)   
 [Monitoraggio dell'utilizzo della memoria](../../relational-databases/performance-monitor/monitor-memory-usage.md)   
 [Oggetto Statistiche generali di SQL Server](../../relational-databases/performance-monitor/sql-server-general-statistics-object.md)   
 [Oggetto Locks di SQL Server](../../relational-databases/performance-monitor/sql-server-locks-object.md)  
  
  