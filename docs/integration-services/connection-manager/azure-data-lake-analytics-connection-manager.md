---
title: Gestione connessione di Azure Data Lake Analytics | Microsoft Docs
description: Un pacchetto di SQL Server Integration Services (SSIS) è in grado di usare la gestione connessione di Azure Data Lake Analytics per connettersi a un account di Data Lake Analytics.
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: a4bcd7368d457b9648baf04285f8e48bcc2a6841
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47691809"
---
# <a name="azure-data-lake-analytics-connection-manager"></a>Gestione connessione di Azure Data Lake Analytics

Un pacchetto di SQL Server Integration Services (SSIS) è in grado di usare la gestione connessione di Azure Data Lake Analytics per connettersi a un account di Data Lake Analytics con uno dei due tipi di autenticazione seguenti:
-   Identità utente di Azure Active Directory (Azure AD)
-   Identità del servizio di Azure AD 

Gestione connessione di Data Lake Analytics è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
 
## <a name="configure-the-connection-manager"></a>Configurare la gestione connessione

1. Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **AzureDataLakeAnalytics** > **Aggiungi**. Viene visualizzata la finestra di dialogo dell'**editor di Gestione connessione di Azure Data Lake Analytics**.
  
2. Nella finestra di dialogo dell'**editor della gestione connessione di Azure Data Lake Analytics** specificare il nome dell'account di Data Lake Analytics nel campo **ADLA Account Name** (Nome account ADLA). Ad esempio: nomeaccountadla.
  
3. Nel campo **Autenticazione** scegliere il tipo di autenticazione appropriato per accedere ai dati in Data Lake Analytics.

   A. Se si seleziona l'opzione di autenticazione **Identità utente di Azure AD**:
   
      i. Specificare i valori per i campi **Nome utente** e **Password**.    
      ii. Fare clic su **Test connessione** per testare la connessione. Se l'utente o l'amministratore del tenant non ha precedentemente autorizzato SSIS ad accedere all'account di Data Lake Analytics, selezionare **Accetto** quando richiesto. Per altre informazioni su questa esperienza di consenso, vedere [Integrazione di applicazioni con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
   > [!NOTE] 
   > Quando si seleziona l'autenticazione dell'**identità del servizio di Azure AD** l'autenticazione a più fattori e l'autenticazione dell'account Microsoft non sono supportate.
    
   B. Se si seleziona l'opzione di autenticazione **Azure AD Service Identity** (Identità del servizio di Azure AD):
   
      i. Creare un'applicazione e l'entità servizio di Azure AD per accedere all'account di Data Lake Analytics. Per altre informazioni su questa opzione di autenticazione, vedere [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) (Usare il portale per creare applicazioni ed entità servizio di Active Directory che possano accedere alle risorse).    
      ii. Assegnare le autorizzazioni appropriate per consentire all'applicazione di Azure AD di accedere all'account di Data Lake Analytics. Informazioni su come concedere autorizzazioni all'account di Data Lake Analytics usando l'[Aggiunta guidata utente](https://docs.microsoft.com/azure/data-lake-analytics/data-lake-analytics-manage-use-portal#add-a-new-user).    
      iii. Specificare i valori per i campi **ID applicazione**, **Chiave di autenticazione** e **ID Tenant**.    
      iv. Fare clic su **Test connessione** per testare la connessione.  

4. Selezionare **OK** per chiudere la finestra di dialogo dell'**editor di Gestione connessione di Azure Data Lake Analytics**.  

## <a name="view-the-properties-of-the-connection-manager"></a>Visualizzare le proprietà della gestione connessione
È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .  
  
  
