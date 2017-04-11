---
title: "Editor attivit&#224; Esegui pacchetto | Microsoft Docs"
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
  - "sql13.dts.designer.executepackagetask.package.f1"
  - "sql13.dts.designer.executepackagetask.parameter.F1"
  - "sql13.dts.designer.executepackagetask.general.f1"
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Editor attivit&#224; Esegui pacchetto
  Utilizzare l'editor attività Esegui pacchetto per configurare la relativa attività. L'attività Esegui pacchetto permette di estendere le funzionalità aziendali di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] consentendo ai pacchetti di eseguire altri pacchetti nell'ambito di un flusso di lavoro.  
  
 **Per saperne di più**  
  
-   [Aprire l'editor attività Esegui pacchetto](#open)  
  
-   [Impostare le opzioni nella pagina Generale](#general)  
  
-   [Impostare le opzioni nella pagina Pacchetto](#package)  
  
-   [Impostare le opzioni nella pagina Associazioni di parametro](#parameter)  
  
##  <a name="open"></a> Aprire l'editor attività Esegui pacchetto  
  
1.  Aprire un progetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] contenente un'attività Esegui pacchetto.  
  
2.  Fare clic con il pulsante destro del mouse sull'attività disponibile in Progettazione SSIS, quindi scegliere **Modifica**.  
  
##  <a name="general"></a> Impostare le opzioni nella pagina Generale  
 **Nome**  
 Specificare un nome univoco per l'attività Esegui pacchetto. Tale nome viene utilizzato come etichetta nell'icona dell'attività.  
  
> [!NOTE]  
>  I nomi delle attività devono essere univoci all'interno di un pacchetto.  
  
 **Description**  
 Digitare una descrizione dell'attività Esegui pacchetto.  
  
##  <a name="package"></a> Impostare le opzioni nella pagina Pacchetto  
 **ReferenceType**  
 Selezionare **Riferimento al progetto** per pacchetti figlio inclusi nel progetto. Selezionare **Riferimento esterno** per pacchetti figlio posizionati esternamente al pacchetto  
  
> [!NOTE]  
>  L'opzione **ReferenceType** è di sola lettura e viene impostata su **Riferimento esterno** se il progetto in cui è contenuto il pacchetto non è stato convertito nel modello di distribuzione del progetto. Per altre informazioni sulla conversione, vedere [Distribuire progetti nel server Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
 **Password**  
 Se il pacchetto figlio è protetto con password, specificare la password per il pacchetto figlio oppure fare clic sul pulsante con i puntini di sospensione (…) per creare una nuova password per il pacchetto figlio.  
  
 **ExecuteOutOfProcess**  
 Specificare se il pacchetto figlio viene eseguito nel processo del pacchetto padre o in un processo a parte. Per impostazione predefinita, la proprietà ExecuteOutOfProcess dell'attività Esegui pacchetto è impostata su **False** e il pacchetto figlio viene eseguito nello stesso processo del pacchetto padre. Se si imposta questa proprietà su **True**, il pacchetto figlio viene eseguito in un processo separato. In questo modo è possibile che l'avvio del pacchetto figlio sia rallentato. Inoltre, se la proprietà viene impostata su **True**, non è possibile eseguire il debug del pacchetto in un'installazione di soli strumenti, ma è necessario installare il prodotto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per altre informazioni, vedere [Installazione di Integration Services](../../integration-services/install-windows/install-integration-services.md).  
  
### Opzioni dinamiche relative a ReferenceType  
  
#### ReferenceType = Riferimento esterno  
 **Percorso**  
 Selezionare il percorso del pacchetto figlio. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**SQL Server**|Impostare il percorso su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**File system**|Impostare il percorso sul file system.|  
  
 **Connessione**  
 Selezionare il tipo di posizione di archiviazione del pacchetto figlio.  
  
 **PackageNameReadOnly**  
 Viene visualizzato il nome del pacchetto.  
  
#### ReferenceType = Riferimento al progetto  
 **PackageNameFromProjectReference**  
 Selezionare un pacchetto contenuto nel progetto affinché sia considerato il pacchetto figlio.  
  
### Opzioni dinamiche relative al percorso  
  
#### Percorso = SQL Server  
 **Connessione**  
 Selezionare una gestione connessione OLE DB nell'elenco o fare clic su \<**Nuova connessione...**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md), [Configura gestione connessione OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)  
  
 **PackageName**  
 Digitare il nome del pacchetto figlio oppure fare clic sul pulsante con i puntini di sospensione (…) per individuare il pacchetto.  
  
#### Percorso = File system  
 **Connessione**  
 Selezionare una gestione connessione file nell'elenco o fare clic su \<**Nuova connessione...**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 **PackageNameReadOnly**  
 Viene visualizzato il nome del pacchetto.  
  
##  <a name="parameter"></a> Impostare le opzioni nella pagina Associazioni di parametro  
 È possibile passare i valori del pacchetto padre o del progetto al pacchetto figlio. Il progetto deve utilizzare il modello di distribuzione del progetto e il pacchetto figlio deve essere contenuto nello stesso progetto in cui è contenuto il pacchetto padre.  
  
 Per informazioni sulla conversione dei progetti nel modello di distribuzione del progetto, vedere [Distribuire progetti nel server Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
 **Parametro del pacchetto figlio**  
 Immettere o selezionare un nome per il parametro del pacchetto figlio.  
  
 **Parametro o variabile di associazione**  
 Selezionare il parametro o la variabile contenente il valore che si desidera passare al pacchetto figlio.  
  
 **Aggiungi**  
 Fare clic su questa opzione per eseguire il mapping di un parametro o una variabile a un parametro del pacchetto figlio.  
  
 **Rimuovi**  
 Fare clic su questa opzione per rimuovere un mapping tra un parametro o una variabile e un parametro del pacchetto figlio.  
  
  