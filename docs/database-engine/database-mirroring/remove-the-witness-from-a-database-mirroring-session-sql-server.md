---
title: "Rimuovere il server di controllo del mirroring da una sessione di mirroring del database (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "server di controllo del mirroring [SQL Server], disabilitazione"
  - "server di controllo del mirroring [SQL Server], rimozione"
  - "mirroring del database [SQL Server], server di controllo del mirroring"
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
caps.latest.revision: 39
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 39
---
# Rimuovere il server di controllo del mirroring da una sessione di mirroring del database (SQL Server)
  In questo argomento verrà descritto come rimuovere un server di controllo del mirroring da una sessione di mirroring del database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Durante una sessione di mirroring del database, il proprietario del database può disabilitare il server di controllo del mirroring in qualsiasi momento.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per rimuovere il server di controllo del mirroring utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [Dopo la rimozione del server di controllo del mirroring](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per rimuovere il server di controllo del mirroring  
  
1.  Connettersi all'istanza del server principale e fare clic sul nome del server per espandere l'albero di server nel riquadro **Esplora oggetti** .  
  
2.  Espandere **Database**e selezionare il database di cui si desidera rimuovere il server di controllo del mirroring.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività** e quindi fare clic su **Server mirror**. Viene visualizzata la pagina **Mirroring** della finestra di dialogo **Proprietà database** .  
  
4.  Per rimuovere il server di controllo del mirroring, eliminare l'indirizzo di rete del server dal campo **Server di controllo del mirroring** .  
  
    > [!NOTE]  
    >  Se si passa dalla modalità a protezione elevata con failover automatico alla modalità a prestazioni elevate, il contenuto del campo **Server di controllo del mirroring** viene automaticamente cancellato.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per rimuovere il server di controllo del mirroring  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)] in qualsiasi istanza del server partner.  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Eseguire l'istruzione seguente:  
  
     [ALTER DATABASE](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md) *nome_database* SET WITNESS OFF  
  
     dove *nome_database* è il nome del database con mirroring.  
  
     Nell'esempio seguente viene rimosso il server di controllo del mirroring dal database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="FollowUp"></a> Completamento: Dopo la rimozione del server di controllo del mirroring  
 La disattivazione del server di controllo del mirroring comporta la modifica della [modalità operativa](../../database-engine/database-mirroring/database-mirroring-operating-modes.md) in base all'impostazione del livello di protezione delle transazioni:  
  
-   Se il livello di protezione delle transazioni è impostato su FULL (impostazione predefinita), nella sessione viene utilizzata la modalità sincrona a protezione elevata senza failover automatico.  
  
-   Se la protezione delle transazioni è impostata su OFF, la sessione viene eseguita in modo asincrono (in modalità a prestazioni elevate) senza richiedere quorum. Ogni volta che la protezione delle transazioni è disattivata, è consigliabile disattivare anche il server di controllo.  
  
> [!TIP]  
>  L'impostazione della sicurezza delle transazioni per il database viene registrata per ogni partner nelle colonne **mirroring_safety_level** e **mirroring_safety_level_desc** della vista del catalogo [sys.database_mirroring](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Aggiungere un server di controllo del mirroring del database tramite l'autenticazione di Windows &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [Aggiunta o sostituzione di un server di controllo del mirroring del database &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
## Vedere anche  
 [Mirroring del database di ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [Modifica della protezione delle transazioni in una sessione di mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)   
 [Aggiungere un server di controllo del mirroring del database tramite l'autenticazione di Windows &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)   
 [Server di controllo del mirroring del database](../../database-engine/database-mirroring/database-mirroring-witness.md)  
  
  