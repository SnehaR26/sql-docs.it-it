---
title: Rimuovere un database secondario da una configurazione per il log shipping (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- deleting secondary databases
- secondary databases [SQL Server], in log shipping
- removing secondary databases
- secondary data files [SQL Server], removing
- log shipping [SQL Server], secondary databases
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c1a3a18900159d6073c3054fb2ab12500ccb24c3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47776697"
---
# <a name="remove-a-secondary-database-from-a-log-shipping-configuration-sql-server"></a>Rimuovere un database secondario da una configurazione per il log shipping (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritto come rimuovere un database secondario per il log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per rimuovere un database secondario per il log shipping utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Attività correlate](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Le stored procedure per il log shipping richiedono l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-remove-a-log-shipping-secondary-database"></a>Per rimuovere un database secondario per il log shipping  
  
1.  Connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che rappresenta attualmente il server primario di log shipping ed espandere l'istanza.  
  
2.  Espandere **Database**, fare clic con il pulsante destro del mouse sul database primario per il log shipping, quindi scegliere **Proprietà**.  
  
3.  Nella casella **Selezionare una pagina**fare clic su **Log shipping delle transazioni**.  
  
4.  Nell'area **Istanze del server e database secondari**fare clic sul database da rimuovere.  
  
5.  Scegliere **Rimuovi**.  
  
6.  Fare clic su **OK** per aggiornare la configurazione.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-remove-a-secondary-database"></a>Per rimuovere un database secondario  
  
1.  Nel server primario eseguire [sp_delete_log_shipping_primary_secondary](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql.md) per eliminare le informazioni relative al database secondario.  
  
2.  Nel server secondario eseguire [sp_delete_log_shipping_secondary_database](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md) per eliminare il database secondario.  
  
    > [!NOTE]  
    >  Se non sono disponibili altri database secondari con lo stesso ID, **sp_delete_log_shipping_secondary_primary** viene richiamata da **sp_delete_log_shipping_secondary_database** e tramite essa viene eliminata la voce relativa all'ID secondario e i processi di copia e ripristino.  
  
3.  Nel server secondario disabilitare i processi di copia e ripristino. Per altre informazioni, vedere [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Aggiornamento del log shipping a SQL Server 2016 &#40;Transact-SQL&#41;](../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Configurare il log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
-   [Aggiungere un database secondario a una configurazione per il log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [Rimuovere il log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   [Visualizzare il report di log shipping &#40;SQL Server Management Studio&#41;](../../database-engine/log-shipping/view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [Monitorare il log shipping &#40;Transact-SQL&#41;](../../database-engine/log-shipping/monitor-log-shipping-transact-sql.md)  
  
-   [Failover su un database secondario per il log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Tabelle e stored procedure relative al log shipping](../../database-engine/log-shipping/log-shipping-tables-and-stored-procedures.md)  
  
  
