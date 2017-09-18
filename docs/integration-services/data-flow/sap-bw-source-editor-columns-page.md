---
title: Editor origine SAP BW (pagina colonne) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sapbwsource.columns.f1
ms.assetid: c2ec8bb7-be9b-4783-ad88-32512de784b0
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2047fddb6986bd3014015d742053bfb0dda42019
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="sap-bw-source-editor-columns-page"></a>Editor origine SAP BW (pagina Colonne)
  Usare la pagina **Colonne** della finestra di dialogo **Editor origine SAP BW** per eseguire il mapping di una colonna di output a ogni colonna esterna (di origine).  
  
 Per sapere di più sul componente di origine SAP BW di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vedere [Origine SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentazione per Microsoft Connector 1.1 for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
> [!IMPORTANT]  
>  L'estrazione di dati da SAP Netweaver BW richiede licenze SAP aggiuntive. Contattare SAP per verificare questi requisiti.  
  
 **Per aprire la pagina Colonne**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene l'origine SAP BW.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sull'origine SAP BW.  
  
3.  Nell' **Editor origine SAP BW**fare clic su **Colonne** per aprire la pagina **Colonne** dell'editor.  
  
## <a name="options"></a>Opzioni  
  
> [!NOTE]  
>  Se non si conoscono tutti i valori richiesti per configurare l'origine, può essere necessario consultare l'amministratore SAP.  
  
 **Colonne esterne disponibili**  
 Visualizzare l'elenco delle colonne esterne disponibili nell'origine dati, quindi selezionare le colonne da includere nel flusso di dati.  
  
 Per includere una colonna nel flusso di dati, selezionare la casella di controllo corrispondente a tale colonna. L'ordine di selezione delle caselle di controllo determina l'ordine di restituzione delle colonne. La prima casella di controllo selezionata sarà la prima colonna di output, la seconda casella di controllo sarà la seconda colonna di output e così via.  
  
 **Colonna esterna**  
 Visualizzare le colonne (di origine) esterne selezionate. Le colonne selezionate sono visualizzate nell'ordine di visualizzazione delle colonne di output corrispondenti quando si configurano i componenti a valle che utilizzano i dati di tale origine.  
  
 Per modificare l'ordine delle colonne, nell'elenco **Colonne esterne disponibili** deselezionare le caselle di controllo per tutte le colonne. Selezionare quindi le colonne nell'ordine in cui si desidera visualizzarle.  
  
 **Colonna di output**  
 Consente di specificare un nome univoco per ogni colonna di output. L'impostazione predefinita è il nome della colonna (di origine) esterna selezionata. Tuttavia, è possibile immettere qualsiasi nome descrittivo univoco. [!INCLUDE[ssIS](../../includes/ssis-md.md)]Finestra di progettazione verrà visualizzato il **colonna di Output** nomi per le colonne quando si configurano i componenti a valle che utilizzano i dati dall'origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor origine SAP BW &#40; Pagina Gestione connessione &#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Editor origine SAP BW &#40; Pagina Output degli errori &#41;](../../integration-services/data-flow/sap-bw-source-editor-error-output-page.md)   
 [Editor origine SAP BW &#40; Pagina avanzate &#41;](../../integration-services/data-flow/sap-bw-source-editor-advanced-page.md)   
 [Guida (F1) di Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  