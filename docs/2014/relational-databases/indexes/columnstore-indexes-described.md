---
title: Descrizione degli indici ColumnStore | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
author: mikeraymsft
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 58bf23c84914d7df4b9f2637cc7682de2021bf08
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109806"
---
# <a name="columnstore-indexes-described"></a>Columnstore Indexes Described
  Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] *indice columnstore in memoria* archivia e gestisce i dati tramite archiviazione dei dati basata su colonne e l'elaborazione di query basata su colonne. Gli indici columnstore sono ideali per i carichi di lavoro di data warehousing che eseguono principalmente caricamenti bulk e query di sola lettura. Usare l'indice columnstore per migliorare fino a **10 volte le prestazioni delle query** rispetto all'archiviazione tradizionale orientata alle righe e fino a **7 volte la compressione dei dati** rispetto alle dimensioni dei dati non compressi.  
  
> [!NOTE]  
>  L'indice columnstore cluster viene considerato lo standard per l'archiviazione di grandi tabelle dei fatti di data warehouse e si prevede venga utilizzato nella maggior parte degli scenari di data warehouse. Poiché l'indice columnstore cluster è aggiornabile, il carico di lavoro può eseguire molte operazioni di inserimento, aggiornamento ed eliminazione.  
  
## <a name="contents"></a>Sommario  
  
