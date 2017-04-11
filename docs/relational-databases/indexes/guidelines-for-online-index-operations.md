---
title: "Linee guida per operazioni di indice online | Microsoft Docs"
ms.custom: ""
ms.date: "03/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "indici cluster, operazioni online"
  - "operazioni sugli indici online"
  - "indici [SQL Server], operazioni online"
  - "spazio su disco [SQL Server], indici"
  - "indici non cluster [SQL Server], operazioni online"
  - "log delle transazioni [SQL Server], indici"
ms.assetid: d82942e0-4a86-4b34-a65f-9f143ebe85ce
caps.latest.revision: 64
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 60
---
# Linee guida per operazioni di indice online
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Quando si eseguono operazioni sugli indici online sono da ritenersi valide le linee guida seguenti:  
  
-   Gli indici cluster devono essere creati, ricompilati o eliminati offline se la tabella sottostante contiene i seguenti tipi di dati dell'oggetto LOB: **image**, **ntext**e **text**.  
  
-   È possibile creare indici non cluster non univoci online quando la tabella contiene tipi di dati LOB ma nessuna di queste colonne è utilizzata nella definizione di indice come colonna chiave o non chiave (inclusa).  
  
-   Non è possibile creare, ricompilare o eliminare online indici su tabelle temporanee locali. Questa limitazione non è valida per gli indici su tabelle temporanee globali.  
  
> [!NOTE]  
>  Le operazioni sugli indici online sono disponibili solo in alcune edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
 Nella tabella seguente sono riportate le operazioni sugli indici che è possibile eseguire online e gli indici che sono esclusi da queste operazioni online. Sono inoltre incluse ulteriori limitazioni.  
  
|Operazione su indice online|Indici esclusi|Altre limitazioni|  
|----------------------------|----------------------|------------------------|  
|ALTER INDEX REBUILD|Indice cluster disabilitato o vista indicizzata disabilitata<br /><br /> Indice XML<br /><br />Indice columnstore <br /><br /> Indice di una tabella temporanea locale|L'operazione può avere esito negativo se la tabella contiene un indice escluso e si utilizza la parola chiave ALL.<br /><br /> Sono applicabili ulteriori restrizioni nella ricompilazione di indici disabilitati. Per altre informazioni, vedere [Disabilitazione di indici e vincoli](../../relational-databases/indexes/disable-indexes-and-constraints.md).|  
|CREATE INDEX|Indice XML<br /><br /> Indice cluster univoco iniziale su una vista<br /><br /> Indice di una tabella temporanea locale||  
|CREATE INDEX WITH DROP_EXISTING|Indice cluster disabilitato o vista indicizzata disabilitata<br /><br /> Indice di una tabella temporanea locale<br /><br /> Indice XML||  
|DROP INDEX|Indice disabilitato<br /><br /> Indice XML<br /><br /> Indice non cluster<br /><br /> Indice di una tabella temporanea locale|Non è possibile specificare più indici in una singola istruzione.|  
|ALTER TABLE ADD CONSTRAINT (PRIMARY KEY o UNIQUE)|Indice di una tabella temporanea locale<br /><br /> Indice cluster|È consentito l'utilizzo di una sola clausola secondaria alla volta. Ad esempio, non è possibile aggiungere ed eliminare vincoli PRIMARY KEY o UNIQUE nella stessa istruzione ALTER TABLE.|  
|ALTER TABLE DROP CONSTRAINT (PRIMARY KEY o UNIQUE)|Indice cluster||  
  
 Non è possibile modificare, troncare o eliminare la tabella sottostante mentre è in corso un'operazione su un indice online.  
  
 L'impostazione di un'opzione online (ON oppure OFF) specificata durante la creazione o l'eliminazione di un indice cluster viene applicata a tutti gli indici non cluster che devono essere ricompilati. Ad esempio, se l'indice cluster viene compilato online utilizzando CREATE INDEX WITH DROP_EXISTING, ONLINE=ON, anche tutti gli indici non cluster associati vengono ricreati online.  
  
 Quando si crea o si ricompila un indice UNIQUE online, il generatore dell'indice e una transazione utente simultanea potrebbero tentare di inserire la stessa chiave, causando una violazione di univocità. Se una riga immessa da un utente viene inserita nel nuovo indice (destinazione) prima che la riga originale della tabella di origine venga spostata nel nuovo indice, l'operazione sull'indice online avrà esito negativo.  
  
 Un'operazione su un indice online può in rari casi provocare un deadlock quando interagisce con aggiornamenti al database a causa di attività dell'utente o dell'applicazione. In questi rari casi, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] selezionerà l'attività dell'utente o dell'applicazione come vittima del deadlock.  
  
 È possibile eseguire operazioni DDL sugli indici online simultanee sulla stessa tabella o vista solo quando si stanno creando più indici nuovi non cluster oppure si stanno riorganizzando indici non cluster. Qualsiasi altra operazione sugli indici online eseguita nello stesso istante avrà esito negativo. Ad esempio, non è possibile creare un nuovo indice online durante la ricompilazione di un indice online esistente sulla stessa tabella.  
  
 Non è possibile eseguire un'operazione online se un indice contiene una colonna di tipo di oggetti di grandi dimensioni e nella stessa transazione sono presenti operazioni di aggiornamento prima di questa operazione online. Per risolvere questo problema, posizionare l'operazione online all'esterno della transazione o prima degli aggiornamenti all'interno della transazione.  
  
