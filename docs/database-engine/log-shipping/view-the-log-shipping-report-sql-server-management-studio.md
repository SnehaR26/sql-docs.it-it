---
title: "Visualizzare il report di log shipping (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualizzazione di report di log shipping"
  - "visualizzazione di report di log shipping"
  - "log shipping [SQL Server], monitoraggio"
  - "log shipping [SQL Server], visualizzazione di report"
ms.assetid: 3b549f2f-3683-45e5-b8e8-8095276c41ab
caps.latest.revision: 18
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 18
---
# Visualizzare il report di log shipping (SQL Server Management Studio)
  In questo argomento viene descritta la procedura per visualizzare il report Stato log shipping delle transazioni in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. È possibile eseguire un report sullo stato in un server di monitoraggio, in un server primario o in un server secondario. Per visualizzare le informazioni più complete sulla configurazione per il log shipping, eseguire il report nell'istanza del server di monitoraggio.  
  
 Nel report è indicato lo stato di qualsiasi attività di log shipping il cui stato sia disponibile nell'istanza del server a cui si è connessi. Se l'istanza del server è coinvolta in più configurazioni in ruoli diversi, ad esempio come server di monitoraggio per un database e come server secondario per un altro database, nei risultati visualizzati saranno incluse le informazioni su ogni configurazione dal punto di vista di ogni ruolo. Se inoltre la stored procedure può eseguire la connessione all'istanza del server di monitoraggio per una determinata configurazione per il log shipping, nel report verranno visualizzate ulteriori informazioni su tale configurazione.  
  
 Per ogni ruolo eseguito dall'istanza del server corrente, è possibile visualizzare le informazioni seguenti:  
  
|Ruolo|Informazioni visualizzate|  
|----------|---------------------------|  
|Monitoraggio|Nome e stato di ogni server primario e secondario in cui questa istanza del server è utilizzata come server di monitoraggio.|  
|Primaria|Per ogni database primario, stato e nome dell'istanza del server corrente, come server primario, e nome del database primario. Nel report viene visualizzato lo stato del processo di backup, archiviato localmente nel server primario.<br /><br /> È inoltre presente una riga per ogni server secondario corrispondente. Se nella configurazione è in uso un server di monitoraggio a cui la stored procedure può effettuare la connessione, nelle righe vengono visualizzati lo stato di copia e ripristino del backup del log più recente.|  
|Secondari|Per ogni database secondario, stato e nome dell'istanza del server corrente, come server secondario, e nome del database secondario.<br /><br /> Nel report viene indicato lo stato dei processi di copia e ripristino nel server secondario.<br /><br /> È inoltre presente una riga per il server primario corrispondente. Se nella configurazione è in uso un server di monitoraggio a cui la stored procedure può effettuare la connessione, nelle righe viene visualizzato lo stato del backup del log più recente.|  
  
 Le informazioni visualizzate dipendono dal fatto che l'istanza del server sia un server di monitoraggio, primario o secondario. Se non sono disponibili informazioni, le celle corrispondenti sono disattivate.  
  
 Per ottenere i dati, tramite il report viene chiamata la procedura **sp_help_log_shipping_monitor**. Per informazioni sulle autorizzazioni richieste, vedere [sp_help_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql.md).  
  
### Per visualizzare il report Stato log shipping delle transazioni su un'istanza del server  
  
1.  Connettersi a un server di monitoraggio, a un server primario o a un server secondario.  
  
2.  In Esplora oggetti fare clic con il pulsante destro del mouse sull'istanza del server, scegliere **Report** e quindi **Report standard**.  
  
3.  Fare clic su **Stato log shipping delle transazioni**.  
  
## Vedere anche  
 [Monitorare il log shipping &#40;Transact-SQL&#41;](../../database-engine/log-shipping/monitor-log-shipping-transact-sql.md)  
  
  