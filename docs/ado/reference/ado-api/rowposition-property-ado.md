---
title: Proprietà RowPosition (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::put_RowPosition
- ADORecordConstruction::PutRowPosition
- ADORecordConstruction::GetRowPosition
- ADORecordConstruction::RowPosition
- ADORecordConstruction::get_RowPosition
helpviewer_keywords:
- RowPosition property [ADO]
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e2e8bab73bfe93e8a78e013572a376b608ca9a3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616439"
---
# <a name="rowposition-property-ado"></a>Proprietà RowPosition (ADO)
Ottiene o imposta un DB OLE **RowPosition** oggetto da/in un **ADORecordsetConstruction** oggetto. Quando si usa **put_RowPosition** per impostare il **RowPosition** oggetto, risultante **Recordset** oggetto utilizza il **RowPosition** dell'oggetto a determinare la riga corrente.  
  
 Proprietà di lettura/scrittura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>Parametri  
 *ppRowPos*  
 Puntatore a OLE DB **RowPosition** oggetto.  
  
 *PRowPos*  
 OLE DB **RowPosition** oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
 Metodo di questa proprietà restituisce i valori HRESULT standard, tra cui S_OK ed E_FAIL.  
  
## <a name="remarks"></a>Note  
 Quando questa proprietà è impostata, se il **set di righe** dell'oggetto nel **RowPosition** oggetto è diverso dal **set di righe** dell'oggetto nel **Recordset**dell'oggetto, il primo esegue l'override di quest'ultimo. Lo stesso comportamento si applica all'oggetto corrente **capitolo** delle **RowPosition** anche.  
  
## <a name="applies-to"></a>Si applica a  
 [Interfaccia ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