## <a name="disk-space-considerations"></a>Considerazioni sullo spazio su disco  
 I requisiti dello spazio su disco sono generalmente gli stessi per operazioni sugli indici online e offline. Un'eccezione è costituita dallo spazio su disco aggiuntivo richiesto dall'indice di mapping temporaneo. Questo indice temporaneo è utilizzato nelle operazioni sugli indici online che creano, ricompilano o eliminano un indice cluster. L'eliminazione di un indice cluster online richiede lo stesso spazio che è necessario per la creazione di un indice cluster online. Per altre informazioni, vedere [Disk Space Requirements for Index DDL Operations](../../relational-databases/indexes/disk-space-requirements-for-index-ddl-operations.md).  
  
## <a name="performance-considerations"></a>Considerazioni sulle prestazioni  
 Sebbene le operazioni sugli indici online consentano l'esecuzione di attività simultanee di aggiornamento utente, le operazioni sugli indici impiegheranno più tempo se l'attività di aggiornamento genera un notevole carico. Le operazioni sugli indici online saranno generalmente più lente delle operazioni sugli indici offline equivalenti, indipendentemente dal livello di attività di aggiornamento simultanee.  
  
 Dato che durante le operazioni sugli indici online vengono mantenute sia la struttura di origine che quella di destinazione, l'utilizzo di risorse per l'inserimento, l'aggiornamento e l'eliminazione delle transazioni viene aumentato, potenzialmente fino al doppio. Ciò può causare una riduzione delle prestazioni e un maggior utilizzo di risorse durante l'operazione sugli indici, specialmente del tempo CPU. Le operazioni sugli indici online vengono registrate completamente.  
  
 Sebbene le operazioni online siano consigliabili, è opportuno valutare l'ambiente e i requisiti specifici, in base ai quali l'esecuzione delle operazioni sugli indici offline potrebbe essere la soluzione ottimale. In quest'ultimo caso gli utenti avrebbero un accesso limitato ai dati durante l'operazione, la quale però terminerebbe più rapidamente e utilizzerebbe meno risorse.  
  
 Nei computer multiprocessore che eseguono [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]le istruzioni per gli indici, analogamente ad altre query, possono utilizzare più processori per eseguire le operazioni di analisi e ordinamento associate all'istruzione. È possibile utilizzare l'opzione dell'indice MAXDOP per controllare il numero di processori dedicati all'operazione di indice online. In questo modo è possibile bilanciare le risorse utilizzate dall'operazione sugli indici con quelle occupate dagli utenti simultanei. Per altre informazioni, vedere [Configurare operazioni parallele sugli indici](../../relational-databases/indexes/configure-parallel-index-operations.md). Per altre informazioni sulle edizioni di SQL Server che supportano le operazioni indicizzate parallele, vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
 Poiché al termine dell'esecuzione dell'operazione sugli indici viene mantenuto un blocco S o Sch-M, è necessario prestare particolare attenzione quando si esegue un'operazione sugli indici online all'interno di una transazione utente esplicita, ad esempio un blocco BEGIN TRANSACTION...COMMIT. Una tale operazione causa il mantenimento del blocco fino alla fine della transazione, impedendo quindi la concorrenza degli utenti.  
  
 La ricompilazione degli indici online può aumentare la frammentazione quando è consentita l'esecuzione con le opzioni `MAX DOP > 1` e `ALLOW_PAGE_LOCKS = OFF` . Per altre informazioni, vedere [Funzionamento: Ricompilazione di indici online - Possibilità di aumento della frammentazione](http://blogs.msdn.com/b/psssql/archive/2012/09/05/how-it-works-online-index-rebuild-can-cause-increased-fragmentation.aspx).  
  
## <a name="transaction-log-considerations"></a>Considerazioni sul log delle transazioni  
 Operazioni sugli indici su larga scala, eseguite online oppure offline, possono generare volumi di dati elevati i quali possono esaurire rapidamente lo spazio disponibile nel log delle transazioni. Per garantire la possibilità di eseguire il rollback dell'operazione sugli indici, non è possibile troncare il log delle transazioni fino al completamento dell'operazione. È tuttavia possibile eseguire il backup del log durante l'operazione sugli indici. È pertanto necessario che il log delle transazioni abbia spazio sufficiente per archiviare sia le transazioni dell'operazione sugli indici sia tutte le transazioni utente simultanee per l'intera durata dell'operazione sugli indici. Per altre informazioni, vedere [Spazio su disco per il log delle transazioni per operazioni sugli indici](../../relational-databases/indexes/transaction-log-disk-space-for-index-operations.md).  
  
## <a name="related-content"></a>Contenuto correlato  
 [Funzionamento delle operazioni sugli indici online](../../relational-databases/indexes/how-online-index-operations-work.md)  
  
 [Eseguire operazioni online sugli indici](../../relational-databases/indexes/perform-index-operations-online.md)  
  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)  
  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
  