---
title: "Assegnare autorizzazioni membri gerarchia (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "autorizzazioni [Master Data Services], assegnazione di autorizzazioni membri"
  - "membri [Master Data Services], assegnazione di autorizzazioni"
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Assegnare autorizzazioni membri gerarchia (Master Data Services)
  Assegnare autorizzazioni ai membri della gerarchia per consentire a utenti o gruppi di accedere e visualizzare i dati nell'area funzionale **Visualizzatore** di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Le autorizzazioni membri gerarchia sono facoltative. Forniscono maggiore granularità alle autorizzazioni dell'oggetto modello, che sono invece obbligatorie.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Autorizzazioni utenti e gruppi** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Per assegnare autorizzazioni membri gerarchia  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Autorizzazioni utenti e gruppi**.  
  
2.  Nella pagina **Utenti** o **Gruppi** selezionare la riga relativa all'utente o al gruppo che si desidera modificare.  
  
3.  Fare clic su **Modifica utente selezionato**.  
  
4.  Fare clic sulla scheda **Membri gerarchia**.  
  
5.  Selezionare un modello dall'elenco **Modello**.  
  
6.  Selezionare una versione dall'elenco **Versione** .  
  
7.  Selezionare una gerarchia dall'elenco **Gerarchia**.  
  
8.  Fare clic su **Modifica**.  
  
9. Espandere l'albero e selezionare il nodo della gerarchia al quale si desidera assegnare le autorizzazioni.  
  
10. Dal menu selezionare una combinazione di autorizzazioni **Create**, **Read, Update** e **Delete** o **Deny**.  
  
11. Fare clic su **Salva**.  
  
    > [!NOTE]  
    >  Le autorizzazioni membri gerarchia non vengono applicate immediatamente. Per altre informazioni, vedere [Applicare immediatamente autorizzazioni membri &#40;Master Data Services&#41;](../master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
## Vedere anche  
 [Eliminare le autorizzazioni membri gerarchia &#40;Master Data Services&#41;](../master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorizzazioni membri gerarchie &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  