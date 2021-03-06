---
title: sp_changemergepublication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_changemergepublication_TSQL
- sp_changemergepublication
helpviewer_keywords:
- sp_changemergepublication
ms.assetid: 81fe1994-7678-4852-980b-e02fedf1e796
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 89e1ca46f323bb565eea9080a0118fb19b39af08
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072295"
---
# <a name="spchangemergepublication-transact-sql"></a>sp_changemergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le proprietà di una pubblicazione di tipo merge. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_changemergepublication [ @publication= ] 'publication'  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@property=**] **'***proprietà***'**  
 Proprietà da modificare per la pubblicazione specificata. *proprietà* viene **sysname**, e può essere uno dei valori elencato nella tabella seguente.  
  
 [  **@value=**] **'***valore***'**  
 Nuovo valore della proprietà specificata. *valore* viene **nvarchar(255**, e può essere uno dei valori elencato nella tabella seguente.  
  
 Nella tabella seguente vengono descritte le proprietà della pubblicazione che è possibile modificare e le limitazioni previste per i valori di tali proprietà.  
  
|Proprietà|valore|Description|  
|--------------|-----------|-----------------|  
|**allow_anonymous**|**true**|Le sottoscrizioni anonime sono consentite.|  
||**false**|Le sottoscrizioni anonime non sono consentite.|  
|**allow_partition_realignment**|**true**|Le eliminazioni che vengono inviate al Sottoscrittore si basano sui risultati delle modifiche effettuate in una sua partizione. Vengono eliminati i dati che non appartengono più a tale partizione. Questo è il comportamento predefinito.|  
||**false**|Nel Sottoscrittore rimangono i dati di una vecchia partizione, mentre non vengono replicate le modifiche apportate a tali dati nel server di pubblicazione. Viceversa, le modifiche apportate nel Sottoscrittore vengono replicate nel server di pubblicazione. Ciò consente di conservare i dati relativi a una sottoscrizione in una vecchia partizione, nel caso in cui sia necessario accedervi per eseguire analisi cronologiche.|  
|**allow_pull**|**true**|È consentita la creazione di sottoscrizioni pull per la pubblicazione specificata.|  
||**false**|Non è consentita la creazione di sottoscrizioni pull per la pubblicazione specificata.|  
|**allow_push**|**true**|È consentita la creazione di sottoscrizioni push per la pubblicazione specificata.|  
||**false**|Non è consentita la creazione di sottoscrizioni push per la pubblicazione specificata.|  
|**allow_subscriber_initiated_snapshot**|**true**|Il Sottoscrittore può avviare il processo di snapshot.|  
||**false**|Il Sottoscrittore non può avviare il processo di snapshot.|  
|**allow_subscription_copy**|**true**|È possibile copiare i database di sottoscrizione che sottoscrivono la pubblicazione.|  
||**false**|Non è possibile copiare i database di sottoscrizione che sottoscrivono la pubblicazione.|  
|**allow_synctoalternate**|**true**|Consente la sincronizzazione di un partner di sincronizzazione alternativo con il server di pubblicazione corrente.|  
||**false**|Non consente la sincronizzazione di un partner di sincronizzazione alternativo con il server di pubblicazione corrente.|  
|**allow_web_synchronization**|**true**|Le sottoscrizioni possono essere sincronizzate tramite HTTPS.|  
||**false**|Le sottoscrizioni non possono essere sincronizzate tramite HTTPS.|  
|**alt_snapshot_folder**||Specifica il percorso della cartella alternativa per lo snapshot.|  
|**automatic_reinitialization_policy**|**1**|Le modifiche vengono caricate dal Sottoscrittore prima della reinizializzazione della sottoscrizione.|  
||**0**|La sottoscrizione viene reinizializzata senza che prima vengano caricate le modifiche.|  
|**centralized_conflicts**|**true**|I record con conflitti vengono archiviati nel server di pubblicazione. La modifica di questa proprietà richiede la reinizializzazione dei Sottoscrittori esistenti.|  
||**false**|I record con conflitti vengono archiviati nel server perdente a livello di risoluzione dei conflitti. La modifica di questa proprietà richiede la reinizializzazione dei Sottoscrittori esistenti.|  
|**compress_snapshot**|**true**|Lo snapshot in una cartella snapshot alternativa viene compresso nel formato CAB. Non è possibile comprimere lo snapshot all'interno della cartella snapshot predefinita. Se si modifica questa proprietà, è necessario un nuovo snapshot.|  
||**false**|Per impostazione predefinita, lo snapshot non viene compresso. Se si modifica questa proprietà, è necessario un nuovo snapshot.|  
|**conflict_logging**|**publisher**|I record con conflitti vengono archiviati nel server di pubblicazione.|  
||**subscriber**|I record con conflitti vengono archiviati nel Sottoscrittore che ha causato il conflitto. Non supportato per [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori *.*|  
||**both**|I record con conflitti vengono archiviati nel server di pubblicazione e nel Sottoscrittore.|  
|**conflict_retention**||Un' **int** che specifica il periodo di memorizzazione, espresso in giorni, per cui è in conflitto. L'impostazione *conflict_retention* al **0** significa che non è necessaria alcuna operazione di pulizia dei conflitti.|  
|**description**||Descrizione della pubblicazione.|  
|**dynamic_filters**|**true**|La pubblicazione viene filtrata in base a una clausola dinamica.|  
||**false**|La pubblicazione non viene filtrata dinamicamente.|  
|**enabled_for_internet**|**true**|La pubblicazione è abilitata per Internet. È possibile utilizzare FTP (File Transfer Protocol) per il trasferimento dei file di snapshot in un Sottoscrittore. I file di sincronizzazione per la pubblicazione vengono inseriti nella directory C:\Programmi\Microsoft SQL Server\MSSQL\Repldata\ftp.|  
||**false**|La pubblicazione non è abilitata per Internet.|  
|**ftp_address**||Indirizzo di rete del servizio FTP per il server di distribuzione. Corrisponde alla posizione in cui sono archiviati i file di snapshot della pubblicazione.|  
|**ftp_login**||Nome utente utilizzato per la connessione al servizio FTP.|  
|**ftp_password**||Password dell'utente utilizzata per la connessione al servizio FTP.|  
|**ftp_port**||Numero di porta del servizio FTP per il server di distribuzione. Corrisponde al numero di porta TCP del sito FTP in cui sono archiviati i file di snapshot della pubblicazione.|  
|**ftp_subdirectory**||Specifica la posizione in cui vengono creati i file di snapshot se la pubblicazione supporta la propagazione di snapshot tramite FTP.|  
|**generation_leveling_threshold**|**int**|Viene specificato il numero di modifiche contenute in una generazione. Una generazione è una raccolta di modifiche recapitate a un server di pubblicazione o a un Sottoscrittore.|  
|**keep_partition_changes**|**true**|La sincronizzazione è ottimizzata e vengono coinvolti solo i Sottoscrittori che includono righe nelle partizioni modificate. Se si modifica questa proprietà, è necessario un nuovo snapshot.|  
||**false**|La sincronizzazione non è ottimizzata e le partizioni inviate ai Sottoscrittori vengono verificate quando i dati contenuti in una di esse vengono modificati. Se si modifica questa proprietà, è necessario un nuovo snapshot.|  
|**max_concurrent_merge**||Si tratta di un' **int** che rappresenta il numero massimo di processi di merge simultanei che possono essere eseguite su una pubblicazione. Se il valore è 0, non vi sono limiti. Se viene pianificata l'esecuzione simultanea di un numero di processi di merge maggiore del numero specificato, i processi in eccesso vengono inseriti in una coda finché non viene completato il processo di merge corrente.|  
|**max_concurrent_dynamic_snapshots**||Si tratta di un' **int** che rappresenta il numero massimo di sessioni di snapshot per generare dei dati filtrati per gli snapshot che può essere eseguito simultaneamente in una pubblicazione di tipo merge che utilizza filtri di riga con parametri. Se **0**, non è previsto alcun limite. Se viene pianificata l'esecuzione simultanea di un numero di processi di snapshot maggiore del numero specificato, i processi in eccesso vengono inseriti in una coda finché non viene completato il processo di merge corrente.|  
|**post_snapshot_script**||Specifica un puntatore a un **con estensione SQL** percorso dei file. Quando si applica una sincronizzazione iniziale, l'agente di distribuzione o di merge esegue lo script post-snapshot dopo l'applicazione degli script degli oggetti replicati e dei dati durante una sincronizzazione iniziale. Se si modifica questa proprietà, è necessario un nuovo snapshot.|  
|**pre_snapshot_script**||Specifica un puntatore a un **con estensione SQL** percorso dei file. Durante l'applicazione dello snapshot in un Sottoscrittore, l'agente di merge esegue lo script pre-snapshot prima degli script degli oggetti replicati. Se si modifica questa proprietà, è necessario un nuovo snapshot.|  
|**publication_compatibility_level**|**100RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
||**90RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**publish_to_activedirectory**|**true**|Questo parametro è deprecato ed è supportato solo per compatibilità con gli script di versioni precedenti. Non è più possibile aggiungere informazioni sulla pubblicazione in Active Directory.|  
||**false**|Rimuove le informazioni sulla pubblicazione da Active Directory.|  
|**replicate_ddl**|**1**|Le istruzioni DDL (Data Definition Language) eseguite nel server di pubblicazione vengono replicate.|  
||**0**|Non viene eseguita la replica delle istruzioni DDL.|  
|**conservazione**||Si tratta di un' **int** che rappresenta il numero della *retention_period_unit* unità per cui si desidera salvare le modifiche per la pubblicazione specificata. Se la sottoscrizione non viene sincronizzata entro il periodo di memorizzazione specificato e se le modifiche che tale sottoscrizione avrebbe dovuto ricevere sono state rimosse tramite un'operazione di rimozione nel server di distribuzione, la sottoscrizione scade e pertanto dovrà essere reinizializzata. Il periodo di memorizzazione massimo consentito è il periodo compreso tra la data corrente e 31 dicembre 9999.<br /><br /> Nota: Il periodo di memorizzazione per le pubblicazioni di tipo merge ha un periodo di tolleranza di 24 ore su 24 per adattarsi ai sottoscrittori dei fusi orari diversi.|  
|**retention_period_unit**|**day**|Il periodo di memorizzazione è specificato in giorni.|  
||**week**|Il periodo di memorizzazione è specificato in settimane.|  
||**month**|Il periodo di memorizzazione è specificato in mesi.|  
||**year**|Il periodo di memorizzazione è specificato in anni.|  
|**snapshot_in_defaultfolder**|**true**|I file di snapshot sono memorizzati nella cartella snapshot predefinita.|  
||**false**|I file di snapshot sono archiviati nel percorso alternativo specificato da *alt_snapshot_folder*. Tale combinazione indica che i file di snapshot vengono archiviati sia nella posizione predefinita che in posizioni alternative.|  
|**snapshot_ready**|**true**|Lo snapshot della pubblicazione è disponibile.|  
||**false**|Lo snapshot della pubblicazione non è disponibile.|  
|**status**|**Attiva**|La pubblicazione è in uno stato attivo.|  
||**inattivo**|La pubblicazione è in uno stato inattivo.|  
|**sync_mode**|**nativo** o<br /><br /> **bcp nativo**|L'output del programma di copia bulk in modalità nativa di tutte le tabelle viene utilizzato per lo snapshot iniziale.|  
||**character**<br /><br /> o **carattere bcp**|L'output del programma di copia bulk in modalità carattere di tutte le tabelle viene utilizzato per lo snapshot iniziale, che è obbligatorio per tutti i Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**use_partition_groups**<br /><br /> Nota: dopo avere utilizzato partition_groups, se si desidera tornare a utilizzare **setupbelongs**e impostare **use_partition_groups = false** nelle **changemergearticle**, questo potrebbe non essere rispecchiati correttamente dopo che viene eseguito uno snapshot. I trigger generati dallo snapshot sono conformi ai gruppi di partizioni.<br /><br /> La soluzione alternativa per questo scenario consiste nell'impostare lo stato su inattivo, modificare il **use_partition_groups**, quindi impostare lo stato su attivo.|**true**|La pubblicazione utilizza partizioni pre-calcolate.|  
||**false**|La pubblicazione non utilizza partizioni pre-calcolate.|  
|**validate_subscriber_info**||Elenca le funzioni utilizzate per recuperare le informazioni relative al Sottoscrittore. Convalida quindi i criteri di applicazione dei filtri dinamici utilizzati per il Sottoscrittore per verificare che le informazioni vengano partizionate in modo coerente.|  
|**web_synchronization_url**||Valore predefinito dell'URL Internet utilizzato per la sincronizzazione tramite il Web.|  
|NULL (predefinito)||Restituisce l'elenco di valori supportati per *proprietà*.|  
  
 [  **@force_invalidate_snapshot =** ] *force_invalidate_snapshot*  
 Segnala che l'azione eseguita da questa stored procedure potrebbe invalidare uno snapshot esistente. *force_invalidate_snapshot* è un **bit**, il valore predefinito è **0**.  
  
 **0** specifica che la modifica della pubblicazione non invalida lo snapshot. Se la stored procedure rileva che la modifica richiede un nuovo snapshot, viene generato un errore e non viene apportata alcuna modifica.  
  
 **1** specifica che la modifica della pubblicazione potrebbe invalidare lo snapshot. Se alcune sottoscrizioni esistenti richiedono un nuovo snapshot, questo valore consente di contrassegnare lo snapshot esistente come obsoleto e di generarne uno nuovo.  
  
 Per informazioni sulle proprietà che richiedono la generazione di un nuovo snapshot quando vengono modificate, vedere la sezione Osservazioni.  
  
 [  **@force_reinit_subscription =** ] *force_reinit_subscription*  
 Segnala che l'azione eseguita dalla stored procedure potrebbe richiedere la reinizializzazione delle sottoscrizioni esistenti. *force_reinit_subscription* è un **bit** con valore predefinito è **0**.  
  
 **0** specifica che la modifica della pubblicazione non richiede reinizializzazione delle sottoscrizioni. Se la stored procedure rileva che la modifica richiede la reinizializzazione delle sottoscrizioni esistenti, viene generato un errore e non viene apportata alcuna modifica.  
  
 **1** specifica che la modifica della pubblicazione comporta la reinizializzazione delle sottoscrizioni esistenti e consente la reinizializzazione della sottoscrizione.  
  
 Per ulteriori informazioni sulle proprietà che richiedono la reinizializzazione di tutte le sottoscrizioni esistenti in caso di modifica, vedere la sezione Osservazioni.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_changemergepublication** viene utilizzata nella replica di tipo merge.  
  
 La modifica delle proprietà seguenti richiede la generazione di un nuovo snapshot. È necessario specificare un valore pari **1** per il *force_invalidate_snapshot* parametro.  
  
-   **alt_snapshot_folder**  
  
-   **compress_snapshot**  
  
-   **dynamic_filters**  
  
-   **ftp_address**  
  
-   **ftp_login**  
  
-   **ftp_password**  
  
-   **ftp_port**  
  
-   **ftp_subdirectory**  
  
-   **post_snapshot_script**  
  
-   **publication_compatibility_level** (per **80SP3** solo)  
  
-   **pre_snapshot_script**  
  
-   **snapshot_in_defaultfolder**  
  
-   **sync_mode**  
  
-   **use_partition_groups**  
  
 La modifica delle proprietà seguenti richiede la reinizializzazione delle sottoscrizioni esistenti. È necessario specificare un valore pari **1** per il *force_reinit_subscription* parametro.  
  
-   **dynamic_filters**  
  
-   **validate_subscriber_info**  
  
 Per l'elenco degli oggetti di pubblicazione in Active Directory usando il *publish_to_active_directory*, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetto deve essere già stato creato in Active Directory.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_changemergepublication](../../relational-databases/replication/codesnippet/tsql/sp-changemergepublicatio_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server oppure **db_owner** ruolo predefinito del database possono eseguire **sp_changemergepublication**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Modificare le proprietà di pubblicazioni e articoli](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
