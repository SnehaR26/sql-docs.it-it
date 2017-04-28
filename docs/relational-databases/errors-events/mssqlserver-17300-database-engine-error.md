---
title: MSSQLSERVER_17300 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ef809a200d3544e5e24549440506b77d6f1a79e5
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver17300"></a>MSSQLSERVER_17300
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17300|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PROC_OUT_OF_SYSTASK_SESSIONS|  
|Testo del messaggio|Impossibile eseguire una nuova attività di sistema. Memoria insufficiente o numero di sessioni configurate maggiore del numero massimo consentito nel server. Verificare che la memoria del server sia adeguata. Per controllare il numero massimo di connessioni utente consentite, eseguire sp_configure con l'opzione 'user connections'. Per controllare il numero di sessioni, inclusi i processi utente, eseguire sys.dm_exec_sessions.|  
  
## <a name="explanation"></a>Spiegazione  
Il tentativo di eseguire una nuova attività di sistema non è riuscito a causa di un problema di memoria insufficiente o perché è stato superato il numero di sessioni configurate nel server.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare che la memoria del server sia sufficiente. Verificare il numero corrente di attività di sistema che utilizzano sys.dm_exec_sessions e il valore configurato di connessioni utente massime mediante sp_configure.  
  
Eseguire le attività seguenti in modo appropriato:  
  
-   Aggiungere una quantità maggiore di memoria al server.  
  
-   Terminare uno o più sessioni.  
  
-   Aumentare il numero massimo di connessioni utente consentite sul server.  
  
## <a name="see-also"></a>Vedere anche  
[sp_configure &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
[Opzioni di configurazione del server &#40;SQL Server&#41;](~/database-engine/configure-windows/server-configuration-options-sql-server.md)  
[sys.dm_exec_sessions &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[Configurare l'opzione di configurazione del server user connections](~/database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)  
[KILL &#40;Transact-SQL&#41;](~/t-sql/language-elements/kill-transact-sql.md)  
  
