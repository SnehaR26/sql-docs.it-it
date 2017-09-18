---
title: SetToArray (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SETTOARRAY
dev_langs:
- kbMDX
helpviewer_keywords:
- SetToArray function
ms.assetid: e408c626-3a2a-4ce9-aeb4-247301334893
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 410a88cdc83839e0fbdde75f7e0c5b4192fe1e0e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="settoarray-mdx"></a>SetToArray (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Converte uno o più set in una matrice da utilizzare in una funzione definita dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SetToArray(Set_Expression1 [ ,Set_Expression2,...n ][ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Osservazioni  
 Il **SetToArray** funzione converte uno o più set in una matrice da utilizzare in una funzione definita dall'utente. Il numero di dimensioni nella matrice risultante corrisponde al numero di set specificati.  
  
 L'espressione numerica facoltativa può specificare i valori per le celle della matrice. Se non viene specificata un'espressione numerica, il cross join dei set viene valutato nel contesto corrente.  
  
 Le coordinate delle celle nella matrice risultante corrispondono alla posizione dei set nell'elenco. Ad esempio, per i tre set `SA`, `SB` e `SC`, ognuno dei quali contiene due elementi, l'istruzione MDX `SetToArray(SA, SB, SC)` crea la matrice tridimensionale seguente:  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  Il tipo restituito del **SetToArray** funzione è di tipo VARIANT VT_ARRAY. Pertanto, l'output del **SetToArray** funzione deve essere usata solo come input per una funzione definita dall'utente.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita una matrice.  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
