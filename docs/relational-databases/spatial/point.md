---
title: "Punto | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Point - sottotipo di geometria [SQL Server]"
  - "tipo di dati geometry [SQL Server], dati spaziali"
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Punto
  Nei dati spaziali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un **punto** è un oggetto senza dimensioni che rappresenta una sola posizione e può contenere valori Z (innalzamento) e M (misura).  
  
## Tipo di dati geography  
 Il tipo Punto del tipo di dati geography rappresenta una singola posizione in cui *Lat* indica la latitudine e *Long* la longitudine. I valori di latitudine e longitudine vengono misurati in gradi. I valori della latitudine sono compresi sempre nell'intervallo [-90, 90], quelli al di fuori genereranno un'eccezione. I valori della longitudine sono compresi sempre nell'intervallo [-180, 180], quelli al fuori, per rientrare in tale intervallo, vengono arrotondati. Ad esempio, se il valore immesso per la longitudine è 190, verrà arrotondato a -170. *SRID* rappresenta l'ID di riferimento spaziale dell'istanza **geography** da restituire.  
  
## Tipo di dati geometry  
 Il tipo Punto per il tipo di dati geometry rappresenta una singola posizione in cui *X* e *Y* rappresentano rispettivamente le coordinate X e Y del punto generato. *SRID* rappresenta l'ID di riferimento spaziale dell'istanza **geometry** da restituire.  
  
## Esempi  
 L'esempio seguente illustra come creare un'istanza `geometry Point` che rappresenta il punto (3, 4) con un SRID pari a 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 L'esempio successivo illustra come creare un'istanza `geometry``Point` che rappresenta il punto (3, 4) con un valore Z (innalzamento) pari a 7, un valore M (misura) pari a 2,5 e SRID predefinito a 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 L'esempio finale restituisce i valori X, Y, Z e M per l'istanza `geometry``Point`.  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 I valori Z e M possono essere specificati in modo esplicito come NULL, così come mostrato nell'esempio seguente.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## Vedere anche  
 [MultiPoint](../../relational-databases/spatial/multipoint.md)   
 [STX &#40;Tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STY &#40;Tipo di dati geometry&#41;](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  