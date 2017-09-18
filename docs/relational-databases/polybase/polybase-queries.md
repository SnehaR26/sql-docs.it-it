---
title: Query di PolyBase | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 03/09/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- PolyBase
helpviewer_keywords:
- PolyBase, import and export
- Hadoop, import with PolyBase
- Hadoop, export with PolyBase
- Azure blob storage, import with PolyBase
- Azure blob storage, export with PolyBase
ms.assetid: 2c5aa2bd-af7d-4f57-9a28-9673c2a4c07e
caps.latest.revision: 18
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d6cc1b4523bdb0b48cfc22b34b205e15613fb290
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="polybase-queries"></a>PolyBase Queries
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Ecco alcune query di esempio che usano la funzionalità [PolyBase](../../relational-databases/polybase/polybase-guide.md) di SQL Server 2016. Prima di usare questi esempi è necessario comprendere anche le istruzioni T-SQL necessarie per configurare PolyBase (vedere [Oggetti T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md)).  
  
## <a name="queries"></a>Query  
 Eseguire istruzioni Transact-SQL su tabelle esterne oppure usare gli strumenti di Business Intelligence per eseguire query su tabelle esterne.  
  
## <a name="select-from-external-table"></a>SELECT da tabella esterna  
 Una query semplice che restituisce i dati da una tabella esterna definita.  
  
```tsql  
SELECT TOP 10 * FROM [dbo].[SensorData];   
```  
  
 Una query semplice che include un predicato.  
  
```  
SELECT * FROM [dbo].[SensorData]   
WHERE Speed > 65;   
```  
  
## <a name="join-external-tables-with-local-tables"></a>JOIN di tabelle esterne con tabelle locali  
  
```  
SELECT InsuranceCustomers.FirstName,   
                           InsuranceCustomers.LastName,   
                           SensorData.Speed  
FROM InsuranceCustomers INNER JOIN SensorData    
ON InsuranceCustomers.CustomerKey = SensorData.CustomerKey   
WHERE SensorData.Speed > 65   
ORDER BY SensorData.Speed DESC  
  
```  
  
## <a name="pushdown-computation-to-hadoop"></a>Calcolo della distribuzione in Hadoop  
 Le variazioni della distribuzione vengono visualizzate qui.  
  
### <a name="pushdown-for-selecting-a-subset-of-rows"></a>Distribuzione per la selezione di un subset di righe  
 Usare la distribuzione del predicato per migliorare le prestazioni se la query seleziona un subset di righe da una tabella esterna.  
  
 In questo caso SQL Server 2016 avvia un processo MapReduce per recuperare le righe che soddisfano il predicato customer.account_balance < 200000 in Hadoop. Poiché la query può essere completata correttamente senza eseguire la scansione di tutte le righe della tabella, vengono copiate in SQL Server solo le righe che soddisfano i criteri del predicato. In questo modo si risparmia molto tempo ed è necessario meno spazio per l'archiviazione temporanea quando il numero di saldi dei clienti inferiori a 200000 è ridotto rispetto al numero di clienti con saldi superiori o uguali a 200000.  
  Copy imageCopy Code   
SELECT * FROM customer WHERE customer.account_balance < 200000.  
  
```  
SELECT * FROM SensorData WHERE Speed > 65;  
```  
  
### <a name="pushdown-for-selecting-a-subset-of-columns"></a>Distribuzione per la selezione di un subset di colonne  
 Usare la distribuzione del predicato per migliorare le prestazioni se la query seleziona un subset di colonne da una tabella esterna.  
  
 In questa query, SQL Server avvia un processo MapReduce per pre-elaborare il file di testo delimitato di Hadoop in modo tale che solo i dati per le due colonne, customer.name e customer.zip_code, verranno copiati in SQL Server PDW.  
  
```  
SELECT customer.name, customer.zip_code FROM customer WHERE customer.account_balance < 200000  
  
```  
  
### <a name="pushdown-for-basic-expressions-and-operators"></a>Distribuzione per operatori ed espressioni di base  
 SQL Server consente gli operatori e le espressioni di base seguenti per la distribuzione del predicato.  
  
-   Operatori di confronto binari (\<, >, =, !=, <>, >=, <=) per valori numerici, di data e di ora.  
  
-   Operatori aritmetici ( +, -, *, /, % ).  
  
-   Operatori logici (AND, OR).  
  
