---
title: Mantenere il valore predefinito per l'opzione di configurazione dei blocchi | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d39cb969d127d29a82a21411d6e1bdb8891d199e
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="keep-the-locks-configuration-option-default-value"></a>Impostazione dell'opzione di configurazione dei blocchi sul valore predefinito
  Questa regola consente di controllare il valore dell'opzione di configurazione dei blocchi, che determina il numero massimo di blocchi disponibili. Tale valore limita la quantità di memoria utilizzata dal [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] per i blocchi. L'impostazione predefinita 0 consente al [!INCLUDE[ssDE](../../includes/ssde-md.md)] di allocare e deallocare strutture di blocco in modo dinamico in base alle variazioni dei requisiti di sistema.  
  
 Se il valore relativo ai blocchi è diverso da zero, i processi batch si arresteranno e verrà generato un messaggio di errore indicante un numero insufficiente di blocchi quando viene superato il valore specificato.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Utilizzare la stored procedure di sistema sp_configure per impostare l'opzione relativa ai blocchi sul valore predefinito tramite l'istruzione seguente:  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Configurare l'opzione di configurazione del server locks](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)  
  
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
  
 [Articolo 271509 della Microsoft Knowledge Base](http://go.microsoft.com/fwlink/?linkid=117788)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  