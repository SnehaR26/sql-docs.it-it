---
title: Visualizzare e leggere i file di log del programma di installazione di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying log files
- Setup [SQL Server], logs
- installation log files [SQL Server]
- installing SQL Server, logs
- errors [SQL Server], Setup
- logs [SQL Server], Setup
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 91a3f00b2aeba382b31713104839d0f2fa2d8821
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101642"
---
# <a name="view-and-read-sql-server-setup-log-files"></a>Visualizzare e leggere i file di log del programma di installazione di SQL Server
  Ogni esecuzione del programma di installazione crea file di log con una nuova cartella dei log con timestamp nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\. Il formato del nome della cartella dei log con indicazione di data e ora è AAAAMMGG_hhmmss. L'esecuzione del programma di installazione in modalità automatica determina la creazione dei file di log nel percorso % temp%\sqlsetup*.log. Tutti i file inclusi nella cartella dei log vengono archiviati nel file Log\*.cab nella rispettiva cartella dei log.  
  
 Una richiesta di installazione tipica viene eseguita in tre fasi:  
  
1.  Testo delle regole globali  
  
2.  Aggiornamento del componente  
  
3.  Azione richiesta dall'utente  
  
 In ogni fase il programma di installazione genererà log di riepilogo e dettagliati e creerà log aggiuntivi in base alle necessità. Il programma di installazione viene richiamato almeno tre volte per ogni azione di installazione richiesta dall'utente.  
  
 I file dell'archivio dati contengono uno snapshot dello stato di tutti gli oggetti di configurazione registrati dal processo di installazione e contribuiscono a risolvere i problemi relativi agli errori di configurazione. Vengono creati file di dump XML per gli oggetti dell'archivio dati per ogni fase dell'esecuzione. Questi file vengono salvati nella rispettiva sottocartella dei log sotto la cartella dei log con indicazione di data e ora, come indicato di seguito:  
  
-   Datastore_GlobalRules  
  
-   Datastore_ComponentUpdated  
  
-   Datastore  
  
 Nelle sezioni seguenti vengono illustrati i file di log del programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="summary-text"></a>Testo di riepilogo  
  
### <a name="overview"></a>Panoramica  
 Nel file sono indicati i componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rilevati durante l'installazione, l'ambiente del sistema operativo, i valori dei parametri della riga di comando eventualmente specificati e lo stato globale di ogni MSI/MSP eseguito.  
  
 Il log è organizzato nelle sezioni seguenti:  
  
-   Riepilogo globale dell'esecuzione.  
  
-   Proprietà e configurazione del computer in cui è stato eseguito il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzionalità del prodotto installate in precedenza nel computer  
  
-   Descrizione delle proprietà relative alla versione dell'installazione e al pacchetto di installazione.  
  
-   Impostazioni di input al runtime fornite durante l'installazione.  
  
-   Percorso del file di configurazione.  
  
-   Dettagli dei risultati di esecuzione.  
  
-   Regole globali.  
  
-   Regole specifiche per lo scenario di installazione.  
  
-   Regole non riuscite.  
  
-   Percorso del file di report delle regole.  
  
### <a name="location"></a>Percorso  
 Si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.  
  
 Per individuare gli errori nel file del testo di riepilogo, eseguire una ricerca nel file utilizzando le parole chiave "error" o "failed".  
  
## <a name="summaryengine-baseyyyymmddhhmmsstxt"></a>Summary_engine-base_AAAAMMGG_HHMMss.txt  
  
### <a name="overview"></a>Panoramica  
 Il file di base summary_engine è simile al file di riepilogo e viene generato durante il flusso di lavoro principale.  
  
### <a name="location"></a>Percorso  
 Si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
## <a name="summaryengine-baseyyyymmddhhmmsscomponentupdatetxt"></a>Summary_engine-base_AAAAMMGG_HHMMss_ComponentUpdate.txt  
  
### <a name="overview"></a>Panoramica  
 Il file di log di riepilogo relativo all'aggiornamento del componente è simile al file di riepilogo e viene generato durante il flusso di lavoro di aggiornamento del componente.  
  
### <a name="location"></a>Percorso  
 Si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
