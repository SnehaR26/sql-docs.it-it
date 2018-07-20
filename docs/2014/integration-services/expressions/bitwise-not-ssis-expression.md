---
title: ~ (NOT bit per bit) (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f422eb2e9b75e7488cff9ceaa089954595d00313
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231491"
---
# <a name="-bitwise-not-ssis-expression"></a>~ (NOT bit per bit) (espressione SSIS)
  Viene eseguita una negazione bit per bit di un valore integer. Questo operatore può essere applicato a tipi di dati integer con e senza segno.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *integer_expression*  
 Espressione valida con qualsiasi tipo di dati integer. *integer*_*expression* è un numero intero trasformato in un numero binario per l'operazione bit per bit. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati di *integer_expression.*  
  
## <a name="remarks"></a>Note  
 None  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene applicato l'operatore ~ (NOT) bit per bit al numero 170 (0000 0000 1010 1010). Il numero è un valore integer con segno.  
  
```  
  
~ 170  
```  
  
 L'espressione restituisce -170 (1111111101010101).  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza e associatività degli operatori](operator-precedence-and-associativity.md)   
 [Gli operatori &#40;espressione di SSIS&#41;](operators-ssis-expression.md)  
  
  