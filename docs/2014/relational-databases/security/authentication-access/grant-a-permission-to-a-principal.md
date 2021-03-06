---
title: Concedere un'autorizzazione a un'entità| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Grant permission to a principal
ms.assetid: 4107389d-05b6-4aa3-9fa8-95b40cdf05dc
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 1e24250bfd313004b81a3d512a163963c070c08d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126349"
---
# <a name="grant-a-permission-to-a-principal"></a>Concedere un'autorizzazione a un'entità
  In questo argomento viene descritto come concedere un'autorizzazione a un'entità in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per concedere un'autorizzazione a un'entità utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Le procedure consigliate riportate di seguito consentono di gestire più facilmente le autorizzazioni.  
  
-   Concedere autorizzazione a ruoli, anziché a singoli account di accesso o utenti. Quando un singolo utente viene sostituito da un altro, rimuovere l'utente che non è più incluso nel ruolo e aggiungere il nuovo utente al ruolo. Le numerose autorizzazioni eventualmente associate al ruolo saranno automaticamente disponibili per il nuovo utente. Se diverse persone in un'organizzazione richiedono le stesse autorizzazioni, l'aggiunta di ciascuna persona al ruolo comporterà la concessione automatica delle stesse autorizzazioni.  
  
-   Configurare entità a protezione diretta simili, quali tabelle, viste e procedure, come di proprietà di uno schema, quindi concedere le autorizzazioni allo schema. Ad esempio, lo schema del libro paga potrebbe possedere diverse tabelle, viste e stored procedure. Concedendo l'accesso allo schema, verranno concesse simultaneamente tutte le necessarie autorizzazioni per eseguire la funzione di retribuzione. Per ulteriori informazioni sulle entità a protezione diretta a cui è possibile concedere le autorizzazioni, vedere [Securables](../securables.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 L'utente che concede le autorizzazioni (o l'entità specificata con l'opzione AS) deve disporre della relativa autorizzazione con GRANT OPTION oppure di un'autorizzazione di livello superiore che include l'autorizzazione che viene concessa. I membri del ruolo predefinito del server **sysadmin** possono concedere qualsiasi autorizzazione.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-grant-permission-to-a-principal"></a>Per concedere un'autorizzazione a un'entità  
  
1.  In Esplora oggetti espandere il database contenente l'oggetto a cui si desiderano concedere autorizzazioni.  
  
    > [!NOTE]  
    >  In questi passaggi viene trattata specificatamente la concessione delle autorizzazioni a una stored procedure, ma è possibile utilizzare passaggi simili per aggiungere autorizzazioni a tabelle, viste, funzioni e assembly e altre entità a protezione diretta. Per altre informazioni, vedere [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).  
  
2.  Espandere la cartella **Programmabilità** .  
  
3.  Espandere la cartella **Stored procedure** .  
  
4.  Fare clic con il pulsante destro del mouse su una stored procedure e selezionare **Proprietà**.  
  
5.  Nella finestra di dialogo **Proprietà stored procedure –***nome_stored_procedure* in Seleziona una pagina selezionare **Autorizzazioni**. Utilizzare questa pagina per aggiungere utenti o ruoli alla stored procedure e specificare le autorizzazioni degli utenti o dei ruoli.  
  
6.  Al termine, fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-grant-permission-to-a-principal"></a>Per concedere un'autorizzazione a un'entità  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- Grants EXECUTE permission on stored procedure HumanResources.uspUpdateEmployeeHireInfo to an application role called Recruiting11.   
    USE AdventureWorks2012;  
    GO  
    GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
        TO Recruiting11;  
    GO  
    ```  
  
 Per altre informazioni, vedere [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) e [GRANT - autorizzazioni per oggetti &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).  
  
## <a name="see-also"></a>Vedere anche  
 [Entità &#40;Motore di database&#41;](principals-database-engine.md)  
  
  
