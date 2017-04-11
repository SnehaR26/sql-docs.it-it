---
title: "Impostare opzioni di traccia globali (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "opzioni di traccia globali [SQL Server]"
ms.assetid: 2854608a-c3c7-4eb8-b567-034bfec4b1a9
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Impostare opzioni di traccia globali (SQL Server Profiler)
  In questo argomento viene illustrato come impostare opzioni applicabili a tutte le tracce create in un'istanza specifica di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### Per impostare le opzioni di traccia globali  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni generali** fare clic su **Scegli carattere** per modificare le opzioni di visualizzazione e fare clic su **OK**.  
  
3.  Facoltativamente, selezionare l'opzione **Avvia traccia non appena viene stabilita una connessione**.  
  
4.  Facoltativamente, selezionare l'opzione**Update trace definition when provider version changes** (Aggiorna la definizione di traccia in caso di modifica della versione del provider). Questa è l'opzione consigliata ed è selezionata per impostazione predefinita. Quando questa opzione è selezionata, la definizione di traccia viene aggiornata automaticamente alla versione attuale del server quando si esegue la traccia.  
  
5.  Facoltativamente, specificare la modalità di gestione dei file di rollover da parte del server:  
  
    -   Selezionare l'opzione **Carica tutti i file di rollover in sequenza senza chiedere conferma** per caricare automaticamente i file di rollover durante la riproduzione.  
  
    -   Selezionare l'opzione **Chiedi conferma prima di caricare file di rollover** per controllare i file di rollover durante la riproduzione.  
  
    -   Selezionare l'opzione **Non caricare mai file di rollover successivi** per riprodurre solo un file alla volta.  
  
6.  Se si desidera, impostare le opzioni di riproduzione:  
  
    -   L'opzione **Numero predefinito di thread di riproduzione** consente di controllare il numero di thread del processore da usare durante la riproduzione. Un numero elevato di thread consente un completamento più rapido della riproduzione, ma provoca la riduzione delle prestazioni del server durante la riproduzione. L'impostazione consigliata è **4**. Nella tabella seguente sono elencate le opzioni disponibili:  
  
        |Valore|Descrizione|  
        |-----------|-----------------|  
        |**2**|Valore minimo. Per la riproduzione vengono utilizzati due thread.|  
        |**4**|Valore predefinito.|  
        |**255**|Valore massimo. L'impostazione di un valore massimo comporta una riduzione delle prestazioni degli altri processi.|  
  
    -   L'opzione **Intervallo di attesa predefinito Health Monitor (sec)** consente di impostare la quantità di tempo massima in secondi per cui un altro processo può essere bloccato da parte di un thread di riproduzione. Nella tabella riportata di seguito vengono illustrati i valori consentiti.  
  
        |Valore|Descrizione|  
        |-----------|-----------------|  
        |**0**|Valore minimo. Se si imposta il valore **0**, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] non arresterà mai un processo di blocco.|  
        |**3600**|Valore predefinito. Sono consentiti processi di blocco che non superano **3600** secondi, ovvero un'ora.|  
        |**86400**|Valore massimo. Sono consentiti processi di blocco che non superano **86400** secondi, ovvero un giorno.|  
  
    -   L'opzione **Intervallo di polling predefinito Health Monitor (sec)** consente di impostare la frequenza del polling dei thread di riproduzione per i processi di blocco. Nella tabella riportata di seguito vengono illustrati i valori consentiti.  
  
        |Valore|Descrizione|  
        |-----------|-----------------|  
        |**1**|Valore minimo. Se si imposta il valore **1**, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] eseguirà il polling dei processi di blocco una volta al secondo.|  
        |**60**|Valore predefinito. Il polling dei processi di blocco viene eseguito una volta al minuto.|  
        |**86400**|Valore massimo. Il polling dei processi di blocco viene eseguito una volta ogni **86400** secondi, ovvero una volta al giorno.|  
  
## Vedere anche  
 [Impostare i valori predefiniti per la visualizzazione delle tracce &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  