---
title: 'Lezione 3: Contrassegna come tabella data | Microsoft Docs'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7cb63b6cb67303dd763263b7d9dbeea30cfc4e3b
ms.sourcegitcommit: e8e013b4d4fbd3b25f85fd6318d3ca8ddf73f31e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2018
ms.locfileid: "42791982"
---
# <a name="lesson-3-mark-as-date-table"></a>Lezione 3: Contrassegnare come tabella data
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Nella Lezione 2: Aggiungere dati è stata importata una tabella delle dimensioni denominata DimDate. Mentre nel modello questa tabella è denominata DimDate, può anche essere nota come un *tabella data*, perché contiene dati di data e ora.  
  
Ogni volta che si usano funzioni di business intelligence DAX nei calcoli, quando si effettueranno quando si creano misure leggermente in un secondo momento, è necessario specificare le proprietà di tabella data, tra cui una *tabella data* e un identificatore univoco *Data colonna* in tale tabella.
  
In questa lezione, si sarà contrassegna la tabella DimDate come le *tabella data* e la colonna Data (nella tabella Date) come il *colonna delle Date* (identificatore univoco).  

Prima si contrassegna la tabella relativa alla data e la colonna di date, è necessario eseguire alcune attività di manutenzione per rendere più facile da comprendere il modello. Si noterà che nella tabella DimDate una colonna denominata **FullDateAlternateKey**. Contiene una riga per ogni giorno dell'anno di calendario incluso nella tabella. Verrà usato in questa colonna molto nelle formule per le misure e nei report. Ma FullDateAlternateKey non è davvero un buon identificatore per questa colonna. È possibile rinominarlo in **data**, rendendo più semplice identificare e includere nelle formule. Quando possibile, è consigliabile rinominare gli oggetti, ad esempio tabelle e colonne per renderle più facilmente identificabile nel client reporting applicazioni come Excel e Power BI. 
  
Tempo stimato per il completamento della lezione: **3 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 2: aggiungere dati](../analysis-services/lesson-2-add-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Per rinominare la colonna FullDateAlternateKey

1.  In Progettazione modelli, scegliere il **DimDate** tabella.

2.  Fare doppio clic sull'intestazione per il **FullDateAlternateKey** colonna e quindi rinominarla **data**.

  
### <a name="to-set-mark-as-date-table"></a>Per impostare Contrassegna come tabella data  
  
1.  Selezionare la colonna **Data** , quindi nella finestra **Proprietà** verificare che **Data**sia selezionata in  **Tipo di dati** .  
  
2.  Fare clic sul menu **Tabella** , selezionare **Data**, quindi scegliere **Contrassegna come tabella data**.  
  
3.  Nella casella di riepilogo **Data** della finestra di dialogo **Contrassegna come tabella data** selezionare la colonna **Data** come identificatore univoco. Verrà in genere selezionato per impostazione predefinita. Fare clic su **OK**. 

    ![come in formato tabulare-lezione 3-data-tabella-](../analysis-services/media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>Quali sono le operazioni successive?
Passare alla lezione successiva: [lezione 4: creare relazioni](../analysis-services/lesson-4-create-relationships.md).
  