## <a name="summaryengine-baseversionnumbermmddhhmmssglobalrulestxt"></a>Summary_engine-base_\<VersionNumber>MMDD_HHMMss_GlobalRules.txt  
  
### <a name="overview"></a>Panoramica  
 Il file di log di riepilogo relativo alle regole globali è simile al file di riepilogo e viene generato durante il flusso di lavoro delle regole globali.  
  
### <a name="location"></a>Percorso  
 Si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
## <a name="detailtxt"></a>Detail.txt  
  
### <a name="overview"></a>Panoramica  
 Il file Detail.txt viene generato per il flusso di lavoro principale, ad esempio installazione o aggiornamento, e fornisce i dettagli dell'esecuzione. Le registrazioni presenti nel file vengono generate in base al momento in cui viene richiamata ogni azione dell'installazione e indicano l'ordine in cui le azioni sono state eseguite, nonché le relative dipendenze.  
  
### <a name="location"></a>Percorso  
 Si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup  
  
 Bootstrap\Log\\<AAAAMMGG_HHMM>\Detail.txt.  
  
 Se si verifica un errore durante il processo di installazione, l'eccezione o l'errore verrà registrato alla fine di questo file. Per individuare gli errori in questo file, esaminare innanzitutto la parte finale del file, quindi eseguire una ricerca nel file delle parole chiave "error" o "exception".  
  
## <a name="detailcomponentupdatetxt"></a>Detail_ComponentUpdate.txt  
  
### <a name="overview"></a>Panoramica  
 Il file Detail_ComponentUpdate.txt viene generato per il flusso di lavoro di aggiornamento del componente ed è simile al file Detail.txt.  
  
### <a name="location"></a>Percorso  
 Si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
## <a name="detailglobalrulestxt"></a>Detail_GlobalRules.txt  
  
### <a name="overview"></a>Panoramica  
 Il file Detail_GlobalRules.txt viene generato per l'esecuzione delle regole globali ed è simile al file Detail.txt.  
  
### <a name="location"></a>Percorso  
 Si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
## <a name="msi-log-files"></a>File di log MSI  
  
### <a name="overview"></a>Panoramica  
 I file di log MSI forniscono dettagli sul processo del pacchetto di installazione. Vengono generati da MSIEXEC durante l'installazione del pacchetto specificato.  
  
 Tipi di file di log MSI:  
  
-   \<Funzionalità>_\<Architettura>\_\<Interazione>.log  
  
-   \<Funzionalità>_\<Architettura>\_\<Linguaggio>\_\<Interazione>.log  
  
-   \<Funzionalità>_\<Architettura>\_\<Interazione>\_\<flusso di lavoro.log  
  
### <a name="location"></a>Percorso  
 I file di log MSI si trovano nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm > \\\< nome\>. log.  
  
 Nella parte finale del file è incluso un riepilogo dell'esecuzione in cui sono indicati lo stato riuscito o non riuscito e le proprietà. Per individuare l'errore nel file MSI, eseguire la ricerca di "value 3", poiché gli errori si trovano in genere in prossimità di tale stringa.  
  
## <a name="configurationfileini"></a>ConfigurationFile.ini  
  
### <a name="overview"></a>Panoramica  
 Il file di configurazione contiene le impostazioni di input fornite durante l'installazione. Può essere utile riavviare l'installazione senza dover immettere manualmente le impostazioni. Nel file di configurazione non vengono tuttavia salvati le password degli account, i PID e alcuni parametri. Le impostazioni possono essere aggiunte al file o specificate tramite una riga di comando o l'interfaccia utente del programma di installazione. Per altre informazioni, vedere [installare SQL Server 2014 tramite un File di configurazione](install-sql-server-using-a-configuration-file.md).  
  
### <a name="location"></a>Percorso  
 Si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
## <a name="systemconfigurationcheckreporthtm"></a>SystemConfigurationCheck_Report.htm  
  
### <a name="overview"></a>Panoramica  
 Il report di controllo della configurazione di sistema contiene una breve descrizione di ogni regola eseguita, nonché lo stato di esecuzione.  
  
### <a name="location"></a>Percorso  
 Si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure di installazione](../../sql-server/install/installation-how-to-topics.md)   
 [Installare SQL Server 2014](install-sql-server.md)  
  
  
