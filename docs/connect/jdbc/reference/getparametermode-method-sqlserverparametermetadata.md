---
title: Metodo getParameterMode (SQLServerParameterMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getParameterMode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d93c9b70-18c2-44bb-a6de-70a7e940d806
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d5c9c03946082f9af3f939c44d13c350bd9b403
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647650"
---
# <a name="getparametermode-method-sqlserverparametermetadata"></a>Metodo getParameterMode (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la modalità del parametro designato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getParameterMode(int param)  
```  
  
#### <a name="parameters"></a>Parametri  
 *param*  
  
 Valore **int** che indica l'indice del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Valore **int** che indica la modalità del parametro designato. Può essere uno dei valori seguenti:  
  
 ParameterMetaData.parameterModeIn  
  
 ParameterMetaData.parameterModeInOut  
  
 ParameterMetaData.parameterModeOut  
  
 ParameterMetaData.parameterModeUnknown  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getParameterMode viene specificato dal metodo getParameterMode nell'interfaccia parametermetadata.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Membri di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Classe SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
