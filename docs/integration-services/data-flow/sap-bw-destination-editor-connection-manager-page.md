---
title: "Editor destinazione SAP BW (pagina Gestione connessione) | Microsoft Docs"
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
  - "sql13.dts.designer.sapbwdestination.connection.f1"
ms.assetid: 04ae38f8-5287-45a3-826a-8aac5dd15a91
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Editor destinazione SAP BW (pagina Gestione connessione)
  Usare la pagina **Gestione connessione** della finestra di dialogo **Editor destinazione SAP BW** per selezionare la gestione connessione SAP BW che verrà usata dalla destinazione SAP BW. In questa pagina vengono inoltre selezionati i parametri per il caricamento dei dati nel sistema SAP Netweaver BW.  
  
 Per altre informazioni sulla destinazione SAP BW di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vedere [Destinazione SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentazione per Microsoft Connector 1.1 for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
 **Per aprire la pagina Gestione connessione**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene la destinazione SAP BW.  
  
2.  Nella scheda **Flusso dati** fare doppio clic sulla destinazione SAP BW.  
  
3.  Nell' **Editor destinazione SAP BW**fare clic su **Gestione connessione** per aprire la pagina **Gestione connessione** dell'editor.  
  
## Opzioni  
  
> [!NOTE]  
>  Se non si conoscono tutti i valori richiesti per configurare la destinazione, può essere necessario consultare l'amministratore SAP.  
  
 **Gestione connessione SAP BW**  
 Selezionare una gestione connessione esistente nell'elenco oppure crearne una nuova facendo clic su **Nuova**.  
  
 **Nuova**  
 Creare una nuova gestione connessione usando la finestra di dialogo **Gestione connessione SAP BW**.  
  
 **Test del carico**  
 Eseguire un test del processo di caricamento che utilizzi le impostazioni selezionate e carichi zero righe.  
  
### Opzioni di InfoPackage/InfoSource  
 Non è necessario conoscere e immettere questi valori in anticipo. Usare il pulsante **Ricerca** per individuare e selezionare l'InfoPackage appropriato. Dopo aver selezionato un InfoPackage, il componente inserisce i valori appropriati per queste opzioni.  
  
 **InfoPackage**  
 Immettere il nome dell'InfoPackage.  
  
 **InfoSource**  
 Immettere il nome dell'InfoSource.  
  
 **Tipo**  
 Immettere il carattere singolo che identifica il tipo di InfoSource. Nella tabella seguente sono elencati i valori a carattere singolo accettabili.  
  
|Valore|Description|  
|-----------|-----------------|  
|**D**|Dati transazione|  
|**M**|Dati master|  
|**T**|Testi|  
|**H**|Dati gerarchia|  
  
 **Sistema logico**  
 Immettere il nome del sistema logico associato all'InfoPackage.  
  
 **Ricerca**  
 Individuare l'InfoPackage usando la finestra di dialogo **Cerca InfoPackage**. Per altre informazioni su questa finestra di dialogo, vedere [Cerca InfoPackage](../../integration-services/data-flow/look-up-infopackage.md).  
  
### Opzioni della destinazione RFC  
 Non è necessario conoscere e immettere questi valori in anticipo. Usare il pulsante **Ricerca** per individuare e selezionare la destinazione RFC appropriata. Dopo aver selezionato una destinazione RFC, il componente inserisce i valori appropriati per queste opzioni.  
  
 **Host gateway**  
 Immettere il nome server o l'indirizzo IP dell'host gateway. In genere, il nome o l'indirizzo IP è uguale a quello del server applicazioni SAP.  
  
 **Servizio gateway**  
 Immettere il nome del servizio del gateway, nel formato **sapgwNN**, dove **NN** è il numero del sistema.  
  
 **ID programma**  
 Immettere l'ID programma associato alla destinazione RFC.  
  
 **Ricerca**  
 Individuare la destinazione RFC usando la finestra di dialogo **Cerca destinazione RFC**. Per altre informazioni su questa finestra di dialogo, vedere [Cerca InfoPackage](../../integration-services/data-flow/look-up-rfc-destination.md).  
  
### Opzioni di Crea oggetti SAP BW  
 **Seleziona il tipo di oggetto**  
 Selezionare il tipo di oggetto SAP Netweaver BW che si desidera creare. È possibile selezionare uno dei tipi seguenti:  
  
-   InfoObject  
  
-   InfoCube  
  
-   InfoSource  
  
-   InfoPackage  
  
 **Create**  
 Creare il tipo selezionato di oggetto SAP Netweaver BW.  
  
|Tipo oggetto|Risultato|  
|-----------------|------------|  
|**InfoObject**|Creare un nuovo InfoObject usando la finestra di dialogo **Crea nuovo InfoObject**. Per altre informazioni su questa finestra di dialogo, vedere [Crea nuovo InfoObject](../../integration-services/data-flow/create-new-infoobject.md).|  
|**InfoCube**|Creare un nuovo InfoCube usando la finestra di dialogo **Crea InfoCube per dati transazione**. Per altre informazioni su questa finestra di dialogo, vedere [Crea InfoCube per dati transazione](../../integration-services/data-flow/create-infocube-for-transaction-data.md).|  
|**InfoSource**|Creare un nuovo InfoSource usando la finestra di dialogo **Crea InfoSource** e quindi la finestra di dialogo **Crea InfoSource per dati transazione** o **Crea InfoSource per dati master**. Per altre informazioni su queste finestre di dialogo, vedere [Crea InfoSource](../../integration-services/data-flow/create-infosource.md), [Crea InfoSource per dati transazione](../../integration-services/data-flow/create-infosource-for-transaction-data.md) e [Crea InfoSource per dati master](../../integration-services/data-flow/create-infosource-for-master-data.md).|  
|**InfoPackage**|Creare un nuovo InfoPackage usando la finestra di dialogo **Crea InfoPackage**. Per altre informazioni su questa finestra di dialogo, vedere [Crea InfoPackage](../../integration-services/data-flow/create-infopackage.md).|  
  
## Vedere anche  
 [Editor destinazione SAP BW &#40;pagina Mapping&#41;](../../integration-services/data-flow/sap-bw-destination-editor-mappings-page.md)   
 [Editor destinazione SAP BW &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/sap-bw-destination-editor-error-output-page.md)   
 [Editor destinazione SAP BW &#40;pagina Avanzate&#41;](../../integration-services/data-flow/sap-bw-destination-editor-advanced-page.md)   
 [Guida (F1) di Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  