---
title: Proprietà processo- Nuovo processo (pagina Notifiche) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7b17a7cc6481e82313901755e23e38aa9da23d5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663659"
---
# <a name="job-properties---new-job-notifications-page"></a>Proprietà processo- Nuovo processo (pagina Notifiche)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Usare questa pagina per impostare le azioni che devono essere eseguite da [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent al completamento del processo.  
  
## <a name="options"></a>Opzioni  
**Posta elettronica**  
Selezionare questa opzione per inviare un messaggio di posta elettronica al completamento del processo. Dopo aver selezionato questa opzione, specificare l'operatore a cui inviare la notifica e la condizione che attiverà tale notifica: **In caso di esito positivo processo**, **In caso di esito negativo processo**o **Al termine del processo**.  
  
**Pagina**  
Selezionare questa opzione per inviare un messaggio di posta elettronica al cercapersone di un operatore al completamento del processo. Dopo aver selezionato questa opzione, specificare l'operatore a cui inviare la notifica e la condizione che attiverà tale notifica: **In caso di esito positivo processo**, **In caso di esito negativo processo**o **Al termine del processo**.  
  
**Net Send**  
Selezionare questa opzione se al completamento del processo si desidera inviare la notifica all'operatore tramite Net Send. Dopo aver selezionato questa opzione, specificare l'operatore a cui inviare la notifica e la condizione che attiverà tale notifica: **In caso di esito positivo processo**, **In caso di esito negativo processo**o **Al termine del processo**.  
  
**Scrivi nel registro eventi applicazioni di Windows**  
Selezionare questa opzione per scrivere una voce nel registro degli eventi dell'applicazione al completamento del processo. Dopo aver selezionato questa opzione, specificare la condizione che causerà la scrittura della voce: **In caso di esito positivo processo**, **In caso di esito negativo processo**o **Al termine del processo**.  
  
**Elimina il processo automaticamente**  
Selezionare questa opzione per eliminare il processo dopo il completamento. Dopo aver selezionato questa opzione, specificare la condizione che attiverà l'eliminazione del processo: **In caso di esito positivo processo**, **In caso di esito negativo processo**o **Al termine del processo**.  
  
## <a name="see-also"></a>Vedere anche  
[Implementazione di processi](../../ssms/agent/implement-jobs.md)  
[Procedura: Configurazione di SQL Server Agent Mail per l'utilizzo di Posta elettronica database (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce)  
  
