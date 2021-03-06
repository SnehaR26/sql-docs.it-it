---
title: Servizi di Data Mining e origini dati | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: b26fd6e3-7d87-4f66-ab47-5303b51b87da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0f74492fc0d177ba87fe29dc73a5cd67e9663a61
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090971"
---
# <a name="data-mining-services-and-data-sources"></a>Servizi di data mining e origini dati
  Il data mining richiede una connessione a un'istanza di SQL Server Analysis Services. I dati di un cubo non sono necessari per il data mining, pertanto è consigliabile l'uso di origini relazionali. Tuttavia, il data mining usa i componenti forniti dal motore di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 In questo argomento vengono fornite informazioni necessarie per la connessione a un'istanza di SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per creare, elaborare, distribuire modelli di data mining o eseguire query su di essi.  
  
## <a name="data-mining-services"></a>Servizi di data mining  
 Il componente server di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è l'applicazione msmdsrv.exe, che viene in genere eseguita come servizio Windows. Questa applicazione è costituita da componenti di sicurezza, un componente listener XML for Analysis (XMLA), un componente di elaborazione delle query e numerosi altri componenti interni che svolgono le funzioni seguenti:  
  
-   Analisi di istruzioni ricevute dai client  
  
-   Gestione di metadati  
  
-   Gestione di transazioni  
  
-   Elaborazione di calcoli  
  
-   Archiviazione di dati relativi a dimensioni e celle  
  
-   Creazione di aggregazioni  
  
-   Pianificazione di query  
  
-   Memorizzazione di oggetti nella cache  
  
-   Gestione di risorse del server  
  
