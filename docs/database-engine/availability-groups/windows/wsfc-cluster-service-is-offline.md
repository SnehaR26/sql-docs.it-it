---
title: Il servizio cluster WSFC è offline | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp1WSFCquorum.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: d502548d-ece6-4a42-9ded-2157d33e3d21
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 0785cd58ffed215f9cebf29a62e40c70cc96c720
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850569"
---
# <a name="wsfc-cluster-service-is-offline"></a>Il servizio cluster WSFC è offline

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
    
## <a name="introduction"></a>Introduzione  
  
|||  
|-|-|  
|**Nome criteri**|Stato del cluster WSFC|  
|**Problema**|Il servizio cluster WSFC è offline.|  
|**Category**|**Critico**|  
|**Facet**|Istanza di SQL Server|  
  
## <a name="description"></a>Descrizione  
 Questi criteri consentono di controllare lo stato di WSCF (Windows Server Failover Clustering). I criteri sono in uno stato non integro e viene generato un avviso quando il cluster WSFC è offline o nello stato di quorum forzato. Tutti i gruppi di disponibilità ospitati all'interno di questo cluster sono offline oppure è necessaria un'azione di ripristino di emergenza.  
  
 Lo stato dei criteri è integro quando quello del cluster è nel quorum normale.  
  
> [!NOTE]  
>  Per questa versione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], le informazioni sulle possibili cause e le soluzioni sono disponibili nella pagina relativa alla situazione in cui il [servizio cluster WSFC è offline](http://go.microsoft.com/fwlink/p/?LinkId=220849) su Wiki di TechNet.  
  
## <a name="possible-causes"></a>Possibili cause  
 Questo problema può essere causato da un problema del servizio cluster o dalla perdita del quorum nel cluster.  
  
## <a name="possible-solution"></a>Possibile soluzione  
 Utilizzare lo strumento Amministratore cluster per eseguire il quorum forzato o il flusso di lavoro del ripristino di emergenza. Se non è possibile risolvere il problema eseguendo il quorum forzato o il ripristino di emergenza, contattare l'amministratore del cluster. Per altre informazioni, vedere [Forzare l'avvio di un cluster WSFC senza un quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) nella documentazione online di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Usare il dashboard Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
