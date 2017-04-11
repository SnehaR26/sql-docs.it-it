---
title: "Propriet&#224; dei gruppi di disponibilit&#224;: Nuovo gruppo di disponibilit&#224; (pagina Preferenze di backup) | Microsoft Docs"
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
  - "sql13.swb.availabilitygroupproperties.backuppreferences.f1"
helpviewer_keywords: 
  - "routing di sola lettura"
ms.assetid: 65fff22d-5963-4a8c-8b31-fe9ab247a03e
caps.latest.revision: 7
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 7
---
# Propriet&#224; dei gruppi di disponibilit&#224;: Nuovo gruppo di disponibilit&#224; (pagina Preferenze di backup)
  Utilizzare questa finestra di dialogo per visualizzare e modificare le preferenze di backup del gruppo di disponibilità selezionato.  
  
 **Per visualizzare le proprietà del gruppo di disponibilità**  
  
-   [Visualizzare le proprietà dei gruppi di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-properties-sql-server.md)  
  
-   [Usare il dashboard Always On &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
## Destinazione dei backup  
 **Preferisco secondario**  
 Specifica che i backup devono essere eseguiti su una replica secondaria tranne quando la replica primaria è l'unica replica online. In tal caso il backup deve essere eseguito sulla replica primaria. Si tratta dell'opzione predefinita.  
  
 **Solo secondaria**  
 Specifica che i backup non devono mai essere eseguiti sulla replica primaria. Se la replica primaria è l'unica replica online, il backup non viene eseguito.  
  
 **Primaria**  
 Specifica che i backup devono essere sempre eseguiti sulla replica primaria. Questa opzione è utile se sono necessarie funzionalità di backup, ad esempio la creazione di backup differenziali, che non sono supportate quando il backup viene eseguito su una replica secondaria.  
  
 **Qualsiasi replica**  
 Specifica che si preferisce che i processi di backup ignorino il ruolo delle repliche di disponibilità nella scelta della replica per l'esecuzione dei backup. Si noti che i processi di backup potrebbero valutare altri fattori, ad esempio la priorità di backup di ogni replica di disponibilità in combinazione con lo stato operativo e lo stato connesso.  
  
> [!IMPORTANT]  
>  L'impostazione della preferenza di backup non viene forzata. L'interpretazione di questa preferenza dipende dall'eventuale logica su cui si basano gli script dei processi di backup per i database in un determinato gruppo di disponibilità. Per altre informazioni, vedere [Repliche secondarie attive: Backup in repliche secondarie &#40;Gruppi di disponibilità Always On&#41;](../Topic/Active%20Secondaries:%20Backup%20on%20Secondary%20Replicas%20\(Always On%20Availability%20Groups\).md).  
  
## Priorità backup repliche  
 In questa griglia è indicata la priorità di backup corrente di ogni istanza del server che ospita una replica per il gruppo di disponibilità. Utilizzare questa griglia per modificare la priorità di backup di una o più repliche di disponibilità.  
  
 **Istanza del server**  
 Nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che ospita la replica di disponibilità.  
  
 **Priorità di backup (Più bassa=1, Più alta=100)**  
 Specifica la priorità di esecuzione dei backup nella replica rispetto alle altre repliche nello stesso gruppo di disponibilità. Il valore è un numero intero compreso nell'intervallo 0-100. 1 indica la priorità più bassa e 100 indica la priorità più alta. Se **Priorità di backup** = 1, la replica di disponibilità viene scelta per l'esecuzione dei backup solo se non sono disponibili repliche di disponibilità con priorità più alta.  
  
 **Escludi replica**  
 Selezionare questa opzione se si desidera che questa replica di disponibilità non venga mai scelta per l'esecuzione dei backup. Ciò si rivela utile, ad esempio, per una replica di disponibilità remota in cui non si desidera eseguire mai il failover dei backup.  
  
## Vedere anche  
 [Repliche secondarie attive: Backup in repliche secondarie &#40;gruppi di disponibilità Always On&#41;](../Topic/Active%20Secondaries:%20Backup%20on%20Secondary%20Replicas%20\(Always On%20Availability%20Groups\).md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  