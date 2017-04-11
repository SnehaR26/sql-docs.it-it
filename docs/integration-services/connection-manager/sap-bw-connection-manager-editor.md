---
title: "Editor gestione connessione SAP BW | Microsoft Docs"
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
  - "sql13.dts.designer.sapbwconnectionmanager.f1"
ms.assetid: ec970319-e749-4753-8675-9cf76ed99669
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Editor gestione connessione SAP BW
  Utilizzare l'**Editor gestione connessione SAP BW** per specificare le proprietà per la connessione a un sistema SAP Netweaver BW versione 7.  
  
 La gestione connessione SAP BW offre connettività a un sistema SAP Netweaver BW 7 per l'utilizzo da parte dell'origine o della destinazione SAP BW. Per sapere di più sulla gestione connessione SAP BW di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 per SAP BW, vedere [Gestione connessione SAP BW](../../integration-services/connection-manager/sap-bw-connection-manager.md).  
  
> [!IMPORTANT]  
>  La documentazione per Microsoft Connector 1.1 for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
 **Per aprire l'editor gestione connessione SAP BW**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene la gestione connessione SAP BW.  
  
2.  Nella scheda **Flusso di controllo** dell'area Gestioni connessioni, effettuare una delle operazioni seguenti:  
  
    -   Fare doppio clic sulla gestione connessione SAP BW.  
  
         -oppure-  
  
    -   Fare clic con il tasto destro del mouse sulla gestione connessione SAP BW, quindi scegliere **Modifica**.  
  
## Opzioni  
  
> [!NOTE]  
>  Se non si conoscono tutti i valori richiesti per configurare la gestione connessione, può essere necessario consultare l'amministratore SAP.  
  
 **Client**  
 Specificare il numero client del sistema.  
  
 **Lingua**  
 Specificare la lingua utilizzata dal sistema. Ad esempio, specificare **IT** per l'italiano.  
  
 **Nome utente**  
 Specificare il nome utente che verrà utilizzato per connettersi al sistema.  
  
 **Password**  
 Specificare la password che verrà utilizzata con il nome utente.  
  
 **Usa server applicazioni singolo**  
 Connettersi a un server applicazioni singolo.  
  
 Per connettersi a un gruppo di server con carico bilanciato, usare in alternativa l'opzione **Usa bilanciamento del carico**.  
  
 **Host**  
 In caso di connessione a un server applicazioni singolo, specificare il nome host.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è stata selezionata l'opzione **Usa server applicazioni singolo**.  
  
 **Numero di sistema**  
 In caso di connessione a un server applicazioni singolo, specificare il numero del sistema.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è stata selezionata l'opzione **Usa server applicazioni singolo**.  
  
 **Usa bilanciamento del carico**  
 Connettersi a un gruppo di server con carico bilanciato.  
  
 Per connettersi a un server applicazioni singolo, usare in alternativa l'opzione **Usa server applicazioni singolo**.  
  
 **Server messaggi**  
 In caso di connessione a un gruppo di server con carico bilanciato, specificare il nome del server messaggi.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è stata selezionata l'opzione **Usa bilanciamento del carico**.  
  
 **Gruppo**  
 In caso di connessione a un gruppo di server con carico bilanciato, specificare il nome del gruppo di server.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è stata selezionata l'opzione **Usa bilanciamento del carico**.  
  
 **SID**  
 In caso di connessione a un gruppo di server con carico bilanciato, specificare l'ID sistema per la connessione.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è stata selezionata l'opzione **Usa bilanciamento del carico**.  
  
 **Directory log**  
 Abilitare la registrazione per i componenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 per SAP BW.  
  
 Per abilitare la registrazione, specificare una directory per i file di log creati prima e dopo ogni chiamata di funzione RFC. Questa funzionalità di registrazione crea molti file di log in formato XML. Poiché questi file di log contengono anche tutte le righe di dati trasferiti, è possibile che occupino una grande quantità di spazio su disco.  
  
> [!IMPORTANT]  
>  Se i dati trasferiti contengono informazioni riservate, anche i file di log conterranno tali informazioni riservate.  
  
 Per specificare la directory di log, è possibile immettere il percorso della directory manualmente oppure fare clic su **Sfoglia** e passare alla directory di log.  
  
 Se non si seleziona una directory di log, la registrazione non è abilitata.  
  
 **Sfoglia**  
 Sfogliare per selezionare una cartella per la directory di log.  
  
 **Test connessione**  
 Verificare la connessione utilizzando i valori forniti. Dopo avere fatto clic su **Test connessione** viene visualizzata una finestra di messaggio che indica se la connessione ha avuto esito positivo o negativo.  
  
## Vedere anche  
 [Guida (F1) di Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  