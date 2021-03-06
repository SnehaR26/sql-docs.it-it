---
title: Attributo definisce il profilo della scheda (Visualizzatore modello di Data Mining) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4c216ce257c513d59a5007637ca4a5642104306f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194541"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a>Scheda Profili attributo (Visualizzatore modello di data mining)
  Usare la scheda **Profili attributo** per vedere il modo in cui la distribuzione dei valori di input in uno stato del modello Naive Bayes contribuisce a ogni stato dell'attributo risultante. La distribuzione dei valori viene mostrata come un istogramma colorato e tutte le distribuzioni vengono presentate in un formato tabulare per rendere più semplice il confronto dei valori.  
  
 **Per altre informazioni:** [Algoritmo Microsoft Naive Bayes](data-mining/microsoft-naive-bayes-algorithm.md)e [Visualizzare un modello utilizzando il Visualizzatore Microsoft Naive Bayes](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Opzioni  
 **Aggiorna contenuto visualizzatore**  
 Consente di ricaricare il modello di data mining nel visualizzatore.  
  
 **Modello di data mining**  
 Consente di scegliere un modello di data mining da visualizzare tra quelli presenti nella struttura di data mining corrente. Il modello di data mining verrà aperto nel visualizzatore associato.  
  
 **Visualizzatore**  
 Consente di scegliere un visualizzatore da utilizzare per l'esplorazione del modello di data mining selezionato. È possibile scegliere il visualizzatore personalizzato fornito per ogni modello di data mining o il Visualizzatore contenuto di data mining [!INCLUDE[msCoName](../includes/msconame-md.md)] . Se disponibili, è anche possibile utilizzare i visualizzatori plug-in.  
  
 **Mostra legenda**  
 Selezionare questa opzione per visualizzare una chiave che consente di far corrispondere ogni valore disponibile in **Stati** a uno dei colori usati nel grafico di distribuzione.  
  
 **Barre istogramma**  
 Consente di selezionare il numero di barre da includere nell'istogramma. Se esistono più barre di quante ne sono state scelte per la visualizzazione, le barre di importanza più alta vengono mantenute, mentre le barre rimanenti vengono raggruppate in **Altro**.  
  
 **Prevedibili**  
 Consente di selezionare una colonna stimabile nel modello di data mining.  
  
 **Profili attributo**  
 La tabella contiene le colonne seguenti:  
  
|valore|Description|  
|-----------|-----------------|  
|**Attributi**|Elenca le colonne del modello di data mining contenute nel modello di data mining.|  
|**Stati**|Colonna facoltativa che descrive lo stato rappresentato dal colore nella riga degli attributi. Aggiungere o rimuovere la colonna usando la casella di controllo **Mostra legenda** .|  
|**Popolazione**|Consente di visualizzare la distribuzione dell'attributo nell'intero set di dati.|  
|**Colonna per gli Stati dell'attributo stimabile**|Consente di visualizzare una colonna per ogni stato della colonna stimabile, con ogni riga corrispondente a un attributo di input nel modello.|  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visualizzatori modello di data mining &#40;Progettazione modelli di Data Mining&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visualizzatori modello di data mining](data-mining/data-mining-model-viewers.md)  
  
  
