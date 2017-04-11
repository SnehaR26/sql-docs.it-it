---
title: "Editor destinazione elaborazione partizione (pagina Gestione connessione) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.partprocessingtransformation.connection.f1"
helpviewer_keywords: 
  - "Editor destinazione elaborazione partizione"
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Editor destinazione elaborazione partizione (pagina Gestione connessione)
  Utilizzare la pagina **Gestione connessione** della finestra di dialogo **Editor destinazione elaborazione partizione** per specificare una connessione a un progetto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Per ulteriori informazioni sulla destinazione elaborazione partizione, vedere [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Le attività qui descritte non si applicano ai modelli tabulari di Analysis Services.  Non è possibile eseguire il mapping di colonne di input a colonne di partizione per i modelli tabulari. È possibile utilizzare invece l'attività Esegui DDL Analysis Services [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) per elaborare la partizione.  
  
## Opzioni  
 **Gestione connessione**  
 Selezionare una gestione connessione esistente nell'elenco o crearne una nuova facendo clic su **Nuova**.  
  
 **Nuovi**  
 Consente di creare una connessione usando la finestra di dialogo **Aggiungi gestione connessione Analysis Services**.  
  
 **Elenco delle partizioni disponibili**  
 Consente di selezionare la partizione da elaborare.  
  
 **Metodo di elaborazione**  
 Consente di selezionare il metodo di elaborazione. Il valore predefinito di questa opzione è **Completo**.  
  
|Valore|Description|  
|-----------|-----------------|  
|Aggiunta (incrementale)|Consente di eseguire un'elaborazione incrementale della partizione.|  
|Completo|Consente di eseguire l'elaborazione completa della partizione.|  
|Solo dati|Consente di eseguire un'elaborazione di aggiornamento della partizione.|  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor destinazione elaborazione partizione &#40;pagina Mapping&#41;](../../integration-services/data-flow/partition-processing-destination-editor-mappings-page.md)   
 [Editor destinazione elaborazione partizione &#40;pagina Avanzate&#41;](../../integration-services/data-flow/partition-processing-destination-editor-advanced-page.md)  
  
  