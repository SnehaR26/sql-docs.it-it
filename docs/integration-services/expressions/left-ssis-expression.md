---
title: LEFT (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fa54997db4caa523ab298077ce8137045c6ee33d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784855"
---
# <a name="left-ssis-expression"></a>LEFT (espressione SSIS)
  Viene restituito il numero specificato di caratteri della parte più a sinistra dell'espressione di caratteri indicata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri da cui estrarre i caratteri.  
  
 *number*  
 Espressione integer in cui viene indicato il numero di caratteri da restituire.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 Se *number* è maggiore della lunghezza di *character_expression*, la funzione restituisce *character_expression*.  
  
 Se *number* ha valore zero, la funzione restituirà una stringa di lunghezza zero.  
  
 Se *number* è un numero negativo, la funzione restituirà un errore.  
  
 L'argomento *number* accetta variabili e colonne.  
  
 È possibile utilizzare LEFT solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da LEFT verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Se l'argomento è Null, verrà restituito Null da LEFT.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 Nell'esempio seguente viene utilizzato un valore letterale stringa. Il risultato restituito sarà `"Mountain"`.  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [RIGHT &#40;espressione SSIS&#41;](../../integration-services/expressions/right-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
