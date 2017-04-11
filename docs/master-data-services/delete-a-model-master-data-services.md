---
title: "Eliminare un modello (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "eliminazione di modelli [Master Data Services]"
  - "modelli [Master Data Services], eliminazione di modelli"
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Eliminare un modello (Master Data Services)
  Eliminare un modello per rimuoverlo, inclusi tutti i relativi dati, da [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
> [!NOTE]  
>  Quando si completa questa procedura, tutti gli oggetti e tutti i dati di tutte le versioni del modello verranno eliminati in modo permanente.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Per eliminare un modello  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Vista modelli** scegliere **Gestisci** dalla barra dei menu, quindi fare clic su **Modelli**.  
  
3.  Dalla griglia della pagina **Gestione modelli** selezionare la riga per il modello che si vuole eliminare.  
  
4.  Fare clic su **Elimina**.  
  
5.  Nella finestra di dialogo di conferma fare clic su **OK**.  
  
6.  Nell'ulteriore finestra di dialogo di conferma fare clic su **OK**.  
  
 La colonna **Stato** nella griglia mostra lo stato dell'operazione sul modello. Quando si fa clic sul pulsante **Salva modello**, viene visualizzata l'immagine ![Updating](../master-data-services/media/mds-model-status-updating.png "Updating") che indica che il modello è in fase di aggiornamento. Se si verificano errori durante la creazione o la modifica di un modello, viene visualizzata l'immagine ![Error](../master-data-services/media/mds-model-status-error.png "Error"). In caso contrario, lo stato è OK e viene visualizzata l'immagine ![OK](../master-data-services/media/mds-model-status-ok.png "OK").  
  
## Vedere anche  
 [Modelli &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)   
 [Creare un modello &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md)  
  
  