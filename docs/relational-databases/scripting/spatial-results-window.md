---
title: Finestra Risultati spaziali | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eea2e1f7fd92847368b2b6645df6dafd174468c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614812"
---
# <a name="spatial-results-window"></a>Finestra Risultati spaziali
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  La finestra **Risultati spaziali** fornisce strumenti di mapping visivo per la visualizzazione di dati spaziali. Per visualizzare i risultati spaziali, è necessario che i risultati delle query contengano una colonna spaziale con dati geometrici o geografici.  
  
> [!NOTE]  
>  La finestra **Risultati spaziali** è disponibile solo se i risultati vengono restituiti in una griglia nella finestra **Risultati** . Se si richiede invece la restituzione dei risultati come testo, tale finestra non sarà disponibile.  
  
## <a name="options"></a>Opzioni  
 **Selezionare la colonna spaziale**  
 Consente di specificare la colonna che si desidera visualizzare tra le colonne spaziali nei risultati delle query. È possibile selezionare solo una colonna alla volta.  
  
 **Selezionare la colonna etichetta**  
 Consente di specificare la colonna non spaziale tra le colonne restituite nei risultati delle query per etichettare i dati spaziali. È possibile selezionare solo una colonna alla volta.  
  
 Questa opzione non è disponibile quando in una query vengono restituite solo istanze di punti.  
  
 **Selezionare la proiezione**  
 Consente di visualizzare i dati geografici in quattro tipi di proiezione, ovvero Equirectangular, Mercator, Robinson e Bonne.  
  
 Questa opzione non è disponibile per i dati geometrici.  
  
 **Zoom**  
 Consente di regolare la visualizzazione del mapping in una scala esponenziale.  
  
 **Mostra linee griglia**  
 Consente di attivare o disattivare le linee della griglia delle coordinate.  
  
 Per le forme poligonali, l'etichetta viene visualizzata solo se la forma è grande abbastanza da contenere il testo dell'etichetta. Per visualizzare le etichette di forme di piccole dimensioni, regolare lo zoom.  
  
> [!NOTE]  
>  Non è possibile etichettare le istanze di punti.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di dati spaziali in Esplora oggetti](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Editor di query del motore di database &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Editor di query e di testo &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
