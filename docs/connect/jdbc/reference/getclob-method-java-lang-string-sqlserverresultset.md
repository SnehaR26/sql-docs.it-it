---
title: Metodo (lang) (SQLServerResultSet) getClob | Documenti Microsoft
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
- SQLServerResultSet.getClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1de9804-1f27-4854-8985-3385fadcbebb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 14c4d1a32bbb408a26f72329ec49d462d978f7ef
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getclob-method-javalangstring-sqlserverresultset"></a>getClob, metodo (lang) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del nome della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto Clob nel linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Clob getClob(java.lang.String colName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *colName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto Clob.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getClob viene specificato dal metodo getClob nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getClob &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getclob-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  