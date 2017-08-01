---
title: "Edizioni e funzionalità supportate di SQL Server 2017 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
- SQL2017_New_Updated
ms.date: 07/14/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Enterprise Edition [SQL Server]
- Developer Edition [SQL Server]
- 32-bit vs. 64-bit editions [SQL Server]
- default components
- Workgroup Edition [SQL Server]
- Internet servers [SQL Server]
- installing SQL Server, components
- Setup [SQL Server], components
- SQL Server, editions
- SQL Server, components
- client/server applications [SQL Server]
- editions [SQL Server]
- versions [SQL Server]
- Setup [SQL Server], editions
- SQL Server Installation Wizard
- components [SQL Server]
- Standard Edition [SQL Server]
- 64-bit edition [SQL Server]
- IIS [SQL Server]
- installing SQL Server, editions
- editions [SQL Server], about edition options
- Setup [SQL Server]
ms.assetid: 
caps.latest.revision: 121
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 6aa73e749d4f308265dfe27a160802c15a391a3e
ms.openlocfilehash: 6c17972f863043a53bf60b6c814aaac0c3c38d51
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="editions-and-supported-features-of-sql-server-2017"></a>Edizioni e funzionalità supportate di SQL Server 2017

<!---[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]--->

Questo argomento offre informazioni dettagliate sulle funzionalità supportate dalle diverse edizioni di SQL Server 2017. 

Per informazioni sulle versioni precedenti, vedere:

