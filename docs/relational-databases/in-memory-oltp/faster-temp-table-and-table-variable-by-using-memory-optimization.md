---
title: "Tabella temporanea e variabile di tabella pi&#249; rapide con l&#39;ottimizzazione per la memoria | Microsoft Docs"
ms.custom: ""
ms.date: "01/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38512a22-7e63-436f-9c13-dde7cf5c2202
caps.latest.revision: 20
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 19
---
# Tabella temporanea e variabile di tabella pi&#249; rapide con l&#39;ottimizzazione per la memoria
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  
Se si usano tabelle temporanee, variabili di tabella o parametri con valori di tabella, è possibile convertirli per usufruire delle tabelle e delle variabili di tabella con ottimizzazione per la memoria per migliorare le prestazioni. Le modifiche al codice sono in genere limitate.  
  
Questo articolo descrive:  
  
- Scenari a sostegno della conversione in elementi in memoria.  
- Passaggi tecnici per l'implementazione della conversione in elementi in memoria.  
- Prerequisiti per la conversione in elementi in memoria.  
- Un esempio di codice che evidenzia i vantaggi in termini di prestazioni dell'ottimizzazione per la memoria
  
  
## A. Introduzione alle variabili di tabella con ottimizzazione per la memoria  
  
Una variabile di tabella con ottimizzazione per la memoria offre una maggiore efficienza grazie all'uso dello stesso algoritmo e delle stesse strutture di dati con ottimizzazione per la memoria usate dalle tabelle con ottimizzazione per la memoria. L'efficienza è particolarmente evidente quando viene eseguito l'accesso alla variabile di tabella dall'interno di un modulo compilato in modo nativo.  
  
  
Una variabile di tabella con ottimizzazione per la memoria:  
  
- È archiviata solo in memoria e non ha alcun componente su disco.  
- Non comporta alcuna attività di I/O.  
- Non comporta alcun utilizzo di tempdb o contesa.  
- Può essere passata in una stored procedure come parametro con valori di tabella (TVP).  
- Deve avere almeno un indice, hash o non cluster.  
  - Per un indice hash, il numero di bucket dovrebbe essere idealmente 1 o 2 volte il numero di chiavi di indice univoco previsto. Tuttavia, sovrastimare il numero di bucket è solitamente corretto (fino a 10 X). Per dettagli, vedere [Indexes for Memory-Optimized Tables](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md) (Indici per tabelle con ottimizzazione per la memoria).  

  
  
#### Tipi di oggetti  
  
OLTP in memoria offre gli oggetti seguenti che possono essere usati per l'ottimizzazione per la memoria di tabelle temporanee e variabili di tabella:  
  
- Tabelle con ottimizzazione per la memoria  
  - Durability = SCHEMA_ONLY  
- Variabili di tabella con ottimizzazione per la memoria  
  - Devono essere dichiarate in due passaggi (anziché inline):  
    - `CREATE TYPE my_type AS TABLE ...;` , quindi  
    - `DECLARE @mytablevariable my_type;`.  
  
  
## B. Scenario: sostituire la tabella temporanea globale  
  
Si supponga di avere la tabella temporanea globale seguente.  
  
  
  
  
    CREATE TABLE ##tempGlobalB  
    (  
        Column1   INT   NOT NULL ,  
        Column2   NVARCHAR(4000)  
    );  
  
  
  
  
È possibile sostituire la tabella temporanea globale con la tabella con ottimizzazione per la memoria seguente che include DURABILITY = SCHEMA_ONLY.  
  
  
  
  
    CREATE TABLE dbo.soGlobalB  
    (  
        Column1   INT   NOT NULL   INDEX ix1 NONCLUSTERED,  
        Column2   NVARCHAR(4000)  
    )  
        WITH  
            (MEMORY_OPTIMIZED = ON,  
            DURABILITY        = SCHEMA_ONLY);  
  
  
  
  
#### B.1 Passaggi  
  
Per convertire la tabella temporanea globale in SCHEMA_ONLY, eseguire i passaggi seguenti:  
  
  
1. Creare la tabella **dbo.soGlobalB**, una sola volta, allo stesso modo di una normale tabella su disco.  
2. Rimuovere da Transact-SQL la creazione della tabella **&#x23;&#x23;tempGlobalB**.  
3. In T-SQL sostituire tutti i riferimenti di **&#x23;&#x23;tempGlobalB** con **dbo.soGlobalB**.  
  
  
## C. Scenario: sostituire la tabella temporanea di sessione  
  
Le operazioni preliminari per la sostituzione di una tabella temporanea di sessione implicano un uso maggiore di T-SQL rispetto allo scenario della tabella temporanea globale precedente. Fortunatamente, una maggior quantità di T-SQL non implica alcuna altra operazione per eseguire la conversione.  
  
