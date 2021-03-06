---
title: Uso di una stored procedure con stato restituito | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b126e95-8458-41d6-af37-fc6662859f19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f5aa998fa6e0e61bc0417aaf9703a0d0809fc4b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737099"
---
# <a name="using-a-stored-procedure-with-a-return-status"></a>Utilizzo di una stored procedure con stato restituito

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Una stored procedure di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che è possibile chiamare restituisce un parametro di stato o risultato che in genere viene utilizzato per indicare l'esito positivo o negativo della stored procedure. Tramite [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] viene fornita la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), che è possibile usare per chiamare questo tipo di stored procedure ed elaborare i dati restituiti.

Quando si chiama questo tipo di stored procedure usando il driver JDBC, è necessario usare la sequenza di escape SQL `call` insieme al metodo [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) della classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). La sintassi della sequenza di escape `call` con parametro con stato restituito è la seguente:

`{[?=]call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Per altre informazioni sulle sequenze di escape SQL, vedere [usando le sequenze di Escape SQL](../../connect/jdbc/using-sql-escape-sequences.md).

Quando si costruisce la sequenza escape `call`, specificare il parametro return status usando il carattere ? (punto interrogativo), che funge da segnaposto per il valore di parametro che verrà restituito dalla stored procedure. Per specificare il valore di un parametro return status, è necessario specificare il tipo di dati del parametro usando il metodo [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) della classe SQLServerCallableStatement prima di eseguire la stored procedure.

> [!NOTE]  
> Quando si usa il driver JDBC con database di SQL Server, il valore specificato per il parametro return status nel metodo registerOutParameter sarà sempre un valore integer che è possibile specificare usando il tipo di dati java.sql.Types.INTEGER.

Inoltre, quando si passa un valore al metodo registerOutParameter per un parametro return status, è necessario specificare non solo il tipo di dati da usare per il parametro, ma anche la posizione ordinale del parametro nella stored procedure. Nel caso del parametro return status, la posizione ordinale sarà sempre 1 perché si tratta sempre del primo parametro nella chiamata alla stored procedure. Sebbene la classe SQLServerCallableStatement fornisca il supporto per l'utilizzo del nome del parametro per indicare il parametro specifico, per i parametri return status è possibile usare solo il numero della posizione ordinale.

Come esempio, viene creata la seguente stored procedure nel database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]:

```sql
CREATE PROCEDURE CheckContactCity  
   (@cityName CHAR(50))  
AS  
BEGIN  
   IF ((SELECT COUNT(*)  
   FROM Person.Address  
   WHERE City = @cityName) > 1)  
   RETURN 1  
ELSE  
   RETURN 0  
END  
```

Questa stored procedure restituisce un valore di stato uguale a 1 o 0, in base alla presenza o meno nella tabella Person.Address della città specificata nel parametro cityName.

Nell'esempio seguente viene passata alla funzione una connessione aperta al database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] e il metodo [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) viene usato per la chiamata alla stored procedure CheckContactCity:

[!code[JDBC#UsingSprocWithReturnStatus1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_1_1.java)]

## <a name="see-also"></a>Vedere anche

[USo di istruzioni con stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)
