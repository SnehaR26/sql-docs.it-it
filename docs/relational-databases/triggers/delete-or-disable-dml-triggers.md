---
title: "Eliminare o disabilitare trigger DML | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-dml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "trigger DML, disabilitazione"
  - "rimozione di trigger DML"
  - "disabilitazione di trigger DML"
  - "rimozione di trigger DML"
  - "eliminazione di trigger DML"
  - "trigger DML, rimozione"
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Eliminare o disabilitare trigger DML
  In questo argomento viene descritto come eliminare o disabilitare un trigger DML in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per eliminare o disabilitare un trigger DML tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Un trigger eliminato viene rimosso dal database corrente, ma la tabella e i dati su cui si basa il trigger non subiscono alcun impatto. L'eliminazione di una tabella comporta automaticamente l'eliminazione di tutti i trigger della tabella.  
  
-   Per impostazione predefinita, un trigger viene abilitato quando viene creato.  
  
-   La disabilitazione di un trigger non ne comporta l'eliminazione. Il trigger continua a esistere come oggetto nel database corrente Il trigger, tuttavia, non viene attivato quando viene eseguita qualsiasi istruzione INSERT, UPDATE o DELETE in cui è stato programmato. I trigger disabilitati possono essere riabilitati. L'abilitazione di un trigger non comporta la sua creazione ex-novo. Il trigger viene attivato allo stesso modo in cui è stato creato in origine.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per l'eliminazione di un trigger DML è richiesta l'autorizzazione ALTER per la tabella o la vista in cui è definito il trigger.  
  
 Per disabilitare o abilitare un trigger DML, è necessario disporre almeno dell'autorizzazione ALTER per la tabella o la vista per cui il trigger è stato creato.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per eliminare un trigger DML  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere il database desiderato, espandere **Tabelle**, quindi espandere la tabella che contiene il trigger da eliminare.  
  
3.  Espandere **Trigger**, fare clic con il pulsante destro del mouse sul trigger da eliminare, quindi fare clic su **Elimina**.  
  
4.  Nella finestra di dialogo **Elimina oggetto** , verificare il trigger da eliminare, quindi fare clic su **OK**.  
  
#### Per abilitare e disabilitare un trigger DML  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere il database desiderato, espandere **Tabelle**, quindi espandere la tabella che contiene il trigger da disabilitare.  
  
3.  Espandere **Trigger**, fare clic con il pulsante destro del mouse sul trigger da disabilitare, quindi fare clic su **Disabilita**.  
  
4.  Per abilitare il trigger, fare clic su **Abilita**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per eliminare un trigger DML  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare gli esempi seguenti nella finestra delle query. Per creare il trigger [, eseguire l'istruzione](../../t-sql/statements/create-trigger-transact-sql.md) CREATE TRIGGER `Sales.bonus_reminder` . Per eliminare il trigger, eseguire l'istruzione [DROP TRIGGER](../../t-sql/statements/drop-trigger-transact-sql.md) .  
  
```tsql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### Per abilitare e disabilitare un trigger DML  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare gli esempi seguenti nella finestra delle query. Per creare il trigger [, eseguire l'istruzione](../../t-sql/statements/create-trigger-transact-sql.md) CREATE TRIGGER `Sales.bonus_reminder` . Per disabilitare e abilitare il trigger, eseguire le istruzioni [DISABLE TRIGGER](../../t-sql/statements/disable-trigger-transact-sql.md) e [ENABLE TRIGGER](../../t-sql/statements/enable-trigger-transact-sql.md) , rispettivamente.  
  
```tsql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```tsql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## Vedere anche  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Ottieni informazioni sui trigger DML](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  