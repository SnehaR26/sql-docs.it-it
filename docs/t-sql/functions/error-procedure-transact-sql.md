---
title: ERROR_PROCEDURE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ERROR_PROCEDURE_TSQL
- ERROR_PROCEDURE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_PROCEDURE function
- messages [SQL Server], trigger where occurred
- errors [SQL Server], stored procedure where occurred
- TRY...CATCH [SQL Server]
- CATCH block
- messages [SQL Server], stored procedure where occurred
- errors [SQL Server], trigger where occurred
ms.assetid: b81edbf0-856a-498f-ba87-48ff1426d980
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 459119eb08117ed52a455fdfb80fe3f393a410fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47807103"
---
# <a name="errorprocedure-transact-sql"></a>ERROR_PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Questa funzione restituisce il nome della stored procedure o del trigger in cui si verifica un errore se tale errore ha causato l'esecuzione del blocco CATCH di un costrutto TRY…CATCH.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ERROR_PROCEDURE ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
**nvarchar(128)**  
  
## <a name="return-value"></a>Valore restituito  
Quando viene chiamata nel blocco CATCH di una stored procedure in cui si verifica un errore, `ERROR_PROCEDURE` restituisce il nome di tale stored procedure.  
  
`ERROR_PROCEDURE` restituisce NULL se l'errore non si è verificato all'interno di una stored procedure o un trigger.  
  
`ERROR_PROCEDURE` restituisce NULL quando viene chiamata all'esterno dell'ambito di un blocco CATCH.  
  
## <a name="remarks"></a>Remarks  
`ERROR_PROCEDURE` supporta le chiamate da un qualsiasi punto nell'ambito di un blocco CATCH.  
  
`ERROR_PROCEDURE` restituisce il nome della stored procedure o del trigger in cui si verifica un errore, indipendentemente dal numero di esecuzioni o dalla posizione in cui viene eseguita nell'ambito del blocco `CATCH`. Questo tipo di comportamento è in contrasto con una funzione come @@ERROR, che restituisce solo un numero di errore nell'istruzione immediatamente successiva a quella che ha provocato un errore.  
  
In un blocco `CATCH` `ERROR_PROCEDURE` restituisce il numero di errore specifico dell'ambito del blocco `CATCH` che ha fatto riferimento a tale blocco `CATCH`. Ad esempio, il blocco `CATCH` di un costrutto esterno TRY...CATCH potrebbe includere un costrutto `TRY...CATCH` interno. In tale blocco `CATCH` interno `ERROR_PROCEDURE` restituisce il numero dell'errore che ha richiamato il blocco `CATCH` interno. Se `ERROR_PROCEDURE` viene eseguito nel blocco `CATCH` esterno, restituisce il numero dell'errore che ha richiamato il blocco `CATCH` esterno.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
  
### <a name="a-using-errorprocedure-in-a-catch-block"></a>A. Utilizzo di ERROR_PROCEDURE in un blocco CATCH  
In questo esempio viene illustrata una stored procedure che genera un errore di divisione per zero. `ERROR_PROCEDURE` restituisce il nome della stored procedure in cui si è verificato l'errore.  
  
```  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_PROCEDURE() AS ErrorProcedure;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorProcedure
--------------------
usp_ExampleProc

(1 row(s) affected)

```  
  
### <a name="b-using-errorprocedure-in-a-catch-block-with-other-error-handling-tools"></a>B. Utilizzo di ERROR_PROCEDURE in un blocco CATCH con altri strumenti di gestione degli errori  
In questo esempio viene illustrata una stored procedure che genera un errore di divisione per zero. Insieme al nome della stored procedure in cui si è verificato l'errore, la stored restituisce informazioni sull'errore.  
  
```  
  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT   
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage,  
        ERROR_LINE() AS ErrorLine;  
        END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState  ErrorProcedure   ErrorMessage                       ErrorLine
----------- ------------- ----------- ---------------- ---------------------------------- -----------
8134        16            1           usp_ExampleProc  Divide by zero error encountered.  6

(1 row(s) affected)

```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40;Transact-SQL&#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

