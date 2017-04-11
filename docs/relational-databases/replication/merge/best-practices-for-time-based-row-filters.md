---
title: "Procedure consigliate per i filtri di riga basati sul tempo | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "procedure consigliate"
ms.assetid: 773c5c62-fd44-44ab-9c6b-4257dbf8ffdb
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Procedure consigliate per i filtri di riga basati sul tempo
  Gli utenti delle applicazioni hanno spesso la necessità di recuperare da diverse tabelle determinati subset di dati basati sul tempo. Un venditore potrebbe ad esempio richiedere i dati relativi agli ordini dell'ultima settimana, così come un responsabile della pianificazione di eventi potrebbe aver bisogno di recuperare i dati relativi agli eventi della settimana in arrivo. In molti casi, le applicazioni utilizzano query che contiene il **GETDATE ()** funzione per eseguire questa operazione. Si consideri l'istruzione di filtro di riga seguente:  
  
```  
WHERE SalesPersonID = CONVERT(INT,HOST_NAME()) AND OrderDate >= (GETDATE()-6)  
```  
  
 Con un filtro di questo tipo, l'esecuzione dell'agente di merge ha in genere due risultati: le righe che soddisfano il filtro vengono replicate nei Sottoscrittori, mentre le righe che non soddisfano più il filtro vengono rimosse dai Sottoscrittori. (Per ulteriori informazioni sull'applicazione di filtri con **HOST_NAME ()**, vedere [i filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md).) La replica di tipo merge, tuttavia, consente di replicare e pulire esclusivamente i dati che sono stati modificati dopo l'ultima sincronizzazione, indipendentemente dalla modalità di definizione di un filtro di riga per tali dati.  
  
 Affinché la replica di tipo merge elabori una riga, è necessario che i dati contenuti in tale riga soddisfino il filtro di riga e che siano stati modificati dopo l'ultima sincronizzazione. Nel caso del **SalesOrderHeader** tabella **OrderDate** viene immesso quando viene inserita una riga. Le righe vengono quindi replicate nel Sottoscrittore come previsto poiché l'inserimento rappresenta una modifica ai dati. Se tuttavia nel Sottoscrittore sono presenti righe che non soddisfano più il filtro, ovvero sono relative a ordini immessi da più di sette giorni, queste verranno rimosse dal Sottoscrittore a meno che non siano state aggiornate per altri motivi.  
  
 L'esempio del responsabile della pianificazione di eventi evidenzia ulteriormente il problema legato a questo tipo di filtro. Si consideri il seguente filtro per un **eventi** tabella:  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND EventDate <= (GETDATE()+6)  
```  
  
 Per una tabella contenente eventi, gli inserimenti potrebbero essere eseguiti molto prima della data dell'evento. Se un mese prima è stato eseguito un inserimento per un evento della settimana successiva a quella corrente, senza che sia stata aggiornata la riga, quest'ultima non verrà replicata nel Sottoscrittore, anche se soddisfa il filtro di riga.  
  
 A seconda inoltre della configurazione della pubblicazione, la replica di tipo merge valuta i filtri in momenti diversi:  
  
-   Se una pubblicazione utilizza partizioni pre-calcolate, in base all'impostazione predefinita, i filtri vengono valutati ad ogni inserimento o aggiornamento di una riga.  
  
-   Se la pubblicazione non utilizza partizioni pre-calcolate, i filtri vengono valutati durante l'esecuzione dell'agente di merge.  
  
 Per ulteriori informazioni sulle partizioni pre-calcolate, vedere [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md). A seconda del momento in cui viene valutato il filtro, il tipo di dati che lo soddisfa sarà diverso. Se ad esempio una pubblicazione utilizza partizioni pre-calcolate e i dati vengono sincronizzati ogni due giorni, il subset di dati per il venditore potrebbe includere righe che risalgono fino a due giorni prima del previsto.  
  
## Indicazioni sull'utilizzo dei filtri di riga basati sul tempo  
 Il metodo seguente offre un approccio semplice ed efficace per il filtraggio basato sul tempo:  
  
-   Aggiungere una colonna alla tabella del tipo di dati **bit**. Questa colonna indica se è necessario replicare una riga.  
  
-   Utilizzare un filtro di riga che fa riferimento alla nuova colonna, anziché a una colonna basata sul tempo.  
  
-   Creare un processo di SQL Server Agent, o un processo pianificato tramite un altro meccanismo, per aggiornare la colonna prima dell'avvio pianificato dell'agente di merge.  
  
 Questo approccio consente di superare i limiti di utilizzo **GETDATE ()** o un altro metodo basato sul tempo e si evita di dover verificare quando i filtri vengono valutati per le partizioni. Si consideri l'esempio seguente di un **eventi** tabella:  
  
|**EventID**|**EventName**|**EventCoordID**|**EventDate**|**Replica**|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|1|Reception|112|2006-10-04|1|  
|2|Pranzo|112|2006-10-10|0|  
|3|Party|112|2006-10-11|0|  
|4|Matrimonio|112|2006-10-12|0|  
  
 Il filtro di riga di questa tabella avrebbe quindi l'aspetto seguente:  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND Replicate = 1  
```  
  
 Il processo di SQL Server Agent può eseguire istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] simili alle seguenti prima dell'esecuzione di ogni agente di merge:  
  
```  
UPDATE Events SET Replicate = 0 WHERE Replicate = 1  
GO  
UPDATE Events SET Replicate = 1 WHERE EventDate <= GETDATE()+6  
GO  
```  
  
 La prima riga reimposta il **replicare** colonna **0**, e la seconda riga imposta la colonna **1** per gli eventi che si verificano nei sette giorni successivi. Se questa istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] viene eseguita il 07/10/2006, la tabella verrà aggiornata nel modo seguente:  
  
|**EventID**|**EventName**|**EventCoordID**|**EventDate**|**Replica**|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|1|Reception|112|2006-10-04|0|  
|2|Pranzo|112|2006-10-10|1|  
|3|Party|112|2006-10-11|1|  
|4|Matrimonio|112|2006-10-12|1|  
  
 Gli eventi della settimana successiva sono ora contrassegnati come pronti per la replica. Alla successiva esecuzione dell'agente di merge per la sottoscrizione utilizzata dal coordinatore di eventi 112, le righe 2, 3 e 4 verranno scaricate nel Sottoscrittore e la riga 1 verrà rimossa dal Sottoscrittore.  
  
## Vedere anche  
 [GETDATE & #40; Transact-SQL & #41;](../../../t-sql/functions/getdate-transact-sql.md)   
 [Implementazione di processi](../../../ssms/agent/implement-jobs.md)   
 [Filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  