-   [Nozioni di base](#basics)  
  
-   [al caricamento dei dati](#dataload)  
  
-   [Suggerimenti sulle prestazioni](#performance)  
  
-   [Gli argomenti e le attività correlate](#related)  
  
##  <a name="basics"></a> Nozioni di base  
 L' *columnstore index* è una tecnologia per l'archiviazione, il recupero e la gestione dei dati utilizzando un formato di dati in colonna, detto columnstore. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta entrambi gli indici columnstore non cluster e non cluster. Entrambi utilizzano la stessa tecnologia columnstore in memoria, ma presentano differenze nello scopo e nelle funzionalità supportate.  
  
###  <a name="benefits"></a> Vantaggi  
 Gli indici columnstore sono ottimali per la maggior parte delle query di sola lettura che eseguono analisi su grandi set di dati. Spesso, si tratta di query per carichi di lavoro di data warehousing. Gli indici columnstore consentono di migliorare notevolmente le prestazioni delle query che utilizzano scansioni complete delle tabelle e non sono particolarmente adatti per le query eseguite per cercare un valore specifico nei dati.  
  
 Vantaggi dell'indice columnstore:  
  
-   Le colonne contengono spesso dati simili che generano frequenze di compressione elevate.  
  
-   Le frequenze di compressione elevate migliorano le prestazioni delle query utilizzando un footprint di memoria più piccolo. A loro volta, le prestazioni delle query costituiscono un miglioramento in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in quanto è possibile eseguire un numero maggiore di operazioni di dati e query in memoria.  
  
-   In SQL Server è stato aggiunto un nuovo meccanismo per l'esecuzione di query, denominato modalità batch, che consente di ridurre in modo significativo l'utilizzo della CPU. L'esecuzione in modalità batch è strettamente integrata al formato di archiviazione columnstore, per il quale è ottimizzata. L'esecuzione in modalità batch talvolta è detta esecuzione basata su vettore o vettorizzata.  
  
-   Le query spesso selezionano solo alcune colonne di una tabella, riducendo il totale delle operazioni di I/O su un supporto fisico.  
  
### <a name="columnstore-versions"></a>Versioni columnstore  
 In SQL Server 2012, SQL Server 2012 Parallel Data Warehouse e SQL Server 2014 vengono utilizzati gli indici columnstore per velocizzare le query di data warehouse comuni. In SQL Server 2012 sono state introdotte due nuove funzionalità: un indice columnstore non cluster e una funzionalità di esecuzione di query basata su vettore che elabora i dati in unità denominate "batch". Oltre alle funzionalità di SQL Server 2012, in SQL Server 2014 sono disponibili gli indici columnstore cluster aggiornabili.  
  
### <a name="key-characteristics"></a>Caratteristiche chiave  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].|  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un indice columnstore cluster:  
  
-   È disponibile nelle edizioni Enterprise, Developer ed Evaluation.  
  
-   È aggiornabile.  
  
-   È il metodo di archiviazione primario per l'intera tabella.  
  
-   Non ha colonne chiave. Tutte le colonne sono incluse.  
  
-   È l'unico indice nella tabella. Non può essere combinato con altri indici.  
  
-   Può essere configurato per utilizzare columnstore o la compressione dell'archivio columnstore.  
  
-   Non archivia fisicamente le colonne in base a un ordinamento. Archivia i dati per migliorare la compressione e le prestazioni.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].|  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un indice columnstore non cluster:  
  
-   È possibile indicizzare un subset di colonne nell'heap o nell'indice cluster. Ad esempio, è possibile indicizzare le colonne utilizzate di frequente.  
  
-   Richiede uno spazio di archiviazione aggiuntivo per archiviare una copia delle colonne dell'indice.  
  
-   Viene aggiornato ricompilando l'indice o cambiando le partizioni. Non è aggiornabile tramite le operazioni DML, ad esempio inserimento, aggiornamento ed eliminazione.  
  
-   Può essere combinato con altri indici nella tabella.  
  
-   Può essere configurato per utilizzare columnstore o la compressione dell'archivio columnstore.  
  
-   Non archivia fisicamente le colonne in base a un ordinamento. Archivia i dati per migliorare la compressione e le prestazioni. Non è obbligatorio preordinare i dati prima di creare l'indice columnstore, ma questa operazione può migliorare la compressione columnstore.  
  
###  <a name="Concepts"></a> Concetti e termini chiave  
 I seguenti concetti e termini chiave sono associati agli indici columnstore.  
  
 indice columnstore  
 L' *columnstore index* è una tecnologia per l'archiviazione, il recupero e la gestione dei dati utilizzando un formato di dati in colonna, detto columnstore. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta entrambi gli indici columnstore non cluster e non cluster. Entrambi utilizzano la stessa tecnologia columnstore in memoria, ma presentano differenze nello scopo e nelle funzionalità supportate.  
  
 columnstore  
 Un *indice columnstore* è costituito da dati organizzati logicamente in una tabella con righe e colonne e archiviati fisicamente in un formato di dati a colonne.  
  
 rowstore  
 Un *indice rowstore* è costituito da dati organizzati logicamente in una tabella con righe e colonne e archiviati fisicamente in un formato di dati a righe. È stata la modalità di archiviazione tradizionale per archiviare dati relazionali di tabella.  
  
 rowgroup e segmenti di colonna  
 Per le frequenze di compressione e prestazioni elevate, l'indice columnstore suddivide la tabella in gruppi di righe, quindi comprime ciascun gruppo di righe per colonne. Il numero di righe nel gruppo di righe deve essere sufficientemente grande da migliorare le frequenze di compressione e sufficientemente ridotto da poter trarre vantaggio dalle operazioni in memoria.  
  
 gruppo di righe  
 Oggetto *rowgroup* è un gruppo di righe che vengono compresse nel formato columnstore contemporaneamente.  
  
 segmento di colonna  
 Un *segmento di colonna* è una colonna di dati all'interno del rowgroup.  
  
-   Un rowgroup contiene in genere il numero massimo di righe per rowgroup, pari a 1.048.576 righe.  
  
-   Ogni rowgroup contiene un segmento di colonna per ogni colonna della tabella.  
  
-   Ogni segmento di colonna è compresso e archiviato su un supporto fisico.  
  
 ![Column segment](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")  
  
 indice columnstore non cluster  
 Oggetto *indice columnstore non cluster* è un indice di sola lettura creato in una tabella heap o indice cluster esistente. Contiene una copia di un subset di colonne, fino a includere tutte le colonne della tabella. La tabella è di sola lettura se contiene un indice columnstore non cluster.  
  
 Un indice columnstore non cluster consente di disporre di un indice columnstore per eseguire query di analisi e, contemporaneamente, operazioni di sola lettura nella tabella originale.  
  
 ![Indice columnstore non cluster](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "indice columnstore non cluster")  
  
 indice columnstore cluster  
 Oggetto *indice columnstore cluster* rappresenta l'archivio fisico per l'intera tabella ed è l'unico indice per la tabella. L'indice cluster è aggiornabile. È possibile eseguire nell'indice operazioni di inserimento, eliminazione e aggiornamento, nonché il caricamento bulk dei dati.  
  
 ![Clustered Columnstore Index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")  
  
 Per ridurre la frammentazione dei segmenti di colonna e migliorare le prestazioni, l'indice columnstore può archiviare alcuni dati temporaneamente in una tabella rowstore, denominata deltastore, nonché un albero B di ID per le righe eliminate. Le operazioni deltastore sono gestite in modo automatico. Per tornare ai risultati della query corretti, l'indice columnstore cluster combina i risultati della query da columnstore e deltastore.  
  
 deltastore  
 Utilizzato con indici columnstore cluster, solo una *deltastore* è una tabella rowstore che archivia le righe finché il numero di righe è sufficientemente grande da essere spostati nel columnstore. Un deltastore viene utilizzato con indici columnstore cluster per migliorare le prestazioni del caricamento e di altre operazioni DML.  
  
 Durante un caricamento bulk di grandi dimensioni, la maggior parte delle righe viene direttamente indirizzata al columnstore senza passare per il deltastore. È possibile che alla fine del caricamento bulk il numero delle righe sia insufficiente a soddisfare le dimensioni minime di un rowgroup, pari a 102.400. In questo caso, le righe finali vengono indirizzate al deltastore anziché al columnstore. Per i caricamenti bulk di piccole dimensioni, con meno di 102.400 righe, tutte le righe passano direttamente al deltastore.  
  
 Quando il deltastore raggiunge il numero massimo di righe, viene chiuso. Un processo tuple-move controlla i gruppi di righe chiusi. Quando trova il rowgroup chiuso, lo comprime e lo archivia nel columnstore.  
  
##  <a name="dataload"></a> Il caricamento dei dati  
  
###  <a name="dataload_nci"></a> Il caricamento dei dati in un indice Columnstore non cluster  
 Per caricare dati in un indice columnstore non cluster, caricare innanzitutto i dati in una tabella rowstore tradizionale archiviata come heap o cluster di indice e quindi creare l'indice columnstore non cluster con [CREATE COLUMNSTORE INDEX &#40;&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).  
  
 ![Il caricamento dei dati in un indice columnstore](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "il caricamento dei dati in un indice columnstore")  
  
 Una tabella con un indice columnstore non cluster è di sola lettura finché l'indice non viene eliminato o disabilitato. Per aggiornare la tabella e l'indice columnstore non cluster è possibile cambiare le partizioni. È inoltre possibile disabilitare l'indice, aggiornare la tabella, quindi ricompilare l'indice.  
  
 Per altre informazioni vedere [Using Nonclustered Columnstore Indexes](indexes.md)  
  
###  <a name="dataload_cci"></a> Il caricamento dei dati in un indice Columnstore cluster  
 ![Caricamento in un indice columnstore cluster](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "Caricamento in un indice columnstore cluster")  
  
 Come suggerisce il diagramma, per caricare dati in un indice columnstore cluster, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
1.  I rowgroup di dimensioni massime vengono inseriti direttamente nel columnstore. Quando i dati vengono caricati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le righe di dati vengono assegnate in ordine di arrivo in un rowgroup aperto.  
  
2.  Per ogni rowgroup, dopo aver raggiunto le dimensioni massime in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
    1.  Il rowgroup viene contrassegnato come CLOSED.  
  
    2.  Il deltastore viene ignorato.  
  
    3.  Ogni segmento di colonna viene compresso con il rowgroup con la compressione del columnstore.  
  
    4.  Ogni segmento di colonna compresso viene fisicamente archiviato nel columnstore.  
  
3.  Le righe rimanenti vengono inserite nel columnstore o nel deltastore come segue:  
  
    1.  Se il numero di righe soddisfa il requisito minimo di righe per rowgroup, le righe vengono aggiunte al columnstore.  
  
    2.  Se il numero di righe è inferiore al requisito minimo di righe per rowgroup, le righe vengono aggiunte al deltastore.  
  
 Per altre informazioni sui processi e attività deltastore, vedere [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)  
  
##  <a name="performance"></a> Suggerimenti sulle prestazioni  
  
### <a name="plan-for-enough-memory-to-create-columnstore-indexes-in-parallel"></a>Pianificare una quantità di memoria sufficiente per creare indici columnstore in parallelo  
 Per impostazione predefinita, la creazione di un indice columnstore è un'operazione parallela, a meno che la memoria non sia vincolata. La creazione dell'indice in parallelo richiede più memoria rispetto alla creazione dell'indice in modo seriale. Se si dispone di un'ampia quantità di memoria, la creazione di un indice columnstore richiede un tempo di circa 1,5 volte superiore rispetto alla compilazione di un albero B nelle stesse colonne.  
  
 La memoria richiesta per la creazione di un indice columnstore dipende dal numero di colonne, dal numero di colonne stringa, dal grado di parallelismo e dalle caratteristiche dei dati. Ad esempio, se la tabella contiene meno di un milione di righe, SQL Server utilizzerà un solo thread per creare l'indice columnstore.  
  
 Se la tabella dispone di più di un milione di righe, ma SQL Server non ha a disposizione memoria sufficiente per creare l'indice utilizzando MAXDOP, SQL Server ridurrà automaticamente MAXDOP secondo le esigenze per adattarsi alla memoria disponibile.  In alcuni casi, è necessario ridurre il grado di parallelismo a uno per compilare l'indice nella memoria vincolata.  
  
##  <a name="related"></a> Gli argomenti e le attività correlate  
  
### <a name="nonclustered-columnstore-indexes"></a>Indici columnstore non cluster  
 Per le attività comuni, vedere [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md).  
  
-   [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)  
  
-   [ALTER INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-index-transact-sql) con REBUILD.  
  
-   [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
### <a name="clustered-columnstore-indexes"></a>Indici columnstore cluster  
 Per le attività comuni, vedere [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md).  
  
-   [CREARE l'indice COLUMNSTORE cluster &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)  
  
-   [ALTER INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-index-transact-sql) con REBUILD o REORGANIZE.  
  
-   [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
-   [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)  
  
-   [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)  
  
-   [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql)  
  
### <a name="metadata"></a>Metadati  
 Tutte le colonne di un indice columnstore vengono archiviate nei metadati come colonne incluse. L'indice columnstore non contiene colonne chiave.  
  
-   [sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
-   [sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)  
  
-   [sys.partitions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql)  
  
-   [sys.column_store_segments &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-segments-transact-sql)  
  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql)  
  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql)  
  
  
