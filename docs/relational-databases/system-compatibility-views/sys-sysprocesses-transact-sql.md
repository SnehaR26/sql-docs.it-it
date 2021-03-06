---
title: Sys. sysprocesses (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysprocesses_TSQL
- sys.sysprocesses_TSQL
- sys.sysprocesses
- sysprocesses
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysprocesses compatibility view
- sysprocesses system table
ms.assetid: 60a36d36-54b3-4bd6-9cac-702205a21b16
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2e1beebcb250f6a12ba612784ccb335c7b036774
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47780329"
---
# <a name="syssysprocesses-transact-sql"></a>sys.sysprocesses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni sui processi in esecuzione in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questi processi possono essere processi client o di sistema. Per accedere a sysprocesses, è necessario trovarsi nel contesto del database master oppure utilizzare il nome in tre parti master.dbo.sysprocesses.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|spid|**smallint**|ID di sessione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|kpid|**smallint**|ID del thread di Windows.|  
|blocked|**smallint**|ID della sessione che sta bloccando la richiesta. Se questa colonna è NULL, la richiesta non è bloccata oppure non sono disponibili o identificabili informazioni di sessione per la sessione da cui è bloccata.<br /><br /> -2 = La risorsa di blocco appartiene a una transazione distribuita orfana.<br /><br /> -3 = La risorsa di blocco appartiene a una transazione di recupero posticipata.<br /><br /> -4 = Non è possibile determinare l'ID di sessione del proprietario del latch di blocco a causa di transizioni nello stato del latch interno.|  
|waittype|**binary(2)**|Riservato.|  
|waittime|**bigint**|Tempo di attesa corrente espresso in millisecondi.<br /><br /> 0 = Il processo non è in attesa.|  
|lastwaittype|**nchar(32)**|Stringa che indica il nome del tipo di attesa più recente o corrente.|  
|waitresource|**nchar(256)**|Rappresentazione testuale di una risorsa di blocco.|  
|dbid|**smallint**|ID del database attualmente utilizzato dal processo.|  
|uid|**smallint**|ID dell'utente che ha eseguito il comando. Causa un errore di overflow o restituisce NULL se il numero di utenti e ruoli è maggiore di 32.767.|  
|cpu|**int**|Tempo CPU totale per il processo. La voce viene aggiornata per tutti i processi, indipendentemente dal fatto che l'opzione SET STATISTICS TIME sia impostata su ON o OFF.|  
|physical_io|**bigint**|Numero totale di letture da disco e scritture su disco per il processo.|  
|memusage|**int**|Numero di pagine della cache delle procedure attualmente assegnate al processo. Un numero negativo indica che il processo sta liberando la memoria allocata da un altro processo.|  
|login_time|**datetime**|Ora dell'accesso al server di un processo client.|  
|last_batch|**datetime**|Ora dell'ultima esecuzione di una chiamata a una stored procedure remota o di un'istruzione EXECUTE da parte di un processo client.|  
|ecid|**smallint**|ID del contesto di esecuzione utilizzato per identificare in modo univoco i thread secondari utilizzati per conto di un unico processo.|  
|open_tran|**smallint**|Numero di transazioni aperte per il processo.|  
|status|**nchar(30)**|Stato dell'ID del processo. I valori possibili sono:<br /><br /> **inattive**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sta reimpostando la sessione.<br /><br /> **esecuzione** = la sessione è in esecuzione uno o più batch. Se si abilita la funzionalità MARS (Multiple Active Result Sets), una sessione può eseguire più batch. Per altre informazioni vedere [Uso di MARS &#40;Multiple Active Result Set&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).<br /><br /> **sfondo** = nella sessione viene eseguita un'attività in background, ad esempio il rilevamento dei deadlock.<br /><br /> **eseguire il rollback** = la sessione è in corso il rollback di una transazione.<br /><br /> **in sospeso** = la sessione è in attesa di un thread di lavoro diventi disponibile.<br /><br /> **Runnable** = l'attività della sessione è in coda eseguibile di un'utilità di pianificazione durante l'attesa di un quantum temporale.<br /><br /> **spinloop** = l'attività della sessione è in attesa di uno spinlock venga resa disponibile.<br /><br /> **sospeso** = la sessione è in attesa di un evento, ad esempio i/o, per il completamento.|  
|sid|**binary(86)**|Identificatore univoco globale (GUID, Globally Unique Identifier) per l'utente.|  
|hostname|**nchar(128)**|Nome della workstation.|  
|program_name|**nchar(128)**|Nome dell'applicazione.|  
|hostprocess|**nchar(10)**|Numero di ID del processo della workstation.|  
|cmd|**nchar(16)**|Comando in fase di esecuzione.|  
|nt_domain|**nchar(128)**|Dominio di Windows per il client, se si utilizza l'autenticazione di Windows, o connessione trusted.|  
|nt_username|**nchar(128)**|Nome utente di Windows per il processo, se si utilizza l'autenticazione di Windows, o connessione trusted.|  
|net_address|**nchar(12)**|Identificatore univoco assegnato alla scheda di rete della workstation di ogni utente. Quando un utente esegue l'accesso, questo identificatore viene inserito nella colonna net_address.|  
|net_library|**nchar(12)**|Colonna in cui viene archiviata la libreria di rete del client. Ogni processo client utilizza una connessione di rete. Le connessioni di rete sono associate a una libreria di rete che consente di stabilire la connessione.|  
|loginame|**nchar(128)**|Nome dell'account di accesso.|  
|context_info|**binary(128)**|Dati archiviati in un batch tramite l'istruzione SET CONTEXT_INFO.|  
|sql_handle|**binary(20)**|Rappresenta il batch o l'oggetto attualmente in esecuzione.<br /><br /> **Nota** questo valore è derivato dall'indirizzo batch o della memoria dell'oggetto. e non viene calcolato tramite l'algoritmo basato su hash di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|stmt_start|**int**|Offset iniziale dell'istruzione SQL corrente per il valore di sql_handle specificato.|  
|stmt_end|**int**|Offset finale dell'istruzione SQL corrente per il valore di sql_handle specificato.<br /><br /> -1 = L'istruzione corrente viene eseguita fino alla fine dei risultati restituiti dalla funzione fn_get_sql per il valore di sql_handle specificato.|  
|request_id|**int**|ID della richiesta. Utilizzato per identificare le richieste in esecuzione in una sessione specifica.|
|page_resource |**binary(8)** |**Si applica a**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] <br /><br /> Una rappresentazione esadecimale a 8 byte della risorsa di pagina se il `waitresource` colonna contiene una pagina. |  
  
## <a name="remarks"></a>Note  
 Se si dispone dell'autorizzazione VIEW SERVER STATE per il server, è possibile visualizzare tutte le sessioni in esecuzione nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In caso contrario, è possibile visualizzare solo la sessione corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
