---
title: "Attività pulizia contenuto cronologia | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.historycleanuptask.f1
helpviewer_keywords:
- history tables [SQL Server]
- History Cleanup task [Integration Services]
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 835d952dd745235ebddbf788a70b5776d7f2711f
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="history-cleanup-task"></a>Attività Pulizia contenuto cronologia
  L'attività Pulizia contenuto cronologia elimina le voci contenute nelle tabelle di cronologia seguenti del database msdb di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   backupfile  
  
-   backupfilegroup  
  
-   backupmediafamily  
  
-   backupmediaset  
  
-   backupset  
  
-   restorefile  
  
-   restorefilegroup  
  
-   restorehistory  
  
 Tramite l'attività Pulizia contenuto cronologia, un pacchetto può eliminare i dati cronologici relativi alle attività di backup e ripristino, ai processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e ai piani di manutenzione del database.  
  
 Questa attività incapsula la stored procedure di sistema sp_delete_backuphistory, a cui passa la data specificata come argomento. Per altre informazioni, vedere [sp_delete_backuphistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md).  
  
## <a name="configuration-of-the-history-cleanup-task"></a>Configurazione dell'attività Pulizia contenuto cronologia  
 L'attività include una proprietà che consente di specificare la data meno recente dei dati da mantenere nelle tabelle della cronologia. È possibile indicare tale data specificando il numero di giorni, settimane, mesi o anni dalla data corrente, affinché l'intervallo venga convertito automaticamente in data dall'attività.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della casella degli strumenti **** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Attività Pulizia contenuto cronologia &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  