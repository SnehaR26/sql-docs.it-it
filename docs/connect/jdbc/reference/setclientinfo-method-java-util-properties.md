---
title: Metodo (java.util.Properties) setClientInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16e71bee35ab777ef8a19bb1ee92a9f9931da04d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813439"
---
# <a name="setclientinfo-method-javautilproperties"></a>Metodo setClientInfo (java.util.Properties)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il valore delle proprietà delle informazioni client della connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### <a name="parameters"></a>Parametri  
 *properties*  
  
 Oggetto Properties contenente l'elenco delle proprietà delle informazioni client da impostare.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo setClientInfo viene specificato dal metodo setClientInfo nell'interfaccia Java.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non supporta alcuna proprietà delle informazioni client. Questo metodo genera avvisi se il parametro di input *properties* non fa riferimento a un set di proprietà vuoto. In altre parole, questo metodo genera avvisi per le proprietà da impostare nell'applicazione. Per le applicazioni è previsto l'uso del metodo [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) della classe [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) per il recupero di ogni avviso.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setClientInfo &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
