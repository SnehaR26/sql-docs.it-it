---
title: "Backup e ripristino di server di pubblicazione Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "recupero [replica di SQL Server], pubblicazione Oracle"
  - "backup [replica di SQL Server], pubblicazione Oracle"
  - "pubblicazione Oracle [replica di SQL Server], backup e ripristino"
  - "ripristino [replica di SQL Server], pubblicazione Oracle"
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Backup e ripristino di server di pubblicazione Oracle
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Durante il backup e il ripristino, attenersi alle linee guida seguenti:  
  
-   Verificare che l'agente di lettura log non sia in esecuzione e che non siano in corso altre attività di database sulle tabelle pubblicate durante il backup del server di pubblicazione.  
  
-   Eseguire il backup del server di pubblicazione e del server di distribuzione contemporaneamente.  
  
-   Se è necessario ripristinare il server di pubblicazione o il server di distribuzione, reinizializzare tutte le sottoscrizioni.  
  
-   Per ripristinare un Sottoscrittore da un backup senza reinizializzarne le sottoscrizioni, devono essere ancora disponibili le transazioni recapitate al database di distribuzione dopo il completamento dell'ultimo backup del database di sottoscrizione. Il periodo di tempo in cui sono disponibili le transazioni dipende dalle impostazioni di memorizzazione per la distribuzione. Per informazioni su queste impostazioni, vedere [disattivazione e scadenza della sottoscrizione](../../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
-   Se il server di pubblicazione o il server di distribuzione risulta non sincronizzato in seguito a un ripristino di database, gli agenti di replica registrano messaggi di errore. A questo punto, è necessario eliminare e ricreare tutte le pubblicazioni e le sottoscrizioni significative:  
  
    1.  Creare script per la definizione delle pubblicazioni e delle sottoscrizioni. Per altre informazioni, vedere [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
         Se la definizione delle pubblicazioni è stata modificata tra le versioni degli stati del server di pubblicazione e del server di distribuzione, sarà necessario modificare gli script.  
  
    2.  Eliminare le pubblicazioni e le sottoscrizioni.  
  
    3.  Eseguire gli script creati nel passaggio 1.  
  
     Se è necessario eliminare e riconfigurare il server di pubblicazione, eliminare il **MSSQLSERVERDISTRIBUTOR** sinonimo public e l'utente di replica Oracle configurato con il **CASCADE** opzione per rimuovere tutti gli oggetti di replica dal server di pubblicazione Oracle.  
  
## Vedere anche  
 [Backup e ripristino di database replicati](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Configurazione di un server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Panoramica della pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  