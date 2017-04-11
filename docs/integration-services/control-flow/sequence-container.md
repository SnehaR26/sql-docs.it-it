---
title: "Contenitore Sequenza | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sequencecontainer.f1"
helpviewer_keywords: 
  - "Sequenza - contenitore"
  - "raggruppamento di flussi di dati"
  - "contenitori [Integration Services], sequenza"
  - "subset di un flusso di controllo [Integration Services]"
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 48
---
# Contenitore Sequenza
  Il contenitore Sequenza definisce un flusso di controllo costituito da un subset del flusso di controllo del pacchetto. I contenitori Sequenza suddividono il pacchetto in più flussi di controllo separati, ognuno dei quali include una o più attività e contenitori che vengono eseguiti nel flusso di controllo globale del pacchetto.  
  
 Il contenitore Sequenza può includere più attività, oltre ad altri contenitori. L'aggiunta di attività e contenitori a un contenitore Sequenza è analoga all'aggiunta di tali elementi a un pacchetto, con la differenza che è necessario trascinare attività e contenitori nel contenitore Sequenza anziché nel contenitore del pacchetto. Se il contenitore Sequenza include più di un contenitore o attività, è possibile connettere tali elementi utilizzando vincoli di precedenza, come avviene nei pacchetti. Per altre informazioni, vedere [Vincoli di precedenza](../../integration-services/control-flow/precedence-constraints.md).  
  
 L'utilizzo del contenitore Sequenza offre molti vantaggi:  
  
-   Consente di disabilitare gruppi di attività per indirizzare il debug su un subset del flusso di controllo del pacchetto.  
  
-   Consente di gestire le proprietà di più attività da un'unica posizione, tramite l'impostazione di proprietà su un contenitore Sequenza anziché sulle singole attività.  
  
     È ad esempio possibile impostare su **True** la proprietà **Disable** del contenitore Sequenza per disabilitare tutti i contenitori e le attività inclusi.  
  
-   Fornisce l'ambito per le variabili utilizzate da un gruppo di attività e contenitori correlati.  
  
-   Consente di raggruppare più attività in modo da poterle gestire più facilmente comprimendo ed espandendo il contenitore Sequenza.  
  
     È inoltre possibile creare gruppi di attività che possono essere compressi ed espansi usando la casella **Gruppo**. La casella **Gruppo** è tuttavia una caratteristica della fase di progettazione che non dispone di proprietà o comportamento in fase di esecuzione. Per altre informazioni, vedere [Raggruppare o separare componenti](../../integration-services/group-or-ungroup-components.md)  
  
-   Impostare un attributo di transazione sul contenitore Sequenza per definire una transazione per un subset del flusso di controllo del pacchetto. In questo modo è possibile gestire le transazioni con un livello di granularità superiore.  
  
     Se ad esempio un contenitore Sequenza include due attività correlate, una che elimina dati da una tabella e un'altra che inserisce dati in una tabella, è possibile configurare una transazione per garantire che se non dovesse riuscire l'azione di inserimento, verrà eseguito il rollback dell'azione di eliminazione. Per altre informazioni, vedere [Transazioni di Integration Services](../../integration-services/integration-services-transactions.md).  
  
## Configurazione del contenitore Sequenza  
 Il contenitore Sequenza non dispone di un'interfaccia utente personalizzata e può essere configurato solo tramite la finestra **Proprietà** di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] o a livello di codice.  
  
 Per informazioni sull'impostazione a livello di codice di queste proprietà, vedere la documentazione relativa alla classe **T:Microsoft.SqlServer.Dts.Runtime.Sequence** nella Guida per gli sviluppatori.  
  
## Attività correlate  
 Per informazioni su come impostare le proprietà del componente, vedere nel [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vedere [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md).  
  
## Vedere anche  
 [Aggiunta o eliminazione di un'attività o un contenitore in un flusso di controllo](../../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Connessione di attività e contenitori tramite un vincolo di precedenza predefinito](../Topic/Connect%20Tasks%20and%20Containers%20by%20Using%20a%20Default%20Precedence%20Constraint.md)   
 [Contenitori in Integration Services](../../integration-services/control-flow/integration-services-containers.md)  
  
  