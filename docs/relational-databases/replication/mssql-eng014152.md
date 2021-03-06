---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c0ce292ca4fd2790eb9b919bae2f4a5caa1a2db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729725"
---
# <a name="mssqleng014152"></a>MSSQL_ENG014152
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14152|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Replica-%s: ripetizione dell'esecuzione dell'agente %s pianificata. %s|  
  
## <a name="explanation"></a>Spiegazione  
 L'agente di replica specificato è stato pianificato in modo da tentare nuovamente l'esecuzione dell'operazione richiesta. Verranno eseguiti nuovi tentativi finché non verrà raggiunto il numero massimo di tentativi configurato per il passaggio del processo.  
  
 Viene in genere eseguito un nuovo tentativo per i motivi seguenti:  
  
-   È stato superato il valore di **QueryTimeout** .  
  
-   È stato superato il valore di **LoginTimeout** .  
  
-   Il processo di replica è stato scelto come vittima del deadlock.  
  
## <a name="user-action"></a>Azione dell'utente  
 Se il messaggio relativo a nuovi tentativi non viene visualizzato di frequente, non è richiesto nessun intervento da parte dell'utente.  
  
 Utilizzare [sp_help_jobstep](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md) per visualizzare l'impostazione corrente relativa al numero massimo di tentativi di esecuzione del passaggio **Run agent** per l'agente di replica specificato. È possibile utilizzare il parametro **@retry_attempts** della stored procedure [sp_update_jobstep](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md) per modificare il numero di tentativi di esecuzione di un passaggio del processo.  
  
 Se il messaggio relativo a nuovi tentativi viene visualizzato di frequente, risolvere il problema in base al messaggio che causa l'esecuzione di nuovi tentativi. Verificare nella cronologia dell'agente la presenza di messaggi che indicano il motivo per cui è stato necessario pianificare il nuovo tentativo. In alcuni casi potrebbe essere necessario attivare un livello di registrazione più dettagliato per l'agente di replica. Per ulteriori informazioni sulla configurazione della registrazione per la replica, vedere l'articolo [312292](http://support.microsoft.com/kb/312292)della Microsoft Knowledge Base.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
