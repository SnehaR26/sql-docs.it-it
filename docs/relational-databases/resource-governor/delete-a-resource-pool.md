---
title: "Eliminare un pool di risorse | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Resource Governor, eliminare un pool di risorse"
  - "pool di risorse [SQL Server], eliminare"
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Eliminare un pool di risorse
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  È possibile eliminare un pool di risorse utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o Transact-SQL.  
  
-   **Prima di iniziare:**  [Limitazioni e restrizioni](#LimitationsRestrictions), [Autorizzazioni](#Permissions)  
  
-   **Per eliminare un pool di risorse usando: ** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
 Non è possibile eliminare un pool di risorse contenente gruppi di carico di lavoro.  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 Non è possibile eliminare pool di risorse predefiniti o interni di Resource Governor. Non è possibile eliminare un pool di risorse contenente gruppi di carico di lavoro. Per altre informazioni, vedere [Delete a Workload Group](../../relational-databases/resource-governor/delete-a-workload-group.md).  
  
###  <a name="Permissions"></a> Autorizzazioni  
 Per eliminare un pool di risorse è necessaria l'autorizzazione CONTROL SERVER.  
  
##  <a name="DelRPSSMS"></a> Eliminare un pool di risorse utilizzando Esplora oggetti  
 **Per eliminare un pool di risorse utilizzando SQL Server Management Studio**  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire Esplora oggetti ed espandere in modo ricorsivo il nodo **Gestione** fino a **Resource Governor**incluso.  
  
2.  Fare clic con il pulsante destro del mouse sul pool di risorse da eliminare, quindi scegliere **Elimina**.  
  
3.  Nella finestra **Elimina oggetto** , il pool di risorse è indicato nell'elenco **Oggetto da eliminare** . Per eliminare il pool di risorse, fare clic su **OK**.  
  
    > [!NOTE]  
    >  Se si tenta di eliminare un pool di risorse in cui è contenuto un gruppo di carico di lavoro, si verificherà un errore.  
  
##  <a name="DelRPTSQL"></a> Eliminare un pool di risorse utilizzando Transact-SQL  
 **Per eliminare un pool di risorse utilizzando Transact-SQL**  
  
1.  Eseguire l'istruzione **DROP RESOURCE POOL** o **DROP EXTERNAL RESOURCE POOL** specificando il nome del pool di risorse da eliminare.  
  
2.  Eseguire l'istruzione **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### Esempio (Transact-SQL)  
 Nell'esempio seguente viene eliminato un gruppo di carico di lavoro denominato `poolAdhoc`.  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## Vedere anche  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Creare un pool di risorse](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Modificare le impostazioni del pool di risorse](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [Gruppo di carico di lavoro di Resource Governor](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Funzione di classificazione di Resource Governor](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  