### <a name="xmla-listener"></a>Listener XMLA  
 Il componente listener XMLA gestisce tutte le comunicazioni XMLA tra [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e i relativi client. È possibile utilizzare l'impostazione di configurazione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `Port` nel file msmdsrv.ini per specificare la porta su cui è in ascolto un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Un valore 0 in questo file indica che [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è in ascolto sulla porta predefinita. Se non specificato diversamente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] userà le porte TCP predefinite seguenti:  
  
|Port|Description|  
|----------|-----------------|  
|2383|Istanza predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|2382|Redirector per altre istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|Assegnata dinamicamente all'avvio del server|Istanza denominata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
 Per altre informazioni sul controllo delle porte usate da questo servizio, vedere [Configurare Windows Firewall per consentire l'accesso ad Analysis Services](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
## <a name="connecting-to-data-sources"></a>Connessione a origini dati  
 Ogni volta che si crea o si aggiorna una struttura o un modello di data mining, vengono utilizzati i dati definiti da un'origine dati. Nell'origine dati non sono contenuti i dati, che potrebbero includere cartelle di lavoro di Excel, file di testo e database SQL Server, ma vengono definite solo le informazioni di connessione.  Una vista origine dati (DSV) può essere utilizzata come un livello di astrazione su quell'origine, modificando o eseguendo il mapping dei dati ottenuti da tale origine.  
  
 La descrizione dei requisiti di connessione per ognuna di queste origini esula dall'ambito di questo argomento. Per ulteriori informazioni, vedere la documentazione del provider. In generale, è comunque necessario tenere presente i requisiti di Analysis Services seguenti correlati all'interazione con i provider:  
  
-   Poiché il data mining è un servizio fornito da un server, l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deve poter accedere all'origine dati.  È necessario poter accedere al percorso e all'identità.  
  
     **Percorso** : se si compila un modello usando i dati archiviati solo nel computer e si distribuisce il modello in un server, il modello non viene elaborato perché non è possibile trovare l'origine dati. Per risolvere questo problema, potrebbe essere necessario trasferire i dati nella stessa istanza di SQL Server in cui [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è in esecuzione oppure spostare i file in un percorso condiviso.  
  
     **Identità** : i servizi in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] devono poter aprire il file di dati o l'origine dati con le credenziali appropriate. È ad esempio probabile che al momento di compilare il modello si disponesse di autorizzazioni illimitate per la visualizzazione dei dati, ma che l'utente che elabora e aggiorna i modelli nel server non disponga dell'accesso ai dati, cosa che può causare errori di elaborazione o compromettere il contenuto di un modello. Come minimo, l'account utilizzato per la connessione all'origine dati remota deve disporre delle autorizzazioni di lettura per i dati.  
  
-   Gli stessi requisiti si applicano allo spostamento di un modello: è necessario configurare l'accesso appropriato al percorso dell'origine dati precedente, copiare le origini dati o configurarne una nuova. È inoltre necessario trasferire i ruoli e gli account di accesso o configurare le autorizzazioni per consentire l'elaborazione e l'aggiornamento degli oggetti di data mining nel nuovo percorso.  
  
## <a name="configuring-permissions-and-server-properties"></a>Configurazione di autorizzazioni e proprietà del server  
 Il data mining richiede autorizzazioni aggiuntive in un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La maggior parte delle proprietà di data mining può essere impostata nella [finestra di dialogo Proprietà computer Analysis Server &#40;Analysis Services&#41;](../analysis-server-properties-dialog-box-analysis-services.md).  
  
 Per altre informazioni sulle proprietà che è possibile configurare, vedere [Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md).  
  
 Le proprietà del server riportate di seguito hanno particolare rilevanza per il data mining:  
  
-   `AllowAdHocOpenRowsetQueries` Controlla l'accesso ad hoc al provider OLE DB, caricati direttamente nello spazio di memoria server.  
  
    > [!IMPORTANT]  
    >  Per migliorare la sicurezza, è consigliabile impostare questa proprietà su `false`. Il valore predefinito è `false`. Tuttavia, anche se questa proprietà è impostata `false`, gli utenti possono continuare a creare query singleton e utilizzare OPENQUERY sulle origini dati consentite.  
  
-   **AllowedProvidersInOpenRowset** Specifica il provider, se l'accesso ad hoc è abilitato. È possibile specificare più provider, immettendo un elenco delimitato da virgole di ProgID.  
  
-   **MaxConcurrentPredictionQueries** Controlla il caricamento sul server causato dalle stime. Il valore predefinito 0 consente query illimitate per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition e un massimo di cinque query simultanee per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition. Le query oltre il limite vengono serializzate e sono soggette a timeout.  
  
 Il server offre proprietà aggiuntive che determinano gli algoritmi di data mining disponibili, incluse eventuali restrizioni sugli algoritmi, e le impostazioni predefinite per tutti i servizi di data mining. Non sono tuttavia disponibili impostazioni che consentano di controllare in modo specifico l'accesso alle stored procedure di data mining. Per altre informazioni, vedere [Proprietà di data mining](../server-properties/data-mining-properties.md).  
  
 È inoltre possibile impostare proprietà che consentono di ottimizzare il server e controllare la sicurezza per l'utilizzo client. Per altre informazioni, vedere [Proprietà di funzionalità](../server-properties/feature-properties.md).  
  
> [!NOTE]  
>  Per altre informazioni sul supporto per algoritmi plug-in delle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [funzionalità supportate dalle edizioni di SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473) (http://go.microsoft.com/fwlink/?linkid=232473).  
  
## <a name="programmatic-access-to-data-mining-objects"></a>Accesso a livello di codice agli oggetti di data mining  
 Per creare una connessione a un database di Analysis Services e utilizzare oggetti di data mining, è possibile utilizzare i modelli a oggetti seguenti:  
  
 **ADO** Usa OLE DB per la connessione a un server Analysis Services. Quando si utilizza ADO, il client è limitato alle query sul set di righe dello schema e alle istruzioni DMX.  
  
 **ADO.NET** Interagisce meglio con i provider SQL Server rispetto ad altri provider. Utilizza adattatori dati per archiviare set di righe dinamici. Utilizza l'oggetto set di dati, ovvero una cache dei dati server archiviati come tabelle di dati che è possibile aggiornare o salvare come XML.  
  
 **ADOMD.NET** Provider di dati gestito ottimizzato per l'uso con data mining e OLAP. ADOMD.NET è più veloce e più efficiente nell'utilizzo della memoria rispetto ad ADO.NET. ADOMD.NET consente inoltre di recuperare metadati relativi agli oggetti server. È consigliato per le applicazioni client tranne nel caso in cui .NET non sia disponibile.  
  
 **Server ADOMD** Modello a oggetti per l'accesso agli oggetti Analysis Services direttamente nel server. Utilizzato dalle stored procedure Analysis Services, non è destinato all'utilizzo client.  
  
 **AMO** Interfaccia di gestione per Analysis Services che sostituisce DSO (Decision Support Objects). Per operazioni quali l'iterazione di oggetti sono necessarie autorizzazioni di livello più alto se si utilizza AMO anziché altre interfacce. Questa condizione è dovuta al fatto che AMO accede direttamente ai metadati, mentre ADOMD.NET e le altre interfacce accedono unicamente agli schemi del database.  
  
### <a name="browse-and-query-access-to-servers"></a>Esplorare ed eseguire query sull'accesso ai server  
 È possibile eseguire qualsiasi tipo di stima tramite un'istanza di Analysis Services in modalità OLAP/Data mining, con le restrizioni seguenti:  
  
-   Se si utilizza ADOMD del server, è possibile utilizzare DMX per accedere al server senza stabilire una connessione. È quindi possibile copiare i risultati direttamente in una tabella di dati. Non è tuttavia possibile utilizzare ADOMD del server con istanze remote. Le query possono essere eseguite solo sul server locale.  
  
-   ADO.NET non supporta parametri denominati per il data mining. È necessario utilizzare ADOMD.NET.  
  
-   Poiché ADOMD.NET consente di passare un'intera tabella da utilizzare come parametro, è possibile utilizzare dati presenti nel client o dati che non sono disponibili per il server. È inoltre possibile utilizzare tabelle con sintassi SHAPE come input della stima.  
  
### <a name="using-data-mining-stored-procedures"></a>Utilizzo di stored procedure di data mining  
 Le stored procedure vengono comunemente utilizzate per incapsulare le query al fine di poterle riutilizzare. Il client può utilizzare CALL per eseguire stored procedure, incluse le stored procedure di sistema di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Se la stored procedure restituisce un set di dati, il client riceverà un set di dati o una tabella di dati con una tabella nidificata che contiene le righe. Se ad esempio viene creata una query sul contenuto del modello, la query restituisce l'intero modello. Per evitare la restituzione di troppe righe, è possibile scrivere stored procedure utilizzando il modello a oggetti ADOMD+.  
  
 Per scrivere una stored procedure del server, è necessario fare riferimento allo spazio dei nomi Microsoft.AnalysisServices.AdomdServer. Per altre informazioni sulla creazione e l'uso di stored procedure, vedere [Funzioni definite dall'utente e stored procedure](../multidimensional-models-adomd-net-server/user-defined-functions-and-stored-procedures.md).  
  
> [!NOTE]  
>  Non è possibile utilizzare le stored procedure per modificare la sicurezza per gli oggetti server dei dati. Quando si esegue una stored procedure, viene utilizzato il contesto corrente dell'utente per determinare l'accesso a tutti gli oggetti server. Gli utenti devono pertanto disporre delle autorizzazioni appropriate per qualsiasi oggetto di database a cui accedono.  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura fisica &#40;Analysis Services - dati multidimensionali&#41;](../multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)   
 [Architettura fisica &#40;Analysis Services - Data Mining&#41;](physical-architecture-analysis-services-data-mining.md)   
 [Gestione degli oggetti e delle soluzioni di data mining](management-of-data-mining-solutions-and-objects.md)  
  
  