-   Operatori unari (NOT, IS NULL, IS NOT NULL).  
  
 Gli operatori BETWEEN, NOT, IN e LIKE possono essere propagati. Ciò dipende dal modo in cui Query Optimizer li riscrive come serie di istruzioni che utilizzano operatori relazionali di base.  
  
 Questa query include più predicati che possono essere propagati ad Hadoop. SQL Server è in grado di distribuire i processi MapReduce in Hadoop per eseguire il predicato customer.account_balance <= 200000. L'espressione BETWEEN 92656 e 92677 è costituita da operazioni binarie e logiche che possono essere distribuite in Hadoop. L'operatore logico AND di customer.account_balance e customer.zipcode è un'espressione finale.  
  
 Con questa combinazione di elementi, i processi MapReduce possono eseguire interamente la clausola WHERE. Solo i dati che soddisfano i criteri SELECT verranno copiati in SQL Server PDW.  
  
```  
SELECT * FROM customer WHERE customer.account_balance <= 200000 AND customer.zipcode BETWEEN 92656 AND 92677  
  
```  
  
### <a name="force-pushdown"></a>Forzare la distribuzione  
  
```  
SELECT * FROM [dbo].[SensorData]   
WHERE Speed > 65  
OPTION (FORCE EXTERNALPUSHDOWN);   
```  
  
### <a name="disable-pushdown"></a>Disabilitare la distribuzione  
  
```  
SELECT * FROM [dbo].[SensorData]   
WHERE Speed > 65  
OPTION (DISABLE EXTERNALPUSHDOWN);  
```  
  
## <a name="import-data"></a>Importazione di dati  
 Importare dati da Hadoop o dall'archiviazione di Azure in SQL Server per l'archivio permanente. Usare SELECT INTO per importare i dati a cui fa riferimento una tabella esterna per l'archivio permanente in SQL Server. Creare un tabella relazionale e quindi creare un indice di archivio colonne nella parte superiore della tabella in un secondo passaggio.  
  
```sql  
-- PolyBase Scenario 2: Import external data into SQL Server.  
-- Import data for fast drivers into SQL Server to do more in-depth analysis and  
-- leverage Columnstore technology.  
  
SELECT DISTINCT   
        Insured_Customers.FirstName, Insured_Customers.LastName,   
        Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
INTO Fast_Customers from Insured_Customers INNER JOIN   
(  
        SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
ORDER BY YearlyIncome  
  
CREATE CLUSTERED COLUMNSTORE INDEX CCI_FastCustomers ON Fast_Customers;  
```  
  
## <a name="export-data"></a>Esportare dati  
Esportare dati da SQL Server in Hadoop o Archiviazione di Azure. Per prima cosa abilitare la funzionalità di esportazione impostando il valore sp_configure di 'allow polybase export' su 1. Creare quindi una tabella esterna che punta alla directory di destinazione. Usare quindi INSERT INTO per esportare i dati da una tabella di SQL Server locale a un'origine dati esterna. L'istruzione INSERT INTO crea la directory di destinazione, se non esiste, e i risultati dell'istruzione SELECT vengono esportati nel percorso specificato nel formato di file specificato. I file esterni sono denominati *QueryID_date_time_ID.format*, dove *ID* è un identificatore incrementale e *format* è il formato dei dati esportati. Ad esempio, QID776_20160130_182739_0.orc.  
  
```sql  
-- PolyBase Scenario 3: Export data from SQL Server to Hadoop.  
-- Create an external table.   
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
        [FirstName] char(25) NOT NULL,   
        [LastName] char(25) NOT NULL,   
        [YearlyIncome] float NULL,   
        [MaritalStatus] char(1) NOT NULL  
)  
WITH (  
        LOCATION='/old_data/2009/customerdata',  
        DATA_SOURCE = HadoopHDP2,  
        FILE_FORMAT = TextFileFormat,  
        REJECT_TYPE = VALUE,  
        REJECT_VALUE = 0  
);  
  
-- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
INSERT INTO dbo.FastCustomer2009  
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  
  
## <a name="new-catalog-views"></a>Nuove viste del catalogo  
 Le nuove viste del catalogo seguenti mostrano le risorse esterne.  
  
```sql  
SELECT * FROM sys.external_data_sources;   
SELECT * FROM sys.external_file_formats;  
SELECT * FROM sys.external_tables;  
```  
  
 Per determinare se una tabella è una tabella esterna, usare `is_external`  
  
```sql  
SELECT name, type, is_external FROM sys.tables WHERE name='myTableName'   
```  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per altre informazioni sulla risoluzione dei problemi, vedere [Risoluzione dei problemi di PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md).  
  
  
