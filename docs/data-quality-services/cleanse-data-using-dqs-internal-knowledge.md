---
title: "Pulizia dei dati mediante le informazioni interne di DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.dqproject.interactivecleansing.f1"
  - "sql13.dqs.dqproject.map.f1"
  - "sql13.dqs.dqproject.correction.f1"
  - "sql13.dqs.dqproject.export.f1"
ms.assetid: c96b13ad-02a6-4646-bcc7-b4a8d490f5cc
caps.latest.revision: 26
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 26
---
# Pulizia dei dati mediante le informazioni interne di DQS
  In questo argomento viene descritto come eseguire la pulizia dei dati utilizzando un progetto Data Quality in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). La pulizia dei dati viene eseguita sui dati di origine utilizzando una Knowledge Base incorporata in DQS e confrontando tali dati con un set di dati di alta qualità. Per altre informazioni, vedere [Building a Knowledge Base](../data-quality-services/building-a-knowledge-base.md).  
  
 Pulizia dei dati viene eseguita in quattro fasi: un *mapping* fase in cui si identifica l'origine dati da pulire ed eseguirne il mapping a domini richiesti in una knowledge base, un *pulizia computerizzata* fase in cui DQS la knowledge base si applica ai dati da pulire e vengono proposte/apporta modifiche ai dati di origine, un *pulizia interattiva* fase in cui amministratori dei dati consente di analizzare le modifiche ai dati e accettare o rifiutare le modifiche dei dati e infine il *esportare* fasi che consente di esportare i dati puliti. Ognuno di questi processi viene eseguito in una pagina separata della procedura guidata relativa all'attività di pulizia, consentendo all'utente di spostarsi da una pagina a un'altra al fine di rieseguire il processo, completare un processo di pulizia specifico e tornare nuovamente a una sua fase specifica. DQS fornisce statistiche sui dati di origine e sui risultati della pulizia che consentono di prendere decisioni informate sulla pulizia dei dati.  
  
## Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario avere specificato valori soglia adatti per l'attività di pulizia. Per informazioni su questa operazione, vedere [Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md).  
  
-   È necessario che in [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] sia disponibile una Knowledge Base DQS con cui confrontare i dati di origine ed eseguirne la pulizia. La Knowledge Base deve inoltre contenere informazioni sul tipo di dati da pulire. Se si desidera pulire dati di origine che contengono indirizzi in Italia, ad esempio, è necessario disporre di una Knowledge Base creata in base a dati di esempio di alta qualità per indirizzi italiani.  
  
