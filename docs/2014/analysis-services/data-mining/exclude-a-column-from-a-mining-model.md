---
title: Escludere una colonna da un modello di Data Mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 656e9dc84c2556cc4f5ea76858764ee9c1fbf556
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068879"
---
# <a name="exclude-a-column-from-a-mining-model"></a>Escludere una colonna da un modello di data mining
  Quando si crea un nuovo modello di data mining, potrebbe non essere necessario utilizzare tutte le colonne presenti nella struttura di data mining su cui il modello è basato. È ad esempio probabile che sia stata aggiunta una colonna nome cliente per il drill-through, ma che non si desideri utilizzarla per la modellazione. In alternativa, è possibile decidere di creare più copie di una colonna con discretizzazioni diverse e utilizzare solo una delle copie in ogni modello e ignorare il resto. È anche possibile aggiungere in modo selettivo le colonne di input in molti modelli diversi per capire come la variabile aggiunta influisce sulla colonna di output.  
  
 Non è necessario creare una nuova struttura di data mining per ogni combinazione di colonne; è semplicemente possibile contrassegnare una colonna come non utilizzata in un determinato modello.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>Per escludere una colonna da un modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]selezionare la cella corrispondente alla colonna che si desidera escludere, nel modello di data mining appropriato.  
  
2.  Selezionare **Ignora** nell'elenco a discesa.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](mining-model-tasks-and-how-tos.md)  
  
  
