---
title: Numero di proprietà (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38135d1afa2fbdf680a7f2c1f89ddcbe513484f8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47803039"
---
# <a name="number-property-ado"></a>Proprietà Number (ADO)
Indica il numero che identifica in modo univoco un' [errore](../../../ado/reference/ado-api/error-object.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **lungo** valore che può corrispondere a uno delle [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) costanti.  
  
## <a name="remarks"></a>Note  
 Usare la **numero** proprietà per determinare l'errore verificatosi. Il valore della proprietà è un numero univoco che corrisponde alla condizione di errore.  
  
 Il [errori](../../../ado/reference/ado-api/errors-collection-ado.md) raccolta restituisce un valore HRESULT in formato esadecimale (ad esempio, 0x80004005) o come valore long (ad esempio, 2147467259). Questi valori HRESULT possono essere generati da componenti sottostanti, ad esempio OLE DB o OLE stesso. Per altre informazioni su questi valori, vedere [errori (OLE DB)](http://msdn.microsoft.com/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) nel [riferimento per programmatori OLE DB](http://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)*.*  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Description, HelpContext, HelpFile, NativeError, numero, origine e SQLState proprietà esempio (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, numero, origine e SQLState esempio di proprietà (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Proprietà Description](../../../ado/reference/ado-api/description-property.md)   
 [Proprietà HelpContext, HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Proprietà Source (errore ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
