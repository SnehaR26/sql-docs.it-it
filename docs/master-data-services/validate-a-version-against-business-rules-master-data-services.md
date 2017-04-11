---
title: "Convalidare una versione rispetto a regole business (Master Data Services) | Microsoft Docs"
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
  - "convalida di versioni [Master Data Services]"
  - "convalida di versioni [Master Data Services], informazioni"
  - "versioni [Master Data Services], convalida"
  - "regole business [Master Data Services], applicazione a tutti i membri"
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Convalidare una versione rispetto a regole business (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] convalidare una versione per applicare regole di business a tutti i membri nella versione del modello.  
  
 In questa procedura viene illustrato come usare l'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] per convalidare i dati. Se si dispone dell'autorizzazione nel database MDS, è possibile utilizzare una stored procedure. Per altre informazioni, vedere [Stored procedure di convalida &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md).  
  
> [!NOTE]  
>  Tutti i membri devono superare la convalida prima che possa essere eseguito il commit di una versione.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale **Gestione versioni**.  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Lo stato della versione deve essere **Aperto** o **Bloccato**.  
  
-   Nella pagina **Convalida versioni** devono essere presenti membri con uno stato diverso da **Convalida completata**.  
  
### Per convalidare una versione  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Gestione versioni**.  
  
2.  Nella pagina **Gestisci versioni** scegliere **Convalida versione** dalla barra dei menu.  
  
3.  Nella pagina **Convalida versioni** selezionare il modello e la versione che si desidera convalidare.  
  
4.  Fare clic su **Convalida**.  
  
5.  Nella finestra di dialogo di conferma fare clic su **OK**.  
  
    > [!NOTE]  
    >  Quando non è più visualizzato l'indicatore di stato, la versione ha terminato la convalida.  
  
## Passaggi successivi  
  
-   [Bloccare una versione &#40;Master Data Services&#41;](../master-data-services/lock-a-version-master-data-services.md)  
  
## Vedere anche  
 [Stati di convalida &#40;Master Data Services&#41;](../master-data-services/validation-statuses-master-data-services.md)   
 [Stored procedure di convalida &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Versioni &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [Regole di business &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)   
 [Convalidare membri specifici rispetto a regole business &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  