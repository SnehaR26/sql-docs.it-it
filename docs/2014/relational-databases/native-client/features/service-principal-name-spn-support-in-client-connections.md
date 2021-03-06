---
title: Supporto del nome dell'entità servizio (SPN) nelle connessioni client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, SPNs
- ODBC, SPNs
- OLE DB, SPNs
- SPNs [SQL Server]
ms.assetid: 96598c69-ce9a-4090-aacb-d546591e8af7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35d602969e0d34fc9ce1af4e796a0bc4fe612cc9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155441"
---
# <a name="service-principal-name-spn-support-in-client-connections"></a>Supporto per nomi SPN nelle connessioni client
  A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], il supporto per i nomi SPN è stato esteso per consentire l'autenticazione reciproca in tutti i protocolli. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i nomi SPN sono supportati solo per Kerberos su TCP quando il nome SPN predefinito per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene registrato con Active Directory.  
  
 I nomi SPN vengono usati dal protocollo di autenticazione per determinare l'account usato per l'esecuzione di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se l'account dell'istanza è noto, è possibile usare l'autenticazione Kerberos per fornire autenticazione reciproca dal client e dal server. Se l'account dell'istanza non è noto, viene usata l'autenticazione NTLM, che fornisce solo l'autenticazione del client da parte del server. Attualmente, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client esegue la ricerca di autenticazione, deducendo SPN dalle proprietà di connessione istanza nome e la rete. Le istanze [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tenteranno di registrare i nomi SPN all'avvio ma è possibile registrarli manualmente. La registrazione, tuttavia, non riuscirà se l'account dispone di diritti di accesso insufficienti per la registrazione dei nomi SPN.  
  
 Gli account di dominio e del computer vengono registrati automaticamente in Active Directory. Questi possono essere usati come SPN oppure gli amministratori possono definire i propri SPN. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rende l'autenticazione più gestibile e affidabile consentendo ai client di specificare direttamente i nomi SPN da usare.  
  
> [!NOTE]  
>  Un nome SPN specificato da un'applicazione client viene usato solo quando viene stabilita una connessione con sicurezza integrata di Windows.  
  
