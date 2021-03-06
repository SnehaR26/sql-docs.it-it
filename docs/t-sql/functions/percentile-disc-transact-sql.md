---
title: PERCENTILE_DISC (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/20/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PERCENTILE_DISC
- PERCENTILE_DISC_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PERCENTILE_DISC function
- analytic functions,PERCENTILE_DISC
ms.assetid: b545413d-c4f7-4c8e-8617-607599a26680
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1624ff7f1ea5f480b5e28741bccc50d8746a5f9a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747860"
---
# <a name="percentiledisc-transact-sql"></a>PERCENTILE_DISC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Calcola un percentile specifico per i valori ordinati in un intero set di righe o all'interno di partizioni distinte di un set di righe in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un valore *P* di percentile specificato, PERCENTILE_DISC ordina i valori dell'espressione nella clausola ORDER BY e restituisce il valore con il più piccolo valore di CUME_DIST (in relazione alla stessa specifica di ordinamento) maggiore o uguale a *P*. PERCENTILE_DISC (0.5) calcolerà ad esempio il cinquantesimo percentile, ovvero la mediana, di un'espressione. PERCENTILE_DISC calcola il percentile in base a una distribuzione discreta dei valori della colonna e restituisce un risultato uguale a un valore specifico nella colonna.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
PERCENTILE_DISC ( numeric_literal ) WITHIN GROUP ( ORDER BY order_by_expression [ ASC | DESC ] )  
    OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *literal*  
 Percentile da calcolare. Il valore deve essere compreso tra 0 e 1.  
  
 WITHIN GROUP **(** ORDER BY *order_by_expression* [ **ASC** | DESC ]**)**  
 Specifica un elenco di valori in base a cui ordinare e calcolare il percentile. È consentito un solo *order_by_expression*. Per impostazione predefinita, l'ordinamento è crescente. L'elenco dei valori può essere di uno qualsiasi dei tipi di dati validi per l'operazione di ordinamento.  
  
 OVER **(** \<partition_by_clause> **)**  
 Suddivide il set di risultati generato dalla clausola FROM in partizioni alle quali viene applicata la funzione di percentile. Per altre informazioni, vedere [Clausola OVER - &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md). Le clausole \<ORDER BY> e \<ROWS o RANGE> non possono essere specificate in una funzione PERCENTILE_DISC.  
  
## <a name="return-types"></a>Tipi restituiti  
 Il tipo restituito viene determinato dal tipo di *order_by_expression*.  
  
## <a name="compatibility-support"></a>Informazioni sulla compatibilità  
 Se il valore del livello di compatibilità è 110 o superiore, WITHIN GROUP è una parola chiave riservata. Per altre informazioni, vedere [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Tutti i valori Null nel set di dati vengono ignorati.  
  
 PERCENTILE_DISC è non deterministico. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-basic-syntax-example"></a>A. Esempio della sintassi di base  
 Nell'esempio seguente vengono utilizzate le funzioni PERCENTILE_CONT e PERCENTILE_DISC per trovare lo stipendio medio del dipendente in ogni reparto. Si noti che queste funzioni possono restituire valori diversi. Questa situazione si verifica perché PERCENTILE_CONT esegue l'interpolazione del valore appropriato, sia che esista o meno nel set di dati, mentre PERCENTILE_DISC restituisce sempre un valore effettivo dal set.  
  
```  
USE AdventureWorks2012;  
  
SELECT DISTINCT Name AS DepartmentName  
      ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianCont  
      ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianDisc  
FROM HumanResources.Department AS d  
INNER JOIN HumanResources.EmployeeDepartmentHistory AS dh   
    ON dh.DepartmentID = d.DepartmentID  
INNER JOIN HumanResources.EmployeePayHistory AS ph  
    ON ph.BusinessEntityID = dh.BusinessEntityID  
WHERE dh.EndDate IS NULL;  
```  
  
 Set di risultati parziale:  
  
 ```
DepartmentName        MedianCont    MedianDisc
--------------------   ----------   ----------
Document Control       16.8269      16.8269
Engineering            34.375       32.6923
Executive              54.32695     48.5577
Human Resources        17.427850    16.5865
```
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-basic-syntax-example"></a>B. Esempio della sintassi di base  
 Nell'esempio seguente vengono utilizzate le funzioni PERCENTILE_CONT e PERCENTILE_DISC per trovare lo stipendio medio del dipendente in ogni reparto. Si noti che queste funzioni possono restituire valori diversi. Questa situazione si verifica perché PERCENTILE_CONT esegue l'interpolazione del valore appropriato, sia che esista o meno nel set di dati, mentre PERCENTILE_DISC restituisce sempre un valore effettivo dal set.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT DepartmentName  
       ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianCont  
       ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianDisc  
FROM dbo.DimEmployee;  
  
```  
  
 Set di risultati parziale:  
  
 ```
DepartmentName        MedianCont    MedianDisc  
--------------------   ----------   ----------  
Document Control       16.826900    16.8269  
Engineering            34.375000    32.6923  
Human Resources        17.427850    16.5865  
Shipping and Receiving  9.250000     9.0000
```  
  
## <a name="see-also"></a>Vedere anche  
 [PERCENTILE_CONT &#40;Transact-SQL&#41;](../../t-sql/functions/percentile-cont-transact-sql.md)  
  
  