Si supponga di avere la tabella temporanea di sessione seguente.  
  
  
  
  
    CREATE TABLE #tempSessionC  
    (  
        Column1   INT   NOT NULL ,  
        Column2   NVARCHAR(4000)  
    );  
  
  
  
  
Innanzitutto, creare la funzione con valori di tabella seguente per applicare un filtro in **@@spid**. La funzione potrà essere usata da tutte le tabelle SCHEMA_ONLY convertite da tabelle temporanee di sessione.  
  
  
  
  
    CREATE FUNCTION dbo.fn_SpidFilter(@SpidFilter smallint)  
        RETURNS TABLE  
        WITH SCHEMABINDING , NATIVE_COMPILATION  
    AS  
        RETURN  
            SELECT 1 AS fn_SpidFilter  
                WHERE @SpidFilter = @@spid;  
  
  
  
  
Creare quindi la tabella SCHEMA_ONLY e i criteri di sicurezza nella tabella.  
  
  
Si noti che ogni tabella con ottimizzazione per la memoria deve contenere almeno un indice.  
  
- Per la tabella dbo.soSessionC potrebbe essere consigliabile un indice HASH, se viene calcolato il BUCKET_COUNT corretto. In questo esempio, tuttavia, viene usato per semplicità un indice NONCLUSTERED.  
  
  
  
  
    CREATE TABLE dbo.soSessionC  
    (  
        Column1     INT         NOT NULL,  
        Column2     NVARCHAR(4000)  NULL,  
  
        SpidFilter  SMALLINT    NOT NULL   DEFAULT (@@spid),  
  
        INDEX ix_SpidFiler NONCLUSTERED (SpidFilter),  
        --INDEX ix_SpidFilter HASH  
        --    (SpidFilter) WITH (BUCKET_COUNT = 64),  
          
        CONSTRAINT CHK_soSessionC_SpidFilter  
            CHECK ( SpidFilter = @@spid ),  
    )  
        WITH  
            (MEMORY_OPTIMIZED = ON,  
             DURABILITY = SCHEMA_ONLY);  
    go  
  
  
    CREATE SECURITY POLICY dbo.soSessionC_SpidFilter_Policy  
        ADD FILTER PREDICATE dbo.fn_SpidFilter(SpidFilter)  
        ON dbo.soSessionC  
        WITH (STATE = ON);  
    go  
  
  
  
  
Infine, nel codice T-SQL generale:  
  
1. Cancellare tutte le istruzioni CREATE TABLE per la tabella temporanea di sessione precedente.  
2. Sostituire il nome di tabella precedente con il nuovo nome:  
  - _Precedente:_ &#x23;tempSessionC  
  - _Nuovo:_ dbo.soSessionC  
  
  
  
## D. Scenario: la variabile di tabella può essere MEMORY_OPTIMIZED=ON  
  
  
Una variabile di tabella tradizionale rappresenta una tabella del database tempdb. Per ottenere migliori prestazioni è possibile convertire la variabile di tabella in variabile di tabella con ottimizzazione per la memoria.  
  
Di seguito è riportato il codice T-SQL per una variabile di tabella tradizionale. L'ambito termina alla fine del batch o della sessione.  
  
  
  
  
    DECLARE @tvTableD TABLE  
        ( Column1   INT   NOT NULL ,  
          Column2   CHAR(10) );  
  
  
  
  
#### D.1 Convertire da inline a esplicito  
  
La sintassi precedente crea la variabile di tabella *inline*. La sintassi inline non supporta l'ottimizzazione per la memoria. È necessario quindi convertire la sintassi inline nella sintassi esplicita per TYPE.  
  
*Ambito:* la definizione TYPE creata dal primo batch delimitato da go rimane valida anche dopo che il server è stato arrestato e riavviato. Tuttavia, dopo il primo delimitatore go, la tabella dichiarata @tvTableC rimane valida solo fino a quando non viene raggiunto il go successivo e la fine del batch.  
  
  
  
  
    CREATE TYPE dbo.typeTableD  
        AS TABLE  
        (  
            Column1  INT   NOT NULL ,  
            Column2  CHAR(10)  
        );  
    go  
          
    SET NoCount ON;  
    DECLARE @tvTableD dbo.typeTableD  
    ;  
    INSERT INTO @tvTableD (Column1) values (1), (2)  
    ;  
    SELECT * from @tvTableD;  
    go  
  
  
  
  
#### D.2 Convertire esplicito su disco in ottimizzato per la memoria  
  
Una variabile di tabella con ottimizzazione per la memoria è memorizzata in tempdb. L'ottimizzazione per la memoria offre una velocità spesso maggiore di 10 volte o più.  
  
La conversione in ottimizzato per la memoria viene eseguita in un solo passaggio. Migliorare la creazione TYPE esplicita come segue, aggiungendo:  
  
