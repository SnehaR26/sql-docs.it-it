---
title: Escludere le righe duplicate (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: db0e9de67c06ef5a11bf2a33a8d9259bc687979c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47609299"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Escludere le righe duplicate (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Per visualizzare solo valori univoci in un set di risultati, è possibile impostare l'esclusione dei duplicati dai risultati.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>Per escludere le righe duplicate dal set di risultati  
  
1.  Fare clic con il pulsante destro del mouse sullo sfondo del riquadro diagramma e scegliere **Proprietà** dal menu di scelta rapida.  
  
2.  Nella finestra Proprietà fare clic su **Valori Distinct** e impostare il valore su **Sì**.  
  
    In Progettazione query e Progettazione viste la parola chiave DISTINCT verrà inserita davanti all'elenco di colonne visualizzate nell'istruzione SQL.  
  
    > [!NOTE]  
    > Se si utilizza la parola chiave DISTINCT, potrebbe non essere possibile modificare il set di risultati nel riquadro Risultati.  
  
## <a name="see-also"></a>Vedere anche  
[Specifica dei criteri di ricerca &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Ordinare e raggruppare i risultati delle query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  