* [SQL Server 2016](editions-and-components-of-sql-server-2016.md).  
* [SQL Server 2014](http://msdn.microsoft.com/library/cc645993(v=sql.120).aspx).

>[!NOTE]
>Tutte le informazioni in questo articolo sono soggette a modifiche poiché si applicano a una versione preliminare di SQL Server 2017. 
  
I requisiti di installazione variano in base alle esigenze dell'applicazione. Le diverse edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] consentono di soddisfare le esigenze specifiche di utenti e organizzazioni in termini di prezzo, esecuzione e prestazioni. I componenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installati dipendono inoltre dai requisiti specifici. Nelle sezioni seguenti vengono fornite tutte le informazioni necessarie per adottare la scelta migliore tra le edizioni e i componenti disponibili in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  

SQL Server Evaluation Edition è disponibile per un periodo di valutazione di 180 giorni.  
  
Per le note sulla versione più recenti e informazioni sulle novità, vedere quanto segue:
- [Note sulla versione di SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)
- [Novità di SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)

### <a name="try-sql-server"></a>Provare SQL Server.    
    
> [![Download da Evaluation Center](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2017-ctp/) **[Download di SQL Server 2017 CTP da Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-ctp/)**    

<!---    
> ![Azure Virtual Machine small](../analysis-services/media/azure-virtual-machine-small.png) **[Spin up a Virtual Machine with SQL Server 2016 already installed](https://azuremarketplace.microsoft.com/marketplace/apps/Microsoft.SQL2016SP1-WS2016?tab=Overview?wt.mc_id=sqL16_vm)**   
--->

## <a name="includessnoversionincludesssnoversion-mdmd-editions"></a>Edizioni di [!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)]  
 La tabella seguente descrive tali edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 
  
|Edizione di[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] |Definizione|  
|---------------------------------------|----------------|  
|Enterprise|L'offerta Premium, [!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Enterprise Edition offre le funzionalità complete dei centri dati di fascia alta con prestazioni velocissime, virtualizzazione illimitata e Business Intelligence end-to-end, abilitando livelli di servizio elevati per carichi di lavoro di importanza critica e l'accesso dell'utente finale per la comprensione dei dati.|  
|Standard|L'edizione[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Standard offre un database di gestione dati e di Business Intelligence di base per l'esecuzione di applicazioni per reparti e piccole organizzazioni e supporta gli strumenti di sviluppo comuni locali e per cloud, abilitando una gestione efficace del database con risorse IT minime.|  
|Web|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Web Edition costituisce un'opzione con un costo totale di proprietà ridotto per provider di servizi di hosting Web e VAP Web, offrendo funzionalità di scalabilità, convenienza e facilità di gestione per proprietà Web di ogni dimensione.|  
|Sviluppatore|L'edizione[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Developer consente agli sviluppatori di compilare qualsiasi tipo di applicazione in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Benché includa tutte le funzionalità dell'edizione Enterprise, ne è consentito l'utilizzo solo come sistema di sviluppo e di prova e non come server di produzione. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Developer rappresenta la scelta ideale per chi vuole compilare<br />                e testare applicazioni[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] .|  
|Edizioni Express|L'edizione Express è un database di base gratuito, ideale per l'apprendimento e la compilazione di applicazioni basate sui dati desktop e server di piccole dimensioni. Questa edizione costituisce la scelta ottimale per fornitori di software indipendenti, sviluppatori e sviluppatori amatoriali di applicazioni client. Se sono necessarie funzionalità di database più avanzate, è possibile aggiornare facilmente [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express a versioni di fascia superiore di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express LocalDB, una versione leggera di Express che, pur includendone tutte le funzionalità di programmazione, viene eseguita in modalità utente e prevede un'installazione veloce senza operazioni di configurazione, nonché un elenco ridotto di prerequisiti.|  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-an-internet-server"></a>Utilizzo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con un server Internet  
 In un server Internet, ad esempio un server in cui viene eseguito Internet Information Services (IIS), vengono in genere installati gli strumenti client di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Gli strumenti client includono i componenti di connettività client utilizzati dalle applicazioni per la connessione a un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
>[!NOTE]
>Benché sia possibile installare un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nello stesso computer in cui è in esecuzione IIS, si tratta in genere di una configurazione utilizzata solo per siti Web di piccole dimensioni che dispongono di un singolo computer server. Nella maggior parte dei siti Web, i sistemi IIS di livello intermedio risiedono in un server o in un cluster di server, mentre i database corrispondenti si trovano in un server separato o in una federazione di server.  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-clientserver-applications"></a>Uso di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con applicazioni client/server  
 È possibile installare solo i componenti client di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in un computer in cui vengono eseguite applicazioni client/server connesse direttamente a un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. L'installazione di componenti client rappresenta una scelta ottimale anche se si amministra un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in un server di database o se si prevede di sviluppare applicazioni basate su [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 La scelta degli strumenti client comporta l'installazione delle seguenti funzionalità [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] : componenti per la compatibilità con le versioni precedenti, [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], componenti di connettività, strumenti di gestione, Software Development Kit e componenti della documentazione online di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Per ulteriori informazioni, vedere [installazione di SQL Server](../database-engine/install-windows/install-sql-server.md).  
  
## <a name="deciding-among-includessnoversionincludesssnoversion-mdmd-components"></a>Scelta dei componenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
 Per selezionare i componenti da includere in un'installazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , utilizzare la pagina di selezione delle funzionalità dell'Installazione guidata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Per impostazione predefinita, non è selezionata alcuna funzionalità inclusa nell'albero.  
  
 Utilizzare le informazioni incluse nelle tabelle seguenti per determinare il set di funzionalità più adatto per le proprie esigenze.  
  
|Componenti server|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] include [!INCLUDE[ssDE](../includes/ssde-md.md)]il motore di database, cioè il servizio di base per l'archiviazione, l'elaborazione e la sicurezza dei dati, la replica, la ricerca full-text, gli strumenti per la gestione di dati XML e relazionali, l'integrazione analitica nel database e l'integrazione PolyBase per l'accesso ad Hadoop e ad altre origini di dati eterogenee, e il server [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] include gli strumenti per la creazione e la gestione delle applicazioni di data mining e Online Analytical Processing (OLAP).|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|In[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sono inclusi componenti client e server per la creazione, la gestione e la distribuzione di report tabulari, matrice, grafici e in formato libero. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] è inoltre una piattaforma estendibile che consente di sviluppare applicazioni di creazione di report.|  
|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è un set di strumenti grafici e oggetti programmabili per lo spostamento, la copia e la trasformazione di dati. È incluso, inoltre, il componente [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) per [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) è la soluzione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per la gestione dei dati master. MDS può essere configurato per gestire qualsiasi dominio (prodotti, clienti, account) e può includere gerarchie, sicurezza granulare, transazioni, controllo delle versioni dei dati e regole business e un [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] che può essere utilizzato per gestire dati.|  
|Machine Learning Services (In-Database)|Machine Learning Services (In-Database) supporta soluzioni di Machine Learning distribuite e scalabili che usano origini dati aziendali. In SQL Server 2016 era supportato il linguaggio R. SQL Server 2017 supporta R e Python.|
|Machine Learning Server (Standalone)|Machine Learning Server (Standalone) supporta la distribuzione di soluzioni di Machine Learning distribuite e scalabili su più piattaforme che usano origini dati aziendali, inclusi Linux, Hadoop e Teradata. In SQL Server 2016 era supportato il linguaggio R. SQL Server 2017 supporta R e Python.|

  
|Strumenti di gestione|Description|  
|----------------------|-----------------|  
|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] è un ambiente integrato per l'accesso, la configurazione, la gestione, l'amministrazione e lo sviluppo di componenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] consente a sviluppatori e amministratori con qualsiasi livello di esperienza di utilizzare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].<br /><br /> Scaricare e installare <br />                [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] da  [Scaricare SQL Server Management Studio](http://msdn.microsoft.com/library/mt238290.aspx)|  
|Gestione configurazione[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] |Gestione configurazione[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] offre funzionalità di base per la gestione della configurazione dei servizi di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , dei protocolli server, dei protocolli client e degli alias per i client.|  
|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] offre un'interfaccia utente grafica per il monitoraggio di un'istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)] o di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|Ottimizzazione guidata[!INCLUDE[ssDE](../includes/ssde-md.md)] |Ottimizzazione guidata[!INCLUDE[ssDE](../includes/ssde-md.md)] consente di creare set di indici, viste indicizzate e partizioni ottimali.|  
|Client Data Quality|Fornisce un'interfaccia utente grafica estremamente intuitiva e semplice per la connessione al server DQS e per eseguire operazioni di pulizia dei dati. Consente inoltre di monitorare centralmente le varie attività eseguite durante l'operazione di pulizia dei dati.|  
|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]|In[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] è disponibile un IDE per la compilazione di soluzioni per i componenti di Business Intelligence: [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]e [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].<br /><br /> (in precedenza denominato Business Intelligence Development Studio).<br /><br /> In[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] è inoltre incluso un ambiente integrato che consente agli sviluppatori di database di svolgere tutte le attività di progettazione di database per qualsiasi piattaforma [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , locale e non, all'interno di Visual Studio. Gli sviluppatori di database possono utilizzare le funzionalità avanzate di Esplora server in Visual Studio per creare o modificare facilmente dati e oggetti di database oppure eseguire query.|  
|Componenti di connettività|Consente di installare i componenti per la comunicazione tra client e server nonché le librerie di rete per DB-Library, ODBC e OLE DB.|  
  
|Documentazione|Description|  
|-------------------|-----------------|  
|Documentazione online di[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] |Documentazione principale di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].| 

