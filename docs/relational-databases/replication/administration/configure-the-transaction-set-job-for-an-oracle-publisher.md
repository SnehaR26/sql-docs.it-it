---
title: Configurare il processo del set di transazioni per un server di pubblicazione Oracle | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 71b5f3a28a8846cae63917f72b13405fb4f75170
ms.lasthandoff: 04/11/2017

---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher"></a>Configurare il processo del set di transazioni per un server di pubblicazione Oracle
  **Xactset** è un processo del database Oracle creato dalla replica eseguita in un server di pubblicazione Oracle per la creazione di set di transazioni, qualora l'agente di lettura log non è connesso al server di pubblicazione. È possibile abilitare e configurare questo processo a livello di programmazione dal server di distribuzione, utilizzando le stored procedure di replica. Per altre informazioni, vedere [Ottimizzazione delle prestazioni per i server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>Per abilitare il processo del set di transazioni  
  
1.  Nel server di pubblicazione Oracle impostare il parametro di inizializzazione **job_queue_processes** su un valore sufficiente per consentire l'esecuzione del processo Xactset. Per ulteriori informazioni su questo parametro, vedere la documentazione del database relativa al server di pubblicazione Oracle.  
  
2.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, il valore **xactsetbatching** per **@propertyname**e il valore **enabled** per **@propertyvalue**.  
  
3.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, il valore **xactsetjobinterval** per **@propertyname**e l'intervallo del processo espresso in minuti per **@propertyvalue**.  
  
4.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, il valore **xactsetjob** per **@propertyname**e il valore **enabled** per **@propertyvalue**.  
  
### <a name="to-configure-the-transaction-set-job"></a>Per configurare il processo del set di transazioni  
  
1.  (Facoltativo) Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**. Vengono restituite le proprietà del processo **Xactset** nel server di pubblicazione.  
  
2.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, il nome della proprietà del processo Xactset impostato per **@propertyname**e la nuova impostazione per **@propertyvalue**.  
  
3.  (Facoltativo) Ripetere il passaggio 2 per ogni proprietà del processo Xactset impostata. Se si modifica la proprietà **xactsetjobinterval** , è necessario riavviare il processo nel server di pubblicazione Oracle per rendere effettivo il nuovo intervallo.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>Per visualizzare le proprietà del processo del set di transazioni  
  
1.  Nel server di distribuzione eseguire [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**.  
  
### <a name="to-disable-the-transaction-set-job"></a>Per disabilitare il processo del set di transazioni  
  
1.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, il valore **xactsetjob** per **@propertyname**e il valore **disabled** per **@propertyvalue**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene abilitato il processo `Xactset` e viene impostato un intervallo di tre minuti tra le esecuzioni.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure-the-transactio_1.sql)]  
  
## <a name="see-also"></a>Vedere anche  
 [Ottimizzazione delle prestazioni per i server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  