---
title: "Generare automaticamente valori per l&#39;attributo Code (Master Data Services) | Microsoft Docs"
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
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
caps.latest.revision: 5
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 5
---
# Generare automaticamente valori per l&#39;attributo Code (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]vengono automaticamente generati valori per l'attributo Code di un'entità quando si desidera che un valore intero venga assegnato automaticamente al valore Code ogni volta che viene creato un nuovo membro.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Deve essere presente l'entità. Per altre informazioni, vedere [Creare un'entità &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
### Per generare automaticamente valori Code  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modello** selezionare la riga per il modello che contiene l'entità da modificare, quindi fare clic su **Entità**.  
  
3.  Nella pagina **Gestisci entità** selezionare la riga per l'entità per cui generare codici, quindi fare clic su **Modifica**.  
  
4.  Selezionare la casella di controllo **Crea valori Code automaticamente** .  
  
5.  Nella casella **Inizia con** digitare un numero da cui iniziare l'incremento. Se i membri esistono già, il valore Code verrà impostato in base al valore esistente più elevato. Ad esempio, se il valore Code esistente più elevato è 299, il valore Code del membro successivo sarà impostato su 300.  
  
6.  Fare clic su **Salva**.  
  
## Vedere anche  
 [Creazione di codice automatica &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md)   
 [Generare automaticamente valori di attributi diversi da Code &#40;Master Data Services&#41;](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  