> [!TIP]  
>  **[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Kerberos Configuration Manager per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]** è uno strumento di diagnostica che semplifica la risoluzione dei problemi di connettività correlati a Kerberos con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Microsoft Kerberos Configuration Manager per SQL Server](http://www.microsoft.com/download/details.aspx?id=39046).  
  
> [!TIP]  
>  **[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Kerberos Configuration Manager per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]** è uno strumento di diagnostica che semplifica la risoluzione dei problemi di connettività correlati a Kerberos con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Microsoft Kerberos Configuration Manager per SQL Server](http://www.microsoft.com/download/details.aspx?id=39046).  
  
 Per altre informazioni su Kerberos, vedere gli articoli seguenti:  
  
-   [Kerberos Technical Supplement for Windows](http://go.microsoft.com/fwlink/?LinkId=101449)  
  
-   [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkID=100758)  
  
## <a name="usage"></a>Utilizzo  
 Nella tabella seguente vengono descritti gli scenari più comuni in cui le applicazioni client possono abilitare l'autenticazione protetta.  
  
|Scenario|Description|  
|--------------|-----------------|  
|Un'applicazione legacy non specifica un nome SPN.|Questo scenario di compatibilità garantisce che non vi saranno differenze di comportamento per le applicazioni sviluppate per le versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se non viene specificato alcun nome SPN, l'applicazione si basa sui nomi SPN generati e non è in grado di identificare il metodo di autenticazione usato.|  
|Un'applicazione client utilizzando la versione corrente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client specifica un nome SPN nella stringa di connessione come account di dominio utente o computer, come nome SPN specifico dell'istanza o come una stringa definita dall'utente.|È possibile utilizzare la parola chiave `ServerSPN` in una stringa del provider, di inizializzazione o di connessione per effettuare le operazioni seguenti:<br /><br /> -Specificare l'account utilizzato dal [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza per una connessione. Questa operazione semplifica l'accesso all'autenticazione Kerberos. Se è presente un centro distribuzione chiavi (KDC, Key Distribution Center) Kerberos ed è stato specificato l'account corretto, è più probabile che venga usata l'autenticazione Kerberos anziché l'autenticazione NTLM. Il centro distribuzione chiavi si trova in genere nello stesso computer del controller di dominio.<br />-Specificare un nome SPN per cercare l'account del servizio per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza. Per ogni istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono generati due nomi SPN predefiniti che possono essere usati a questo scopo. Non è tuttavia garantito che tali chiavi siano presenti in Active Directory, pertanto in questa situazione non è garantita neanche l'autenticazione Kerberos.<br />-Specificare un nome SPN che verrà utilizzato per cercare l'account del servizio per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza. Può trattarsi di qualsiasi stringa definita dall'utente di cui è stato eseguito il mapping all'account del servizio. In questo caso, la chiave deve essere registrata manualmente nel centro distribuzione chiavi e deve essere conforme alle regole relative ai nomi SPN definiti dall'utente.<br /><br /> Il `FailoverPartnerSPN` parola chiave può essere usata per specificare il nome SPN per il server partner di failover. L'intervallo di valori per gli account e per le chiavi di Active Directory coincide con i valori che è possibile specificare per il server principale.|  
|Un'applicazione ODBC specifica un nome SPN come attributo di connessione per il server principale o il server partner di failover.|È possibile utilizzare l'attributo di connessione `SQL_COPT_SS_SERVER_SPN` per specificare il nome SPN per una connessione al server principale.<br /><br /> È possibile utilizzare l'attributo di connessione `SQL_COPT_SS_FAILOVER_PARTNER_SPN` per specificare il nome SPN per il server partner di failover.|  
|Un'applicazione OLE DB specifica un nome SPN come proprietà di inizializzazione dell'origine dati per il server principale o per un server partner di failover.|La proprietà di connessione `SSPROP_INIT_SERVER_SPN` nella `DBPROPSET_SQLSERVERDBINIT` set di proprietà può essere utilizzato per specificare il nome SPN per una connessione.<br /><br /> È possibile utilizzare la proprietà di connessione `SSPROP_INIT_FAILOVER_PARTNER_SPN` nel set di proprietà `DBPROPSET_SQLSERVERDBINIT` per specificare il nome SPN per il server partner di failover.|  
|Un utente specifica un nome SPN per un server o per un server partner di failover in un nome di origine dati ODBC.|È possibile specificare il nome SPN in un nome di origine dati ODBC tramite le finestre di dialogo di configurazione del nome dell'origine dati.|  
|L'utente specifica un nome SPN per un server o per un server partner di failover in una finestra di dialogo **Collegamento dati** o **Account di accesso** OLE DB.|È possibile specificare il nome SPN in una finestra di dialogo **Collegamento dati** o **Account di accesso** . La finestra di dialogo **Account di accesso** può essere usata con ODBC o OLE DB.|  
|Un'applicazione ODBC determina il metodo di autenticazione usato per stabilire una connessione.|Se una connessione è stata aperta correttamente, un'applicazione può eseguire una query sull'attributo di connessione `SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD` per determinare il metodo di autenticazione utilizzato. I valori includono, ma non sono limitati a, `NTLM` e `Kerberos`.|  
|Un'applicazione OLE DB determina il metodo di autenticazione utilizzato per stabilire una connessione.|Quando una connessione è stata aperta correttamente, un'applicazione può richiedere la proprietà di connessione `SSPROP_AUTHENTICATION_METHOD` nella `DBPROPSET_SQLSERVERDATASOURCEINFO` imposta proprietà per determinare il metodo di autenticazione utilizzato. I valori includono, ma non sono limitati a, `NTLM` e `Kerberos`.|  
  
## <a name="failover"></a>Failover  
 I nomi SPN non vengono archiviati nella cache di failover e pertanto non possono essere passati tra connessioni. I nomi SPN verranno usati in tutti i tentativi di connessione al server principale e al partner se specificati nella stringa di connessione o negli attributi di connessione.  
  
## <a name="connection-pooling"></a>Pool di connessioni  
 Nelle applicazioni è necessario tenere presente che la specifica dei nomi SPN solo in alcune stringhe di connessione può implicare la frammentazione del pool.  
  
 Le applicazioni possono specificare a livello di programmazione i nomi SPN come attributi di connessione anziché specificare parole chiave della stringa di connessione. In questo modo, viene semplificata la gestione della frammentazione del pool di connessioni.  
  
 Nelle applicazioni è inoltre necessario tenere presente che i nomi SPN nelle stringhe di connessione possono essere sostituiti dagli attributi di connessione corrispondenti, mentre le stringhe di connessione utilizzate dal pool di connessioni utilizzeranno i valori della stringa di connessione ai fini del pool.  
  
## <a name="down-level-server-behavior"></a>Comportamento dei server legacy  
 Poiché il nuovo comportamento di connessione viene implementato dal client, non è specifico di una determinata versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="linked-servers-and-delegation"></a>Server collegati e delega  
 Quando si creano server collegati, i `@provstr` del parametro [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) può essere utilizzato per specificare il server e partner di failover i nomi SPN. L'uso di questo parametro offre gli stessi vantaggi ottenuti specificando i nomi SPN nelle stringhe di connessione del client e consente di stabilire in modo più semplice e affidabile connessioni che usano l'autenticazione Kerberos.  
  
 La delega con server collegati richiede l'autenticazione Kerberos.  
  
## <a name="management-aspects-of-spns-specified-by-applications"></a>Aspetti correlati alla gestione dei nomi SPN specificati dalle applicazioni  
 Nel determinare se specificare nomi SPN in un'applicazione (tramite stringhe di connessione) o a livello di programmazione tramite proprietà di connessione (anziché basandosi sui nomi SPN generati dal provider predefinito), considerare gli aspetti seguenti:  
  
-   Sicurezza: verificare se il nome SPN specificato comporta la divulgazione di informazioni protette.  
  
-   Affidabilità: per consentire l'uso di nomi SPN predefiniti, è necessario che l'account del servizio usato per l'esecuzione dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] disponga di privilegi sufficienti per l'aggiornamento di Active Directory nel Centro distribuzione chiavi.  
  
-   Utilità e trasparenza a livello di posizione: valutare le conseguenze sui nomi SPN di un'applicazione se il database viene spostato in un'istanza diversa di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Questa considerazione si applica sia al server principale sia al relativo partner di failover se si usa il mirroring del database. Se una modifica apportata al server comporta la modifica dei nomi SPN, valutare le conseguenze sulle applicazioni e determinare se sarà possibile gestire tutte le modifiche.  
  
## <a name="specifying-the-spn"></a>Definizione del nome SPN  
 È possibile specificare un nome SPN nelle finestre di dialogo e nel codice. In questa sezione viene descritto come specificare un nome SPN.  
  
 La lunghezza massima consentita per un nome SPN è 260 caratteri.  
  
 Di seguito viene indicata la sintassi usata per i nomi SPN nella stringa di connessione o negli attributi di connessione:  
  
|Sintassi|Description|  
|------------|-----------------|  
|MSSQLSvc/*fqdn*|Nome SPN predefinito generato dal provider per un'istanza predefinita quando si utilizza un protocollo diverso da TCP.<br /><br /> *fqdn* è un nome di dominio completo.|  
|MSSQLSvc/*fqdn*:*port*|Nome SPN predefinito generato dal provider quando si usa il protocollo TCP.<br /><br /> *port* è un numero di porta TCP.|  
|MSSQLSvc/*fqdn*:*InstanceName*|Nome SPN predefinito generato dal provider per un'istanza denominata quando si usa un protocollo diverso da TCP.<br /><br /> *InstanceName* è il nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|HOST/*fqdn*<br /><br /> HOST/*MachineName*|Nome SPN di cui viene eseguito il mapping ad account del computer predefiniti registrati automaticamente in Windows.|  
|*Username*@*Domain*|Specifica diretta di un account di dominio.<br /><br /> *Username* è un nome di account utente di Windows.<br /><br /> *Domain* è un nome di dominio di Windows o un nome di dominio completo.|  
|*MachineName*$@*Domain*|Specifica diretta di un account del computer.<br /><br /> (Se il server ci si connette a è in esecuzione nel sistema locale o account del servizio di rete, per ottenere l'autenticazione Kerberos `ServerSPN` può essere nel *MachineName*$@*dominio* formato).|  
|*KDCKey*/*MachineName*|Nome SPN specificato dall'utente.<br /><br /> *KDCKey* è una stringa alfanumerica conforme alle regole relative alle chiavi KDC.|  
  
## <a name="odbc-and-ole-db-syntax-supporting-spns"></a>Sintassi ODBC e OLE DB con supporto di nomi SPN  
 Per informazioni specifiche della sintassi, vedere gli argomenti seguenti:  
  
-   [Nomi dell'entità servizio &#40;entità servizio&#41; nelle connessioni Client &#40;ODBC&#41;](../odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [Nomi SPN &#40;Service Principal Name&#41; nelle connessioni client &#40;OLE DB&#41;](../ole-db/service-principal-names-spns-in-client-connections-ole-db.md)  
  
 Per informazioni sulle applicazioni di esempio in cui viene illustrata questa funzionalità, vedere la pagina relativa agli [esempi di programmazione dati di SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](sql-server-native-client-features.md)  
  
  
