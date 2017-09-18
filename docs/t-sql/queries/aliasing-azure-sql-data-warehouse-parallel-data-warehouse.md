---
title: Alias (Azure SQL Data Warehouse, Parallel Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b3a5c74-05cf-4385-8ee6-6176d003cb8a
caps.latest.revision: 11
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: edc81ce4377f490b482d920871ad361c98f961c5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="aliasing-azure-sql-data-warehouse-parallel-data-warehouse"></a>Alias (Azure SQL Data Warehouse, Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  L'aliasing consente la sostituzione temporanea di una stringa breve e facile da ricordare al posto di un nome di tabella o una colonna in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] [!INCLUDE[DWsql](../../includes/dwsql-md.md)] query. Gli alias di tabella vengono spesso utilizzati nelle query JOIN perché la sintassi JOIN richiede nomi completi degli oggetti quando si fa riferimento a colonne.  
  
 Gli alias devono essere conformi alle regole di denominazione di oggetti di singole parole. Per ulteriori informazioni, vedere "Regole di denominazione degli oggetti" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. Alias non può contenere spazi vuoti e non possono essere racchiusi tra virgolette singole o doppie.  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
object_source [ AS ] alias  
```  
  
## <a name="arguments"></a>Argomenti  
 *object_source*  
 Il nome della tabella di origine o della colonna.  
  
 AS  
 Preposizione un alias facoltativo. Quando si lavora con l'aliasing di variabile di intervallo, la parola chiave AS non è consentita.  
  
 *alias*  
 Il nome di riferimento temporaneo desiderato per la tabella o colonna. Può essere utilizzato qualsiasi nome di oggetto valido. Per ulteriori informazioni, vedere "Regole di denominazione degli oggetti" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente viene illustrata una query con più join. Alias di tabella e di colonna sono illustrati in questo esempio.  
  
-   Alias di colonna: Entrambe le colonne e le espressioni che includono colonne nell'elenco di selezione sono stati creati alias in questo esempio. `SalesTerritoryRegion AS SalesTR`viene illustrato un alias di colonna semplice. `Sum(SalesAmountQuota) AS TotalSales`di seguito viene illustrato  
  
-   Alias di tabella: `dbo.DimSalesTerritory AS st` viene illustrata la creazione del `st` alias per il `dbo.DimSalesTerritory` tabella.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion AS SalesTR,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
  
```  
  
 La parola chiave AS può essere esclusi, come illustrato di seguito, ma spesso è inclusa per migliorare la leggibilità.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) TotalSales, SalesTerritoryRegion SalesTR,  
RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) RankResult  
FROM dbo.DimEmployee e  
INNER JOIN dbo.FactSalesQuota sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  