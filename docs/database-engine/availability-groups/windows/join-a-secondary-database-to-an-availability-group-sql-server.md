---
title: "Creare un join di un database secondario a un gruppo di disponibilit&#224; (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.availabilitygroup.joindbs.f1"
helpviewer_keywords: 
  - "database secondari [SQL Server], in un gruppo di disponibilità"
  - "database secondari [SQL Server]"
  - "gruppi di disponibilità [SQL Server], creazione di join"
  - "gruppi di disponibilità [SQL Server], configurazione"
  - "Gruppi di disponibilità [SQL Server], database"
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
caps.latest.revision: 39
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 39
---
# Creare un join di un database secondario a un gruppo di disponibilit&#224; (SQL Server)
  In questo argomento si spiega come creare un join di un database secondario a un gruppo di disponibilità AlwaysOn utilizzando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Dopo aver preparato un database secondario per una replica di secondaria, è necessario creare un join del database al gruppo di disponibilità non appena possibile. In questo modo verrà avviato lo spostamento di dati dal database primario corrispondente al database secondario.  
  
-   **Prima di iniziare:**  
  
     [Prerequisiti](#Prerequisites)  
  
     [Sicurezza](#Security)  
  
-   **Per preparare un database secondario tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  Per informazioni su ciò che si verifica dopo la creazione di un join di un database secondario al gruppo, vedere [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario essere connessi all'istanza del server che ospita la replica secondaria.  
  
-   È necessario avere già creato un join della replica secondaria al gruppo di disponibilità. Per altre informazioni, vedere [Creare un join di una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
-   Il database secondario deve essere stato preparato recentemente. Per altre informazioni, vedere [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessaria l'autorizzazione ALTER AVAILABILITY GROUP nel gruppo di disponibilità, l'autorizzazione CONTROL AVAILABILITY GROUP, l'autorizzazione ALTER ANY AVAILABILITY GROUP o l'autorizzazione CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per creare un join di un database secondario a un gruppo di disponibilità**  
  
1.  In Esplora oggetti connettersi all'istanza del server in cui viene ospitata la replica secondaria ed espandere l'albero del server.  
  
2.  Espandere il nodo **Disponibilità elevata AlwaysOn** e il nodo **Gruppi di disponibilità**.  
  
3.  Espandere il gruppo di disponibilità che si desidera modificare, quindi espandere il nodo **Database disponibili** .  
  
4.  Fare clic con il pulsante destro del mouse sul database e scegliere **Crea un join del gruppo di disponibilità**.  
  
5.  In questo modo verrà aperta la finestra di dialogo **Creare un join dei database al gruppo di disponibilità** . Verificare il nome del gruppo di disponibilità, visualizzato sulla barra del titolo, e il nome o i nomi dei database visualizzati nella griglia, quindi fare clic su **OK**o su **Annulla**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 **Per creare un join di un database secondario a un gruppo di disponibilità**  
  
1.  Connettersi all'istanza del server che ospita la replica secondaria.  
  
2.  Utilizzare la [clausola SET HADR dell'istruzione ALTER DATABASE](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md) come indicato di seguito:  
  
     ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*  
  
     dove *database_name* è il nome del database di cui creare il join e *group_name* è il nome del gruppo di disponibilità.  
  
     Nell'esempio seguente viene creato un join del database secondario, `Db1`, alla replica secondaria locale del gruppo di disponibilità `MyAG`.  
  
    ```  
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  Per un esempio di questa istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] impiegata in un contesto, vedere [Creare un gruppo di disponibilità &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Utilizzo di PowerShell  
 **Per creare un join di un database secondario a un gruppo di disponibilità**  
  
1.  Spostarsi nella directory (**cd**) dell'istanza del server che ospita la replica secondaria.  
  
2.  Usare il cmdlet **Add-SqlAvailabilityDatabase** per creare un join di uno o più database secondari al gruppo di disponibilità.  
  
     Ad esempio, il seguente comando crea un join di un database secondario, `Db1`, al gruppo di disponibilità `MyAG` in una delle istanze del server che ospita una replica secondaria.  
  
    ```  
    Add-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG `   
    -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  Per visualizzare la sintassi di un cmdlet, usare il cmdlet **Get-Help** nell'ambiente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Creare un join di una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## Vedere anche  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Risolvere i problemi relativi alla configurazione di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  