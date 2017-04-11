---
title: "Opzioni di Richiesta profilo Rapporto di valori Null nella colonna (Attivit&#224; Profiling dati) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editor attività Profiling dati"
ms.assetid: 157ef8e4-fd23-4f81-8194-eebf74e9fd86
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# Opzioni di Richiesta profilo Rapporto di valori Null nella colonna (Attivit&#224; Profiling dati)
  Utilizzare il riquadro **Proprietà richiesta** della pagina **Richieste profilo** per impostare le opzioni per la richiesta **Richiesta profilo Rapporto di valori Null nella colonna** selezionata nel riquadro delle richieste. Il profilo Rapporto di valori Null nella colonna segnala la percentuale di valori Null nella colonna selezionata e consente di identificare eventuali problemi nei dati, ad esempio un rapporto inaspettatamente elevato di valori Null in una colonna. Un profilo Rapporto di valori Null nella colonna può analizzare, ad esempio, una colonna contenente CAP e individuare una percentuale eccessivamente elevata di CAP mancanti.  
  
> [!NOTE]  
>  Le opzioni descritte in questo argomento vengono visualizzate nella pagina **Richieste profilo** in **Editor attività Profiling dati**. Per altre informazioni su questa pagina dell'editor, vedere [Editor attività Profiling dati &#40;Pagina Richieste profilo&#41;](../../integration-services/control-flow/data-profiling-task-editor-profile-requests-page.md).  
  
 Per altre informazioni sull'uso dell'attività Profiling dati, vedere [Impostazione dell'attività Profiling dati](../../integration-services/control-flow/setup-of-the-data-profiling-task.md). Per altre informazioni sull'uso del Visualizzatore profilo dati per analizzare l'output dell'attività Profiling dati, vedere [Visualizzatore profilo dati](../../integration-services/control-flow/data-profile-viewer.md).  
  
## Opzioni del riquadro Proprietà richiesta  
 Nel riquadro **Proprietà richiesta**per **Richiesta profilo Rapporto di valori Null nella colonna** vengono visualizzati i gruppi di opzioni seguenti:  
  
-   **Dati**che include le opzioni **TableOrView** e **Column**  
  
-   **Generale**  
  
### Opzioni dati  
 **ConnectionManager**  
 Consente di selezionare la gestione connessione [!INCLUDE[vstecado](../../includes/vstecado-md.md)] esistente che usa il provider di dati .NET per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) per la connessione al database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenente la tabella o la vista di cui eseguire il profiling.  
  
 **TableOrView**  
 Consente di selezionare la tabella o la vista esistente che contiene la colonna da analizzare.  
  
 Per ulteriori informazioni, vedere la sezione "Opzioni TableorView" in questo argomento.  
  
 **Colonna**  
 Consente di selezionare la colonna esistente da analizzare. Selezionare **(\*)** per analizzare tutte le colonne.  
  
 Per ulteriori informazioni, vedere la sezione "Opzioni Column" in questo argomento.  
  
#### Opzioni TableOrView  
 **Schema**  
 Specifica lo schema a cui appartiene la tabella selezionata. Questa opzione è di sola lettura.  
  
 **Tabella**  
 Visualizza il nome della tabella selezionata. Questa opzione è di sola lettura.  
  
#### Opzioni relative alle colonne  
 **IsWildCard**  
 Specifica se è stato selezionato il carattere jolly **(\*)**. Questa opzione è impostata su **True** se è stato selezionato **(\*)** per analizzare tutte le colonne. È impostata su **False** se è stata selezionata una singola colonna da analizzare. Questa opzione è di sola lettura.  
  
 **ColumnName**  
 Visualizza il nome della colonna selezionata. È vuota se è stato selezionato **(\*)** per analizzare tutte le colonne. Questa opzione è di sola lettura.  
  
 **StringCompareOptions**  
 Questa opzione non si applica al profilo Rapporto di valori Null nella colonna.  
  
### Opzioni generali  
 **RequestID**  
 Nome descrittivo per identificare la richiesta di profilo. Non è in genere necessario modificare il valore generato automaticamente.  
  
## Vedere anche  
 [Editor attività Profiling dati &#40;Pagina Generale&#41;](../../integration-services/control-flow/data-profiling-task-editor-general-page.md)   
 [Form profilo rapido singola tabella &#40;Attività Profiling dati&#41;](../../integration-services/control-flow/single-table-quick-profile-form-data-profiling-task.md)  
  
  