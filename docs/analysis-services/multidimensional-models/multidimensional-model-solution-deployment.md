---
title: Distribuzione di soluzioni di modelli multidimensionali | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e5f4b4f7f30ec9f94993e34596d348ae22842fd
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023958"
---
# <a name="multidimensional-model-solution-deployment"></a>Distribuzione di soluzioni di modelli multidimensionali
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dopo aver completato lo sviluppo di un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è possibile distribuire il database in un server Analysis Services. In Analysis Services sono disponibili sei possibili metodi di distribuzione che possono essere utilizzati per spostare il database in un server di prova o di produzione. I metodi di distribuzione sono elencati di seguito in ordine di convenienza: automazione AMO, XMLA, Distribuzione guidata, Utilità di distribuzione, Sincronizzazione guidata database, Backup e ripristino.  
  
 In questo argomento sono contenute le sezioni seguenti:  
  
 [Metodi di distribuzione](#bkmk_meth)  
  
 [Considerazioni sulla distribuzione](#bkmk_considerations)  
  
 [Attività correlate](#bkmk_rel)  
  
##  <a name="bkmk_meth"></a> Metodi di distribuzione  
  
|Metodo|Description|Collegamento|  
|------------|-----------------|----------|  
|**Automazione AMO (Analysis Management Objects)**|AMO (Analysis Management Objects) offre un'interfaccia di programmazione per il set di comandi completo per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], inclusi comandi che possono essere utilizzati per la distribuzione della soluzione. Come approccio per la distribuzione della soluzione, l'automazione AMO (Analysis Management Objects) è la più flessibile, ma richiede anche un lavoro di programmazione.  Il vantaggio principale offerto da AMO è che consente di utilizzare SQL Server Agent insieme all'applicazione AMO per eseguire la distribuzione in base a una pianificazione predefinita.|[Lo sviluppo con Analysis Management Objects & #40; AMO & #41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)|  
|**XMLA**|Utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per generare uno script XMLA dei metadati di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esistente, quindi eseguire tale script in un altro server per ricreare il database iniziale. Per creare script XMLA in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , è sufficiente definire il processo di distribuzione e quindi codificarlo e memorizzarlo in uno script XMLA. Dopo aver salvato lo script XMLA in un file, è possibile eseguire lo script in base a una pianificazione oppure incorporarlo nello script di un'applicazione che si connette direttamente a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].<br /><br /> È inoltre possibile eseguire script XMLA a intervalli predefiniti tramite SQL Server Agent, ma questo metodo non è caratterizzato dalla stessa flessibilità del metodo basato sull'automazione AMO. Nella libreria AMO è disponibile un'ampia gamma di funzionalità che supportano l'insieme completo di comandi amministrativi.|[Distribuire soluzioni di modelli utilizzando XMLA](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)|  
|**Distribuzione guidata**|Distribuzione guidata consente di utilizzare i file di output XMLA generati da un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per distribuire i metadati del progetto in un server di destinazione. Grazie alla Distribuzione guidata è possibile eseguire la distribuzione direttamente dal file di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] creato nella directory di output tramite la compilazione del progetto.<br /><br /> Il vantaggio principale rappresentato dall'utilizzo della Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è la praticità. È possibile salvare script della Distribuzione guidata nello stesso modo in cui è possibile salvare uno script XMLA per un utilizzo successivo in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. La Distribuzione guidata può essere eseguita sia in modalità interattiva sia dal prompt dei comandi tramite l'utilità di distribuzione.|[Distribuire soluzioni di modelli tramite la distribuzione guidata](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)|  
|**Utilità di distribuzione**|L'utilità di distribuzione consente di avviare il motore di distribuzione di Analysis Services da un prompt dei comandi.|[Distribuire soluzioni di modelli con l'utilità di distribuzione](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|  
|**Sincronizzazione guidata database**|Sincronizzazione guidata database consente di sincronizzare i metadati e i dati tra due database qualsiasi di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .<br /><br /> È possibile utilizzare la Sincronizzazione guidata database per copiare sia dati sia metadati da un server di origine in un server di destinazione. Se nel server di destinazione non è disponibile una copia del database che si desidera distribuire, in tale server viene copiato un nuovo database. Se invece nel database di destinazione è già inclusa una copia dello stesso database, il database nel server di destinazione viene aggiornato per utilizzare i metadati e i dati del database di origine.|[Sincronizzare i database di Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)|  
|**Backup e ripristino**|Il backup rappresenta il metodo di trasferimento di database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] più semplice. Nella finestra di dialogo **Backup** è possibile definire la configurazione delle opzioni desiderate e quindi eseguire il backup dalla finestra di dialogo stessa. In alternativa, è possibile creare uno script che può essere salvato ed eseguito in base alle specifiche esigenze.<br /><br /> Il metodo Backup e ripristino non viene utilizzato con la stessa frequenza degli altri metodi, anche se consente di completare rapidamente un'operazione di distribuzione con requisiti di infrastrutture minimi.|[Backup e ripristino di database di Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)|  
  
##  <a name="bkmk_considerations"></a> Considerazioni sulla distribuzione  
 Prima di distribuire un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , si considerino quali di queste domande riguardano la soluzione in uso, quindi controllare il collegamento correlato per apprendere come risolvere il problema:  
  
|Considerazione|Collegamento a ulteriori informazioni|  
|-------------------|------------------------------|  
|Quali risorse hardware e software sono richieste per questa soluzione?|[Requisiti e considerazioni per la distribuzione di Analysis Services](../../analysis-services/multidimensional-models/requirements-and-considerations-for-analysis-services-deployment.md)|  
|Come verranno distribuiti gli oggetti correlati che non rientrano nell'ambito del progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , quali pacchetti, report o schemi del database relazionale di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ?||  
|Come sono stati caricati e aggiornati i dati nel database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuito?<br /><br /> Come verranno aggiornati i metadati (ad esempio calcoli) nel database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuito?|[Metodi di distribuzione](#bkmk_meth) in questo argomento.|  
|Si desidera concedere agli utenti l'accesso ai dati di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tramite Internet?|[Configurare l'accesso HTTP ad Analysis Services in Internet Information Services & #40; IIS & #41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)|  
|Si desidera fornire accesso continuo ai dati [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per query?|[Requisiti e considerazioni per la distribuzione di Analysis Services](../../analysis-services/multidimensional-models/requirements-and-considerations-for-analysis-services-deployment.md)|  
|Si desidera distribuire oggetti in un ambiente distribuito utilizzando oggetti collegati o partizioni remote?|[Creare e gestire una partizione locale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md), [Creare e gestire una partizione remota &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) e [Gruppi di misure collegati](../../analysis-services/multidimensional-models/linked-measure-groups.md).|  
|Come verranno protetti i dati di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]?|[Per l'autorizzazione di accesso per gli oggetti e operazioni & #40; Analysis Services & #41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)|  
  
##  <a name="bkmk_rel"></a> Attività correlate  
 [Requisiti e considerazioni per la distribuzione di Analysis Services](../../analysis-services/multidimensional-models/requirements-and-considerations-for-analysis-services-deployment.md)  
  
 [Distribuire soluzioni di modelli utilizzando XMLA](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)  
  
 [Distribuire soluzioni di modelli tramite la distribuzione guidata](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)  
  
 [Distribuire soluzioni di modelli con l'utilità di distribuzione](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  
