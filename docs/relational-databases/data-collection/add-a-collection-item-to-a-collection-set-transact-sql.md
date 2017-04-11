---
title: "Aggiunta di un elemento della raccolta a un set di raccolta (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "elementi della raccolta [SQL Server]"
  - "set di raccolta [SQL Server], aggiunta di elementi"
ms.assetid: 9fe6454e-8c0e-4b50-937b-d9871b20fd13
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 21
---
# Aggiunta di un elemento della raccolta a un set di raccolta (Transact-SQL)
  È possibile aggiungere un elemento della raccolta a un set di raccolta esistente utilizzando le stored procedure fornite con l'agente di raccolta dati.  
  
 Eseguire i seguenti passaggi utilizzando l'Editor di query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
### Aggiunta di un elemento della raccolta a un set di raccolte  
  
1.  Arrestare il set di raccolta a cui aggiungere l'elemento eseguendo la stored procedure **sp_syscollector_stop_collection_set**. Ad esempio, per arrestare un set di raccolta denominato "Test Collection Set", eseguire le istruzioni seguenti:  
  
    ```tsql  
    USE msdb  
    DECLARE @csid int  
    SELECT @csid = collection_set_id  
    FROM syscollector_collection_sets  
    WHERE name = 'Test Collection Set'  
    SELECT @csid  
    EXEC dbo.sp_syscollector_stop_collection_set @collection_set_id = @csid  
    ```  
  
    > [!NOTE]  
    >  È anche possibile arrestare il set di raccolta utilizzando Esplora oggetti in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [Avviare o arrestare un set di raccolta](../../relational-databases/data-collection/start-or-stop-a-collection-set.md).  
  
2.  Dichiarare il set di raccolta al quale si desidera aggiungere l'elemento della raccolta. Nel codice seguente viene fornito un esempio su come dichiarare l'ID del set di raccolta.  
  
    ```tsql  
    DECLARE @collection_set_id_1 int  
    SELECT @collection_set_id_1 = collection_set_id FROM [msdb].[dbo].[syscollector_collection_sets]  
    WHERE name = N'Test Collection Set'; -- name of collection set  
    ```  
  
3.  Dichiarare il tipo di agente di raccolta. Nel codice seguente viene fornito un esempio su come dichiarare il tipo di agente di raccolta Query T-SQL generico.  
  
    ```tsql  
    DECLARE @collector_type_uid_1 uniqueidentifier  
    SELECT @collector_type_uid_1 = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
       WHERE name = N'Generic T-SQL Query Collector Type';  
    ```  
  
     È possibile eseguire il codice seguente per ottenere un elenco dei tipi di agente di raccolta installati:  
  
    ```tsql  
    USE msdb  
    SELECT * from syscollector_collector_types  
    GO  
    ```  
  
4.  Eseguire la stored procedure **sp_syscollector_create_collection_item** per creare l'elemento della raccolta. È necessario dichiarare lo schema per l'elemento della raccolta in modo tale da eseguirne il mapping allo schema richiesto per il tipo di agente di raccolta desiderato. Nell'esempio seguente viene utilizzato lo schema di input Query T-SQL generico.  
  
    ```tsql  
    DECLARE @collection_item_id int;  
    EXEC [msdb].[dbo].[sp_syscollector_create_collection_item]   
    @name=N'OS Wait Stats', --name of collection item  
    @parameters=N'  
    <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
     <Query>  
      <Value>select * from sys.dm_os_wait_stats</Value>  
      <OutputTable>os_wait_stats</OutputTable>  
    </Query>  
    </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 60,  
    @collection_set_id = @collection_set_id_1, --- Provides the collection set ID number  
    @collector_type_uid = @collector_type_uid_1 -- Provides the collector type UID  
    SELECT @collection_item_id     
    ```  
  
5.  Prima di avviare il set di raccolta aggiornato, eseguire la query seguente per verificare che il nuovo elemento della raccolta sia stato creato:  
  
    ```xaml  
    USE msdb  
    SELECT * from syscollector_collection_sets  
    SELECT * from syscollector_collection_items  
    GO  
    ```  
  
     I set di raccolta e i rispettivi elementi della raccolta sono visualizzati nella scheda **Risultati**.  
  
## Vedere anche  
 [Creare un set di raccolta personalizzato che usa il tipo agente di raccolta Query T-SQL generico &#40;Transact-SQL&#41;](../../relational-databases/data-collection/create custom collection set - generic t-sql query collector type.md)   
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  