---
title: "Creare e modificare origini dati incorporate | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c38c2e8-7a29-4f79-a4a3-85ed2b13723b
caps.latest.revision: 10
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 10
---
# Creare e modificare origini dati incorporate
  Un'origine dati incorporata viene definita in una definizione del report e viene utilizzata solo dal report specifico,  
  
## Per creare un'origine dati incorporata in Progettazione report  
  
1.  Nel riquadro dei dati del report fare clic su **Nuova** nella barra degli strumenti, quindi su **Origine dati**. Verrà visualizzata la finestra di dialogo **Proprietà origine dati** .  
  
    > [!NOTE]  
    >  Se il riquadro Dati report non è visualizzato, scegliere **Dati report** dal menu **Visualizza**.  
  
2.  Nella casella di testo **Nome** digitare un nome per l'origine dati oppure accettare quello predefinito. Il nome dell'origine dati viene utilizzato internamente nell'ambito del report. Per maggiore chiarezza è consigliabile assegnare all'origine dati un nome che includa il nome del database specificato nella stringa di connessione.  
  
3.  Verificare che l'opzione **Connessione incorporata** sia selezionata, quindi eseguire la procedura seguente.  
  
    1.  Dall'elenco a discesa **Tipo** selezionare un tipo di origine dati, ad esempio **Microsoft SQL Server** o **OLE DB**.  
  
    2.  Specificare una stringa di connessione utilizzando una delle alternative seguenti:  
  
        -   Digitare la stringa di connessione direttamente nella casella di testo **Stringa di connessione** . Per un elenco di stringhe di connessione di esempio, vedere [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md) o [Connessioni dati, origini dati e stringhe di connessione in Generatore report e SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
        -   Fare clic sul pulsante relativo all'espressione (**fx)**) per creare un'espressione che restituisca una stringa di connessione. Nella finestra di dialogo **Espressione** digitare l'espressione nel riquadro relativo. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
        -   Fare clic su **Modifica** per aprire la finestra di dialogo **Proprietà connessione** per il tipo di origine dati scelto nel passaggio 2.  
  
             Nei campi della finestra di dialogo **Proprietà connessione** inserire le informazioni appropriate per il tipo di origine dati. Le proprietà della connessione includono il tipo e il nome dell'origine dati e le credenziali da utilizzare. Dopo avere specificato i valori in questa finestra di dialogo, fare clic su **Test connessione** per verificare che l'origine dati sia disponibile e che le credenziali specificate siano corrette. Per altre informazioni sui tipi di origini dati specifici, vedere [Aggiungere dati da origini dati esterne &#40;SSRS&#41;](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md).  
  
    3.  Fare clic su **Credenziali**.  
  
         Specificare le credenziali da utilizzare per questa origine dati. Il tipo di credenziali supportato viene determinato dal proprietario dell'origine dati.  
  
4.  La nuova origine dati incorporata verrà visualizzata nel riquadro Dati report.  
  
## Per creare un'origine dati incorporata in Generatore report  
  
1.  Nel riquadro dei dati del report della barra degli strumenti fare clic su **Nuova**, quindi su **Origine dati**. Verrà visualizzata la finestra di dialogo **Proprietà origine dati** .  
  
2.  Nella casella di testo **Nome** digitare un nome per l'origine dati oppure accettare quello predefinito.  
  
3.  Verificare che l'opzione **Usa una connessione incorporata nel report** sia selezionata.  
  
    1.  Dall'elenco a discesa **Seleziona tipo di connessione** selezionare un tipo di origine dati, ad esempio **Microsoft SQL Server** o **OLE DB**.  
  
    2.  Specificare una stringa di connessione utilizzando una delle alternative seguenti:  
  
        -   Digitare la stringa di connessione direttamente nella casella di testo **Stringa di connessione** . Per esempi di stringhe di connessione, vedere [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md).  
  
        -   Fare clic sul pulsante relativo all'espressione (**fx)**) per creare un'espressione che restituisca una stringa di connessione. Nella finestra di dialogo **Espressione** digitare l'espressione nel riquadro relativo. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
        -   Fare clic su **Compila** per aprire la finestra di dialogo **Proprietà connessione** per il tipo di origine dati scelto nel passaggio 2.  
  
             Nei campi della finestra di dialogo **Proprietà connessione** inserire le informazioni appropriate per il tipo di origine dati. Le proprietà della connessione includono il tipo e il nome dell'origine dati e le credenziali da utilizzare. Dopo avere specificato i valori in questa finestra di dialogo, fare clic su **Test connessione** per verificare che l'origine dati sia disponibile e che le credenziali specificate siano corrette.  
  
4.  Fare clic su **Credenziali**.  
  
     Specificare le credenziali da utilizzare per questa origine dati. Il tipo di credenziali supportato viene determinato dal proprietario dell'origine dati. Per altre informazioni, vedere [Specifica di credenziali in Generatore report](../Topic/Specify%20Credentials%20in%20Report%20Builder.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     L'origine dati verrà visualizzata nel riquadro dei dati del report.  
  
## Vedere anche  
 [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Specifica di credenziali in Generatore report](../Topic/Specify%20Credentials%20in%20Report%20Builder.md)  
  
  