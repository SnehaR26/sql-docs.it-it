---
title: Creare un operatore | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 0d08bc1ab245786d16665ba6e00097adab66be1a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837209"
---
# <a name="create-an-operator"></a>Create an Operator
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In questo argomento viene illustrato come configurare un utente per la ricezione di notifiche relative ai processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per creare un operatore utilizzando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
  
-   Le opzioni Cercapersone e **net send** verranno rimosse da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in una versione futura di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare pertanto di utilizzarle in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui sono state implementate.  
  
-   Si noti che per inviare notifiche tramite posta elettronica e cercapersone agli operatori, è necessario configurare SQL Server Agent per l'utilizzo di Posta elettronica database. Per ulteriori informazioni, vedere [Procedura: Assegnazione di avvisi a un operatore (SQL Server Management Studio)](assign-alerts-to-an-operator.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è incluso un semplice strumento grafico per la gestione dei processi, che è lo strumento consigliato per la creazione e la gestione dell'infrastruttura dei processi.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Solo i membri del ruolo predefinito del server **sysadmin** possono creare gli operatori.  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-an-operator"></a>Per creare un operatore  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si desidera creare un operatore di SQL Server Agent.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Operatori** e quindi scegliere **Nuovo operatore**.  
  
    Nella pagina **Generale** della finestra di dialogo **Nuovo operatore** sono disponibili le opzioni indicate di seguito.  
  
    **Nome**  
    Consente di modificare il nome dell'operatore.  
  
    **Abilitata**  
    Consente di abilitare l'operatore. Se non è abilitato, all'operatore non verranno inviate notifiche.  
  
    **Indirizzo posta elettronica**  
    Specifica l'indirizzo di posta elettronica dell'operatore.  
  
    **Indirizzo Net Send**  
    Specifica l'indirizzo da usare per **Net Send**.  
  
    **Indirizzo cercapersone**  
    Specifica l'indirizzo di posta elettronica da utilizzare per il cercapersone dell'operatore.  
  
    **Pianificazione cercapersone per operatore in servizio**  
    Consente di impostare gli orari in cui il cercapersone è attivo.  
  
    **Lunedì - Domenica**  
    Consente di selezionare i giorni in cui il cercapersone è attivo.  
  
    **Inizio giornata lavorativa**  
    Consente di selezionare l'ora a partire da cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent invierà messaggi al cercapersone.  
  
    **Fine giornata lavorativa**  
    Consente di selezionare l'ora oltre cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent non invierà più messaggi al cercapersone.  
  
    Nella pagina **Generale** della finestra di dialogo **Notifiche** sono disponibili le opzioni indicate di seguito.  
  
    **Avvisi**  
    Consente di visualizzare gli avvisi nell'istanza.  
  
    **Processi**  
    Consente di visualizzare i processi nell'istanza.  
  
    **Elenco avvisi**  
    Consente di visualizzare l'elenco degli avvisi nell'istanza.  
  
    **Elenco processi**  
    Consente di visualizzare l'elenco dei processi nell'istanza.  
  
    **Posta elettronica**  
    Consente di inviare una notifica all'operatore tramite posta elettronica.  
  
    **Cercapersone**  
    Inviare una notifica all'operatore tramite un messaggio di posta elettronica all'indirizzo del cercapersone.  
  
    **Net send**  
    Notificare questo operatore tramite **Net Send**.  
  
4.  Al termine della creazione del nuovo operatore, fare clic su **OK**.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-create-an-operator"></a>Per creare un operatore  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- sets up the operator information for user 'danwi.'
    -- The operator is enabled.   
    -- SQL Server Agent sends notifications by pager 
    -- from Monday through Friday from 8 A.M. to 5 P.M.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_operator  
        @name = N'Dan Wilson',  
        @enabled = 1,  
        @email_address = N'danwi',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 62 ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_add_operator (Transact-SQL)](http://msdn.microsoft.com/817cd98a-4dff-4ed8-a546-f336c144d1e0).  
  
