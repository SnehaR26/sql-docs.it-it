---
title: Pianificare un pacchetto tramite SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3d389cce-05af-4e1d-b684-7bbff413c806
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d3112f43436fa7e0a0bb87d58cca062857bae8e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215761"
---
# <a name="schedule-a-package-by-using-sql-server-agent"></a>Pianificare un pacchetto tramite SQL Server Agent
  Nella procedura riportata di seguito vengono illustrati i passaggi per automatizzare l'esecuzione di un pacchetto tramite un passaggio di processo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent per eseguire il pacchetto.  
  
### <a name="to-automate-package-execution-by-using-sql-server-agent"></a>Per automatizzare l'esecuzione dei pacchetti tramite SQL Server Agent  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]connettersi all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in cui si desidera creare un processo oppure all'istanza contenente il processo a cui si desidera aggiungere un passaggio.  
  
2.  Espandere il nodo [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent in Esplora oggetti ed eseguire una delle attività seguenti:  
  
    -   Per creare un nuovo processo, fare clic con il pulsante destro del mouse su **Processi** , quindi scegliere **Nuovo processo**.  
  
    -   Per aggiungere un passaggio a un processo esistente, espandere il nodo **Processi**, fare clic con il pulsante destro del mouse sul processo, quindi scegliere **Proprietà**.  
  
3.  Nella pagina **Generale** , se si crea un nuovo processo specificare un nome per il processo, selezionare un proprietario e una categoria di processo e, facoltativamente, fornire una descrizione.  
  
4.  Per rendere il processo disponibile per la pianificazione, selezionare **Abilitato**.  
  
5.  Per creare un passaggio di processo per il pacchetto che si desidera pianificare, fare clic su **Passaggi**, quindi su **Nuovo**.  
  
6.  Selezionare **Pacchetto di Integration Services** per il tipo di passaggio di processo.  
  
7.  Nell'elenco **Esegui come** selezionare **Account del servizio SQL Server Agent** oppure selezionare un account proxy che dispone delle credenziali che verranno utilizzate dal passaggio di processo. Per informazioni sulla creazione di un account proxy, vedere [Create a SQL Server Agent Proxy](../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
     L'utilizzo di un account proxy anziché dell' **Account del servizio SQL Server Agent** può risolvere i problemi comuni che possono verificarsi quando si esegue un pacchetto tramite [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent. Per ulteriori informazioni su questi problemi, vedere l'articolo della [!INCLUDE[msCoName](../includes/msconame-md.md)] Knowledge Base relativo a [un pacchetto SSIS che non viene eseguito quando viene chiamato da un passaggio di processo di SQL Server Agent](http://support.microsoft.com/kb/918760).  
  
    > [!NOTE]  
    >  Se viene modificata la password per le credenziali utilizzate dall'account proxy, è necessario aggiornare la password delle credenziali. In caso contrario, il passaggio di processo avrà esito negativo.  
  
     Per informazioni sulla configurazione dell'account del servizio SQL Server Agent, vedere [Impostazione dell'account di avvio del servizio SQL Server Agent &#40;Gestione configurazione SQL Server&#41;](../relational-databases/sql-server-configuration-manager.md).  
  
8.  Nella casella di riepilogo **Origine pacchetto** fare clic sull'origine del pacchetto e quindi configurare le opzioni per il passaggio di processo.  
  
     **Nella tabella seguente vengono descritte le possibili origini pacchetto.**  
  
    |Origine pacchetto|Description|  
    |--------------------|-----------------|  
    |**Catalogo SSIS**|Pacchetti archiviati nel database SSISDB. I pacchetti sono contenuti nei progetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] distribuiti nel server [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .|  
    |**SQL Server**|Pacchetti archiviati nel database MSDB. Utilizzare il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] per gestire i pacchetti.|  
    |**Archivio pacchetti SSIS**|Pacchetti archiviati nella cartella predefinita nel computer. La cartella predefinita è *\<unità>*:\Programmi\Microsoft SQL Server\110\DTS\Packages. Utilizzare il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] per gestire i pacchetti.<br /><br /> Nota: è possibile specificare un'altra cartella o cartelle aggiuntive nel file system da gestire con il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] modificando il file di configurazione per [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Per altre informazioni, vedere [Configurazione del servizio Integration Services &#40;SSIS&#41;](service/integration-services-service-ssis-service.md).|  
    |**File System**|Pacchetti archiviati in qualsiasi cartella nel computer locale.|  
  
     **Nelle tabelle seguenti vengono descritte le opzioni di configurazione disponibili per il passaggio di processo in base all'origine del pacchetto selezionata.**  
  
    > [!IMPORTANT]  
    >  Se il pacchetto è protetto da password, quando si fa clic su una delle schede nella pagina **Generale** della finestra di dialogo **Nuovo passaggio di processo**, ad eccezione della scheda **Pacchetto**, è necessario immettere la password nella finestra di dialogo **Password pacchetto** che viene visualizzata. In caso contrario, il processo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent non sarà in grado di eseguire il pacchetto.  
  
     **Origine pacchetto**: catalogo SSIS  
  
    |Scheda|Opzioni|  
    |---------|-------------|  
    |**Pacchetto**|**Server**<br /><br /> Digitare o selezionare il nome dell'istanza del server di database che ospita il catalogo SSISDB.<br /><br /> Quando **Catalogo SSIS** è l'origine del pacchetto, è possibile accedere al server utilizzando solo un account utente di Microsoft Windows. L'autenticazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non è disponibile.|  
    ||**Pacchetto**<br /><br /> Fare clic sul pulsante con i puntini di sospensione e selezionare un pacchetto.<br /><br /> Viene selezionato un pacchetto in una cartella nel nodo **Cataloghi di Integration Services** in **Esplora oggetti**.|  
    |**Parametri**<br /><br /> Si trova nella scheda **Configurazione** .|Immettere nuovi valori per i parametri contenuti nel pacchetto. È possibile immettere un valore letterale o utilizzare il valore contenuto in una variabile di ambiente server di cui è già stato eseguito il mapping al parametro.  **\*\* Importanti \* \* ** se è stato eseguito il mapping più parametri e/o proprietà di gestione connessione alle variabili contenute in più ambienti, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent Visualizza un messaggio di errore. Per un'esecuzione specifica, un pacchetto può essere eseguito solo con i valori contenuti in un ambiente server singolo.<br /><br /> Per immettere il valore letterale, fare clic sul pulsante con i puntini di sospensione accanto a un parametro. Viene visualizzata la finestra di dialogo **Modifica valore letterale per l'esecuzione** .<br /><br /> Per utilizzare una variabile di ambiente, fare clic su **Ambiente** e selezionare l'ambiente che contiene la variabile da utilizzare.<br /><br /> <br /><br /> Nella scheda **Parametri** sono visualizzati i parametri aggiunti dopo la progettazione del pacchetto, ad esempio tramite [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Nella scheda sono inoltre visualizzati i parametri aggiunti al pacchetto durante la conversione del progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dal modello di distribuzione del pacchetto nel modello di distribuzione del progetto. La **Conversione guidata progetto di Integration Services** consente di sostituire le configurazioni del pacchetto con i parametri.<br /><br /> Per informazioni sulla creazione di un ambiente server e il mapping di una variabile a un parametro, vedere [Creare ed eseguire il mapping di un ambiente server](../../2014/integration-services/create-and-map-a-server-environment.md).|  
    |**Gestioni connessioni**<br /><br /> Si trova nella scheda **Configurazione** .|Modificare i valori per le proprietà di gestione connessione. Ad esempio, è possibile modificare il nome del server.<br /><br /> I parametri vengono automaticamente generati nel server SSIS per le proprietà di gestione connessione.<br /><br /> Per modificare il valore di una proprietà, è possibile immettere un valore letterale o utilizzare il valore contenuto in una variabile di ambiente server di cui è già stato eseguito il mapping alla proprietà di gestione connessione. **\*\* Importanti \* \* ** se è stato eseguito il mapping più parametri e/o proprietà di gestione connessione alle variabili contenute in più ambienti, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent Visualizza un messaggio di errore. Per un'esecuzione specifica, un pacchetto può essere eseguito solo con i valori contenuti in un ambiente server singolo.<br /><br /> Per immettere il valore letterale, fare clic sul pulsante con i puntini di sospensione accanto a un parametro. Viene visualizzata la finestra di dialogo **Modifica valore letterale per l'esecuzione** .<br /><br /> Per utilizzare una variabile di ambiente, fare clic su **Ambiente** e selezionare l'ambiente che contiene la variabile da utilizzare.<br /><br /> <br /><br /> Per informazioni sulla creazione di un ambiente server e il mapping di una variabile a una proprietà della gestione connessione, vedere [Creare ed eseguire il mapping di un ambiente server](../../2014/integration-services/create-and-map-a-server-environment.md).|  
    |**Advanced**<br /><br /> Si trova nella scheda **Configurazione** .|Configurare le impostazioni aggiuntive seguenti per l'esecuzione del pacchetto.<br /><br /> <br /><br /> **Gli override delle proprietà**: fare clic su **Add** per immettere un nuovo valore per una proprietà del pacchetto, specificare il percorso della proprietà e indicare se il valore della proprietà è sensibile. Il server [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] crittografa i dati sensibili. Per modificare o rimuovere le impostazioni per una proprietà, fare clic su una riga nel contenitore di override **Proprietà** , quindi fare clic su **Modifica** o **Rimuovi**. Si noti che il **esegue l'override di proprietà** opzione è destinata ai pacchetti con configurazioni aggiornate da una versione precedente di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. I pacchetti creati tramite [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] e distribuiti al server [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] utilizzano parametri anziché configurazioni. È possibile trovare il percorso della proprietà con una delle operazioni seguenti:<br /><br /> Copiare il percorso della proprietà dal file di configurazione XML (\*dtsconfig) file. Il percorso è elencato nella sezione Configurazione del file, come valore dell'attributo Path. Di seguito è riportato un esempio del percorso per la proprietà MaximumErrorCount.<br /><br /> \Package.Properties[MaximumErrorCount]<br /><br /> Eseguire la **configurazione guidata pacchetto** e copiare i percorsi delle proprietà da finale **Completamento procedura guidata** pagina. È possibile annullare la procedura guidata.|  
    ||**Livello di registrazione**: il livello di registrazione selezionato determina quali informazioni vengono visualizzate nelle viste SSISDB e nei report per il [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server. La selezione del livello di registrazione **Prestazioni** o **Dettagliato** può influire sulle prestazioni di esecuzione del pacchetto. Selezionare uno dei seguenti livelli di registrazione per l'esecuzione del pacchetto:<br /><br /> **Nessuno**: la registrazione è disabilitata. Solo lo stato dell'esecuzione del pacchetto viene registrato.<br /><br /> **Base**: tutti gli eventi vengono registrati, ad eccezione degli eventi personalizzati e di diagnostici. È il valore predefinito per il livello di registrazione.<br /><br /> **Prestazioni**: vengono registrati solo le statistiche sulle prestazioni e gli eventi OnError e OnWarning.<br /><br /> **Verbose**: tutti gli eventi vengono registrati, inclusi gli eventi personalizzati e di diagnostici.<br /><br /> Per altre informazioni, vedere [Enable Logging for Package Execution on the SSIS Server](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md).|  
    ||**Dump su errori**: specificare se i file dump del debug vengono generati quando si verifica un errore durante l'esecuzione del pacchetto.<br /><br /> I file contengono le informazioni sull'esecuzione del pacchetto che possono consentire di risolvere i problemi dell'esecuzione.<br /><br /> Quando si seleziona questa opzione e si verifica un errore durante l'esecuzione, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] crea un file con estensione MDMP (file binario) e un file con estensione TMP (file di testo). Per impostazione predefinita, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] archivia i file nella cartella *\<unità>:* \Programmi\Microsoft SQL Server\110\Shared\ErrorDumps.|  
    ||**runtime a 32 bit** indicare se si desidera eseguire il pacchetto usando la versione a 32 bit dell'utilità dtexec in un computer a 64 bit che ha la versione a 64 bit dello [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installato l'agente.<br /><br /> Potrebbe essere necessario eseguire il pacchetto utilizzando la versione a 32 bit di dtexec se, ad esempio, il pacchetto utilizza un provider OLE DB nativo che non è disponibile in una versione a 64 bit. Per ulteriori informazioni, vedere [Considerazioni a 64r bit per Integration Services](http://msdn.microsoft.com/library/ms141766\(SQL.105\).aspx).<br /><br /> Per impostazione predefinita, quando si seleziona il tipo di passaggio di processo **Pacchetto di SQL Server Integration Services** , [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent esegue il pacchetto utilizzando la versione dell'utilità dtexec che è richiamata automaticamente dal sistema. Il sistema richiama la versione a 32 bit o la versione a 64 bit dell'utilità a seconda del processore del computer e la versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent in esecuzione nel computer.|  
  
     **Origine pacchetto**: SQL Server, archivio pacchetti SSIS o file system  
  
     Molte delle opzioni che è possibile impostare per i pacchetti archiviati in SQL Server, Store il pacchetto SSIS o nel file system corrispondono alle opzioni della riga di comando per il `dtexec` utilità della riga di comando. Per ulteriori informazioni sull'utilità e sulle opzioni della riga di comando, vedere [Utilità dtexec](packages/dtexec-utility.md).  
  
    |Scheda|Opzioni|  
    |---------|-------------|  
    |**Pacchetto**<br /><br /> Di seguito sono riportate le opzioni della scheda per i pacchetti archiviati in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o nell'archivio pacchetti [!INCLUDE[ssIS](../includes/ssis-md.md)] .|**Server**<br /><br /> Digitare o selezionare il nome dell'istanza del server di database per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .|  
    ||**Usa autenticazione di Windows**<br /><br /> Selezionare questa opzione per accedere al server mediante un account utente di Microsoft Windows.|  
    ||**Usa autenticazione di SQL Server**<br /><br /> Quando un utente si connette con un nome di account di accesso e una password da una connessione non trusted, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] esegue l'autenticazione controllando se è stato impostato un account di accesso di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e se la password specificata corrisponde a quella registrata in precedenza. Se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non riesce a trovare un account di accesso, l'autenticazione ha esito negativo e viene visualizzato un messaggio di errore.|  
    ||**Nome utente**|  
    ||**Password**|  
    ||**Pacchetto**<br /><br /> Fare clic sul pulsante con i puntini di sospensione e selezionare il pacchetto.<br /><br /> Viene selezionato un pacchetto in una cartella nel nodo **Pacchetti archiviati** in **Esplora oggetti**.|  
    |**Password pacchetto**<br /><br /> Di seguito sono riportate le opzioni della scheda per i pacchetti archiviati nel file system.|**Pacchetto**<br /><br /> Digitare il percorso completo del file del pacchetto oppure fare clic sul pulsante con i puntini di sospensione per selezionare il pacchetto.|  
    |**Configurazioni**|Aggiungere un file di configurazione XML per eseguire il pacchetto con una configurazione specifica. Per aggiornare i valori delle proprietà del pacchetto in fase di esecuzione utilizzare una configurazione di pacchetto.<br /><br /> Questa opzione corrisponde al **/ConfigFile** opzione per `dtexec`.<br /><br /> Per informazioni sull'applicazione delle configurazioni dei pacchetti, vedere [Package Configurations](../../2014/integration-services/package-configurations.md). Per informazioni su come creare la configurazione di un pacchetto, vedere [Create Package Configurations](../../2014/integration-services/create-package-configurations.md).|  
    |**File di comando**|Specificare le opzioni aggiuntive da eseguire con `dtexec`, in un file separato.<br /><br /> Ad esempio, è possibile includere un file contenente l'opzione /Dump *errorcode* per generare file di dump del debug quando uno o più eventi specificati si verificano durante l'esecuzione del pacchetto.<br /><br /> È possibile eseguire un pacchetto con diversi set di opzioni creando più file e specificando il file appropriato tramite l'opzione **File di comando** .<br /><br /> Il **file di comando** opzione corrisponde al `/CommandFile` opzione `dtexec`.|  
    |**Origini dati**|Visualizzare le gestioni connessioni contenute nel pacchetto. Per modificare una stringa di connessione, fare clic sulla gestione connessione e quindi fare clic sulla stringa di connessione.<br /><br /> Questa opzione corrisponde al `/Connection` opzione per `dtexec`.|  
    |**Opzioni di esecuzione**|**Interrompi il pacchetto in caso di avvisi di convalida**<br /> Indica se un messaggio di avviso viene considerato un errore. Se si seleziona questa opzione e viene generato un avviso durante la convalida, il pacchetto ha esito negativo durante la convalida. Questa opzione corrisponde al `/WarnAsError` opzione per `dtexec`.<br /><br /> **Convalida pacchetto senza esecuzione**<br /> Indica se l'esecuzione del pacchetto viene arrestata dopo la fase di convalida, senza eseguire effettivamente il pacchetto. Questa opzione corrisponde al `/Validate` opzione per `dtexec`.<br /><br /> **Esegui override proprietà MaxConcurrentExecutables**<br /> Consente di specificare il numero di file eseguibili che il pacchetto è in grado di eseguire contemporaneamente. Il valore -1 indica che il pacchetto può eseguire un numero massimo di file eseguibili uguale al numero totale di processori nel computer in cui è eseguito il pacchetto, più due. Questa opzione corrisponde al `/MaxConcurrent` opzione per `dtexec`.<br /><br /> **Abilita checkpoint pacchetto**<br /> Indica se il pacchetto utilizzerà checkpoint durante l'esecuzione del pacchetto. Per ulteriori informazioni, vedere [Riavvio dei pacchetti tramite checkpoint](packages/restart-packages-by-using-checkpoints.md).<br /><br /> Le opzioni corrispondono all'opzione `/CheckPointing` per `dtexec`.<br /><br /> **Ignora opzioni di riavvio**<br /> Indica se un nuovo valore viene impostato per il `CheckpointUsage` proprietà del pacchetto. Selezionare un valore nell'elenco a discesa **Opzione di avvio** .<br /><br /> Questa opzione corrisponde al `/Restart` opzione per `dtexec`.<br /><br /> **Utilizza run-time a 32 bit**<br /> Indicare se eseguire il pacchetto utilizzando la versione a 32 bit dell'utilità dtexec in un computer a 64 bit con la versione a 64 bit di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent installata.<br /><br /> Potrebbe essere necessario eseguire il pacchetto utilizzando la versione a 32 bit di dtexec se, ad esempio, il pacchetto utilizza un provider OLE DB nativo che non è disponibile in una versione a 64 bit. Per ulteriori informazioni, vedere [Considerazioni a 64r bit per Integration Services](http://msdn.microsoft.com/library/ms141766\(SQL.105\).aspx).<br /><br /> Per impostazione predefinita, quando si seleziona il tipo di passaggio di processo **Pacchetto di SQL Server Integration Services** , [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent esegue il pacchetto utilizzando la versione dell'utilità dtexec che è richiamata automaticamente dal sistema. Il sistema richiama la versione a 32 bit o la versione a 64 bit dell'utilità a seconda del processore del computer e la versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent in esecuzione nel computer.|  
    |**Registrazione**|Associare un provider di log all'esecuzione del pacchetto.<br /><br /> **Provider di log SSIS per file di testo**<br /> Scrive le voci di log in file di testo ASCII<br /><br /> **Provider di log SSIS per SQL Server**<br /> Scrive le voci di log nella tabella sysssislog nel database MSDB.<br /><br /> **Provider di log SSIS per SQL Server Profiler**<br /> Scrive tracce che è possibile visualizzare utilizzando SQL Server Profiler.<br /><br /> **Provider di log SSIS per il registro eventi di Windows**<br /> Scrive voci di log nel log applicazioni nel registro eventi di Windows.<br /><br /> **Provider di log SSIS per file XML**<br /> Scrive file di log in un file XML.<br /><br /> Per il file di testo, il file XML e i provider di log di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler, si selezionano gestioni connessione file contenute nel pacchetto. Per il provider di log di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , si seleziona una gestione connessione OLE DB contenuta nel pacchetto.<br /><br /> Questa opzione corrisponde al `/Logger` opzione per `dtexec`.|  
    |**Imposta valori**|Eseguire l'override dell'impostazione delle proprietà di un pacchetto. Nella casella **Proprietà** immettere i valori nelle colonne **Percorso proprietà** e **Valore** . Dopo avere immesso valori per una proprietà, viene visualizzata una riga vuota nella casella **Proprietà** che consente di immettere valori per un'altra proprietà.<br /><br /> Per rimuovere una proprietà dalla casella Proprietà, fare clic sulla riga e quindi su **Rimuovi**.<br /><br /> È possibile trovare il percorso della proprietà effettuando una delle operazioni seguenti.<br /><br /> Copiare il percorso della proprietà dal file di configurazione XML (\*dtsconfig) file. Il percorso è elencato nella sezione Configurazione del file, come valore dell'attributo Path. Di seguito è riportato un esempio del percorso per la proprietà MaximumErrorCount.<br /><br /> \Package.Properties[MaximumErrorCount]<br /><br /> Eseguire la **configurazione guidata pacchetto** e copiare i percorsi delle proprietà da finale **Completamento procedura guidata** pagina. È possibile annullare la procedura guidata.|  
    |**Verifica**|**Esegui solo pacchetti firmati**<br /> Indica se la firma del pacchetto è controllata. Se il pacchetto non è firmato o se la firma non è valida, il pacchetto ha esito negativo. Questa opzione corrisponde al `/VerifySigned` opzione per `dtexec`.<br /><br /> **Verifica build pacchetto**<br /> Indica se il numero di build del pacchetto viene verificato rispetto al numero di build immesso nella casella **Compilazione** accanto all'opzione. Se i numeri non corrispondono, il pacchetto non verrà eseguito. Questa opzione corrisponde al `/VerifyBuild` opzione per `dtexec`.<br /><br /> **Verifica ID pacchetto**<br /> Indica se il GUID del pacchetto viene verificato, confrontandolo con l'ID pacchetto immesso nella casella **ID pacchetto** accanto all'opzione. Questa opzione corrisponde al `/VerifyPackageID` opzione per `dtexec`.<br /><br /> **Verifica ID versione**<br /> Indica se il GUID della versione del pacchetto viene verificato, confrontandolo con l'ID versione immesso nella casella **ID versione** accanto all'opzione. Questa opzione corrisponde al `/VerifyVersionID` opzione per `dtexec`.|  
    |**Riga di comando**|Modificare le opzioni della riga di comando per dtexec. Per ulteriori informazioni sulle opzioni, vedere [dtexec Utility](packages/dtexec-utility.md).<br /><br /> Suggerimento: È possibile copiare la riga di comando in una finestra del prompt dei comandi, aggiungere `dtexec`, ed eseguire il pacchetto dalla riga di comando. Si tratta di testo della riga di comando facile da generare.<br /><br /> **Ripristina opzioni originali**<br /> Utilizzare le opzioni della riga di comando impostate nelle schede **Pacchetto**, **Configurazioni**, **File di comando**, **Origini dati**, **Opzioni di esecuzione**, **Registrazione**, **Imposta valori**e **Verifica** della finestra di dialogo **Proprietà set processo** .<br /><br /> **Modificare il comando manualmente**<br /> Digitare opzioni della riga di comando aggiuntive nella casella **Riga di comando** .<br /><br /> Prima di fare clic su **OK** per salvare le modifiche apportate al passaggio di processo, è possibile rimuovere tutte le opzioni aggiuntive digitate nella casella **Riga di comando** facendo clic su **Ripristina opzioni originali**.|  
  
