---
title: "Editor origine ADO NET (pagina Gestione connessione) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.adonetsource.connection.f1"
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# Editor origine ADO NET (pagina Gestione connessione)
  Usare la pagina **Gestione connessione** della finestra di dialogo **Editor origine ADO.NET** per selezionare la gestione connessione [!INCLUDE[vstecado](../../includes/vstecado-md.md)] per l'origine. Tramite questa pagina è inoltre possibile selezionare una tabella o una vista del database.  
  
 Per ulteriori informazioni sull'origine ADO NET, vedere [ADO NET Source](../../integration-services/data-flow/ado-net-source.md).  
  
 **Per aprire la pagina Gestione connessione**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], aprire il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] con l'origine ADO NET.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sull'origine ADO NET.  
  
3.  In **Editor origine ADO.NET**, fare clic su **Gestione connessione**.  
  
## Opzioni statiche  
 **Gestione connessione ADO.NET**  
 Selezionare una gestione connessione esistente nell'elenco o crearne una nuova facendo clic su **Nuova**.  
  
 **Nuovi**  
 Consente di creare una nuova gestione connessione usando la finestra di dialogo **Configura gestione connessione ADO.NET**.  
  
 **Modalità di accesso ai dati**  
 Consente di specificare il metodo per la selezione dei dati dall'origine.  
  
|Opzione|Description|  
|------------|-----------------|  
|Tabella o vista|Consente di recuperare dati da una tabella o da una vista nell'origine dei dati [!INCLUDE[vstecado](../../includes/vstecado-md.md)].|  
|Comando SQL|Consente di recuperare dati dall'origine dei dati [!INCLUDE[vstecado](../../includes/vstecado-md.md)] usando una query SQL.|  
  
 **Anteprima**  
 Consente di visualizzare in anteprima i risultati nella finestra di dialogo **Vista dati**. L'**anteprima** supporta la visualizzazione di un massimo di 200 righe.  
  
> [!NOTE]  
>  Quando vengono visualizzati i dati in anteprima, le colonne con tipo definito dall'utente CLR (UDT) non contengono dati. Vengono invece visualizzati i valori \<dimensione valore eccessiva per la visualizzazione> o System.Byte[]. Il primo viene visualizzato se si accede all'origine dei dati mediante il [!INCLUDE[vstecado](../../includes/vstecado-md.md)], il secondo se si utilizza il provider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## Opzioni dinamiche relative alla modalità di accesso ai dati  
  
### Modalità di accesso ai dati = Tabella o vista  
 **Nome tabella o vista**  
 Consente di selezionare il nome della tabella o della vista nell'elenco dei nomi disponibili nell'origine dei dati.  
  
### Modalità di accesso ai dati = Comando SQL  
 **Testo comando SQL**  
 Immettere il testo di una query SQL, fare clic su **Compila query** per compilare la query o fare clic su **Sfoglia** per individuare il file che contiene il testo della query.  
  
 **Compila query**  
 Usare la finestra di dialogo **Generatore query** per creare la query SQL con strumenti grafici.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file contenente il testo della query SQL.  
  
## Vedere anche  
 [Editor origine ADO NET &#40;pagina Colonne&#41;](../../integration-services/data-flow/ado-net-source-editor-columns-page.md)   
 [Editor origine ADO NET &#40;pagina Output errori&#41;](../../integration-services/data-flow/ado-net-source-editor-error-output-page.md)   
 [Gestione connessione ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)  
  
  