---
title: "Visualizzatore profilo dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visualizzatore profilo dati [Integration Services]"
  - "attività Profiling dati [Integration Services], visualizzatore output"
ms.assetid: b9043428-ce26-45bb-910c-588d07579565
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Visualizzatore profilo dati
  La visualizzazione e l'analisi dei profili dati costituiscono il passaggio successivo del processo di profiling dei dati. È possibile visualizzare tali profili dopo avere eseguito l'attività Profiling dati in un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e avere calcolato i profili dati. Per altre informazioni su come configurare ed eseguire le attività Profiling dati, vedere [Impostazione dell'attività Profiling dati](../../integration-services/control-flow/setup-of-the-data-profiling-task.md).  
  
> [!IMPORTANT]  
>  Il file di output potrebbe contenere dati sensibili sul database e i dati inclusi nel database. Per suggerimenti su come rendere più sicuro questo file, vedere [Accesso ai file utilizzati dai pacchetti](../../integration-services/security/access-to-files-used-by-packages.md).  
  
## Profili dati  
 Per visualizzare i profili dati, è necessario configurare l'attività Profiling dati per inviare l'output a un file e quindi utilizzare il Visualizzatore profilo dati autonomo. Per aprire il Visualizzatore profilo dati, effettuare una delle azioni seguenti:  
  
-   Fare clic con il pulsante destro del mouse sull'attività **Profiling dati** in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], quindi scegliere **Modifica**. Fare clic su **Apri Visualizzatore profilo** nella pagina **Generale** dell'**Editor attività Profiling dati**.  
  
-   Nella cartella *\<unità>*:\Programmi (x86) | Programmi\Microsoft SQL Server\110\DTS\Binn eseguire DataProfileViewer.exe.  
  
 Il visualizzatore contiene più riquadri per visualizzare i profili richiesti e i risultati calcolati, con funzionalità di drill-down e dettagli facoltativi:  
  
 Riquadro **Profili**  
 Nel riquadro **Profili** vengono visualizzati i profili richiesti nell'attività Profiling dati. Per visualizzare i risultati calcolati per il profilo, selezionare il profilo nel riquadro **Profili**. I risultati verranno visualizzati negli altri riquadri del visualizzatore.  
  
 Riquadro**Risultati**   
 Il riquadro **Risultati** usa una singola riga per riepilogare i risultati calcolati del profilo. Se, ad esempio, si richiede un **profilo Distribuzione lunghezze di colonna**, questa riga include le lunghezze minima e massima e il conteggio delle righe. Per la maggior parte dei profili è possibile selezionare questa riga nel riquadro **Risultati** per visualizzare altri dettagli nel riquadro **Dettagli** facoltativo.  
  
 Riquadro **Dettagli**  
 Per la maggior parte dei tipi di profilo, il riquadro **Dettagli** contiene informazioni aggiuntive sui risultati del profilo selezionati nel riquadro **Risultati**. Se, ad esempio, si richiede un **profilo Distribuzione lunghezze di colonna**, nel riquadro **Dettagli** verrà visualizzata ogni lunghezza di colonna rilevata. Nel riquadro viene inoltre visualizzato il numero e la percentuale di righe in cui il valore di colonna ha la lunghezza di colonna specificata.  
  
 Per i tre tipi di profilo calcolati in più colonne (profili Chiave candidata, Dipendenza funzionale e Inclusione valore), nel riquadro **Dettagli** vengono visualizzate le eventuali violazioni della relazione prevista. Se, ad esempio, si richiede un profilo Chiave candidata, nel riquadro Dettagli verranno visualizzati i valori duplicati che violano l'univocità della chiave candidata.  
  
 Se l'origine dati usata per calcolare il profilo è disponibile, è possibile fare doppio clic su una riga nel riquadro **Dettagli** per visualizzare le righe di dati corrispondenti nel riquadro **Drill-down**.  
  
 Riquadro **Drill-down**  
 È possibile fare doppio clic su una riga nel riquadro **Dettagli** per visualizzare le righe di dati corrispondenti nel riquadro **Drill-down** quando sono vere le condizioni seguenti:  
  
-   L'origine dati utilizzata per calcolare il profilo è disponibile.  
  
-   Si dispone dell'autorizzazione per visualizzare i dati.  
  
 Per la connessione al database di origine per una richiesta di drill-down, il Visualizzatore profilo dati utilizza l'autenticazione di Windows e le credenziali dell'utente corrente. Tramite il Visualizzatore profilo dati non vengono utilizzate le informazioni di connessione archiviate nel pacchetto che ha eseguito l'attività Profiling dati.  
  
> [!IMPORTANT]  
>  La funzionalità di drill-down, disponibile nel Visualizzatore profilo dati, consente di inviare query in tempo reale all'origine dati originale. Queste query possono avere un impatto negativo sulle prestazioni del server.  
>   
>  Se si esegue il drill-down da un file di output non creato recentemente, le query di drill-down potrebbero restituire un set di righe diverso rispetto a quello utilizzato per calcolare l'output originale.  
  
 Per altre informazioni sull'interfaccia utente del Visualizzatore profilo dati, vedere [Guida sensibile al contesto del Visualizzatore profilo dati](../../integration-services/control-flow/data-profile-viewer-f1-help.md).  
  
  