---
title: "Set di risultati di automazione OLE | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-ole"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipi di dati [SQL Server], automazione OLE"
  - "matrici bidimensionali"
  - "matrici unidimensionali"
  - "set di risultati [SQL Server], automazione OLE"
  - "automazione OLE [SQL Server], set di risultati"
  - "matrici [SQL Server]"
ms.assetid: b2f99e33-2303-427c-94b9-9d55f8e2a6ab
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Set di risultati di automazione OLE
  Se una proprietà o un metodo di automazione OLE restituisce dati in una matrice a una o a due dimensioni, tale matrice verrà restituita al client come set di risultati:  
  
-   Una matrice unidimensionale viene restituita al client come set di risultati a riga singola con lo stesso numero di colonne del numero di elementi nella matrice. La matrice (10), ad esempio, viene restituita come singola riga con 10 colonne.  
  
-   Una matrice bidimensionale viene restituita al client come set di risultati costituito da un numero di colonne pari al numero di elementi della prima dimensione della matrice e un numero di righe pari al numero di elementi della seconda dimensione della matrice. La matrice (2,3), ad esempio, viene restituita come 2 colonne in 3 righe.  
  
 Quando il valore restituito da una proprietà o da un metodo è una matrice, sp_OAGetProperty o sp_OAMethod restituisce un set di risultati al client. I parametri di output dei metodi non possono essere rappresentati da matrici. Queste procedure eseguono un'analisi di tutti i valori di dati della matrice per determinare quali sono i tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appropriati e la lunghezza di dati da utilizzare per ogni colonna del set di risultati. Per una colonna specifica queste procedure utilizzano il tipo di dati e la lunghezza necessari per rappresentare tutti i valori di dati della colonna.  
  
 Se a tutti i valori di dati di una colonna è associato lo stesso tipo di dati, tale tipo verrà applicato all'intera colonna. Se ai valori sono invece associati tipi di dati diversi, il tipo di dati dell'intera colonna verrà scelto in base alla tabella seguente. Per utilizzare la tabella seguente, individuare un tipo di dati lungo l'asse della riga sinistra e un secondo tipo di dati lungo l'asse della colonna superiore. L'intersezione della riga e della colonna descrive il tipo di dati della colonna del set di risultati.  
  
||||||||  
|-|-|-|-|-|-|-|  
||**int**|**float**|**money**|**datetime**|**varchar**|**nvarchar**|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## Contenuto correlato  
 [Stored procedure di automazione &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
  
 [Opzione di configurazione del server Ole Automation Procedures](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  