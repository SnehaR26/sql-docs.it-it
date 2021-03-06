---
title: sp_executesql (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_executesql
- sp_executesql_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_executesql
- dynamic SQL
ms.assetid: a8d68d72-0f4d-4ecb-ae86-1235b962f646
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 20ddff9570c3d7bd092b9dbd757fb0541234b4af
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647059"
---
# <a name="spexecutesql-transact-sql"></a>sp_executesql (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Esegue un'istruzione o un batch [!INCLUDE[tsql](../../includes/tsql-md.md)] che può essere riutilizzato più volte o che è stato compilato in modo dinamico. L'istruzione o il batch [!INCLUDE[tsql](../../includes/tsql-md.md)] può contenere parametri incorporati.  
  
> [!IMPORTANT]  
>  Istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] compilate in fase di esecuzione possono esporre le applicazioni ad attacchi dannosi, ad esempio intrusioni nel codice SQL.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_executesql [ @stmt = ] statement  
[   
  { , [ @params = ] N'@parameter_name data_type [ OUT | OUTPUT ][ ,...n ]' }   
     { , [ @param1 = ] 'value1' [ ,...n ] }  
]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ \@stmt =] *istruzione*  
 È una stringa Unicode che contiene un [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione o il batch. \@stmt deve essere una costante Unicode o una variabile Unicode. Non sono consentite le espressioni Unicode più complesse, ad esempio per la concatenazione di due stringhe tramite l'operatore +. Le costanti di tipo carattere non sono consentite. Se viene specificata una costante Unicode, devono essere preceduto da un **N**. Ad esempio, la costante Unicode **n' sp_who'** valido, ma la costante carattere **'sp_who'** non. Le dimensioni massime della stringa dipendono dalla memoria disponibile nel server di database. Nei server a 64 bit, le dimensioni della stringa sono limitate a 2 GB, la dimensione massima del **nvarchar (max)**.  
  
> [!NOTE]  
>  \@stmt può contenere parametri con lo stesso formato di un nome di variabile, ad esempio: `N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 Ogni parametro incluso in \@stmt deve avere una voce corrispondente in entrambe le \@params elenco di definizioni di parametro e il parametro di elenco di valori.  
  
 [ \@params =] N'\@*parameter_name * * data_type* [,... *n* ] '  
 Stringa che contiene le definizioni di tutti i parametri che sono stati incorporati in \@stmt. La stringa deve essere una costante o una variabile Unicode. Ogni definizione di parametro è costituita da un nome del parametro e da un tipo di dati. *n* è un segnaposto che indica definizioni di parametro aggiuntive. Ogni parametro specificato in \@stmtmust essere definite in \@params. Se il [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione o il batch nel \@stmt non contiene parametri, \@params non è obbligatorio. Il valore predefinito per questo parametro è NULL.  
  
 [ \@param1 =] '*value1*'  
 Valore per il primo parametro definito nella stringa di parametri. Il valore può essere una costante o una variabile Unicode. Deve esistere un valore di parametro per ogni parametro incluso in \@stmt. I valori non sono necessari se il [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione o il batch in \@stmt non ha parametri.  
  
 [ OUT | OUTPUT ]  
 Indica che si tratta di un parametro di output. **testo**, **ntext**, e **immagine** parametri possono essere utilizzati come parametri di OUTPUT, a meno che la procedura è una routine di runtime (CLR) di linguaggio comuni. Un parametro di output che utilizza la parola chiave OUTPUT può essere il segnaposto di un cursore, a meno che la procedura non sia una procedura CLR.  
  
 *n*  
 Segnaposto per i valori di parametri aggiuntivi. I valori possono essere solo costanti o variabili. Non sono consentite espressioni più complesse quali funzioni o espressioni compilate tramite operatori.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o valore diverso da zero (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Restituisce i set di risultati di tutte le istruzioni SQL compilate nella stringa SQL.  
  
## <a name="remarks"></a>Note  
 i parametri di stored procedure sp_executesql devono essere immesso nell'ordine specifico, come descritto nella sezione "Sintassi" più indietro in questo argomento. Se i parametri non vengono immessi in ordine, verrà visualizzato un messaggio di errore.  
  
 La stored procedure sp_executesql funziona in modo analogo a EXECUTE per quanto riguarda i batch, l'ambito dei nomi e il contesto del database. Il [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione o un batch di sp_executesql \@stmt parametro non viene compilato finché non viene eseguita l'istruzione sp_executesql. Il contenuto di \@stmt viene quindi compilato ed eseguito come piano di esecuzione distinto dal piano di esecuzione del batch che ha chiamato sp_executesql. Il batch di sp_executesql non può fare riferimento a variabili dichiarate nel batch che chiama sp_executesql. I cursori o le variabili locali del batch sp_executesql non sono visibili per il batch che chiama sp_executesql. Le modifiche apportate al contesto del database durano solo fino al termine dell'esecuzione dell'istruzione sp_executesql.  
  
 È possibile utilizzare sp_executesql anziché stored procedure per eseguire un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] più volte quando l'unica variazione è costituita dalla modifica dei valori dei parametri. Poiché l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] stessa rimane costante e cambiano solo i valori dei parametri, è probabile che Query Optimizer di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] riutilizzi il piano di esecuzione generato per la prima esecuzione.  
  
> [!NOTE]  
>  Per ottimizzare le prestazioni, utilizzare nomi di oggetto completi nella stringa dell'istruzione.  
  
 L'impostazione dei valori dei parametri è supportata in modo autonomo da sp_executesql rispetto alla stringa  [!INCLUDE[tsql](../../includes/tsql-md.md)], come illustrato nell'esempio seguente.  
  
```  
DECLARE @IntVariable int;  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
  
/* Build the SQL string one time.*/  
SET @SQLString =  
     N'SELECT BusinessEntityID, NationalIDNumber, JobTitle, LoginID  
       FROM AdventureWorks2012.HumanResources.Employee   
       WHERE BusinessEntityID = @BusinessEntityID';  
SET @ParmDefinition = N'@BusinessEntityID tinyint';  
/* Execute the string with the first parameter value. */  
SET @IntVariable = 197;  
EXECUTE sp_executesql @SQLString, @ParmDefinition,  
                      @BusinessEntityID = @IntVariable;  
/* Execute the same string with the second parameter value. */  
SET @IntVariable = 109;  
EXECUTE sp_executesql @SQLString, @ParmDefinition,  
                      @BusinessEntityID = @IntVariable;  
```  
  
 È inoltre possibile utilizzare parametri di output con sp_executesql. Nell'esempio seguente un titolo professionale viene recuperato dalla tabella `AdventureWorks2012.HumanResources.Employee` e restituito nel parametro di output `@max_title`.  
  
```  
DECLARE @IntVariable int;  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
DECLARE @max_title varchar(30);  
  
SET @IntVariable = 197;  
SET @SQLString = N'SELECT @max_titleOUT = max(JobTitle)   
   FROM AdventureWorks2012.HumanResources.Employee  
   WHERE BusinessEntityID = @level';  
SET @ParmDefinition = N'@level tinyint, @max_titleOUT varchar(30) OUTPUT';  
  
EXECUTE sp_executesql @SQLString, @ParmDefinition, @level = @IntVariable, @max_titleOUT=@max_title OUTPUT;  
SELECT @max_title;  
```  
  
 La possibilità di sostituire i parametri in sp_executesql offre i vantaggi seguenti rispetto all'utilizzo dell'istruzione EXECUTE per l'esecuzione di una stringa:  
  
-   Dato che il testo effettivo dell'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] nella stringa sp_executesql rimane invariato tra un'esecuzione e la successiva, Query Optimizer cerca probabilmente di far corrispondere l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] nella seconda esecuzione con il piano di esecuzione generato per la prima esecuzione. Di conseguenza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non deve compilare la seconda istruzione.  
  
-   La stringa [!INCLUDE[tsql](../../includes/tsql-md.md)] viene compilata una sola volta.  
  
-   Il parametro integer viene specificato nel formato nativo. Non è necessario eseguire il cast a Unicode.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-executing-a-simple-select-statement"></a>A. Esecuzione di un'istruzione SELECT semplice  
 Nell'esempio seguente viene creata ed eseguita un'istruzione `SELECT` semplice che contiene un parametro incorporato denominato `@level`.  
  
```  
EXECUTE sp_executesql   
          N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
          WHERE BusinessEntityID = @level',  
          N'@level tinyint',  
          @level = 109;  
```  
  
### <a name="b-executing-a-dynamically-built-string"></a>B. Esecuzione di una stringa compilata in modo dinamico  
 Nell'esempio seguente viene illustrato l'utilizzo di `sp_executesql` per l'esecuzione di una stringa compilata in modo dinamico. La stored procedure di esempio consente di inserire dati in un set di tabelle utilizzate per il partizionamento dei dati relativi alle vendite annuali. È disponibile una sola tabella per ogni mese dell'anno nel formato seguente:  
  
```  
CREATE TABLE May1998Sales  
    (OrderID int PRIMARY KEY,  
    CustomerID int NOT NULL,  
    OrderDate  datetime NULL  
        CHECK (DATEPART(yy, OrderDate) = 1998),  
    OrderMonth int  
        CHECK (OrderMonth = 5),  
    DeliveryDate datetime  NULL,  
        CHECK (DATEPART(mm, OrderDate) = OrderMonth)  
    )  
```  
  
 Questa stored procedure di esempio compila in modo dinamico ed esegue un'istruzione `INSERT` per l'inserimento di nuovi ordini nella tabella corretta. La data dell'ordine viene utilizzata per compilare il nome della tabella che deve contenere i dati, quindi il nome viene incorporato in un'istruzione `INSERT`.  
  
> [!NOTE]  
>  Si tratta di un semplice esempio di utilizzo di sp_executesql. Non è previsto alcun controllo degli errori o delle regole business, ad esempio non viene verificato che i numeri di ordine siano univoci tra le tabelle.  
  
```  
CREATE PROCEDURE InsertSales @PrmOrderID INT, @PrmCustomerID INT,  
                 @PrmOrderDate DATETIME, @PrmDeliveryDate DATETIME  
AS  
DECLARE @InsertString NVARCHAR(500)  
DECLARE @OrderMonth INT  
  
-- Build the INSERT statement.  
SET @InsertString = 'INSERT INTO ' +  
       /* Build the name of the table. */  
       SUBSTRING( DATENAME(mm, @PrmOrderDate), 1, 3) +  
       CAST(DATEPART(yy, @PrmOrderDate) AS CHAR(4) ) +  
       'Sales' +  
       /* Build a VALUES clause. */  
       ' VALUES (@InsOrderID, @InsCustID, @InsOrdDate,' +  
       ' @InsOrdMonth, @InsDelDate)'  
  
/* Set the value to use for the order month because  
   functions are not allowed in the sp_executesql parameter  
   list. */  
SET @OrderMonth = DATEPART(mm, @PrmOrderDate)  
  
EXEC sp_executesql @InsertString,  
     N'@InsOrderID INT, @InsCustID INT, @InsOrdDate DATETIME,  
       @InsOrdMonth INT, @InsDelDate DATETIME',  
     @PrmOrderID, @PrmCustomerID, @PrmOrderDate,  
     @OrderMonth, @PrmDeliveryDate  
  
GO  
```  
  
 L'utilizzo di sp_executesql in questa procedura è più funzionale rispetto all'utilizzo di EXECUTE per l'esecuzione di una stringa. Quando si utilizza sp_executesql, vengono generate solo 12 versioni della stringa INSERT, una per ogni tabella mensile. Con l'istruzione EXECUTE ogni stringa INSERT è univoca, in quanto i valori dei parametri sono diversi. Sebbene entrambi i metodi generino lo stesso numero di batch, data la similarità delle stringhe INSERT generate da sp_executesql è più probabile che Query Optimizer riutilizzi i piani di esecuzione.  
  
### <a name="c-using-the-output-parameter"></a>C. Utilizzo del parametro OUTPUT  
 L'esempio seguente usa un' `OUTPUT` parametro per archiviare il set di risultati generato dal `SELECT` istruzione il `@SQLString` parametro. Due `SELECT` vengono quindi eseguite che utilizzano il valore di istruzioni il `OUTPUT` parametro.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
DECLARE @SalesOrderNumber nvarchar(25);  
DECLARE @IntVariable int;  
SET @SQLString = N'SELECT @SalesOrderOUT = MAX(SalesOrderNumber)  
    FROM Sales.SalesOrderHeader  
    WHERE CustomerID = @CustomerID';  
SET @ParmDefinition = N'@CustomerID int,  
    @SalesOrderOUT nvarchar(25) OUTPUT';  
SET @IntVariable = 22276;  
EXECUTE sp_executesql  
    @SQLString  
    ,@ParmDefinition  
    ,@CustomerID = @IntVariable  
    ,@SalesOrderOUT = @SalesOrderNumber OUTPUT;  
-- This SELECT statement returns the value of the OUTPUT parameter.  
SELECT @SalesOrderNumber;  
-- This SELECT statement uses the value of the OUTPUT parameter in  
-- the WHERE clause.  
SELECT OrderDate, TotalDue  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderNumber = @SalesOrderNumber;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-executing-a-simple-select-statement"></a>D. Esecuzione di un'istruzione SELECT semplice  
 Nell'esempio seguente viene creata ed eseguita un'istruzione `SELECT` semplice che contiene un parametro incorporato denominato `@level`.  
  
```  
-- Uses AdventureWorks  
  
EXECUTE sp_executesql   
          N'SELECT * FROM AdventureWorksPDW2012.dbo.DimEmployee   
          WHERE EmployeeKey = @level',  
          N'@level tinyint',  
          @level = 109;  
```  
  
 Per altri esempi, vedere [sp_executesql (Transact-SQL)](http://msdn.microsoft.com/library/ms188001.aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