9. Scegliere **OK** per salvare le impostazioni e chiudere la finestra di dialogo **Nuovo passaggio di processo** .  
  
    > [!NOTE]  
    >  Per i pacchetti archiviati nel **Catalogo SSIS**il pulsante **OK** è disabilitato se è presente un parametro o un'impostazione della proprietà di gestione connessione non risolto. Un'impostazione non risolta si verifica quando si utilizza un valore contenuto in una variabile di ambiente server per impostare il parametro o la proprietà e si verifica una delle seguenti condizioni.  
    >   
    >  -   La casella di controllo **Ambiente** nella scheda **Configurazione** non è selezionata.  
    > -   L'ambiente server che contiene la variabile non è selezionato nella casella di riepilogo della scheda **Configurazione** .  
  
10. Per creare una pianificazione per un passaggio di processo, fare clic su **Pianificazioni** nel riquadro **Selezione pagina** . Per informazioni su come configurare una pianificazione, vedere [Schedule a Job](../ssms/agent/schedule-a-job.md).  
  
    > [!TIP]  
    >  Quando si assegna un nome alla pianificazione, utilizzare un nome univoco e descrittivo in modo da distinguere più facilmente la pianificazione da altre pianificazioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di progetti e pacchetti](packages/run-integration-services-ssis-packages.md)  
  
  