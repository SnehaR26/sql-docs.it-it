---
title: Attivare l'integrazione di Power Pivot per le raccolte siti in Autorità di certificazione | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77c8cb0d9e9617bfa0560ae1e9bc6389a297a5c2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34026118"
---
# <a name="activate-power-pivot-integration-for-site-collections-in-ca"></a>Attivare l'integrazione di Power Pivot per le raccolte siti in Autorità di certificazione
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  L'attivazione dell'integrazione della caratteristica [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per raccolte siti specifiche è obbligatoria se è stata usata l'opzione di installazione Farm esistente per installare SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint. Se [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint è stato installato usando l'opzione Nuovo server, è possibile ignorare questa attività perché il programma di installazione di SQL Server ha già attivato l'integrazione della caratteristica [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per la raccolta siti radice durante la configurazione della distribuzione.  
  
 L'attivazione della caratteristica a livello di raccolta siti è necessaria per rendere disponibili pagine e modelli ai siti, incluse le pagine di configurazione per l'aggiornamento dei dati pianificato e le pagine dell'applicazione per Raccolta [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e raccolte Feed di dati.  
  
 È necessario attivare l'integrazione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per ogni raccolta siti in cui è supportata l'elaborazione di query [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## <a name="prerequisites"></a>Prerequisiti  
 È necessario essere un amministratore della raccolta siti.  
  
## <a name="activate-power-pivot-features"></a>Attivare le funzionalità di Power Pivot  
  
1.  Da un sito di SharePoint scegliere **Azioni sito**.  
  
     Per impostazione predefinita, l'accesso alle applicazioni Web SharePoint viene effettuato tramite la porta 80. Ciò significa che è possibile accedere spesso a un sito di SharePoint immettendo http://\<nome computer > per aprire la raccolta siti radice.  
  
2.  Fare clic su **Impostazioni sito**.  
  
3.  In Amministrazione raccolta siti selezionare **Caratteristiche raccolta siti**.  
  
4.  Scorrere la pagina verso il basso fino a trovare **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Caratteristica della raccolta siti per l'integrazione**di .  
  
5.  Fare clic su **Attiva**.  
  
6.  Ripetere per le raccolte siti aggiuntive aprendo ogni sito e facendo clic su **Azioni sito**.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione e configurazione del server PowerPivot in Amministrazione centrale](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Configurazione iniziale (Power Pivot per SharePoint)](http://msdn.microsoft.com/en-us/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)   
 [Installazione di Power Pivot per SharePoint 2010](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
  