- Un indice. Si noti che ogni tabella con ottimizzazione per la memoria deve contenere almeno un indice.  
- MEMORY_OPTIMIZED = ON.  
  
  
  
  
    CREATE TYPE dbo.typeTableD  
        AS TABLE  
        (  
            Column1  INT   NOT NULL   INDEX ix1,  
            Column2  CHAR(10)  
        )  
        WITH  
            (MEMORY_OPTIMIZED = ON);  
  
  
  
  
La conversione è stata completata.  
  
  
## E. FILEGROUP prerequisito per SQL Server  
  
In Microsoft SQL Server per usare le funzionalità di ottimizzazione per la memoria, è necessario che il database includa un FILEGROUP dichiarato con **MEMORY_OPTIMIZED_DATA**.  
  
- Il database SQL di Azure non richiede la creazione del FILEGROUP.  
  
  
*Prerequisito:* il seguente codice Transact-SQL per un FILEGROUP è un prerequisito per i lunghi esempi di codice T-SQL riportati nelle sezioni successive di questo articolo.  
  
1. È necessario usare SSMS.exe o un altro strumento che può inviare T-SQL.  
2. Incollare il codice T-SQL di FILEGROUP di esempio in SQL Server Management Studio.  
3. Modificare il codice T-SQL per cambiare i nomi e i percorsi di directory in base alle proprie esigenze.  
  - Tutte le directory nel valore FILENAME devono essere già esistenti, ad eccezione della directory finale.  
4. Eseguire il codice T-SQL modificato.  
  - Non è necessario eseguire il FILEGROUP T-SQL più di una volta, anche nel caso in cui il codice T-SQL di confronto della velocità venga modificato e rieseguito più volte.  
  
  
  
 
  
    ALTER DATABASE InMemTest2  
        ADD FILEGROUP FgMemOptim3  
            CONTAINS MEMORY_OPTIMIZED_DATA;  
    go  
    ALTER DATABASE InMemTest2  
        ADD FILE  
        (  
            NAME = N'FileMemOptim3a',  
            FILENAME = N'C:\DATA\FileMemOptim3a'  
                     --  C:\DATA\    preexisted.  
        )  
        TO FILEGROUP FgMemOptim3;  
    go  
  
  
Lo script seguente crea automaticamente il filegroup e configura le impostazioni di database consigliate: [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)
  
Per altre informazioni su `ALTER DATABASE ... ADD` per FILE e FILEGROUP, vedere:  
  
- [Opzioni per file e filegroup ALTER DATABASE (Transact-SQL)](ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20(Transact-SQL).xml)  
- [Filegroup con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)    
  
  
## F. Test rapido per dimostrare il miglioramento della velocità  
  
  
Questa sezione include il codice Transact-SQL che è possibile eseguire per testare e confrontare l'aumento della velocità di INSERT-DELETE dovuto all'uso di una variabile di tabella con ottimizzazione per la memoria. Il codice è suddiviso in due parti pressoché uguali, ad eccezione del fatto che nella prima parte il tipo di tabella corrisponde a una tabella con ottimizzazione per la memoria.  
  
Il test di confronto richiede circa 7 secondi. Per eseguire l'esempio:  
  
1. *Prerequisito:* è necessario avere già eseguito il codice T-SQL di FILEGROUP della sezione precedente.  
2. Eseguire lo script INSERT-DELETE T-SQL seguente.  
  - Si noti l'istruzione 'GO 5001' che invia il codice T-SQL 5001 volte. È possibile modificare il numero ed eseguire di nuovo lo script.  
  
