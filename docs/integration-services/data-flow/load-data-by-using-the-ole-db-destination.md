---
title: "Caricamento dei dati tramite la destinazione OLE DB | Microsoft Docs"
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
  - "caricamento di dati"
  - "destinazione OLE DB [Integration Services]"
  - "destinazioni [Integration Services], OLE DB"
ms.assetid: 78899498-725e-4300-a7af-f983f4ea384b
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Caricamento dei dati tramite la destinazione OLE DB
  È possibile aggiungere e configurare una destinazione OLE DB solo se il pacchetto include già almeno un'attività Flusso di dati e un'origine.  
  
### Per caricare dati tramite una destinazione OLE DB  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di dati** e quindi, dalla **Casella degli strumenti**, trascinare la destinazione OLE DB sull'area di progettazione.  
  
4.  Connettere la destinazione OLE DB al flusso di dati trascinando un connettore da un'origine dati o una trasformazione precedente alla destinazione.  
  
5.  Fare doppio clic sulla destinazione OLE DB.  
  
6.  Nella pagina **Gestione connessione** della finestra di dialogo **Editor destinazione OLE DB** selezionare una gestione connessione OLE DB esistente oppure fare clic su **Nuova** per creare una nuova gestione connessione. Per altre informazioni, vedere [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
7.  Selezionare il metodo di accesso ai dati:  
  
    -   **Tabella o vista** Selezionare una tabella o una vista nel database che contiene i dati.  
  
    -   **Tabella o vista - Caricamento rapido** Selezionare una tabella o una vista nel database che contiene i dati e quindi impostare le opzioni relative al caricamento rapido: **Mantieni valori Identity**, **Mantieni valori Null**, **Blocco di tabella**, **Verifica vincoli**, **Righe per batch** o **Dimensioni massime commit inserimento**.  
  
    -   **Variabile nome vista o nome tabella** Selezionare una variabile definita dall'utente contenente il nome di una tabella o vista del database.  
  
    -   **Variabile nome vista o nome tabella - Caricamento rapido** Selezionare la variabile definita dall'utente contenente il nome di una tabella o vista del database che contiene i dati e quindi impostare le opzioni relative al caricamento rapido.  
  
    -   **Comando SQL** Digitare un comando SQL oppure fare clic su **Compila query** per scrivere un comando SQL utilizzando **Generatore query**.  
  
8.  Fare clic su **Mapping** e quindi eseguire il mapping delle colonne nell'elenco **Colonne di input disponibili** alle colonne nell'elenco **Colonne di destinazione disponibili** , trascinando le colonne da un elenco all'altro.  
  
    > [!NOTE]  
    >  La destinazione OLE DB esegue automaticamente il mapping delle colonne con lo stesso nome.  
  
9. Per configurare l'output degli errori, fare clic su **Output errori**. Per altre informazioni, vedere [Configurazione di un output degli errori in un componente del flusso di dati](../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md).  
  
10. Scegliere **OK**.  
  
11. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## Vedere anche  
 [Destinazione OLE DB](../../integration-services/data-flow/ole-db-destination.md)   
 [Trasformazioni di Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Percorsi in Integration Services](../../integration-services/data-flow/integration-services-paths.md)   
 [Attività Flusso di dati](../../integration-services/control-flow/data-flow-task.md)  
  
  