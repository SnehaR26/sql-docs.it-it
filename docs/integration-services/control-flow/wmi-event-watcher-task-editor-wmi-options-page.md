---
title: "Editor attivit&#224; Monitoraggio eventi WMI (pagina Opzioni WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.wmieventwatcher.wmiquery.f1"
helpviewer_keywords: 
  - "Editor attività Monitoraggio eventi WMI"
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Editor attivit&#224; Monitoraggio eventi WMI (pagina Opzioni WMI)
  Usare la pagina **Opzioni WMI** della finestra di dialogo **Editor attività Monitoraggio eventi WM** per specificare l'origine della query WQL e la modalità di risposta dell'attività Monitoraggio eventi WMI agli eventi del servizio Strumentazione Gestione Windows (WMI).  
  
 Per ulteriori informazioni su questa attività, vedere [WMI Event Watcher Task](../../integration-services/control-flow/wmi-event-watcher-task.md). Per altre informazioni su WQL (WMI Query Language), vedere l'argomento relativo a WMI (Windows Management Instrumentation) "[Query con WQL](http://go.microsoft.com/fwlink/?LinkId=79045)" in MSDN Library.  
  
## Opzioni statiche  
 **WMIConnectionName**  
 Consente di selezionare una gestione connessione WMI nell'elenco o di creare una nuova gestione connessione facendo clic su \<**Nuova connessione WMI**>.  
  
 **Argomenti correlati**: [Gestione connessione WMI](../../integration-services/connection-manager/wmi-connection-manager.md), [Editor gestione connessione WMI](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Consente di selezionare il tipo di origine della query WQL eseguita dall'attività. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Input diretto**|Consente di impostare l'origine su una query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySource**.|  
|**Connessione file**|Consente di selezionare un file contenente la query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySource**.|  
|**Variabile**|Consente di impostare l'origine su una variabile che definisce la query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySource**.|  
  
 **ActionAtEvent**  
 Consente di specificare se l'evento WMI registra l'evento e inizia un'azione [!INCLUDE[ssIS](../../includes/ssis-md.md)] oppure se si limita a registrare l'evento.  
  
 **AfterEvent**  
 Consente di specificare se l'attività ha esito positivo o negativo dopo avere ricevuto l'evento WMI oppure se deve continuare a monitorare l'evento per controllare se viene generato nuovamente.  
  
 **ActionAtTimeout**  
 Consente di specificare se l'attività registra un timeout della query WMI e inizia un evento [!INCLUDE[ssIS](../../includes/ssis-md.md)] in risposta oppure se si limita a registrare il timeout.  
  
 **AfterTimeout**  
 Consente di specificare se l'attività ha esito positivo o negativo in risposta a un timeout oppure se deve continuare il monitoraggio per controllare se viene generato un altro timeout.  
  
 **NumberOfEvents**  
 Consente di specificare il numero di eventi da monitorare.  
  
 **Timeout**  
 Consente di specificare il numero di secondi di attesa per la generazione dell'evento. Un valore pari a 0 significa che non è attivo alcun timeout.  
  
## Opzioni dinamiche di WQLQuerySource  
  
### WQLQuerySource = Input diretto  
 **WQLQuerySource**  
 Consente di specificare una query o di immettere una query nella finestra di dialogo **Query WQL** visualizzata facendo clic sul pulsante (...).  
  
### WQLQuerySource = Connessione file  
 **WQLQuerySource**  
 Selezionare una gestione connessione file nell'elenco oppure fare clic su \<**Nuova connessione**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### WQLQuerySource = Variabile  
 **WQLQuerySource**  
 Selezionare una variabile nell'elenco oppure fare clic su \<**Nuova variabile**> per crearne una nuova.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Aggiungi variabile](../Topic/Add%20Variable.md)  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Monitoraggio eventi WMI &#40;pagina Generale&#41;](../../integration-services/control-flow/wmi-event-watcher-task-editor-general-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)   
 [Attività Lettore di dati WMI](../../integration-services/control-flow/wmi-data-reader-task.md)  
  
  