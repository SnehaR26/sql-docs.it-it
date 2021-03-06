---
title: Intersect (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b24049cb81982075fa9234c6fa792db273d404db
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740560"
---
# <a name="intersect-mdx"></a>Intersect (MDX)


  Restituisce l'intersezione di due set di input, mantenendo facoltativamente i duplicati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Intersect(Set_Expression1 , Set_Expression2 [ , ALL ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Remarks  
 Il **Intersect** funzione restituisce l'intersezione di due set. Per impostazione predefinita la funzione rimuove i duplicati da entrambi i set prima di eseguire l'intersezione. I due set specificati devono disporre della stessa dimensionalità.  
  
 Facoltativo **tutti** flag consente di mantenere i duplicati. Se **tutti** è specificato, il **Intersect** funzione come di consueto l'intersezione degli elementi e ogni elemento duplicato nel primo set che corrisponde a un elemento duplicato nel secondo set. I due set specificati devono disporre della stessa dimensionalità.  
  
## <a name="example"></a>Esempio  
 Per la seguente query vengono restituiti gli anni 2003 e 2004, ovvero i due membri visualizzati in entrambi i set specificati:  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001], [Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003]}`  
  
 `, {[Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 La query seguente non viene eseguita correttamente perché i due set specificati contengono membri da gerarchie diverse:  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001]}`  
  
 `, {[Customer].[City].&[Abingdon]&[ENG]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
