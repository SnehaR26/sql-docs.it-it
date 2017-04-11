---
title: "Eliminare viste | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-views"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "eliminazione di viste"
  - "eliminazione di viste"
  - "viste [SQL Server], eliminazione"
  - "rimozione di viste"
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Eliminare viste
  È possibile eliminare (rimuovere) le viste in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per eliminare una vista da un database utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Quando si rimuove una vista, dal catalogo di sistema vengono eliminate la definizione e altre informazioni della vista. Vengono inoltre eliminate tutte le autorizzazioni per la vista.  
  
-   Qualsiasi vista di una tabella che viene eliminata tramite `DROP TABLE` deve essere eliminata in modo esplicito utilizzando `DROP VIEW`.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per l'autorizzazione SCHEMA o CONTROL per OBJECT.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per eliminare una vista da un database  
  
1.  In **Esplora oggetti**espandere il database contenente la vista da eliminare, quindi espandere la cartella **Viste** .  
  
2.  Fare clic con il pulsante destro del mouse sulla vista da eliminare e scegliere **Elimina**.  
  
3.  Nella finestra di dialogo **Elimina oggetto** fare clic su **OK**.  
  
    > [!IMPORTANT]  
    >  Fare clic su **Mostra dipendenze** nella finestra di dialogo **Elimina oggetto** per aprire la finestra di dialogo *Dipendenze* di **nome_vista**. Verranno visualizzati tutti gli oggetti che dipendono dalla vista e tutti gli oggetti da cui dipende la vista.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per eliminare una vista da un database  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. Nell'esempio si elimina la vista specificata solo se la vista già esiste.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 Per altre informazioni, vedere [DROP VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/drop-view-transact-sql.md).  
  
  