**Edizioni Developer ed Evaluation**  
Per le funzionalità supportate dalle edizioni Developer ed Evaluation, vedere le funzionalità elencate per SQL Server Enterprise Edition nelle tabelle seguenti.

L'edizione Developer continua a supportare solo 1 client per [SQL Server Distributed Replay](../tools/distributed-replay/sql-server-distributed-replay.md). 
  
##  <a name="Cross-BoxScaleLimits"></a> Limiti di scalabilità  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|
|Capacità di calcolo massima usata da una singola istanza - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|valore massimo del sistema operativo|Limitato a meno di 4 socket o 24 core|Limitato a meno di 4 socket o 16 core|Limitato a meno di 1 socket o 4 core|Limitato a meno di 1 socket o 4 core| 
|Capacità di calcolo massima usata da una singola istanza - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] oppure [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|valore massimo del sistema operativo|Limitato a meno di 4 socket o 24 core|Limitato a meno di 4 socket o 16 core|Limitato a meno di 1 socket o 4 core|Limitato a meno di 1 socket o 4 core|  
|Memoria massima per il pool di buffer per ogni istanza di [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|valore massimo del sistema operativo|128 GB|64 GB|1410 MB|1410 MB|
|Memoria massima per la cache dei segmenti Columnstore per ogni istanza di [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Memoria illimitata| 32 GB| 16 GB| 352 MB| 352 MB|  
|Dimensione massima dati con ottimizzazione per la memoria per ogni database in [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Memoria illimitata| 32 GB| 16 GB| 352 MB| 352 MB|  
|Memoria massima usata per ogni istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|valore massimo del sistema operativo|Tabella: 16 GB<br /><br /> MOLAP: 64 GB|N/D|N/D|N/D|  
|Memoria massima usata per ogni istanza di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|valore massimo del sistema operativo|64 GB|64 GB|4 GB|N/D|
|Dimensione massima del database relazionale|524 PB|524 PB|524 PB|10 GB|10 GB|  
  
<sup>1</sup> La licenza basata su Enterprise Edition con Server + Licenza CAL (Client Access License), non disponibile per nuovi contratti, è limitata a un massimo di 20 core per istanza di SQL Server. Non sono previsti limiti nel modello di licenza server basato su core. Per altre informazioni, vedere [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
 
##  <a name="RDBMSHA"></a> Disponibilità elevata RDBMS  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Supporto di Server Core <sup>1</sup>|Sì|Sì|Sì|Sì|Sì|  
|Log shipping|Sì|Sì|Sì|No|No|  
|Mirroring del database|Sì|Sì<br /><br /> Solo modalità di protezione Full|Solo server di controllo|Solo server di controllo|Solo server di controllo| 
|Compressione backup|Sì|Sì|No|No|No| 
|Snapshot del database|Sì|Sì|Sì|Sì|Sì|
|Istanze del cluster di failover Always On|Sì<br /><br /> Il numero di nodi è il valore massimo del sistema operativo|Sì<br /><br /> Supporto per 2 nodi|No|No|No|  
|Gruppi di disponibilità Always On|Sì<br /><br /> Fino a 8 repliche secondarie, incluse 2 repliche secondarie sincrone|No|No|No|No|
|Gruppi di disponibilità di base <sup>2</sup>|No|Sì<br /><br /> Supporto per 2 nodi|No|No|No|
|Ripristino di pagine e file online|Sì|No|No|No|No|
|Indicizzazione online|Sì|No|No|No|No|
|Ricompilazioni dell'indice online ripristinabili|Sì|No|No|No|No|
|Modifica dello schema online|Sì|No|No|No|No|
|Recupero rapido|Sì|No|No|No|No|
|Backup con mirroring|Sì|No|No|No|No|
|Aggiunta di memoria a caldo e CPU|Sì|No|No|No|No|
|Database Recovery Advisor|Sì|Sì|Sì|Sì|Sì|
|Backup crittografato|Sì|Sì|No|No|No|
|Backup ibrido in Microsoft Azure (backup nell'URL)|Sì|Sì|No|No|No|
|Gruppo di disponibilità senza cluster|Sì|Sì|Sì|No|No|No|
|Gruppo di disponibilità con commit di un numero minimo di repliche|Sì|Sì|Sì|No|No|No|
  
 <sup>1</sup> per ulteriori informazioni sull'installazione di SQL Server in Server Core, vedere [installazione di SQL Server in Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md). 

<sup>2</sup> Per altre informazioni sui gruppi di disponibilità di base, vedere [Gruppi di disponibilità di base](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md).  

##  <a name="RDBMSSP"></a> Scalabilità e prestazioni RDBMS  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Columnstore <sup>1</sup>|Sì|Sì|Sì|Sì|Sì|  
|File binari di oggetti di grandi dimensioni in indici columnstore cluster|Sì|Sì|Sì|Sì|Sì|  
|Ricompilazione dell'indice columnstore non cluster online|Sì|No|No|No|No|
|OLTP in memoria <sup>1</sup>|Sì|Sì|Sì|Sì, <sup>2</sup>|Sì|
|Estensione database|Sì|Sì|Sì|Sì|Sì|
|Memoria principale persistente|Sì|Sì|Sì|Sì|Sì|
|Supporto di più istanze|50|50|50|50|50|
|Partizionamento di tabelle e indici|Sì|Sì|Sì|Sì|Sì|  
|Compressione dati|Sì|Sì|Sì|Sì|Sì|
|Resource Governor|Sì|No|No|No|No|  
|Parallelismo della tabella partizionata|Sì|No|No|No|No|
|Più contenitori Filestream|Sì|Sì|Sì|Sì|Sì|
|Allocazione di una matrice di buffer e di memoria in pagine grandi con supporto NUMA|Sì|No|No|No|No|
|Estensione pool di buffer|Sì|Sì|No|No|No|
|Governance delle risorse di I/O|Sì|No|No|No|No|  
|Durabilità posticipata|Sì|Sì|Sì|Sì|Sì|
|Ottimizzazione automatica|Sì|No|No|No|No|
|Join adattivi in modalità batch|Sì|No|No|No|No|
|Commenti della concessione di memoria batch|Sì|No|No|No|No|
|Miglioramenti dell'inserimento bulk|Sì|Sì|Sì|Sì|Sì|


<sup>1</sup> Le dimensioni dati OLTP in memoria e la cache dei segmenti Columnstore sono limitate alla quantità di memoria specificata dall'edizione nella sezione Limiti di scalabilità. I gradi di parallelismo (DOP) massimi sono limitati. I gradi di parallelismo del processo (DOP) per una compilazione indice sono limitati a 2 DOP per l'edizione Standard e 1 DOP per le edizioni Web ed Express. Questo si riferisce agli indici columnstore creati tramite le tabelle basate su disco e le tabelle con ottimizzazione per la memoria.

<sup>2</sup> Questa funzionalità non è inclusa nell'opzione di installazione LocalDB.

##  <a name="RDBMSS"></a> Sicurezza RDBMS  
  
|Funzionalità|Enterprise|Standard|Web|Express|Express with Advanced Services|  
|-------------|----------------|--------------|---------|-------------|------------------------------------| 
|Sicurezza a livello di riga|Sì|Sì|Sì|Sì|Sì|  
|Crittografia sempre attiva|Sì|Sì|Sì|Sì|Sì| 
|Mascheramento dati dinamici|Sì|Sì|Sì|Sì|Sì|   
|Controllo di base|Sì|Sì|Sì|Sì|Sì| 
|Controllo con granularità fine|Sì|Sì|Sì|Sì|Sì| 
|Crittografia trasparente del database|Sì|No|No|No|No|   
|Extensible Key Management|Sì|No|No|No|No| 
|Ruoli definiti dall'utente|Sì|Sì|Sì|Sì|Sì| 
|Database indipendenti|Sì|Sì|Sì|Sì|Sì| 
|Crittografia per backup|Sì|Sì|No|No|No|  

##  <a name="Replication"></a> Replica  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Sottoscrittori eterogenei|Sì|Sì|No|No|No|  
|Replica di tipo merge|Sì|Sì|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|   
|Pubblicazione Oracle|Sì|No|No|No|No| 
|Replica transazionale peer-to-peer|Sì|No|No|No|No|   
|Replica snapshot|Sì|Sì|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|   
|Rilevamento delle modifiche in SQL Server|Sì|Sì|Sì|Sì|Sì| 
|Replica transazionale|Sì|Sì|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|   
|Replica transazionale in Azure|Sì|Sì|No|No|No|   
|Sottoscrizione aggiornabile con replica transazionale|Sì|No|No|No|No|  
  
##  <a name="SSMS"></a> Strumenti di gestione  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SMO (SQL Management Objects)|Sì|Sì|Sì|Sì|Sì|  
|Gestione configurazione SQL Server|Sì|Sì|Sì|Sì|Sì|   
|CMD SQL (strumento da riga di comando)|Sì|Sì|Sì|Sì|Sì|      
|Riesecuzione distribuita - Strumento di amministrazione|Sì|Sì|Sì|Sì|No|  
|Riesecuzione distribuita - Client|Sì|Sì|Sì|No|No|  
|Distributed Replay - Controller|Sì (fino a 16 client)|Sì (1 client)|Sì (1 client)|No|No|   
|SQL Profiler|Sì|Sì|No <sup>1</sup>|No <sup>1</sup>|No <sup>1</sup>|  
|SQL Server Agent|Sì|Sì|Sì|No|No| 
|Management Pack di Microsoft System Center Operations Manager|Sì|Sì|Sì|No|No|  
|Ottimizzazione guidata motore di database (DTA)|Sì|Sì <sup>2</sup>|Sì <sup>2</sup>|No|No|      
  
 <sup>1</sup> È possibile eseguire il profiling di SQL Server Web, SQL Server Express, SQL Server Express with Tools ed SQL Server Express with Advanced Services usando le edizioni SQL Server Standard ed SQL Server Enterprise Edition.  
  
 <sup>2</sup> Ottimizzazione abilitata solo sulle funzionalità dell'edizione Standard.  
  
##  <a name="RDBMSM"></a> Gestibilità RDBMS  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Istanze utente|No|No|No|Sì|Sì| 
|Database locale|No|No|No|Sì|No| 
|Connessione amministrativa dedicata|Sì|Sì|Sì|Sì, con flag di traccia|Sì, con flag di traccia|   
|Supporto per script di PowerShell|Sì|Sì|Sì|Sì|Sì| 
|Supporto SysPrep <sup>1</sup>|Sì|Sì|Sì|Sì|Sì| 
|Supporto per le operazioni del componente dell'applicazione livello dati (DAC) - estrazione, distribuzione, aggiornamento, eliminazione|Sì|Sì|Sì|Sì|Sì| 
|Automazione dei criteri (controllo pianificato e modifica)|Sì|Sì|Sì|No|No|   
|Agente di raccolta dati relativi alle prestazioni|Sì|Sì|Sì|No|No| 
|Possibilità di registrarsi come un'istanza gestita in una gestione a più istanze|Sì|Sì|Sì|No|No|   
|Report di prestazioni standard|Sì|Sì|Sì|No|No| 
|Guide di piano e blocco del piano per le guide di piano|Sì|Sì|Sì|No|No|   
|Query diretta di viste indicizzate (tramite hint NOEXPAND)|Sì|Sì|Sì|Sì|Sì| 
|Gestione automatica viste indicizzate|Sì|Sì|Sì|No|No| 
|Viste partizionate distribuite|Sì|No|No|No|No| 
|Operazioni indicizzate parallele|Sì|No|No|No|No|  
|Utilizzo automatico di viste indicizzate da Query Optimizer|Sì|No|No|No|No| 
|Verifica di coerenza parallela|Sì|No|No|No|No| 
|Punto di controllo dell'Utilità SQL Server|Sì|No|No|No|No|    
|Estensione pool di buffer|Sì|Sì|No|No|No| 
  
 <sup>1</sup> Per altre informazioni, vedere [Considerazioni sull'installazione di SQL Server tramite SysPrep](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
 
##  <a name="DevTools"></a> Strumenti di sviluppo  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Integrazione con Microsoft Visual Studio|Sì|Sì|Sì|Sì|Sì| 
|Intellisense (Transact-SQL e MDX)|Sì|Sì|Sì|Sì|Sì| 
|SQL Server Data Tools (SSDT)|Sì|Sì|Sì|Sì|No|    
|Strumenti di progettazione, debug e modifica MDX|Sì|Sì|No|No|No|   
  
##  <a name="Programmability"></a> Programmability  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Integrazione di R di base|Sì|Sì|Sì|Sì|No|   
|Integrazione di R avanzato|Sì|No|No|No|No| 
|Integrazione di Python di base|Sì|Sì|Sì|Sì|No|
|Integrazione di Python avanzata|Sì|No|No|No|No| 
|Machine Learning Server (Standalone)|Sì|No|No|No|No|   
|Nodo di calcolo Polybase|Sì|Sì <sup>1</sup>|Sì <sup>1</sup>, <sup>2</sup>|Sì <sup>1</sup>,|Sì <sup>1</sup>, | 
|Nodo head Polybase|Sì|No|No|No|No| 
|JSON|Sì|Sì|Sì|Sì|Sì|   
|Archivio query|Sì|Sì|Sì|Sì|Sì|   
|Temporale|Sì|Sì|Sì|Sì|Sì|   
|Integrazione con Common Language Runtime (CLR)|Sì|Sì|Sì|Sì|Sì|   
|Supporto XML nativo|Sì|Sì|Sì|Sì|Sì| 
|Indicizzazione XML|Sì|Sì|Sì|Sì|Sì| 
|Funzionalità MERGE e UPSERT|Sì|Sì|Sì|Sì|Sì|   
|Supporto FILESTREAM|Sì|Sì|Sì|Sì|Sì| 
|FileTable|Sì|Sì|Sì|Sì|Sì| 
|Tipi di dati data e ora|Sì|Sì|Sì|Sì|Sì|  
|Supporto di internazionalizzazione|Sì|Sì|Sì|Sì|Sì| 
|Ricerca full-text e semantica|Sì|Sì|Sì|Sì|No| 
|Impostazione della lingua nelle query|Sì|Sì|Sì|Sì|No|   
|Service Broker (messaggistica)|Sì|Sì|No (solo client)|No (solo client)|No (solo client)|   
|Transact-SQL - endpoint|Sì|Sì|Sì|No|No| 
|Grafico|Sì|Sì|Sì|Sì|Sì|  


<sup>1</sup> La scalabilità orizzontale con più nodi di calcolo richiede un nodo head.

## <a name="IS"></a> Integration Services

Per informazioni sulle funzionalità di Integration Services (SSIS) supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)], vedere [Integration Services Features Supported by the Editions of SQL Server](../integration-services/integration-services-features-supported-by-the-editions-of-sql-server.md) (Funzionalità di Integration Services supportate dalle edizioni di SQL Server).

##  <a name="MDS"></a> Master Data Services  
 Per informazioni di [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] e Data Quality Services funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)], vedere [Master Data Services e Data Quality Services funzionalità supportate dalle edizioni di SQL Server](../master-data-services/master-data-services-and-data-quality-services-features-support.md). 

  
##  <a name="DW"></a> Data warehouse  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Creazione di cubi senza database|Sì|Sì|No|No|No |   
|Generazione automatica dello schema della gestione temporanea e del data warehouse|Sì|Sì|No|No|No| 
|Change Data Capture|Sì|Sì|No|No|No| 
|Ottimizzazione query join a stella|Sì|No|No|No|No| 
|Configurazione scalabile di Analysis Services di sola lettura|Sì|No|No|No|No| 
|Elaborazione di query parallela su tabelle e indici partizionati|Sì|No|No|No|No|   
|Aggregazione batch globale|Sì|No|No|No|No| 

##  <a name="SSAS"></a> Analysis Services  
  
Per informazioni sulle funzionalità di Analysis Services supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)], vedere [Analysis Services funzionalità supportate dalle edizioni di SQL Server](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md). 
  
##  <a name="BIMD"></a> BI Semantic Model (multidimensionale)  
  
Per informazioni sulle funzionalità di Analysis Services supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)], vedere [Analysis Services funzionalità supportate dalle edizioni di SQL Server](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
   
##  <a name="BIT"></a> BI Semantic Model (tabulare)  
  
Per informazioni sulle funzionalità di Analysis Services supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)], vedere [Analysis Services funzionalità supportate dalle edizioni di SQL Server](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="PPSP"></a> Power Pivot for SharePoint  
  
Per informazioni su Power Pivot per le caratteristiche di SharePoint supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)], vedere [Analysis Services funzionalità supportate dalle edizioni di SQL Server](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="DM"></a> Data mining  
  
Per informazioni sulle funzionalità di Data Mining supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)], vedere [Analysis Services funzionalità supportate dalle edizioni di SQL Server](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="SSRS"></a> Reporting Services  
  
Per informazioni sulle funzionalità di Reporting Services supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)], vedere [Reporting Services funzionalità supportate dalle edizioni di SQL Server](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md).

