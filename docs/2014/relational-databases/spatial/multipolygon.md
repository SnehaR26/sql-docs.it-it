---
title: MultiPolygon | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3ae25be65e0fdf0cf88bf8dec6cf5c3f59f9c9e6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311403"
---
# <a name="multipolygon"></a>MultiPolygon
  Oggetto `MultiPolygon` istanza è una raccolta di zero o più `Polygon` istanze.  
  
## <a name="polygon-instances"></a>Istanze Polygon  
 La figura seguente mostra esempi di `MultiPolygon` istanze.  
  
 ![Esempi di istanze di geometria MultiPolygon](../../database-engine/media/multipolygon.gif "Esempi di istanze di geometria MultiPolygon")  
  
 Come indicato nell'illustrazione:  
  
-   Figura 1 è un `MultiPolygon` istanza con due `Polygon` elementi. Il limite è definito dai due anelli esterni e dai tre anelli interni.  
  
-   Nella figura 2 viene rappresentata un'istanza `MultiPolygon` con due elementi `Polygon`. Il limite è definito dai due anelli esterni e dai tre anelli interni. I due elementi `Polygon` si intersecano in un punto di tangenza.  
  
### <a name="accepted-instances"></a>Istanze accettate  
 Oggetto `MultiPolygon` istanza viene accettata una delle seguenti condizioni è soddisfatta.  
  
-   È un oggetto vuoto `MultiPolygon` istanza.  
  
-   Tutte le istanze che comprendono il `MultiPolygon` istanza vengono accettati `Polygon` istanze. Per altre informazioni su accettato `Polygon` istanze, vedere [poligono](../spatial/polygon.md).  
  
 Negli esempi seguenti vengono illustrate alcune istanze `MultiPolygon` accettate.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
```  
  
 Nell'esempio seguente viene illustrata un'istanza MultiPolygon che genererà un'eccezione `System.FormatException`.  
  
```  
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';  
```  
  
 La seconda istanza in MultiPolygon è un'istanza di LineString e non un'istanza Polygon accettata.  
  
### <a name="valid-instances"></a>Istanze valide  
 Un'istanza `MultiPolygon` è valida se è un'istanza `MultiPolygon` vuota o se soddisfa i criteri indicati di seguito.  
  
1.  Tutte le istanze che comprendono l'istanza `MultiPolygon` sono istanze `Polygon` valide. Per valido `Polygon` istanze, vedere [poligono](../spatial/polygon.md).  
  
2.  Nessuna delle istanze `Polygon` che comprendono l'istanza `MultiPolygon` si sovrappone.  
  
 Nell'esempio seguente vengono indicate due istanze `MultiPolygon` valide e un'istanza `MultiPolygon` valida.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g2` è valido perché i due `Polygon` istanze si toccano solo in un punto tangente. `@g3` non è valida perché gli interni dei due `Polygon` istanze si sovrappongono tra loro.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente illustra la creazione di un'istanza `geometry``MultiPolygon` e viene restituito il Well-Known Text (WKT) del secondo componente.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');  
SELECT @g.STGeometryN(2).STAsText();  
```  
  
 In questo esempio viene creata un'istanza `MultiPolygon` vuota.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Polygon](../spatial/polygon.md)   
 [STArea &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type)   
 [STCentroid &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)   
 [STPointOnSurface &#40;tipodi dati geometry&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [Dati spaziali &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)  
  
  