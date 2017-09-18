---
title: Configurare le impostazioni HealthCheckTimeout | Microsoft Docs
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fe45e057f3e8a9a4cd105cad16ef773c2aed0928
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="configure-healthchecktimeout-property-settings"></a>Configurazione delle impostazioni HealthCheckTimeout
  L'impostazione HealthCheckTimeout viene usata per specificare la durata, in millisecondi, dell'attesa della DLL della risorsa di SQL Server relativamente alle informazioni restituite dalla stored procedure [sp_server_diagnostics](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) prima di stabilire la mancata risposta da parte dell'istanza del cluster di failover AlwaysOn. Le modifiche apportate alle impostazioni del timeout vengono applicate immediatamente e non richiedono il riavvio della risorsa di SQL Server.  
  
-   **Before you begin:**  [Limitations and Restrictions](#Limits), [Security](#Security)  
  
-   **To Configure the HeathCheckTimeout setting, using:**  [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Limits"></a> Limitazioni e restrizioni  
 Il valore predefinito di questa proprietà è 30.000 millisecondi (30 secondi). Il valore minimo è 15.000 millisecondi (15 secondi).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessario disporre delle autorizzazioni ALTER SETTINGS e VIEW SERVER STATE.  
  
##  <a name="PowerShellProcedure"></a> Utilizzo di PowerShell  
  
##### <a name="to-configure-healthchecktimeout-settings"></a>Per configurare le impostazioni HealthCheckTimeout  
  
1.  Avviare Windows PowerShell con privilegi elevati tramite **Esegui come amministratore**.  
  
2.  Importare il modulo **FailoverClusters** per abilitare i cmdlet del cluster.  
  
3.  Usare il cmdlet **Get-ClusterResource** per cercare la risorsa [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , quindi usare il cmdlet **Set-ClusterParameter** per impostare la proprietà **HealthCheckTimeout** per l'istanza del cluster di failover.  
  
> [!TIP]  
>  Ogni volta che viene aperta una nuova finestra di PowerShell, è necessario importare il modulo **FailoverClusters** .  
  
### <a name="example-powershell"></a>Esempio (PowerShell)  
 Nell'esempio seguente, l'impostazione HealthCheckTimeout nella risorsa di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] "`SQL Server (INST1)`" viene impostata su 60.000 millisecondi.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
  
```  
  
### <a name="related-content-powershell"></a>Contenuto correlato (PowerShell)  
  
-   [Clustering and High-Availability](http://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (Failover Clustering and Network Load Balancing Team Blog) (Clustering e disponibilità elevata - Blog del team di clustering di failover e bilanciamento del carico di rete)  
  
-   [Introduzione a Windows PowerShell in un cluster di failover](http://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Comandi di risorse cluster e cmdlet di Windows PowerShell equivalenti](http://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> Utilizzo dello snap-in Gestione cluster di failover  
 **Per configurare le impostazioni HealthCheckTimeout**  
  
1.  Aprire lo snap-in Gestione cluster di failover.  
  
2.  Espandere **Servizi e applicazioni** e selezionare l'istanza del cluster di failover.  
  
3.  Fare clic con il pulsante destro del mouse sulla risorsa **SQL Server** in **Altre risorse** e selezionare **Proprietà** dal menu di scelta rapida. Verrà aperta la finestra di dialogo **Proprietà** della risorsa di SQL Server.  
  
4.  Selezionare la scheda **Proprietà** , immettere il valore desiderato per la proprietà **HealthCheckTimeout** , quindi fare clic su **OK** per applicare la modifica.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Mediante l'istruzione [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] , è possibile specificare il valore della proprietà HealthCheckTimeOut.  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 Nell'esempio seguente l'opzione HealthCheckTimeout viene impostata su 15.000 millisecondi (15 secondi).  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Criteri di failover per istanze del cluster di failover](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
