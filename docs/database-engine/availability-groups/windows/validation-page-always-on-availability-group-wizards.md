---
title: "Pagina Convalida (procedure guidate gruppi di disponibilità Always On) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.addreplicawizard.validation.f1
- sql13.swb.adddatabasewizard.validation.f1
- sql13.swb.newagwizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6f8c43c0c8a698fb38f67f7ba6ba0ad897692f00
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="validation-page-always-on-availability-group-wizards"></a>Pagina Convalida (procedure guidate gruppi di disponibilità Always On)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  
    
  Questo argomento della Guida descrive le opzioni della pagina **Convalida** . Questo argomento si applica alla [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], alla [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], alla [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Utilizzare questa pagina per verificare che l'ambiente supporta tutte le scelte di configurazione effettuate nelle pagine precedenti della procedura guidata.  
  
##  <a name="PageOptions"></a> Opzioni della pagina Convalida  
 **Risultati della convalida del gruppo di disponibilità.**  
 In questa griglia vengono visualizzati i risultati di ogni passaggio di convalida completato. Le colonne della griglia sono le seguenti:  
  
 **Nome**  
 Visualizza una frase che descrive un passaggio specifico.  
  
 **Risultato**  
 Visualizza uno dei seguenti testi di collegamenti ipertestuali. Per ulteriori informazioni sul risultato del passaggio di convalida specificato, fare clic sul collegamento ipertestuale.  
  
|Risultato|Descrizione|  
|------------|-----------------|  
|**Errore**|Indica che il passaggio di convalida non è riuscito. Fare clic sul collegamento per visualizzare il messaggio di errore.|  
|**Operazione ignorata**|Indica che il passaggio di convalida è stato ignorato perché non è necessario in base alle selezioni. Fare clic sul collegamento per visualizzare il motivo per cui un passaggio è stato ignorato.|  
|**Operazione completata**|Indica che il passaggio di convalida è riuscito.|  
|**Avviso**|Indica un potenziale problema con la configurazione del gruppo di disponibilità.  Fare clic sul collegamento per visualizzare il messaggio di avviso.|  
  
 **Ripeti convalida**  
 Fare clic per ripetere i passaggi di convalida se si apporta una modifica al di fuori della procedura guidata in risposta a un errore di convalida.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Usare la finestra di dialogo Nuovo gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utilizzare la procedura guidata Aggiungi replica a gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Usare la procedura guidata Aggiungi database a gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
