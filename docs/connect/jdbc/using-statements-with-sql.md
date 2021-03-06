---
title: Uso di istruzioni con SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fb555b3731f9afc5296f7f558bb7a4b58b5b6bc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694619"
---
# <a name="using-statements-with-sql"></a>Utilizzo di istruzioni SQL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Quando si gestiscono dati in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] e istruzioni SQL inline, è possibile usare diverse classi. in base al tipo di istruzione SQL che si desidera eseguire.  
  
Se l'istruzione SQL non contiene parametri IN, usare la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md); se, invece, contiene parametri IN, usare la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
> [!NOTE]  
> Se è necessario usare istruzioni SQL che contengono sia parametri IN che OUT, è necessario implementarle come stored procedure e chiamarle usando la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Per altre informazioni sull'uso di stored procedure, vedere [istruzioni Using con le Stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
Nelle sezioni seguenti sono descritti i diversi scenari di utilizzo di dati in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante istruzioni SQL.  

## <a name="in-this-section"></a>Contenuto della sezione  

| Argomento                                                                                                                        | Descrizione                                                       |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [Uso di un'istruzione SQL senza parametri](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)                 | Descrive come utilizzare istruzioni SQL che non contengono parametri.   |
| [Uso di istruzioni SQL con parametri](../../connect/jdbc/using-an-sql-statement-with-parameters.md)                       | Descrive come utilizzare istruzioni SQL che contengono parametri.      |
| [Uso di un'istruzione SQL per modificare gli oggetti di database](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md) | Descrive come utilizzare istruzioni SQL per modificare gli oggetti di database.   |
| [Uso di un'istruzione SQL per modificare i dati](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)                         | Descrive come utilizzare istruzioni SQL per modificare i dati in un database. |
  
## <a name="see-also"></a>Vedere anche

[Uso delle istruzioni con il driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