Quando si esegue lo script in un database SQL di Azure, assicurarsi di eseguire lo script da una macchina virtuale nella stessa area.
  
  
    PRINT ' ';  
    PRINT '---- Next, memory-optimized, faster. ----';  
  
    DROP TYPE IF EXISTS dbo.typeTableC_mem;  
    go  
    CREATE TYPE dbo.typeTableC_mem  -- !!  Memory-optimized.  
         AS TABLE  
         (  
              Column1  INT NOT NULL INDEX ix1,  
              Column2  CHAR(10)  
         )  
         WITH  
              (MEMORY_OPTIMIZED = ON);  
    go  
    DECLARE @dateString_Begin nvarchar(64) =  
        Convert(nvarchar(64), GetUtcDate(), 121);  
    PRINT Concat(@dateString_Begin, '  = Begin time, _mem.');  
    go  
    SET NoCount ON;  
    DECLARE @tvTableC dbo.typeTableC_mem;  -- !!  
  
    INSERT INTO @tvTableC (Column1) values (1), (2);  
    INSERT INTO @tvTableC (Column1) values (3), (4);  
    DELETE @tvTableC;  
  
    GO 5001  
  
    DECLARE @dateString_End nvarchar(64) =  
        Convert(nvarchar(64), GetUtcDate(), 121);  
    PRINT Concat(@dateString_End, '  = End time, _mem.');  
    go  
    DROP TYPE IF EXISTS dbo.typeTableC_mem;  
    go  
  
    ---- End memory-optimized.  
    -------------------------------------------------  
    ---- Start traditional on-disk.  
  
    PRINT ' ';  
    PRINT '---- Next, tempdb based, slower. ----';  
  
    DROP TYPE IF EXISTS dbo.typeTableC_tempdb;  
    go  
    CREATE TYPE dbo.typeTableC_tempdb  -- !!  Traditional tempdb.  
        AS TABLE  
        (  
            Column1  INT NOT NULL ,  
            Column2  CHAR(10)  
        );  
    go  
    DECLARE @dateString_Begin nvarchar(64) =  
        Convert(nvarchar(64), GetUtcDate(), 121);  
    PRINT Concat(@dateString_Begin, '  = Begin time, _tempdb.');  
    go  
    SET NoCount ON;  
    DECLARE @tvTableC dbo.typeTableC_tempdb;  -- !!  
  
    INSERT INTO @tvTableC (Column1) values (1), (2);  
    INSERT INTO @tvTableC (Column1) values (3), (4);  
    DELETE @tvTableC;  
  
    GO 5001  
  
    DECLARE @dateString_End nvarchar(64) =  
        Convert(nvarchar(64), GetUtcDate(), 121);  
    PRINT Concat(@dateString_End, '  = End time, _tempdb.');  
    go  
    DROP TYPE IF EXISTS dbo.typeTableC_tempdb;  
    go  
    ----  
  
    PRINT '---- Tests done. ----';  
  
    go  
  
    /*** Actual output, SQL Server 2016:  
  
    ---- Next, memory-optimized, faster. ----  
    2016-04-20 00:26:58.033  = Begin time, _mem.  
    Beginning execution loop  
    Batch execution completed 5001 times.  
    2016-04-20 00:26:58.733  = End time, _mem.  
  
    ---- Next, tempdb based, slower. ----  
    2016-04-20 00:26:58.750  = Begin time, _tempdb.  
    Beginning execution loop  
    Batch execution completed 5001 times.  
    2016-04-20 00:27:05.440  = End time, _tempdb.  
    ---- Tests done. ----  
    ***/  
  

  
  
  
## G. Stimare il consumo di memoria attiva  
  
È possibile imparare a prevedere la quantità di memoria attiva richiesta dalle tabelle con ottimizzazione per la memoria con le risorse seguenti:  
  
- [Stimare i requisiti di memoria delle tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)  
- [Dimensioni di tabelle e righe per le tabelle con ottimizzazione per la memoria: esempio di calcolo](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
Per le variabili di tabella di dimensioni maggiori, gli indici non cluster usano una maggior quantità di memoria rispetto a quella usata per le *tabelle* con ottimizzazione per la memoria. Maggiore è il totale delle righe e la chiave di indice, maggiore sarà la differenza.  
  
Se l'accesso alla variabile di tabella con ottimizzazione per la memoria avviene soltanto con un determinato valore di chiave a ogni accesso, è consigliabile usare un indice hash anziché un indice non cluster. Tuttavia, se non si è in grado di stimare il valore BUCKET_COUNT appropriato, un indice NONCLUSTERED rappresenta una buona scelta.  
  
## H. Vedere anche  
  
- [Tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)
- [Definizione di durabilità per gli oggetti con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/defining-durability-for-memory-optimized-objects.md)  
  
  
  
  
\<!--  
CAPS Title: "Faster temp table and table variable by using memory optimization"  
  
https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/  
  
  
[ALTER DATABASE File and Filegroup Options (Transact-SQL)](http://msdn.microsoft.com/library/bb522469.aspx)  
  
[The Memory Optimized Filegroup](http://msdn.microsoft.com/library/dn639109.aspx)  
  
[Resource Governor Resource Pool](http://msdn.microsoft.com/library/hh510189.aspx)  
  
  
[Memory Optimization Advisor](http://msdn.microsoft.com/library/dn284308.aspx)  
  
[Estimate Memory Requirements for Memory-Optimized Tables](http://msdn.microsoft.com/library/dn282389.aspx)  
  
[Table and Row Size in Memory-Optimized Tables: Example Calculation](http://msdn.microsoft.com/library/dn205318.aspx)  
  
  
[Durability for Memory-Optimized Tables](http://msdn.microsoft.com/library/dn553125.aspx)  
  
[Defining Durability for Memory-Optimized Objects](http://msdn.microsoft.com/library/dn553122.aspx)  
  
[Memory-Optimized Table Variables](http://msdn.microsoft.com/library/dn535766.aspx)  
  
  
GeneMi , 2016-05-02  Monday  18:40pm  
-->  
  
  
  