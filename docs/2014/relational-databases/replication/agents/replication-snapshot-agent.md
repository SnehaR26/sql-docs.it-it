---
title: Agente snapshot repliche | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e6b6fe366014bdffce0eeef77c7e2e79872f22e5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087161"
---
# <a name="replication-snapshot-agent"></a>Agente snapshot repliche
  Agente snapshot repliche è un file eseguibile che consente di preparare i file di snapshot contenenti lo schema e i dati delle tabelle pubblicate e degli oggetti di database, di archiviare i file nella cartella snapshot e di registrare i processi di sincronizzazione nel database di distribuzione.  
  
> [!NOTE]  
>  I parametri possono essere specificati in qualsiasi ordine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      snapshot [ -?]   
-Publisherserver_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSizebcp_batch_size]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostNamedynamic_filter_host_name]  
[-DynamicFilterLogindynamic_filter_login]  
[-DynamicSnapshotLocationdynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiterfield_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocksnumber_of_blocks ]  
[-HRBcpBlockSizeblock_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageIntervalkeep_alive_interval]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreadsnumber_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSizepacket_size]
[-PrefetchTables [0|1] ]  
[-ProfileNameprofile_name]  
[-PublisherDBpublisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOutquery_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiterrow_delimiter]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-UsePerArticleContentsViewuse_per_article_contents_view]  
```  
  
## <a name="arguments"></a>Argomenti  
 **-?**  
 Stampa tutti i parametri disponibili.  
  
 **-Publisher**  *nome_server*[**\\***nome_istanza*]  
 Nome del server di pubblicazione. Specificare server_name per l'istanza predefinita di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server. Specificare *server_name***\\***instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server.  
  
 **-Publication** *pubblicazione*  
 Nome della pubblicazione. Questo parametro è valido solo se la pubblicazione è configurata in modo che sia sempre disponibile uno snapshot per le sottoscrizioni nuove o reinizializzate.  
  
 **-70Subscribers**  
 Deve essere utilizzato se qualsiasi Sottoscrittore esegue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versione 7.0.  
  
 **-BcpBatchSize** *bcp*_ *batch*\_ *size*  
 Numero di righe da inviare in un'operazione di copia bulk. Quando si esegue un'operazione **bcp in** , la dimensione del batch indica il numero di righe da inviare al server come unica transazione, nonché il numero di righe che devono essere inviate prima che l'agente di distribuzione registri un messaggio di stato **bcp** . Quando si esegue un'operazione **bcp out** , viene utilizzata una dimensione batch fissa di 1000. Il valore 0 indica che non vengono registrati messaggi.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 Percorso del file di definizione dell'agente. Un file di definizione dell'agente contiene argomenti della riga di comando per l'agente. Il contenuto del file viene analizzato come file eseguibile. Utilizzare virgolette doppie (") per specificare valori dell'argomento contenenti caratteri arbitrari.  
  
 **-Distributor** *nome_server*[**\\***nome_istanza*]  
 Nome del database di distribuzione. Specificare *server_name* per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server. Specificare *server_name***\\***instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server.  
  
 **-DistributorDeadlockPriority** [**-1**|**0**|**1**]  
 Priorità della connessione dell'agente snapshot con il server di distribuzione quando si verifica un deadlock. Questo parametro è specificato per risolvere deadlock che possono verificarsi tra l'agente snapshot e le applicazioni utente durante la generazione dello snapshot.  
  
|Valore di DistributorDeadlockPriority|Description|  
|---------------------------------------|-----------------|  
|**-1**|Le applicazioni diverse dall'agente snapshot hanno la priorità quando si verifica un deadlock nel server di distribuzione.|  
|**0** (predefinito)|La priorità non è assegnata.|  
|**1**|L'agente snapshot ha la priorità quando si verifica un deadlock nel server di distribuzione.|  
  
 **-DistributorLogin** *distributor_login*  
 Account di accesso utilizzato per la connessione al server di distribuzione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 **-DistributorPassword** *distributor_password*  
 Password utilizzata per la connessione al server di distribuzione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . .  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del database di distribuzione. Un valore **0** indica la modalità di autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (impostazione predefinita), mentre un valore **1** indica la modalità di autenticazione di Windows.  
  
 **-DynamicFilterHostName** *dynamic_filter_host_name*  
 Usato per impostare un valore per i filtri per [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) quando viene creato uno snapshot dinamico. Se, ad esempio, per un articolo viene specificata la clausola di filtro di subset `rep_id = HOST_NAME()` e si imposta la proprietà **DynamicFilterHostName** su "FBJones" prima di chiamare l'agente di merge, verranno replicate solo le righe con "FBJones" nella colonna **rep_id** .  
  
 **-DynamicFilterLogin** *dynamic_filter_login*  
 Usato per impostare un valore per i filtri per [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) quando viene creato uno snapshot dinamico. Se, ad esempio, per un articolo viene specificata la clausola di filtro di subset `user_id = SUSER_SNAME()` e si imposta la proprietà **DynamicFilterLogin** su "rsmith" prima di chiamare il metodo **Run** dell'oggetto **SQLSnapshot** , verranno incluse nello snapshot solo le righe con "rsmith" nella colonna **user_id** .  
  
 **-DynamicSnapshotLocation** *dynamic_snapshot_location*  
 Posizione di generazione dello snapshot dinamico.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Livello di crittografia SSL (Secure Sockets Layer) utilizzato dall'agente snapshot quando vengono stabilite le connessioni.  
  
|Valore di EncryptionLevel|Description|  
|---------------------------|-----------------|  
|**0**|Specifica che SSL non viene utilizzato.|  
|**1**|Specifica che SSL viene utilizzato, ma l'agente non verifica che il certificato server SSL sia firmato da un'autorità emittente attendibile.|  
|**2**|Specifica che SSL viene utilizzato e che il certificato viene verificato.|  
  
 Per altre informazioni, vedere [Panoramica della sicurezza &#40;replica&#41;](../security/security-overview-replication.md).  
  
 **-FieldDelimiter** *field_delimiter*  
 Carattere o sequenza di caratteri che contrassegna la fine di un campo nel file di dati di copia bulk [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Il valore predefinito è \n\<x$3>\n.  
  
 **-HistoryVerboseLevel** [ **1**| **2**| **3**]  
 Specifica la quantità di cronologia registrata durante un'operazione snapshot. Per ridurre al minimo l'effetto della registrazione della cronologia sulle prestazioni, selezionare **1**.  
  
|Valore di HistoryVerboseLevel|Description|  
|-------------------------------|-----------------|  
|**0**|I messaggi di stato vengono scritti nella console o in un file di output. I record della cronologia non vengono registrati nel database di distribuzione.|  
|**1**|Aggiorna sempre un messaggio di cronologia precedente con lo stesso stato (avvio, avanzamento, esito positivo e così via). Se non è presente un record precedente con lo stesso stato, inserisce un nuovo record.|  
|**2** (impostazione predefinita)|Inserisce nuovi record della cronologia, a meno che il record sia per eventi come messaggi inattivi o messaggi di processo con esecuzione prolungata, nel qual caso aggiorna i record precedenti.|  
|**3**|Inserisce sempre nuovi record, a meno che non si tratti di record per messaggi inattivi.|  
  
 **-HRBcpBlocks** *number_of_blocks*  
 Numero di blocchi di dati **bcp** in coda tra i thread di scrittura e di lettura. Il valore predefinito è 50. **HRBcpBlocks** viene utilizzato solo con pubblicazioni Oracle.  
  
> [!NOTE]  
>  Questo parametro viene utilizzato per ottimizzare le prestazioni di **bcp** da un server di pubblicazione Oracle.  
  
 -**HRBcpBlockSize***dimensione_blocco*  
 Dimensione, in kilobyte (KB), di ogni blocco di dati **bcp** . Il valore predefinito è 64 KB. **HRBcpBlocks** viene utilizzato solo con pubblicazioni Oracle.  
  
> [!NOTE]  
>  Questo parametro viene utilizzato per ottimizzare le prestazioni di **bcp** da un server di pubblicazione Oracle.  
  
 **-HRBcpDynamicBlocks**  
 Indica se la dimensione di ogni blocco di dati **bcp** può o meno crescere dinamicamente. **HRBcpBlocks** viene utilizzato solo con pubblicazioni Oracle.  
  
> [!NOTE]  
>  Questo parametro viene utilizzato per ottimizzare le prestazioni di **bcp** da un server di pubblicazione Oracle.  
  
 **-KeepAliveMessageInterval** *keep_alive_interval*  
 Tempo di attesa, in secondi, da parte dell'agente snapshot prima di registrare un messaggio di attesa del back-end nella tabella [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) . Il valore predefinito è 300 secondi.  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 Numero di secondi prima del timeout di accesso. Il valore predefinito è **15** secondi.  
  
 **-MaxBcpThreads** *number_of_threads*  
 Specifica il numero di operazioni di copia bulk che possono essere eseguite in parallelo. Il numero massimo di connessioni ODBC e thread presenti simultaneamente corrisponde a **MaxBcpThreads** o al numero di richieste di copia bulk presenti nella transazione di sincronizzazione nel database di distribuzione, a seconda di quale sia il valore minore. **MaxBcpThreads** deve avere un valore maggiore di **0** e non ha un limite massimo specificato a livello di codice. Il valore predefinito è **1**.  
  
 \- **MaxNetworkOptimization** [ **0**| **1**]  
 Indica se le eliminazioni irrilevanti vengono inviate al Sottoscrittore. Le eliminazioni irrilevanti sono comandi DELETE inviati ai Sottoscrittori per righe che non appartengono alla partizione del Sottoscrittore. Le eliminazioni irrilevanti non influiscono sulla convergenza o sull'integrità dei dati, ma possono comportare traffico di rete non necessario. Il valore predefinito di **MaxNetworkOptimization** è **0**. Impostando **MaxNetworkOptimization** su **1** è possibile ridurre al minimo le possibilità di eliminazioni irrilevanti, riducendo pertanto il traffico e ottimizzando le prestazioni di rete. L'impostazione di questo parametro su **1** comporta inoltre l'aumento dell'archiviazione di metadati e può provocare una riduzione delle prestazioni nel server di pubblicazione se sono presenti più livelli di filtri di join e filtri di subset complessi. Valutare inoltre attentamente la topologia di replica e impostare **MaxNetworkOptimization** su **1** solo se il traffico di rete dovuto a eliminazioni irrilevanti è eccessivo.  
  
> [!NOTE]  
>  L'impostazione di questo parametro su **1** è utile solo quando l'opzione di ottimizzazione della sincronizzazione della pubblicazione di tipo merge è impostata su **true** (parametro **@keep_partition_changes** di [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).  
  
 **-Output** *output_path_and_file_name*  
 Percorso del file di output dell'agente. Se non viene specificato il nome file, l'output viene inviato alla console. Se il nome file specificato esiste già, l'output viene aggiunto al file.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Specifica se l'output deve essere dettagliato.  
  
|Valore di OutputVerboseLevel|Description|  
|------------------------------|-----------------|  
|**0**|Vengono stampati solo i messaggi di errore.|  
|**1** (impostazione predefinita)|Vengono stampati tutti i messaggi di report di stato (impostazione predefinita).|  
|**2**|Vengono stampati tutti i messaggi di errore e i messaggi di report di stato. Questa opzione è utile per l'esecuzione del debug.|  

 **-PrefetchTables** [ **0**| **1**]  
 Parametro facoltativo che specifica se per gli oggetti tabella verranno eseguite la prelettura e la memorizzazione nella cache.  Il comportamento predefinito prevede la prelettura di determinate proprietà delle tabelle usando il componente SMO in base a un calcolo interno.  Questo parametro può essere utile in scenari in cui l'operazione di prelettura SMO richiede notevole tempo per l'esecuzione. Se questo parametro non viene usato, questa decisione viene presa in fase di esecuzione in base alla percentuale di tabelle che vengono aggiunte come articoli alla pubblicazione.  
  
|Valore di OutputVerboseLevel|Description|  
|------------------------------|-----------------|  
|**0**|La chiamata al metodo Prefetch del componente SMO è disabilitata.|  
|**1**|L'agente di snapshot chiamerà il metodo Prefetch per memorizzare nella cache alcune proprietà di tabella tramite SMO|  
  
 **-PacketSize** *packet_size*  
 Dimensione del pacchetto, in byte, utilizzata dall'agente snapshot durante la connessione a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore predefinito è 8192 byte.  
  
> [!NOTE]  
>  È consigliabile modificare le dimensioni dei pacchetti solo se si è certi che l'operazione determinerà un miglioramento delle prestazioni. Per la maggior parte delle applicazioni, le dimensioni predefinite risultano ottimali.  
  
 **-ProfileName** *profile_name*  
 Specifica un profilo agente da utilizzare per i parametri dell'agente. Se **ProfileName** è NULL, il profilo agente è disabilitato. Se **ProfileName** non viene specificato, viene utilizzato il profilo predefinito per il tipo di agente. Per altre informazioni, vedere [Profili degli agenti di replica](replication-agent-profiles.md).  
  
 **-PublisherDB** *publisher_database*  
 Nome del database di pubblicazione. *Questo parametro non è supportato per i server di pubblicazione Oracle*.  
  
 **-PublisherDeadlockPriority** [**-1**|**0**|**1**]  
 Priorità della connessione dell'agente snapshot con il server di pubblicazione quando si verifica un deadlock. Questo parametro è specificato per risolvere deadlock che possono verificarsi tra l'agente snapshot e le applicazioni utente durante la generazione dello snapshot.  
  
|Valore di PublisherDeadlockPriority|Description|  
|-------------------------------------|-----------------|  
|**-1**|Le applicazioni diverse dall'agente snapshot hanno la priorità quando si verifica un deadlock nel server di pubblicazione.|  
|**0** (predefinito)|La priorità non è assegnata.|  
|**1**|L'agente snapshot ha la priorità quando si verifica un deadlock nel server di pubblicazione.|  
  
 **-PublisherFailoverPartner** *nome_server*[**\\***nome_istanza*]  
 Specifica l'istanza del partner di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che partecipa in una sessione di mirroring del database con il database di pubblicazione. Per altre informazioni, vedere [Mirroring e replica del database &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherLogin** *publisher_login*  
 Account di accesso utilizzato per la connessione al server di pubblicazione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 **-PublisherPassword**  *password_server_pubblicazione*  
 Password utilizzata per la connessione al server di pubblicazione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . .  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del server di pubblicazione. Un valore **0** indica la modalità di autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (impostazione predefinita), mentre un valore **1** indica la modalità di autenticazione di Windows.  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 Numero di secondi prima del timeout delle query. Il valore predefinito è 1800 secondi.  
  
 **-ReplicationType** [ **1**| **2**]  
 Specifica il tipo di replica. Un valore **1** indica la replica transazionale, mentre un valore **2** indica la replica di tipo merge.  
  
 **-RowDelimiter** *row_delimiter*  
 Carattere o sequenza di caratteri che contrassegna la fine di una riga nel file di dati di copia bulk [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Il valore predefinito è \n\<,@g>\n.  
  
 **-StartQueueTimeout** *start_queue_timeout_seconds*  
 Numero massimo di secondi di attesa da parte dell'agente snapshot quando il numero di processi snapshot dinamici simultanei in esecuzione raggiunge il limite impostato tramite la proprietà **@max_concurrent_dynamic_snapshots** di [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Se viene raggiunto il numero massimo di secondi e l'agente snapshot è ancora in attesa, si chiude. Un valore 0 indica che l'agente attende indefinitamente, sebbene possa essere annullato.  
  
 \- **UsePerArticleContentsView** *use_per_article_contents_view*  
 Questo parametro è deprecato ed è ancora supportato solo per garantire la compatibilità con le versioni precedenti.  
  
## <a name="remarks"></a>Note  
  
> [!IMPORTANT]  
>  Se [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent è stato installato per l'esecuzione con un account di sistema locale anziché un account utente di dominio (impostazione predefinita), il servizio può accedere solo al computer locale. Se l'agente snapshot in esecuzione in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent è configurato per l'utilizzo della modalità di autenticazione di Windows durante l'accesso a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'agente snapshot si interrompe. L'impostazione predefinita prevede l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Per avviare l'agente snapshot, eseguire **snapshot.exe** dal prompt dei comandi. Per informazioni, vedere [File eseguibili dell'Agente di replica](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione dell'agente di replica](replication-agent-administration.md)  
  
  
