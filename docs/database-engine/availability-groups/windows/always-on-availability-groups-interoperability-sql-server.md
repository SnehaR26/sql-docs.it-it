---
title: "Gruppi di disponibilit&#224; AlwaysOn: interoperabilit&#224; (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gruppi di disponibilità [SQL Server], informazioni"
  - "Gruppi di disponibilità [SQL Server], interoperabilità"
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
caps.latest.revision: 21
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 20
---
# Gruppi di disponibilit&#224; AlwaysOn: interoperabilit&#224; (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In questo argomento viene descritta l'interoperabilità di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] con altre funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   [Funzionalità di interoperabilità con i gruppi di disponibilità AlwaysOn](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md#Interop)  
  
-   [Funzionalità in grado di interagire con i gruppi di disponibilità AlwaysOn con restrizioni](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md#restrictions)  
  
-   [Funzionalità prive di interoperabilità con i gruppi di disponibilità AlwaysOn](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md#NoInterop)  
  
-   [Contenuto correlato](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md#RelatedContent)  
  
##  <a name="Interop"></a> Funzionalità di interoperabilità con i gruppi di disponibilità AlwaysOn  
 Nella tabella seguente vengono elencate le funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di interoperabilità con [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Un collegamento nella colonna **Ulteriori informazioni** indica che per una determinata funzionalità esistono le considerazioni di interoperabilità.  
  
|Funzionalità|Ulteriori informazioni|  
|-------------|----------------------|  
|Change Data Capture|[Replica, Rilevamento modifiche, Change Data Capture e Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/replicate, track, change data capture - always on availability.md)|  
|Rilevamento modifiche|[Replica, Rilevamento modifiche, Change Data Capture e Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/replicate, track, change data capture - always on availability.md)|  
|Database indipendenti|[Database indipendenti con gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/contained-databases-with-always-on-availability-groups-sql-server.md)|  
|Crittografia del database|[Database crittografati con gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|Snapshot di database|[Snapshot del database con gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM e tabelle FileTable|[FILESTREAM e FileTable con gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|Ricerca full-text|Nota: gli indici full-text sono sincronizzati con i database secondari AlwaysOn.|  
|Log shipping|[Prerequisiti per la migrazione dal log shipping ai gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs migrating log shipping to always on availability groups.md)|  
|Archivio BLOB remoto (RBS)|[Archivio BLOB remoti &#40;RBS&#41; e gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|Replica|[Configurare la replica per i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [Gestione di un database di pubblicazione AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [Replica, Rilevamento modifiche, Change Data Capture e Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/replicate, track, change data capture - always on availability.md)<br /><br /> [Sottoscrittori della replica e gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Analysis Services|[Analysis Services con i gruppi di disponibilità AlwaysOn](../../../database-engine/availability-groups/windows/analysis-services-with-always-on-availability-groups.md)|  
|Reporting Services|Utilizzare solo repliche secondarie come origine dei dati di Reporting Services e ridurre il carico nella replica primaria di lettura e scrittura.<br /><br /> [Reporting Services con i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Service Broker|[Service Broker con i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md)|  
|SQL Server Agent||  
  
##  <a name="restrictions"></a> Funzionalità in grado di interagire con i gruppi di disponibilità AlwaysOn con restrizioni  
 Le funzionalità seguenti interagiscono con [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] con restrizioni specifiche. Per informazioni dettagliate, vedere gli argomenti collegati.  
  
-   Transazioni tra database/distribuite ([!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] e Windows Server 2016 Technical Preview 2). Per altre informazioni, vedere [Transazioni tra database non supportate per il mirroring del database o i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/transactions - always on availability and database mirroring.md)  
  
##  <a name="NoInterop"></a> Funzionalità prive di interoperabilità con i gruppi di disponibilità AlwaysOn  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] non è in grado di interagire con le funzionalità:  
  
-   Mirroring del database. Per altre informazioni, vedere [Transazioni tra database non supportate per il mirroring del database o i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/transactions - always on availability and database mirroring.md).  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
  
-   **Blog:**  
  
     [Pagina relativa alla guida alla migrazione in cui viene illustrata la migrazione al clustering di failover e ai gruppi di disponibilità di SQL Server 2012 dal clustering e dalle distribuzioni del mirroring precedenti](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [SQL Server AlwaysOn Team Blog: blog ufficiale del team di SQL Server AlwaysOn](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [Pagina relativa ai blog del Servizio Supporto Tecnico Clienti per gli ingegneri di SQL Server](http://blogs.msdn.com/b/psssql/)  
  
-   **White paper:**  
  
     [Pagina relativa alla guida alla migrazione in cui viene illustrata la migrazione in gruppi di disponibilità AlwaysOn da distribuzioni precedenti in cui vengono combinati il mirroring del database e il log shipping](http://msdn.microsoft.com/library/jj635217)  
  
     [Pagine relative alla guida alle soluzioni AlwaysOn di Microsoft SQL Server per la disponibilità elevata e il ripristino di emergenza](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Pagina relativa ai white paper Microsoft per SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Pagina relativa ai white paper del team di consulenza clienti di SQL Server](http://sqlcat.com/)  
  
## Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Prerequisiti, restrizioni e consigli per i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)  
  
  