-   Se i dati di origine da pulire si trovano in un file di Excel, è necessario che Microsoft Excel sia installato nel computer [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . In caso contrario, non sarà possibile selezionare il file di Excel nella fase di mapping. I file creati da Microsoft Excel potranno presentare l'estensione xlsx, xls o csv. Se viene utilizzata la versione a 64 bit di Excel, sono supportati solo i file di Excel 2003 (xls), mentre non sono supportati file di Excel 2007 o 2010 (xlsx). Se si utilizza una versione a 64 bit di Excel 2007 o 2010, salvare il file come file xls o csv o installare una versione a 32 bit di Excel.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per eseguire la pulizia dei dati è necessario disporre del ruolo dqs_kb_editor o dqs_kb_operator nel database DQS_MAIN.  
  
##  <a name="Create"></a> Creazione di un progetto Data Quality per la pulizia dei dati  
 Per eseguire l'operazione di pulizia dei dati è necessario utilizzare un progetto Data Quality. Per creare un progetto Data Quality per la pulizia dei dati:  
  
1.  Seguire i passaggi da 1 a 3 nell'argomento [creare un progetto Data Quality](../data-quality-services/create-a-data-quality-project.md).  
  
2.  Nel passaggio 3.d, selezionare l'attività **Pulizia** .  
  
3.  Fare clic su **Crea** per creare un progetto Data Quality per la pulizia dei dati.  
  
 Viene creato un progetto Data Quality per la pulizia dei dati e viene aperta la pagina **Mappa** della procedura guidata Data Quality per la pulizia dei dati.  
  
##  <a name="Mapping"></a> Fase di mapping  
 Nella fase di mapping è possibile specificare la connessione ai dati di origine da pulire ed eseguire il mapping delle colonne dei dati di origine ai domini appropriati nella Knowledge Base selezionata.  
  
1.  Nella pagina **Mappa** della procedura guidata Data Quality per la pulizia dei dati, selezionare i dati di origine da pulire: **SQL Server** o **File di Excel**:  
  
    1.  **SQL Server**: selezionare **DQS_STAGING_DATA** come origine database se è stato copiato i dati di origine al database e quindi selezionare appropriato tabella o vista che contiene i dati di origine. In alternativa, selezionare il database di origine e la tabella o vista appropriata. Il database di origine deve essere presente nella stessa istanza di SQL Server come [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] disponibile al **Database** elenco a discesa.  
  
    2.  **File di Excel**: fare clic su **Sfoglia**e selezionare il file di Excel contenente i dati da pulire. Per selezionare un file di Excel, è necessario che Microsoft Excel sia installato nel computer [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . In caso contrario, il pulsante **Sfoglia** non sarà disponibile e verrà visualizzata una notifica sotto questa casella di testo in cui si avvisa che Microsoft Excel non è installato. Lasciare inoltre selezionata la casella di controllo **Utilizza la prima riga come intestazione** se la prima riga del file di Excel contiene dati dell'intestazione.  
  
2.  In **mapping**, mappare le colonne di dati nei dati di origine ai domini appropriati nella knowledge base selezionando una colonna di origine dall'elenco a discesa nel **colonna di origine** colonna e quindi selezionando un dominio dall'elenco a discesa nel **dominio** colonna nella stessa riga. Ripetere questo passaggio per eseguire il mapping di tutte le colonne nei dati di origine ai domini appropriati nella Knowledge Base. Se necessario, è possibile fare clic sull'icona **Aggiungi un mapping colonne** per aggiungere righe alla tabella di mapping.  
  
    > [!NOTE]  
    >  È possibile eseguire il mapping dei dati di origine a un dominio DQS per eseguire la pulizia dei dati solo se il tipo di dati di origine è supportato in DQS e corrisponde al tipo di dati del dominio DQS. Per informazioni sui tipi di dati di origine supportati, vedere [Supported SQL Server and SSIS Data Types for DQS Domains](../data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md).  
  
3.  Fare clic sull'icona **Anteprima origine dati** per visualizzare i dati nella tabella o vista di SQL Server selezionata o nel foglio di lavoro di Excel selezionato.  
  
4.  Fare clic su **Visualizza/seleziona domini compositi** per visualizzare un elenco di domini compositi di cui viene eseguito il mapping a una colonna di origine. Questo pulsante è disponibile solo se si dispone di almeno di un dominio composito di cui è stato eseguito il mapping a una colonna di origine.  
  
5.  Fare clic su **Avanti** per passare alla fase di pulizia assistita da computer (**Pulisci** pagina).  
  
##  <a name="ComputerAssisted"></a> Fase di pulizia computerizzata  
 In questa fase viene eseguito un processo automatico di pulizia dei dati tramite il quale i dati di origine vengono analizzati rispetto ai domini di cui è stato eseguito il mapping nella Knowledge Base e vengono apportate o proposte delle modifiche dei dati.  
  
1.  Nel **Pulisci** pagina della procedura guidata data quality, fare clic su **avviare** per eseguire il processo di pulizia computerizzato. DQS utilizza algoritmi e livelli di confidenza avanzati basati sui livelli di soglia specificati per l'analisi dei dati da confrontare alla Knowledge Base selezionata e procedere quindi alla loro pulizia. Per informazioni dettagliate sulla pulizia assistita da computer viene eseguita in DQS, vedere [pulizia assistita da Computer](../data-quality-services/data-cleansing.md#ComputerAssisted) in [pulizia dei dati](../data-quality-services/data-cleansing.md).  
  
    > [!IMPORTANT]  
    >  -   Una volta completata l'analisi dei dati, il pulsante **Avvia** viene sostituito dal pulsante **Riavvia** . Se i risultati dall'analisi precedente non sono stati ancora salvati, facendo clic su **Riavvia** si causerà la perdita di tali dati non salvati. Durante l'esecuzione dell'analisi, non lasciare la pagina o il processo di analisi verrà interrotto.  
    > -   Se la Knowledge Base utilizzata per il progetto di pulizia è stata aggiornata e pubblicata dopo l'ora di creazione del progetto di pulizia stesso, quando si fa clic su **Avvia** verrà richiesto se utilizzare la Knowledge Base più recente per la pulizia. Ciò può verificarsi se è stato creato un progetto data quality utilizzando una knowledge base, la pulizia metà progetto chiuso facendo **Chiudi**, e quindi riaprire il progetto data quality in un secondo momento per effettuare la pulizia. Nel frattempo, la Knowledge Base utilizzata nel progetto di pulizia è stata aggiornata e pubblicata.  
    >   
    >      Analogamente, se la knowledge base utilizzata per il progetto di pulizia è stata aggiornata e pubblicata dopo l'ultima è stata eseguita la pulizia computerizzata, facendo clic su **riavviare** richiede se si desidera utilizzare la knowledge base più recente per la pulizia.  
    >   
    >      In entrambi i casi, fare clic su **Sì** da utilizzare la knowledge base aggiornata per la pulizia computerizzata. Inoltre, se è presente qualsiasi conflitto tra i mapping correnti e la Knowledge Base aggiornata (ad esempio domini eliminati o modifiche al tipo di dati del dominio) viene richiesto anche di correggere i mapping correnti per utilizzare la Knowledge Base aggiornata. Facendo clic su **Sì** consente di passare per il **mappa** pagina in cui è possibile correggere i mapping prima di continuare con la pulizia computerizzata.  
  
2.  Durante la fase di pulizia computerizzata, è possibile attivare il profiler facendo la **Profiler** scheda per visualizzare dati in tempo reale di profiling e notifiche. Per altre informazioni, vedere [Statistiche del profiler](#Profiler).  
  
3.  Se non si è soddisfatti dei risultati, fare clic su **Indietro** per tornare alla pagina **Mappa** , modificare uno o più mapping come desiderato, tornare alla pagina **Pulisci** , quindi fare clic su **Riavvia**.  
  
4.  Al termine il processo di pulizia assistita da computer, fare clic su **Avanti** procedere alla fase di pulizia interattiva (**Gestisci e Visualizza risultati** pagina).  
  
##  <a name="Interactive"></a> Fase di pulizia interattiva  
 Nella fase di pulizia interattiva, è possibile visualizzare le modifiche proposte da DQS e decidere se implementarle o meno, approvandole o rifiutandole. Nel riquadro sinistro della finestra di **Gestisci e Visualizza risultati** pagina, viene visualizzato un elenco di tutti i domini che è stato eseguito il mapping in precedenza in fase di mapping insieme al numero di valori nei dati di origine analizzati per ogni dominio durante la fase di pulizia computerizzato. Nel riquadro destro della pagina **Gestisci e visualizza risultati** , in base al rispetto delle regole di dominio, alle regole relative agli errori di sintassi e ad algoritmi avanzati, tramite DQS i dati vengono suddivisi in categorie in cinque schede, utilizzando il *livello di confidenza*. Il livello di confidenza indica il livello di certezza da parte di DQS in relazione a una correzione o suggerimento e si basa sui valori soglia seguenti:  
  
-   **Soglia di correzione automatica**: qualsiasi valore con un livello di confidenza al di sopra di questa soglia viene corretto automaticamente da DQS. L'amministratore dei dati può tuttavia ignorare la modifica durante la pulizia interattiva. È possibile specificare il valore soglia di correzione automatica nella scheda **Impostazioni generali** della schermata **Configurazione** . Per altre informazioni, vedere [Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md).  
  
-   **Soglia di suggerimento automatico**: qualsiasi valore con un livello di confidenza al di sopra di questa soglia, ma al di sotto della soglia di correzione automatica, viene suggerito come valore sostitutivo. In DQS la modifica viene apportata solo se approvata dall'amministratore dei dati. È possibile specificare il valore soglia di suggerimento automatico nella scheda **Impostazioni generali** della schermata **Configurazione** . Per altre informazioni, vedere [Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md).  
  
-   **Altro**: qualsiasi valore al di sotto del valore soglia di suggerimento automatico non viene modificato da DQS.  
  
 In base al livello di confidenza, i valori vengono visualizzati nelle cinque schede seguenti:  
  
|Scheda|Descrizione|  
|---------|-----------------|  
|**Suggeriti**|Visualizza i valori di dominio per il quale DQS sono stati trovati valori suggeriti che dispongono di un livello di confidenza maggiore di *soglia di suggerimento automatico* valore ma inferiore di *soglia di correzione automatica* valore.<br /><br /> Nella colonna **Correggi in** vengono visualizzati i valori suggeriti rispetto al valore originale. È possibile fare clic sul pulsante di opzione nella colonna **Approva** o **Rifiuta** rispetto a un valore nella griglia superiore per accettare o rifiutare il suggerimento per tutte le istanze di tale valore. In questo caso, il valore accettato viene spostato nella scheda **Con correzione** e il valore respinto viene spostato nella scheda **Non validi** .|  
|**Nuovi**|Mostra il dominio valido per il quale DQS non dispone di informazioni sufficienti e del quale non è pertanto possibile eseguire il mapping a nessuna altra scheda. Inoltre, questa scheda contiene inoltre valori che presentano un livello di confidenza inferiore a quello di *soglia di suggerimento automatico* valore, ma sufficientemente elevato per essere contrassegnati come validi.<br /><br /> Se il valore è ritenuto corretto, fare clic sul pulsante di opzione nella colonna **Approva** . Altrimenti, fare clic sul pulsante di opzione nella colonna **Rifiuta** . Il valore accettato viene spostato nella scheda **Corretti** e il valore respinto viene spostato nella scheda **Non validi** . È anche possibile digitare il valore corretto manualmente sostituendo il valore originale nella colonna **Correggi in** , quindi fare clic sul pulsante di opzione nella colonna **Approva** per accettare la modifica. In questo caso, il valore viene spostato nella scheda **Con correzione** .|  
|**Non validi**|Mostra i valori del dominio contrassegnati come non validi nel dominio della Knowledge Base o i valori che non hanno superato una regola di dominio. Questa scheda contiene inoltre i valori rifiutati dall'utente in qualsiasi delle altre quattro schede.<br /><br /> Se il valore è ritenuto corretto, tuttavia, è possibile fare clic sul pulsante di opzione nella colonna **Approva** . Il valore accettato viene spostato nella scheda **Corretti** . È anche possibile digitare il valore corretto manualmente sostituendo il valore originale nella colonna **Correggi in** , quindi fare clic sul pulsante di opzione nella colonna **Approva** per accettare la modifica. In questo caso, il valore viene spostato nella scheda **Con correzione** .|  
|**Con correzione**|Visualizza i valori di dominio corretti da DQS durante il processo automatico di pulizia, nel caso in cui sia stata trovata una correzione per il valore con un livello di confidenza superiore al valore soglia di correzione automatica.<br /><br /> Nella colonna **Correggi in** vengono visualizzati i valori con correzione rispetto al valore originale. Per impostazione predefinita, il pulsante di opzione nella colonna **Approva** per il valore viene selezionato. Se necessario, è possibile rifiutare la correzione proposta facendo clic sul pulsante di opzione nella colonna **Rifiuta** per spostarlo nella scheda **Non validi** o digitare manualmente il valore corretto nella colonna **Correggi in** , quindi fare clic sul pulsante di opzione nella colonna **Approva** per accettare la modifica e spostare il valore nella scheda **Con correzione** .|  
|**Corretti**|Mostra i valori di dominio che sono risultati corretti, Ad esempio, un valore corrispondente a un valore di dominio. Questa scheda contiene anche valori approvati dall'utente facendo clic sul pulsante di opzione nella colonna **Approva** nelle schede **Nuovi** e **Non validi** .<br /><br /> Per impostazione predefinita, il pulsante di opzione nella colonna **Approva** è selezionato per ciascun valore. Se tuttavia si ritiene che un valore in questa scheda sia errato, è possibile fare clic sul pulsante di opzione nella colonna **Rifiuta** per quel valore e spostarlo nella scheda **Non validi** oppure digitare manualmente il valore corretto con cui sostituirlo nella colonna **Correggi in** , quindi fare clic sul pulsante di opzione nella colonna **Approva** per accettare la modifica e spostarlo nella scheda **Con correzione** .|  
  
 Per pulire i dati in modo interattivo:  
  
1.  Nella pagina **Gestisci e visualizza risultati** della procedura guidata Data Quality per la pulizia dei dati, fare clic su un nome di dominio nel riquadro sinistro.  
  
2.  Rivedere i valori di dominio nelle cinque schede e intraprendere le azioni appropriate come illustrato in precedenza.  
  
    -   Nel riquadro superiore destro vengono visualizzate le informazioni seguenti per ogni valore nel dominio selezionato: valore originale, il numero di istanze (record), una casella per specificare un altro valore (corretto), il livello di confidenza (non disponibile per i valori sotto il **corretti** scheda), il motivo per l'azione DQS sul valore e l'opzione per approvare e rifiutare le correzioni e suggerimenti per il valore.  
  
        > [!TIP]  
        >  È possibile approvare o rifiutare tutti i valori nel dominio selezionato nel riquadro superiore destro facendo **approvare tutti i termini** o **Rifiuta tutti i termini** icona rispettivamente. In alternativa, è possibile fare doppio clic su un valore nel dominio selezionato e fare clic su **accettare tutti** o **Rifiuta tutto** nel menu di scelta rapida.  
  
    -   Nel riquadro inferiore vengono visualizzate occorrenze singole del valore di dominio selezionato nel riquadro superiore destro. Vengono visualizzate le informazioni seguenti: una casella per specificare un altro valore (corretto), il livello di confidenza (non disponibile per i valori di **corretti** scheda), il motivo per l'azione DQS sul valore, l'opzione per approvare e rifiutare le correzioni e suggerimenti per il valore e il valore originale.  
  
3.  Se è stata abilitata la funzionalità **Correttore ortografico** per un dominio durante la sua creazione, vengono visualizzati dei caratteri di sottolineatura rossi ondulati insieme a quei valori di dominio identificati come potenziali errori. La sottolineatura viene visualizzata per l'intero valore. Se ad esempio "New York" è stato erroneamente digitato "Neu York", la sottolineatura rossa verrà visualizzata sotto "Neu York" e non solo sotto "Neu." Se si fa clic con il pulsante destro del mouse sul valore, verranno visualizzate le correzioni suggerite. Se sono presenti più di 5 suggerimenti, è possibile fare clic su **Ulteriori suggerimenti** nel menu di scelta rapida per visualizzare quelli rimanenti. Così come avviene per la visualizzazione degli errori, i suggerimenti rappresentano sostituzioni per l'intero valore. Il suggerimento visualizzato per l'esempio precedente sarà ad esempio "New York" e non solo "New". È possibile scegliere uno dei suggerimenti o aggiungere al dizionario una voce da visualizzare per quel valore. I valori vengono archiviati nel dizionario a livello di account utente. Quando si seleziona un suggerimento dal menu di scelta rapida del correttore ortografico, tale suggerimento viene aggiunto alla colonna **Correggi in** . Se si seleziona un suggerimento nella colonna **Correggi in** , tuttavia, il valore nella colonna viene sostituito dal suggerimento selezionato.  
  
     La funzionalità di correzione ortografica è abilitata per impostazione predefinita nella fase di pulizia interattiva. È possibile disabilitare il correttore ortografico nella fase di pulizia interattiva facendo la **Abilita/Disabilita correttore ortografico** sull'icona o pulsante destro del mouse nell'area dei valori di dominio e quindi fare clic su **correttore ortografico** nel menu di scelta rapida. Per abilitarlo nuovamente, seguire la stessa procedura.  
  
    > [!NOTE]  
    >  La funzionalità di correzione ortografica è disponibile solo nel riquadro superiore (valori di dominio). Non è inoltre possibile abilitare o disabilitare il correttore ortografico per domini compositi. Per i domini figlio di tipo stringa abilitati per la funzionalità di correzione ortografica in un dominio composito, tale funzionalità viene abilitata per impostazione predefinita durante la fase di pulizia interattiva.  
  
4.  Durante la fase di pulizia interattiva, è possibile attivare il profiler facendo la **Profiler** scheda per visualizzare dati in tempo reale di profiling e notifiche. Per altre informazioni, vedere [Statistiche del profiler](#Profiler).  
  
5.  Dopo avere rivisto tutti i valori di dominio, fare clic su **Avanti** per procedere alla fase di esportazione.  
  
##  <a name="Export"></a> Fase di esportazione  
 Nella fase di esportazione si specificano i parametri per indicare quali dati puliti esportare e in quale ubicazione.  
  
1.  Nella pagina **Esporta** della procedura guidata Data Quality per la pulizia dei dati, selezionare il tipo di destinazione per l'esportazione dei dati puliti: **SQL Server**, **File CSV**o **File di Excel**.  
  
    > [!IMPORTANT]  
    >  Se si utilizza la versione a 64 bit di Excel, non è possibile esportare i propri dati puliti in un file di Excel. È possibile eseguire l'esportazione solo in un database di SQL Server o in un file con estensione csv.  
  
    1.  **SQL Server**: selezionare **DQS_STAGING_DATA** come destinazione database se si desidera esportare i dati in esso e quindi specificare un nome di tabella che verrà creato per archiviare i dati esportati. Altrimenti, se si desidera esportare i dati in un database diverso, sceglierlo e specificare un nome di tabella che verrà creata per archiviare i dati esportati. Il database di destinazione deve essere presente nella stessa istanza di SQL Server come [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] disponibile al **Database** elenco a discesa.  
  
    2.  **File CSV**: fare clic su **Sfoglia**e specificare il nome e il percorso del file csv nel quale si desidera esportare i dati puliti. È anche possibile digitare il nome per il file csv insieme al percorso completo in cui si desidera esportare i dati puliti, ad esempio, "C:\ExportedData.csv". Il file viene salvato nel computer in cui è installato [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] .  
  
    3.  **File di Excel**: fare clic su **Sfoglia**e specificare il nome e il percorso del file di Excel nel quale si desidera esportare i dati puliti. È anche possibile digitare il nome per il file di Excel insieme al percorso completo in cui si desidera esportare i dati puliti, Ad esempio, "C:\ExportedData.xlsx”. Il file viene salvato nel computer in cui è installato [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] .  
  
2.  Selezionare la casella di controllo **Standardizzare output** per standardizzare l'output in base al formato selezionato per il dominio. Ad esempio, modificare il valore stringa in caratteri maiuscoli o cambiare al maiuscolo l'iniziale della parola. Per informazioni sulla specifica del formato di output di un dominio, vedere l'elenco **Formato output in** in [Set Domain Properties](../data-quality-services/set-domain-properties.md).  
  
3.  Selezionare quindi l'output dei dati: esportare solo i dati puliti o i dati puliti insieme alle informazioni relative alla pulizia.  
  
    -   **Solo dati**: fare clic sul pulsante di opzione per esportare solo i dati puliti.  
  
    -   **Dati e informazioni pulizia**: fare clic sul pulsante di opzione per esportare i dati seguenti per ogni dominio:  
  
        -   **\< dominio>Source**: il valore originale nel dominio.  
  
        -   **\< dominio>output**: I valori puliti nel dominio.  
  
        -   **\< dominio>_Reason**: il motivo specificato per la correzione del valore.  
  
        -   **\< dominio>Confidence**: il livello di confidenza per tutti i termini corretti. Viene visualizzato come valore decimale equivalente al valore percentuale corrispondente. Un livello di confidenza del 95% viene ad esempio visualizzato come 0,9500000.  
  
        -   **\< dominio>_Status**: lo stato del valore di dominio dopo la pulizia dei dati. Ad esempio **Suggeriti**, **Nuovi**, **Non validi**, **Con correzione**o **Corretti**.  
  
        -   **Registrare lo stato**: oltre a disporre di un campo di stato per ogni dominio mappato **(\< NomeDominio>_Status**), il **stato Record** campo viene visualizzato lo stato di un record. Se uno stato del dominio nel record è *Nuovi* o *Corretti*, il valore di **Stato record** viene impostato su *Corretti*. Se uno stato del dominio nel record è *Suggeriti*, *Non validi*o *Con correzione*, il valore di **Stato record** viene impostato sul rispettivo valore. Ad esempio, se uno stato del dominio nel record è *Suggeriti*, il valore di **Stato record** viene impostato su *Suggeriti*.  
  
            > [!NOTE]  
            >  Se si utilizza un servizio dati di riferimento per l'operazione di pulizia, sono disponibili dati aggiuntivi sui valori di dominio per l'esportazione. Per ulteriori informazioni, vedere [pulire i dati utilizzando dati di riferimento & #40; N. 41; & esterni Knowledge Base](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).  
  
4.  Fare clic su **Esporta** per esportare i dati nella destinazione selezionata. Se si è selezionato  
  
    -   **SQL Server** come destinazione dei dati, nel database selezionato verrà creata una nuova tabella con il nome specificato.  
  
    -   **File CSV** come destinazione dei dati, verrà creato un file csv nel percorso nel computer [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] con il nome file specificato in precedenza nella casella **Nome file CSV** .  
  
    -   **File di Excel** come destinazione dei dati, verrà creato un file di Excel nel percorso nel computer [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] con il nome file specificato in precedenza nella casella **Nome file di Excel** .  
  
5.  Fare clic su **Fine** per chiudere il progetto Data Quality.  
  
##  <a name="Profiler"></a> Statistiche del profiler  
 La scheda **Profiler** fornisce statistiche che indicano la qualità dei dati di origine. Il profiling consente di valutare il livello di efficacia dell'attività di pulizia dei dati e potenzialmente di determinare in quale misura tale attività è stata in grado di migliorare la qualità dei dati.  
  
 La scheda **Profiler** fornisce le statistiche seguenti per i dati di origine, per campo e dominio:  
  
-   **Record**: il numero di record nei dati di esempio analizzati per l'attività di pulizia dei dati  
  
-   **Record corretti**: il numero di record che sono risultati corretti  
  
-   **Record con correzione**: il numero di record cui sono state apportate correzioni  
  
-   **Record suggeriti**: il numero di record che sono stati suggeriti  
  
-   **Record non validi**: il numero di record che sono risultati non validi  
  
 Le statistiche relative ai campi includono:  
  
-   **Campo**: nome del campo nei dati di origine  
  
-   **Dominio**: nome del dominio di cui è stato eseguito il mapping al campo  
  
-   **Valori con correzione**: il numero di valori di dominio che sono stati corretti  
  
-   **Valori consigliati**: il numero di valori di dominio che sono stati suggeriti  
  
-   **Completezza**: la completezza di ogni campo di origine di cui è stato eseguito il mapping per l'attività di pulizia  
  
-   **Accuratezza**: l'accuratezza di ogni campo di origine di cui è stato eseguito il mapping per l'attività di pulizia  
  
 Profiling DQS fornisce due dimensioni della qualità dei dati: *completezza* (l'entità a cui sono presenti dati) e *accuratezza* (l'entità cui dati possono essere utilizzati per gli scopi previsti). Se il profiling suggerisce che un campo è relativamente incompleto, è necessario rimuoverlo dalla Knowledge Base di un progetto Data Quality. È possibile che il profiling non fornisca statistiche di completezza affidabili per i domini compositi. Se sono necessarie statistiche di completezza, utilizzare domini singoli anziché domini compositi. Se si desidera utilizzare domini compositi, è consigliabile creare una Knowledge Base con domini singoli di cui eseguire il profiling per determinare la completezza, quindi creare un altro dominio con un dominio composito per il processo di pulizia. Ad esempio, il profiling potrebbe mostrare una completezza del 95% per record relativi a indirizzi, utilizzando un dominio composito, ma potrebbe esservi un livello di incompletezza molto più alto per una delle colonne, ad esempio una colonna relativa al codice postale (CAP). In questo esempio, è necessario misurare la completezza della colonna del CAP con un solo dominio. Il profiling fornirà probabilmente statistiche di accuratezza affidabili per i domini compositi perché è possibile misurare l'accuratezza di più colonne allo stesso tempo. Il valore di questi dati sta nell'aggregazione composta, pertanto è consigliabile misurarne l'accuratezza con un dominio composito.  
  
 Se non si utilizza un servizio dati di riferimento, le statistiche di accuratezza richiederanno probabilmente un maggior livello di interpretazione. Se si utilizza un servizio dati di riferimento per la pulizia dei dati, si otterrà un certo livello di attendibilità nelle statistiche di accuratezza. Per ulteriori informazioni sui dati di pulizia utilizzando un servizio dati di riferimento, vedere [pulire i dati utilizzando dati di riferimento & #40; N. 41; & esterni Knowledge Base](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).  
  
### Notifiche relative alla pulizia  
 Le condizioni seguenti danno luogo a notifiche:  
  
-   Non sono presenti correzioni o suggerimenti per un campo. Potrebbe essere necessario rimuovere tale campo dal mapping, eseguire prima l'individuazione delle informazioni oppure utilizzare una Knowledge Base diversa.  
  
-   È presente un numero relativamente basso di correzioni o suggerimenti per un campo. Potrebbe essere necessario rimuovere tale campo dal mapping, eseguire prima l'individuazione delle informazioni oppure utilizzare una Knowledge Base diversa.  
  
-   Il livello di accuratezza del campo è molto basso. Potrebbe essere necessario verificare il mapping o considerare l'esecuzione dell'individuazione delle informazioni.  
  
 Per ulteriori informazioni sul profiling, vedere [Data Profiling and Notifications in DQS](../data-quality-services/data-profiling-and-notifications-in-dqs.md).  
  
  