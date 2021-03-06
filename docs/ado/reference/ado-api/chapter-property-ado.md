---
title: Proprietà Chapter (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction::Chapter
- ADORecordsetConstruction::put_Chapter
- ADORecordsetConstruction::get_Chapter
helpviewer_keywords:
- Chapter property [ADO]
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 601573a34082f386bfee238308a8f97c41743e4b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655415"
---
# <a name="chapter-property-ado"></a>Proprietà Chapter (ADO)
Ottiene o imposta un DB OLE **capitolo** oggetto da/in un [interfaccia ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md) oggetto. Quando si usa **put_Chapter** per impostare le **capitolo** dell'oggetto, un subset di righe viene trasformato in un oggetto ADO [oggetto Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto. Consente di impostare il capitolo corrente dei **set di righe**oggetto. Si tratta di una proprietà di lettura/scrittura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT get_Chapter([out, retval] long* plChapter);  
HRESULT put_Chapter([in] long lChapter);  
```  
  
## <a name="parameters"></a>Parametri  
 *plChapter*  
 Puntatore all'handle del capitolo.  
  
 *LChapter*  
 Handle del capitolo.  
  
## <a name="return-values"></a>Valori restituiti  
 Metodo di questa proprietà restituisce i valori HRESULT standard, tra cui S_OK ed E_FAIL.  
  
## <a name="applies-to"></a>Si applica a  
 [Interfaccia ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
