---
title: Metodo (lang) prepareCall | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.prepareCall (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cb83b567-4ce5-447a-93cc-895d4eaf3a05
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f65f30f5c3ccbe70452546a40c8c1fdb25074386
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="preparecall-method-javalangstring"></a>Metodo prepareCall (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) oggetto per la chiamata di stored procedure del database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *SQL*  
  
 Oggetto **stringa** contenente un'istruzione SQL.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto CallableStatement.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo prepareCall viene specificato dal metodo prepareCall nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo prepareCall &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  