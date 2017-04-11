---
title: "Considerazioni e limitazioni relative alla progettazione dei server di pubblicazione Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazione Oracle [replica di SQL Server], considerazioni e limitazioni relative alla progettazione"
ms.assetid: 8d9dcc59-3de8-4d36-a61f-bc3ca96516b6
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 48
---
# Considerazioni e limitazioni relative alla progettazione dei server di pubblicazione Oracle
  Pubblicazione da un database Oracle è progettata per funzionare in modo quasi identico alla pubblicazione da un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database. È tuttavia necessario tenere conto delle limitazioni e dei problemi seguenti:  
  
-   L'opzione Oracle Gateway offre prestazioni migliori rispetto all'opzione Oracle Complete, ma non è possibile utilizzarla per pubblicare la stessa tabella in più pubblicazioni transazionali. Una tabella può essere visualizzata al massimo in una pubblicazione transazionale e in qualsiasi numero di pubblicazioni snapshot. Se è necessario pubblicare la stessa tabella in più pubblicazioni transazionali, scegliere l'opzione Oracle Complete.  
  
-   La replica supporta la pubblicazione di tabelle, indici e viste materializzate. Gli altri oggetti non vengono replicati.  
  
-   L'archiviazione e l'elaborazione dei dati in Oracle e nei database [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] presentano alcune piccole differenze che influiscono sulla replica.  
  
-   Quando si utilizza un server di pubblicazione Oracle le caratteristiche della replica transazionale vengono supportate in modo differente.  
  
## Supporto per la pubblicazione di oggetti da Oracle  
 Utilizzando la replica è possibile replicare gli oggetti seguenti dai database Oracle:  
  
-   Tabelle  
  
-   Tabelle organizzate in indici  
  
-   Indici  
  
-   Viste materializzate (replicate come tabelle)  
  
 Nelle tabelle pubblicate possono essere presenti gli oggetti seguenti non replicati:  
  
-   Indici basati sui domini  
  
-   Indici basati sulle funzioni  
  
-   Valori predefiniti  
  
-   Vincoli CHECK  
  
-   Chiavi esterne  
  
-   Opzioni di archiviazione (spazi tabella, cluster e così via)  
  
 Non è possibile replicare gli oggetti seguenti:  
  
-   Tabelle nidificate  
  
-   Viste  
  
-   Pacchetti, corpi dei pacchetti, procedure e trigger  
  
-   Code  
  
-   Sequenze  
  
-   Sinonimi  
  
 Per informazioni sui tipi di dati supportati, vedere [Mapping di tipi di dati per server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
## Differenze tra Oracle e SQL Server  
  
-   Oracle presenta limiti di dimensione massima differenti per alcuni oggetti. Gli oggetti creati nel database di pubblicazione Oracle devono rispettare i limiti di dimensione massima per gli oggetti corrispondenti in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per informazioni sui limiti in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [specifiche di capacità massima per SQL Server](../../../sql-server/maximum-capacity-specifications-for-sql-server.md).  
  
-   Per impostazione predefinita, i nomi degli oggetti Oracle vengono creati in caratteri maiuscoli. Specificare i nomi degli oggetti Oracle in caratteri maiuscoli durante la relativa pubblicazione mediante un server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], se nel database Oracle sono riportati con tali caratteri. L'utilizzo di un formato di carattere errato per gli oggetti può generare un messaggio di errore che indica che non è stato possibile reperirli.  
  
-   Il sottolinguaggio SQL di Oracle è leggermente diverso da quello di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. I filtri di riga devono essere scritti con una sintassi conforme a Oracle.  
  
### Considerazioni sugli oggetti di grandi dimensioni  
 I dati LOB (Large Object) non vengono archiviati nella tabella del log degli articoli e i relativi aggiornamenti vengono sempre recuperati direttamente dalla tabella pubblicata. Gli aggiornamenti vengono replicati in pubblicazioni transazionali solo se l'operazione che influisce sui dati LOB attiva il trigger di replica sulla tabella replicata. I trigger Oracle vengono attivati in seguito all'inserimento o all'eliminazione di righe contenenti dati LOB, ma non quando vengono aggiornate le colonne LOB. Un aggiornamento di una colonna LOB verrà replicato subito solo se nella stessa transazione Oracle viene aggiornata anche una colonna non LOB della stessa riga. In caso contrario, la colonna LOB verrà aggiornata nel Sottoscrittore al successivo aggiornamento di una colonna non LOB nella stessa riga. Verificare che questo comportamento sia accettabile per l'applicazione in uso.  
  
 Per replicare aggiornamenti di colonne LOB nelle pubblicazioni transazionali, prendere in considerazione una delle strategie seguenti durante la scrittura dell'applicazione:  
  
