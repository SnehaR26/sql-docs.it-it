---
title: Opzioni di backup | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 44251ff0abf155564102f0cf94ca8cd998718462
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34020928"
---
# <a name="backup-options"></a>Opzioni di backup
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  È possibile eseguire il backup dei database di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in molti modi e in tutti i casi è necessario disporre delle autorizzazioni di amministratore del server e del database. È possibile visualizzare la finestra di dialogo **Backup** di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], selezionare le opzioni di configurazione appropriate e quindi eseguire il backup dalla finestra di dialogo. In alternativa, è possibile creare uno script utilizzando le impostazioni già specificate nel file. Sarà quindi possibile salvare lo script ed eseguirlo quando necessario.  
  
## <a name="backup-and-synchronize"></a>Backup e sincronizzazione  
 Se il database si trova in un'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è possibile usare la caratteristica di sincronizzazione per eseguire il backup del database nell'istanza locale. In questo modo, è possibile spostare le build di sviluppo di un database nell'ambiente di produzione. Per spostare la build di sviluppo nell'ambiente di produzione, è inoltre possibile utilizzare le procedure tradizionali di backup e ripristino basate su file, ma la sincronizzazione offre funzionalità aggiuntive. Il computer di sviluppo e quello di produzione potrebbero, ad esempio, avere impostazioni di sicurezza diverse. Tramite la sincronizzazione è possibile mantenere tali impostazioni e sincronizzare tutti gli oggetti a esclusione dei ruoli. La sincronizzazione, inoltre, comporta in genere un aggiornamento incrementale degli oggetti che sono diversi nei computer di origine e in quelli di destinazione. Questo tipo di backup incrementale non è disponibile quando si utilizza la caratteristica di backup e ripristino. Per altre informazioni, vedere [Sincronizzare database di Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md).  
  
> [!IMPORTANT]  
>  L'account del servizio Analysis Services deve disporre delle autorizzazioni per scrivere nel percorso di backup specificato per ogni file. L'utente deve inoltre avere uno dei ruoli seguenti: ruolo di amministratore per l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o membro di un ruolo del database con autorizzazioni Controllo completo (amministratore) per il database di cui eseguire il backup.  
  
## <a name="see-also"></a>Vedere anche  
 [Nella finestra di dialogo backup Database & #40; Analysis Services - dati multidimensionali & #41;](http://msdn.microsoft.com/library/7811ce7d-6c37-4189-bfa6-ef36fb4932db)   
 [Backup e ripristino di database di Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Elemento backup & #40; XMLA & #41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Il backup, ripristino e sincronizzazione di database & #40; XMLA & #41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
