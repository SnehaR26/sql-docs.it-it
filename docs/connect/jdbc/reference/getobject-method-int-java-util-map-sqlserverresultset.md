---
title: Metodo getObject (int, java.util.Map) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getObject (int, java.util.Map)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: df85a514-ab43-4bf6-98dd-f7f37fad1850
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5cbed2006e259b25d484e98b77b68b33f383de2d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47726909"
---
# <a name="getobject-method-int-javautilmap-sqlserverresultset"></a>Metodo getObject (int, java.util.Map) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ottiene il valore dell'indice di colonna designato nella riga corrente di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) come oggetto nel linguaggio di programmazione Java, usando l'oggetto Map specificato.  
  
> [!NOTE]  
>  Questo metodo non è attualmente supportato da [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. L'utilizzo di questo metodo restituirà sempre il mapping predefinito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.Object getObject(int i,  
                                  java.util.Map map)  
```  
  
#### <a name="parameters"></a>Parametri  
 *i*  
  
 Valore **int** che indica l'indice di colonna.  
  
 *map*  
  
 Un oggetto Map.  
  
## <a name="return-value"></a>Valore restituito  
 Valore **Object**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getObject viene specificato dal metodo nell'interfaccia ResultSet getObject.  
  
 Il metodo restituirà il valore della colonna specificata come oggetto Java. Il tipo dell'oggetto Java sarà il tipo di oggetto Java predefinito che corrisponde al tipo SQL della colonna, in base al mapping per i tipi predefiniti indicato nella specifica JDBC. Se si tratta di un valore NULL SQL, il driver restituisce un valore Null Java.  
  
 Questo metodo può essere utilizzato anche per leggere tipi di dati astratti specifici del database. Nell'API di JDBC 2.0, il comportamento del metodo getObject è esteso ai fini della materializzazione dei dati di tipi SQL definiti dall'utente. Quando una colonna contiene un valore di tipo Structured o Distinct, il comportamento di questo metodo è analogo a quello di una chiamata a `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 A partire da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0:  
  
-   Un valore di tipo date sarà restituito come oggetto java.sql.Date.  
  
-   Un valore di tipo time sarà restituito come oggetto java.sql.Time.  
  
-   Un valore di tipo datetime2 sarà restituito come oggetto java.sql.Timestamp.  
  
-   Un valore di tipo datetimeoffset sarà restituito come oggetto microsoft.sql.DateTimeOffset.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getObject &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