-   Eliminare e reinserire le righe all'interno di una transazione anziché aggiornarle. Specificare il nuovo oggetto LOB durante il reinserimento della riga. Poiché le operazioni di eliminazione e inserimento attivano entrambe i trigger, la riga verrà replicata.  
  
-   Includere una colonna non LOB nell'aggiornamento di riga oltre alla colonna LOB oppure aggiornare una colonna non LOB della riga durante la stessa transazione Oracle. In entrambi i casi, l'aggiornamento della colonna non LOB garantisce l'attivazione del trigger.  
  
 Per ulteriori informazioni sugli oggetti LOB, vedere [Mapping di tipi di dati per server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
### Indici e vincoli univoci  
 Sia per la replica snapshot che per quella transazionale, le colonne contenute in indici e vincoli univoci, inclusi i vincoli di chiave primaria, devono rispettare determinate restrizioni. Se tali restrizioni vengono violate, il vincolo o l'indice non verrà replicato.  
  
-   Il numero massimo di colonne consentite in un indice di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è pari a 16.  
  
-   Tutte le colonne incluse in vincoli univoci devono contenere tipi di dati supportati. Per ulteriori informazioni sui tipi di dati, vedere [Mapping di tipi di dati per server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
-   Tutte le colonne incluse in vincoli univoci devono essere pubblicate e non possono essere filtrate.  
  
-   Le colonne interessate da vincoli o indici univoci non devono essere null.  
  
 È inoltre consigliabile considerare quanto segue:  
  
-   Oracle e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consentono di gestire i valori NULL in modo differente. In Oracle sono supportate più righe con valori NULL per le colonne per consentono la specifica di valori NULL e sono incluse in vincoli o indici univoci. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] impone l'univocità mediante il supporto di una singola riga con un valore NULL per la stessa colonna. Non è possibile pubblicare un vincolo o un indice univoco che consente valori NULL in quanto nel Sottoscrittore si verifica una violazione di vincolo se la tabella pubblicata contiene più righe con valori NULL per una delle colonne incluse nell'indice o nel vincolo.  
  
-   Durante la verifica dell'univocità, gli spazi vuoti finali in un campo vengono ignorati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ma non in Oracle.  
  
 Come nella replica transazionale [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le tabelle delle pubblicazioni transazionali Oracle richiedono una chiave primaria che deve essere univoca in base alle regole specificate sopra. In caso contrario, non sarà possibile pubblicare la tabella per la replica transazionale.  
  
## Differenze tra il server di pubblicazione Oracle e la replica transazionale standard  
  
-   Un server di pubblicazione Oracle non può avere lo stesso nome del server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] corrispondente, dei server di pubblicazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che utilizzano il server di distribuzione o dei Sottoscrittori che ricevono la pubblicazione. Le pubblicazioni gestite dallo stesso server di distribuzione devono avere un nome univoco.  
  
-   Una tabella pubblicata in una pubblicazione Oracle non può ricevere dati replicati. La pubblicazione Oracle non supporta pertanto pubblicazioni con sottoscrizioni ad aggiornamento immediato e ad aggiornamento in coda, oppure topologie in cui le tabelle della pubblicazione fungono anche da tabelle delle sottoscrizioni, ad esempio la replica bidirezionale e peer-to-peer.  
  
-   Le relazioni tra chiave primaria e chiave esterna nel database Oracle non vengono replicate nei Sottoscrittori. Tali relazioni vengono tuttavia mantenute tra i dati via via che le modifiche vengono recapitate.  
  
-   Le pubblicazioni transazionali standard supportano tabelle contenenti fino a 1000 colonne. Le pubblicazioni transazionali Oracle supportano 995 colonne (la replica aggiunge cinque colonne a ogni tabella pubblicata).  
  
-   Le clausole COLLATE vengono aggiunte alle istruzioni CREATE TABLE per consentire confronti con distinzione tra maiuscole e minuscole, che sono importanti per le chiavi primarie e i vincoli univoci. Questo comportamento viene controllato con l'opzione dello schema 0x1000 specificata con il **@schema_option** parametro [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
-   Se si utilizzano stored procedure per configurare o gestire un server di pubblicazione Oracle, non inserire le procedure all'interno di una transazione esplicita. Questa operazione non è supportata sul server collegato utilizzato per connettersi al server di pubblicazione Oracle.  
  
-   Se si crea una sottoscrizione pull in una pubblicazione Oracle mediante una procedura guidata, è necessario utilizzare la Creazione guidata nuova sottoscrizione fornita con [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive. Per le versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è tuttavia possibile utilizzare la stored procedure e le interfacce SQL-DMO per impostare le sottoscrizioni pull nelle pubblicazioni Oracle.  
  
-   Se si utilizzano stored procedure per propagare le modifiche ai Sottoscrittori (impostazione predefinita), tenere presente che la sintassi MCALL è supportata ma presenta un comportamento differente quando la pubblicazione proviene da un server di pubblicazione Oracle. Generalmente MCALL include una bitmap in cui vengono illustrate le colonne che sono state aggiornate nel server di pubblicazione. Con una pubblicazione Oracle, la bitmap indica sempre che sono state aggiornate tutte le colonne. Per ulteriori informazioni sull'utilizzo di stored procedure, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
### Supporto della replica transazionale  
  
-   Le pubblicazioni Oracle non supportano tutte le opzioni di schema supportate nelle pubblicazioni SQL Server. Per ulteriori informazioni sulle opzioni di schema, vedere [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
-   I Sottoscrittori delle pubblicazioni Oracle non possono utilizzare le sottoscrizioni ad aggiornamento immediato o ad aggiornamento in coda né possono essere nodi in una topologia peer-to-peer o bidirezionale.  
  
-   I Sottoscrittori delle pubblicazioni Oracle non possono essere inizializzati automaticamente da un backup.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta due tipi di convalida: binaria e conteggio delle righe. I server di pubblicazione Oracle supportano la convalida mediante il conteggio delle righe. Per ulteriori informazioni, vedere [convalidare i dati replicati](../../../relational-databases/replication/validate-replicated-data.md).  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] offre due formati di snapshot: modalità bcp nativa e in modalità carattere. I server di pubblicazione Oracle supportano gli snapshot in modalità carattere.  
  
-   Le modifiche dello schema delle tabelle Oracle pubblicate non sono supportate. Per apportare tali modifiche, eliminare innanzitutto la pubblicazione, inserire le modifiche e quindi ricreare la pubblicazione e le eventuali sottoscrizioni.  
  
    > [!NOTE]  
    >  Se le modifiche dello schema e le successive operazioni di eliminazione e ricreazione della pubblicazione e delle sottoscrizioni vengono eseguite in un momento in cui non è in corso alcuna attività sulle tabelle pubblicate, è possibile specificare l'opzione relativa al supporto esclusivo della replica per le sottoscrizioni. In questo modo sarà possibile sincronizzarle senza dover copiare uno snapshot in ogni Sottoscrittore. Per ulteriori informazioni, vedere [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
### Modello di sicurezza della replica  
 Il modello di sicurezza per il server di pubblicazione Oracle è identico a quello per la replica transazionale standard, con le eccezioni seguenti:  
  
-   L'account con il quale l'agente snapshot e l'agente di lettura log effettuano la connessione dal server di distribuzione al server di pubblicazione viene specificato mediante uno dei metodi seguenti:  
  
    -   Il **@security_mode** parametro [sp_adddistpublisher & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md) (specificare inoltre i valori per **@login** e **@password** Se viene utilizzata l'autenticazione Oracle)  
  
    -   Nel **Connetti al Server** in SQL Server Management Studio, che viene utilizzato quando si configura il server di pubblicazione Oracle nella finestra di dialogo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server di distribuzione.  
  
     Nella replica transazionale standard, l'account viene specificato con [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) e [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md).  
  
-   L'account con cui l'agente Snapshot e l'agente di lettura Log effettuano connessioni non può essere modificato con [sp_changedistpublisher & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md) o tramite una proprietà può essere modificato foglio, ma la password.  
  
-   Se si specifica un valore pari a 1 (autenticazione integrata di Windows) per il **@security_mode** parametro [sp_adddistpublisher & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md):  
  
    -   L'account del processo e la password utilizzata per l'agente Snapshot e l'agente di lettura Log (il **@job_login** e **@job_password** parametri di [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) e [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)) deve essere quello utilizzato per l'account e password utilizzati per connettersi al server di pubblicazione Oracle.  
  
    -   Non è possibile modificare il **@job_login** parametro tramite [sp_changepublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md) o [sp_changelogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md), ma la password può essere modificata.  
  
 Per ulteriori informazioni sulla sicurezza della replica, vedere [sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md).  
  
## Vedere anche  
 [Considerazioni amministrative per i server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/administrative-considerations-for-oracle-publishers.md)   
 [Configurazione di un server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Panoramica della pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  