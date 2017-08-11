---
title: Istruzione CREATE CELL CALCULATION (MDX) | Documenti Microsoft
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
- CELL CALCULATION
- CREATE
- CALCULATION
- CELL
- CREATE_CELL_CALCULATION
- CREATE CELL
- CREATE CELL CALCULATION
dev_langs:
- kbMDX
helpviewer_keywords:
- calculations [Analysis Services], creating
- CREATE CELL CALCULATION statement
- cubes [Analysis Services], calculations
ms.assetid: 01ced1b3-ada1-4b55-b350-e4255c3cc679
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8d371e3ca64f848cb30f54fe1f0ce4eb98a648a4
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---create-cell-calculation"></a>Definizione dei dati MDX - CREATE CELL CALCULATION
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea una formula di calcolo che valuta un'espressione MDX (Multidimensional Expression) su un set di tuple specificato all'interno di un cubo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
[WITH <CELL CALCULATION clause> Calculation_Name  
   [,WITH <CELL CALCULATION clause> Calculation_Name...n]  
CREATE CELL CALCULATION CURRENTCUBE | Cube_Name.Calculation_Name   
  
<CELL CALCULATION clause> ::=  
   FOR Set_Expression AS 'MDX_Expression'   
      [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Stringa valida che specifica il nome di un cubo.  
  
 *Calculation_Name*  
 Stringa valida che specifica il nome di una formula per il calcolo di celle.  
  
 *Set_Expression*  
 Espressione MDX valida che restituisce un set.  
  
 *String*  
 Valore stringa valido.  
  
 *MDX_Expression*  
 Espressione MDX valida.  
  
 *Logical_Expression*  
 Espressione logica MDX valida.  
  
 *Integer*  
 Valore integer valido.  
  
 *Calculation_Name*  
 Stringa valida che specifica il nome per la proprietà di calcolo di una cella.  
  
 *Scalar_Expression*  
 Espressione scalare MDX valida.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzando celle calcolate, l'applicazione client può specificare un valore di rollup per un particolare set di celle, anziché per un intero set di celle come avviene nel caso di un membro calcolato o di una formula di rollup personalizzata. È ad esempio possibile specificare che tutte le celle nel set definito da `{[Canada],[Time].[2000]}` possono contenere un valore definito da una formula. Tutte le altre celle non contenute nel set vengono calcolate normalmente.  
  
> [!NOTE]  
>  Per compatibilità con le versioni precedenti, la sintassi BNF di `{*(<comment> | <whitespace> | <newline>)}` verrà analizzata come `{*}`.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di celle calcolate con ambito sessione](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells.md)   
 [Creazione di calcoli di celle con ambito Query &#40; MDX &#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md)   
 [Creazione di calcoli di celle in MDX &#40; MDX &#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)   
 [Utilizzando le proprietà della cella &#40; MDX &#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)   
 [Contenuto di FORMAT_STRING &#40; MDX &#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)   
 [Contenuto di FORE_COLOR e BACK_COLOR contenuto &#40; MDX &#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)   
 [Le istruzioni di definizione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
