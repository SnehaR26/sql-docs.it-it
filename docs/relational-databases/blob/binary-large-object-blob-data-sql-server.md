---
title: "Dati BLOB (Binary Large Object) (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FILESTREAM [SQL Server], progettazione e implementazione"
ms.assetid: 97509274-c3f8-43e5-a37c-52f1ffe0961a
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Dati BLOB (Binary Large Object) (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce soluzioni per l'archiviazione di file e documenti nel database o su dispositivi di archiviazione remoti.  
  
##  <a name="section"></a> Argomenti della sezione  
 [Confrontare opzioni per l'archiviazione di BLOB &#40;SQL Server&#41;](../../relational-databases/blob/compare-options-for-storing-blobs-sql-server.md)  
 Confrontare i vantaggi di FILESTREAM, FileTable e Archivio BLOB remoti.  
  
 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
 FILESTREAM consente l'archiviazione nel file system di dati non strutturati, ad esempio documenti e immagini, da parte delle applicazioni basate su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le applicazioni possono sfruttare le numerose API di flusso e le prestazioni del file system e contemporaneamente mantenere la coerenza transazionale tra i dati non strutturati e i corrispondenti dati strutturati.  
  
 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
 La funzionalità FileTable fornisce supporto per lo spazio dei nomi dei file di Windows e la compatibilità con le applicazioni di Windows ai dati dei file archiviati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. FileTable consente l'integrazione dei componenti di archiviazione e gestione dei dati da parte di un'applicazione e fornisce servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integrati, incluse la ricerca full-text e la ricerca semantica, su dati e metadati non strutturati.  
  
 In altre parole, è possibile archiviare file e documenti in speciali tabelle denominate FileTable in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma accedere a tali file e documenti da applicazioni di Windows come se questi fossero archiviati nel file system, senza apportare alcuna modifica alle applicazioni del client.  
  
 [Archivio BLOB remoto &#40;RBS&#41; &#40;SQL Server&#41;](../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
 Archivio BLOB remoti (RBS) per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente agli amministratori del database di archiviare oggetti BLOB (Binary Large Object) in soluzioni di archiviazione apposite anziché direttamente sul server. Ciò consente di risparmiare una considerevole quantità di spazio ed evita un inutile consumo di costose risorse hardware del server. RBS fornisce un set di librerie API che definiscono un modello standardizzato tramite cui le applicazioni accedono ai dati BLOB. RBS include anche strumenti di manutenzione come Garbage Collection, per facilitare la gestione dei dati BLOB remoti.  
  
 Tale componente è incluso nei supporti di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ma non viene installato dal programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  