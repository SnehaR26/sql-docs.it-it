---
title: Metodo setSelectMethod (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 629c92aaf5ffb23976ad2e4ff2377cc53f87120d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842559"
---
# <a name="setselectmethod-method-sqlserverdatasource"></a>Metodo setSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il tipo di cursore predefinito usato per tutti i set di risultati creati tramite questo oggetto [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>Parametri  
 *selectMethod*  
  
 Valore **String** contenente il tipo di cursore predefinito.  
  
## <a name="remarks"></a>Remarks  
 selectMethod è il tipo di cursore predefinito utilizzato per un set di risultati. Questa proprietà è utile in caso di set di risultati di grandi dimensioni e se non desidera archiviare tutto il set di risultati in memoria nel lato client. Impostando la proprietà su "cursor", è possibile creare un cursore sul lato server che può recuperare i blocchi di dati più piccoli in una sola volta. Se la proprietà selectMethod non è impostata, il metodo [getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) restituisce il valore predefinito "direct".  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
