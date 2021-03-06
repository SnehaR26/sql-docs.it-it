---
title: Log di traccia del servizio del server di report | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- logs [Reporting Services], trace
- traces [Reporting Services]
- system information [Reporting Services]
- versions [Reporting Services]
ms.assetid: 2fde08b2-137d-4f4b-88e5-216030216e0d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2621f9a8e69cc27d5012e0c6a6f90946bec07dc5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161931"
---
# <a name="report-server-service-trace-log"></a>Report Server Service Trace Log
  Il [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] log di traccia di server di report è un file di testo ASCII che contiene informazioni dettagliate per operazioni del servizio Server di Report, ad esempio operazioni eseguite dal Report Server Web service, gestione Report e l'elaborazione in background. Nel file di log di traccia sono contenute inoltre informazioni ridondanti, che vengono registrate in altri file di log, e informazioni aggiuntive non disponibili altrove. Le informazioni contenute nel log di traccia sono utili se si esegue il debug di un'applicazione che include un server di report o se è necessario analizzare un problema specifico scritto nel log eventi o nel log di esecuzione.  
  
> [!NOTE]  
>  Nelle versioni precedenti sono presenti più file di log di traccia, uno per ogni applicazione. I file seguenti sono obsoleti e non vengono più creati [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive: reportserverwebapp _*\<timestamp >*. log, ReportServer_*\<timestamp >*. log e reportserverservice_main _*\<timestamp >*. log.  
  
 **Contenuto dell'argomento:**  
  
-   [Dove si trovano i file di log del Server di Report?](#bkmk_view_log)  
  
-   [Impostazioni di configurazione della traccia](#bkmk_trace_configuration_settings)  
  
-   [Aggiunta di impostazione di configurazione personalizzata per specificare il percorso del File di Dump](#bkmk_add_custom)  
  
-   [Campi del File di log](#bkmk_log_file_fields)  
  
##  <a name="bkmk_view_log"></a> Dove si trovano i file di log del server di report?  
 I file di log di traccia sono denominati `ReportServerService_<timestamp>.log` e si trovano nella cartella seguente:  
  
 `C:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles`  
  
 I log di traccia vengono creati quotidianamente, a partire dalla prima voce registrata dopo la mezzanotte (ora locale) e tutte le volte in cui il servizio viene riavviato. Il timestamp si basa su l'ora UTC (Coordinated Universal Time). Il file è in formato en-US Per impostazione predefinita, i log di traccia possono occupare uno spazio massimo di 32 MB e vengono eliminati dopo 14 giorni.  
  
 Visualizzare un breve video che illustra l'uso di Microsoft Power Query per visualizzare [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] i file di log.  
  
 ![visualizzare un video sui log di Power Query e SSRS](../media/generic-video-thumbnail.png "visualizzare un video sui log di Power Query e SSRS")  
  
##  <a name="bkmk_trace_configuration_settings"></a> Impostazioni di configurazione della traccia  
 Il comportamento del log di traccia viene gestito nel file di configurazione **Reportingservicesservice.exe.config**. Il file di configurazione si trova nel seguente percorso:  
  
 `\Program Files\Microsoft SQL Server\MSRS12.<instance name>\Reporting Services\ReportServer\bin` (Indici per tabelle con ottimizzazione per la memoria).  
  
 Nell'esempio seguente viene illustrata la struttura XML delle impostazioni `RStrace`. Il valore per `DefaultTraceSwitch` determina il tipo di informazioni aggiunte al log. Fatta eccezione per il `Components` , i valori per l'attributo `RStrace` sono gli stessi in tutti i file di configurazione.  
  
```  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
```  
  
 Nella tabella seguente sono incluse informazioni su ogni impostazione.  
  
|Impostazione|Description|  
|-------------|-----------------|  
|`RStrace`|Specifica gli spazi dei nomi utilizzati per errori e traccia.|  
|`DefaultTraceSwitch`|Specifica il livello delle informazioni da includere nel log di traccia ReportServerService. Ogni livello include anche le informazioni raccolte da tutti i livelli inferiori. Non è consigliabile disabilitare la funzionalità di traccia. I valori validi sono:<br /><br /> 0= Disabilita la funzionalità di traccia. Il file di log ReportServerService è abilitato per impostazione predefinita. Per disattivarlo, impostare il livello di traccia su 0.<br /><br /> 1= Eccezioni e riavvii<br /><br /> 2= Eccezioni, riavvii, avvisi<br /><br /> 3= Eccezioni, riavvii, avvisi, messaggi di stato (valore predefinito)<br /><br /> 4= Modalità dettagliata|  
|**FileName**|Specifica la prima parte del nome del file di log. Il resto del nome viene completato con il valore specificato da `Prefix`.|  
|**FileSizeLimitMb**|Specifica il limite massimo per le dimensioni del log di traccia. Il file è misurato in megabyte. I valori validi sono compresi tra 0 e il valore integer massimo. Il valore predefinito è (32). Se si specifica 0 o un numero negativo, il server di report lo considera come 1.<br /><br /> È possibile controllare le dimensioni del file impostando i livelli di traccia da 0 a 4 per definire la quantità di contenuto registrata. È inoltre possibile specificare i componenti per la traccia. Se il valore massimo del file di log viene raggiunto prima della data di scadenza di 14 giorni, le voci meno recenti verranno sostituite con le voci nuove.|  
|**KeepFilesForDays**|Specifica dopo quanti giorni un file di log di traccia viene eliminato. I valori validi sono compresi tra 0 e il valore integer massimo. Il valore predefinito è 14. Se si specifica 0 o un numero negativo, il server di report lo considera come 1.|  
|`Prefix`|Specifica un valore generato che distingue ogni istanza del log dalle altre. Per impostazione predefinita, ai nomi file dei log di traccia vengono aggiunti valori timestamp. Questo valore è impostato su "tid, time". Non modificare questa impostazione.|  
|**TraceListeners**|Specifica una destinazione per l'output del contenuto del log di traccia. È possibile specificare più destinazioni, separandole con una virgola. I valori validi sono:<br /><br /> DebugWindow<br /><br /> File (valore predefinito)<br /><br /> StdOut|  
|**TraceFileMode**|Specifica se i log di traccia devono contenere dati per un periodo di 24 ore. È consigliabile utilizzare un solo log di traccia al giorno per ogni componente. Questo valore è impostato su "Unique" (valore predefinito). Non modificare questo valore.|  
|`Components`|Specifica i componenti per i quali vengono generate informazioni nel log di traccia e il livello di traccia nel formato seguente:<br /><br /> \<categoria componente>:\<livellotraccia><br /><br /> Le categorie dei componenti possono essere impostate nei modi seguenti:<br />Il valore `All` viene utilizzato per tracciare l'attività generale del server di report per tutti i processi che non sono suddivisi in categorie specifiche.<br />`RunningJobs` viene usato per tracciare un'operazione di report o una sottoscrizione in corso.<br />Il valore `SemanticQueryEngine` viene utilizzato per tracciare una query semantica elaborata quando un utente esegue un'esplorazione dei dati ad hoc in un report basato su modello.<br />Il valore `SemanticModelGenerator` viene utilizzato per tracciare la generazione del modello.<br />Il valore `http` viene utilizzato per abilitare il file di log HTTP del server di report. Per altre informazioni, vedere [Log HTTP del Server di Report](report-server-http-log.md).<br /><br /> <br /><br /> I valori validi del livello di traccia sono i seguenti:<br /><br /> 0= Disabilita la funzionalità di traccia<br /><br /> 1= Eccezioni e riavvii<br /><br /> 2= Eccezioni, riavvii, avvisi<br /><br /> 3= Eccezioni, riavvii, avvisi, messaggi di stato (valore predefinito)<br /><br /> 4= Modalità dettagliata<br /><br /> Il valore predefinito per il server di report è: "all:3".<br /><br /> È possibile specificare tutti o alcuni dei componenti (`all`, `RunningJobs`, `SemanticQueryEngine`, `SemanticModelGenerator`). Se non si desidera generare informazioni per un componente specifico, è possibile disabilitare la traccia per tale componente (ad esempio "SemanticModelGenerator:0"). Non disabilitare la funzionalità di traccia per il componente `all`.<br /><br /> Se non si aggiunge un livello di traccia dopo il nome del componente, verrà utilizzato il valore specificato per `DefaultTraceSwitch`. Ad esempio, se si specifica "all,RunningJobs,SemanticQueryEngine,SemanticModelGenerator", per tutti i componenti verrà utilizzato il livello di traccia predefinito.<br /><br /> È possibile impostare "SemanticQueryEngine:4" se si desidera visualizzare le istruzioni Transact-SQL che vengono generate per ogni query semantica. Le istruzioni Transact-SQL vengono registrate nel log di traccia. Nell'esempio seguente viene illustrata l'impostazione di configurazione per l'aggiunta delle istruzioni Transact-SQL al log:<br /><br /> \<add name="Components" value="all,SemanticQueryEngine:4" />|  
  
##  <a name="bkmk_add_custom"></a> Aggiunta di un'impostazione di configurazione personalizzata per specificare il percorso del file di dump  
 È possibile aggiungere un'impostazione personalizzata per definire la directory di archiviazione utilizzata dallo strumento Dr. per Windows per archiviare i file di dump. L'impostazione personalizzata è `Directory`. Nell'esempio seguente viene illustrato come specificare questa impostazione di configurazione nella sezione `RStrace`:  
  
```  
<add name="Directory" value="U:\logs\" />  
```  
  
 Per ulteriori informazioni, vedere l' [articolo della Knowledge Base 913046](http://support.microsoft.com/?kbid=913046) nel sito Web [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
##  <a name="bkmk_log_file_fields"></a> Campi del file di log  
 Nei log di traccia sono disponibili i campi seguenti:  
  
-   Informazioni sul sistema, quali il sistema operativo, la versione, il numero di processori e la memoria.  
  
-   Informazioni sul componente [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e sulla versione.  
  
-   Eventi registrati nel registro applicazioni.  
  
-   Eccezioni generate dal server di report.  
  
-   Avvisi di risorse insufficienti registrati da un server di report.  
  
-   Buste SOAP in ingresso e buste SOAP in uscita riepilogate.  
  
-   Informazioni sull'intestazione HTTP, sull'analisi dello stack e sulla traccia di debug.  
  
 Esaminando le informazioni dei log di traccia è possibile stabilire se ha avuto luogo un recapito di report, chi ha ricevuto il report e quanti tentativi di recapito sono stati eseguiti. Nei log di traccia vengono inoltre registrati l'attività di esecuzione del report e le variabili di ambiente attive durante l'elaborazione del report, nonché gli errori e le eccezioni. Ad esempio, è possibile trovare report errori di timeout (indicato come un `ThreadAbortExceptions` voce).  
  
## <a name="see-also"></a>Vedere anche  
 [File di log e origini di Reporting Services](../report-server/reporting-services-log-files-and-sources.md)   
 [Gli errori e riferimento degli eventi &#40;Reporting Services&#41;](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
