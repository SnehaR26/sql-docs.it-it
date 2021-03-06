---
title: Selezione metodo di creazione (Creazione guidata cubo) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 48a6ef3849e91f606cb94ae7fa1f7c67817bfff7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152807"
---
# <a name="select-creation-method-cube-wizard"></a>Seleziona metodo di creazione (Creazione guidata cubo)
  Utilizzare la pagina **Seleziona metodo di creazione** per specificare la modalità di creazione del cubo.  
  
## <a name="options"></a>Opzioni  
 **Usa tabelle esistenti**  
 Selezionare per creare un cubo utilizzando le tabelle esistenti in un'origine dati. La procedura guidata descriverà dettagliatamente il processo di selezione e definizione dei gruppi di misure e delle dimensioni in base alle tabelle esistenti per compilare il cubo nuovo.  
  
 **Creare un cubo vuoto**  
 Selezionare per creare un cubo vuoto. Questa opzione è utile per creare tutto manualmente o quando tutti i gruppi di misure nel cubo sono gruppi di misure collegati.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo quando si lavora a un progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e non quando si è connessi direttamente a un database [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Genera tabelle nell'origine dati**  
 Selezionare per creare prima un cubo e quindi generare tabelle nuove nell'origine dati in base alla definizione del cubo.  
  
> [!NOTE]  
>  Per utilizzare questa opzione, si deve disporre delle autorizzazioni per creare gli oggetti nell'origine dei dati sottostante.  
  
 La selezione di questa opzione renderà disponibile l'opzione **Modello** .  
  
 **Modello**  
 Selezionare il modello che si desidera utilizzare per creare il cubo. I modelli offrono un set completo di definizioni orientate ad applicazioni aziendali specifiche.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo quando l'opzione viene selezionata l'opzione **Genera tabelle nell'origine dati** .  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti cubo &#40;Analysis Services - dati multidimensionali&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)   
 [Cubi nei modelli multidimensionali](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Dimensioni nei modelli multidimensionali](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
