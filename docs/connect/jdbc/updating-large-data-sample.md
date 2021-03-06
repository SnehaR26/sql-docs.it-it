---
title: Esempio di dati di grandi dimensioni di aggiornamento | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c410e119ccc544901ea6734eff97f847429045fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760899"
---
# <a name="updating-large-data-sample"></a>Esempio di aggiornamento di dati di grandi dimensioni

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Con questa applicazione di esempio [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] viene illustrato come aggiornare una colonna di grandi dimensioni in un database.

Il file di codice per questo esempio è UpdateLargeData.java ed è disponibile nel seguente percorso:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Requisiti

Per eseguire questa applicazione di esempio, è necessario accedere al database di esempio di [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], nonché impostare il classpath per includere il file sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione comune di classe non trovata. Per altre informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Con [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] vengono offerti i file di libreria di classi sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar o sqljdbc42.jar da usare a seconda delle impostazioni Java Runtime Environment (JRE) preferite. In questo esempio vengono usati i metodi [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) e [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md), introdotti nell'API di JDBC 4.0, per accedere ai metodi di memorizzazione delle risposte nel buffer specifici del driver. Per compilare ed eseguire questo esempio, sarà necessaria la libreria di classi sqljdbc4.jar, che fornisce il supporto per JDBC 4.0. Per altre informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Esempio

Nell'esempio seguente, mediante il codice di esempio viene eseguita una connessione al database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Viene quindi creato un oggetto Statement e viene usato il metodo [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) per verificare se l'oggetto Statement è un wrapper per la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) specificata. Per accedere ai metodi di memorizzazione delle riposte nel buffer specifici del driver, viene usato il metodo [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md).

Viene quindi impostata la modalità di memorizzazione delle risposte nel buffer come "**adaptive**" usando il metodo [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) della classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) e viene inoltre illustrato come ottenere la modalità del buffer adattivo.

Viene quindi eseguita l'istruzione SQL e i dati restituiti vengono collocati in un oggetto [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) aggiornabile.

Viene infine eseguita un'iterazione nelle righe di dati nel set di risultati. Se viene trovato un riepilogo di documento vuoto, verrà usata la combinazione di metodi [updateString](../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) e [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) per aggiornare la riga di dati e renderla di nuovo permanente nel database. Se sono già presenti dati, verrà usato il metodo [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) per visualizzare parte dei dati.

Il comportamento predefinito del driver è "**adaptive**". Tuttavia, per i set di risultati aggiornabili forward-only e quando le dimensioni del set di risultati sono maggiori della memoria dell'applicazione, l'applicazione deve impostare la modalità di memorizzazione nel buffer adattiva in modo esplicito usando il metodo [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) della classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md).

[!code[JDBC#UsingAdaptiveBuffering3](../../connect/jdbc/codesnippet/Java/updating-large-data-sample_1.java)]

## <a name="see-also"></a>Vedere anche

[Utilizzo di dati di grandi dimensioni](../../connect/jdbc/working-with-large-data.md)
