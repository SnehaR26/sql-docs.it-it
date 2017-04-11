---
title: "Gestire gli avvisi dati in Gestione avvisi dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestione, avvisi"
  - "gestione, avvisi dati"
ms.assetid: e0e4ffdf-bd4c-4ebd-872b-07486cbb47c2
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 13
---
# Gestire gli avvisi dati in Gestione avvisi dati
  Gli utenti di SharePoint possono visualizzare un elenco degli avvisi dati creati e le informazioni sugli avvisi. Possono inoltre eliminare i propri avvisi, aprire definizioni di avviso per la modifica nella finestra di progettazione Avviso dati ed eseguire i propri avvisi. Nella figura seguente sono illustrate le funzionalità disponibili per gli utenti in Gestione avvisi dati.  
  
 ![Funzionalità di Gestione avvisi per gli utenti di SharePoint](../reporting-services/media/rs-alertmanageriw.gif "Funzionalità di Gestione avvisi per gli utenti di SharePoint")  
  
### Per visualizzare un elenco di avvisi  
  
1.  Passare alla raccolta di SharePoint in cui sono stati salvati i report per i quali sono stati creati avvisi dati.  
  
2.  Fare clic sull'icona per espandere il menu a discesa in un report, quindi fare clic su **Gestisci avvisi dati**. Nella figura seguente è illustrato il menu a discesa.  
  
     ![Aprire Gestione avvisi dal menu di scelta rapida del report](../reporting-services/media/rs-openalertmanager.gif "Aprire Gestione avvisi dal menu di scelta rapida del report")  
  
     Verrà aperto Gestione avvisi dati. Per impostazione predefinita, vengono elencati gli avvisi per il report selezionati nella raccolta.  
  
3.  Fare clic sulla freccia GIÙ accanto all'elenco **Visualizza avvisi per il report** e selezionare un report per visualizzare i relativi avvisi oppure fare clic su **Mostra tutto** per elencare tutti gli avvisi.  
  
    > [!NOTE]  
    >  Se il report selezionato non dispone di avvisi, non è necessario tornare alla raccolta di SharePoint per individuare e selezionare un report che disponga di avvisi. È invece possibile fare clic su **Mostra tutto** per visualizzare un elenco di tutti gli avvisi.  
  
     In una tabella vengono elencati il nome dell'avviso, il nome del report, il nome del creatore dell'avviso, il numero di volte in cui l'avviso è stato inviato, l'ultima modifica alla definizione di avviso e lo stato dell'avviso. Se l'avviso non può essere generato o inviato, nella colonna relativa allo stato sono incluse informazioni sull'errore che consentono di risolvere il problema.  
  
### Per modificare una definizione di avviso  
  
-   Fare clic con il pulsante destro del mouse sull'avviso dati per il quale si desidera modificare la definizione, quindi scegliere **Modifica**.  
  
     La definizione di avviso viene aperta in Gestione avvisi dati. Per altre informazioni, vedere [Modificare un avviso dati nella finestra di progettazione di avvisi](../reporting-services/edit-a-data-alert-in-alert-designer.md) e [Finestra di progettazione Avviso dati](../reporting-services/data-alert-designer.md).  
  
    > [!NOTE]  
    >  La definizione di avviso dati può essere modificata solo dall'utente che l'ha creata.  
  
    > [!NOTE]  
    >  Se il report è cambiato e i feed di dati generati dal report sono cambiati, la definizione di avviso potrebbe non essere più valida. Questa condizione si verifica quando una colonna, a cui fa riferimento l'avviso nelle regole, viene eliminata dal report, quando il tipo di dati contenuto in tale colonna viene modificato, quando la colonna viene inclusa in un feed di dati diverso oppure quando il report viene eliminato o spostato. È possibile aprire una definizione di avviso che non è valida, ma non è possibile salvarla di nuovo fino a quando non diventa valida in base alla versione corrente del feed di dati del report in base a cui è compilata. Per sapere di più sulla modalità di generazione di feed di dati dai report, vedere [Generazione di feed di dati dai report &#40;Generatore report e SSRS&#41;](../reporting-services/report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
### Per eliminare una definizione di avviso  
  
-   Fare clic con il pulsante destro del mouse sull'avviso dati che si desidera eliminare, quindi scegliere **Elimina**.  
  
     Dopo avere eliminato l'avviso, non verranno inviati ulteriori messaggi di avviso.  
  
### Per eseguire un avviso  
  
-   Fare clic con il pulsante destro del mouse sull'avviso dati che si desidera eseguire, quindi scegliere **Esegui**.  
  
     L'istanza di avviso viene creata e il messaggio di avviso dati viene inviato immediatamente, indipendentemente dalle opzioni di pianificazione specificate nella finestra di progettazione Avviso dati. Un avviso configurato per essere inviato ogni settimana e solo se i risultati cambiano viene ad esempio inviato.  
  
## Vedere anche  
 [Gestione avvisi dati per gli amministratori di avvisi](../reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Avvisi dati di Reporting Services](../reporting-services/reporting-services-data-alerts.md)  
  
  