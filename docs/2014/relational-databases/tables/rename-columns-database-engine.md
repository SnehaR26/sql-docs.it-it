---
title: Rinominare colonne (motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], names
- renaming columns
- column names [SQL Server]
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4e09e9c5ea66582a2333693282496d9b3ddeed38
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057201"
---
# <a name="rename-columns-database-engine"></a>Ridenominazione di colonne (motore di database)
  È possibile rinominare un nome tabella in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per rinominare colonne utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Se una colonna viene ridenominata, i riferimenti a tale colonna non vengono ridenominati automaticamente ed è necessario modificare manualmente tutti gli oggetti che fanno riferimento alla colonna rinominata. Se, ad esempio, si rinomina una colonna di una tabella a cui viene fatto riferimento all'interno di un trigger, è necessario modificare il trigger in base al nuovo nome della colonna. Usare [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) per elencare le dipendenze dall'oggetto prima di rinominarlo.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessario disporre dell'autorizzazione ALTER per l'oggetto.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-rename-a-column-using-object-explorer"></a>Per rinominare una colonna utilizzando Esplora oggetti  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  In **Esplora oggetti**fare clic con il pulsante destro del mouse sulla tabella in cui si vuole rinominare le colonne, quindi selezionare **Rinomina**.  
  
3.  Digitare un nuovo nome colonna.  
  
#### <a name="to-rename-a-column-using-table-designer"></a>Per rinominare una colonna utilizzando Progettazione tabelle  
  
1.  In **Esplora oggetti**fare clic con il pulsante destro del mouse sulla tabella di cui si vuole rinominare le colonne e selezionare **Progetta**.  
  
2.  In **Nome colonna**, selezionare il nome da cambiare e digitarne uno nuovo.  
  
3.  Scegliere **Salva***nome tabella* dal menu **File**.  
  
> [!NOTE]  
>  Per cambiare il nome di una colonna, è anche possibile utilizzare la scheda **Proprietà colonne** . A tale scopo, selezionare la colonna di cui si desidera cambiare il nome e digitare un nuovo valore per **Nome**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per rinominare una colonna**  
  
#### <a name="to-rename-a-column"></a>Per rinominare una colonna  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Nell'esempio seguente la colonna `TerritoryID` della tabella `Sales.SalesTerritory` viene rinominata in `TerrID`. Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).  
  
  
