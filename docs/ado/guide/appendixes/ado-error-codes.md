---
title: Codici di errore ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], error codes
ms.assetid: 3aee61c7-a9b7-4596-b78e-5828a00d0281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: edafc34bc4a2e9e860edd1101b5ce17bddd02a37
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718039"
---
# <a name="capture-ado-error-codes"></a>Acquisire i codici di errore ADO
Oltre agli errori del provider restituiti nel [errore](../../../ado/reference/ado-api/error-object.md) gli oggetti delle [errori](../../../ado/reference/ado-api/errors-collection-ado.md) insieme, ADO può restituire gli errori al meccanismo di gestione delle eccezioni dell'ambiente di runtime. Usare il meccanismo di intercettazione degli errori del linguaggio di programmazione, come le **in caso di errore** istruzione in Microsoft® Visual Basic, o il **try-catch** blocco in Microsoft Visual C++®, per acquisire gli errori ADO.

 Per l'elenco dei codici di errore ADO, vedere [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>Vedere anche
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md) [raccolta di errori (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)