##  <a name="BIC"></a> Client di business intelligence  

Per informazioni sulle funzionalità di Business Intelligence Client supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)], vedere [Analysis Services funzionalità supportate dalle edizioni di SQL Server](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) o [Reporting Services funzionalità supportate dalle edizioni di SQL Server](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="SLS"></a> Servizi spaziali e basati sulla posizione  
  
|Nome funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|Indici spaziali|Sì|Sì|Sì|Sì|Sì|   
|Tipi di dati planari e geodetici|Sì|Sì|Sì|Sì|Sì| 
|Librerie spaziali avanzate|Sì|Sì|Sì|Sì|Sì|   
|Importazione/esportazione di formati di dati spaziali standard del settore|Sì|Sì|Sì|Sì|Sì|   
  
##  <a name="ADS"></a> Servizi di database aggiuntivi  
  
|Nome funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------| 
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|Sì|Sì|Sì|Sì|Sì|   
|Posta elettronica database|Sì|Sì|Sì|No|No| 
  
##  <a name="Other"></a> Altri componenti  
  
|Nome funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------|  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|No|No| 
|StreamInsight HA|StreamInsight Premium Edition|No|No|No|No|   
  
> [![Download di SSMS](../analysis-services/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[Scaricare la versione più recente di SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**    
  
## <a name="next-steps"></a>Passaggi successivi 
 [Specifiche del prodotto per SQL Server](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)   
 [Installazione per SQL Server](../database-engine/install-windows/installation-for-sql-server-2016.md)  
 
  
  
