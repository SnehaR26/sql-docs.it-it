---
title: Utilizzo della Trattenibilità | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: aa48306c-e7a0-4dcb-af21-9ebb6898e45a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 520468faa2398bcb11dc237826859e12cb027815
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47780236"
---
# <a name="using-holdability"></a>Utilizzo della trattenibilità

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Per impostazione predefinita, i set di risultati creati in una transazione vengono mantenuti aperti non appena viene eseguito il commit della transazione nel database oppure il rollback della transazione. Può talvolta essere utile, tuttavia, chiudere il set di risultati dopo il commit della transazione. A questo scopo, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta l'uso della trattenibilità dei set di risultati.

La trattenibilità può essere impostata usando il metodo [setHoldability](../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) della classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Quando si imposta la trattenibilità con il metodo setHoldability, è possibile usare le costanti `ResultSet.HOLD_CURSORS_OVER_COMMIT` o `ResultSet.CLOSE_CURSORS_AT_COMMIT` del set di risultati.

Il driver JDBC supporta inoltre l'impostazione della trattenibilità quando si crea uno degli oggetti Statement. Quando si creano gli oggetti Statement che presentano overload rispetto ai parametri di trattenibilità dei set di risultati, la trattenibilità di tali oggetti deve corrispondere a quella della connessione. In caso di mancata corrispondenza, viene generata un'eccezione. In SQL Server la trattenibilità è infatti supportata solo a livello di connessione.

La trattenibilità di un set di risultati corrisponde alla trattenibilità di un oggetto SQLServerConnection associato al set di risultati al momento della creazione del set solo per i cursori sul lato server. Non si applica ai cursori sul lato client. Per tutti i set di risultati con cursori sul lato client il valore della trattenibilità è sempre `ResultSet.HOLD_CURSORS_OVER_COMMIT`.

Per i cursori sul lato server, se connessi a SQL Server 2005 o versioni successive, l'impostazione influisce solo sulla trattenibilità dei nuovi set di risultati ancora da creare in tale connessione. Non interessa pertanto eventuali set di risultati creati in precedenza e già aperti in tale connessione.

Nell'esempio seguente viene impostata la trattenibilità del set di risultati durante l'esecuzione di una transazione locale formata da due istruzioni diverse nel blocco `try`. Le istruzioni vengono eseguite sulla tabella Production.ScrapReason del database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Viene prima di tutto attivata la modalità di transazione manuale impostando l'autocommit su `false`. Dopo aver disabilitato la modalità di autocommit, non verrà eseguito il commit di istruzioni SQL finché l'applicazione non chiama in modo esplicito il metodo [commit](../../connect/jdbc/reference/commit-method-sqlserverconnection.md). Il codice nel blocco catch esegue il rollback della transazione se viene generata un'eccezione.

[!code[JDBC#UsingHoldability1](../../connect/jdbc/codesnippet/Java/using-holdability_1.java)]

## <a name="see-also"></a>Vedere anche

[Esecuzione di transazioni con il driver JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)
