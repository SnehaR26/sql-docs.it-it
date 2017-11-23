---
title: Utilizzare cursori (ODBC) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: cursors [ODBC], how to topics
ms.assetid: c502736f-bca0-45c3-ae25-d2ad52d296bf
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5116bd61887153c546b021d9db2553a4f9563480
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="use-cursors-odbc"></a>Utilizzare cursori (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-use-cursors"></a>Per utilizzare i cursori  
  
1.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare gli attributi del cursore desiderati:  
  
     Impostare gli attributi SQL_ATTR_CURSOR_TYPE e SQL_ATTR_CONCURRENCY (opzione consigliata).  
  
     Oppure  
  
     Impostare gli attributi SQL_CURSOR_SCROLLABLE e SQL_CURSOR_SENSITIVITY.  
  
2.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare le dimensioni del set di righe usando l'attributo SQL_ATTR_ROW_ARRAY_SIZE.  
  
3.  Facoltativamente, è possibile chiamare [SQLSetCursorName](http://go.microsoft.com/fwlink/?LinkId=58406) per impostare un nome di cursore se gli aggiornamenti posizionati verranno eseguiti usando la clausola WHERE CURRENT OF.  
  
4.  Eseguire l'istruzione SQL.  
  
5.  Facoltativamente, è possibile chiamare [SQLGetCursorName](../../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) per ottenere il nome del cursore se gli aggiornamenti posizionati verranno eseguiti usando la clausola WHERE CURRENT OF e se con [SQLSetCursorName](http://go.microsoft.com/fwlink/?LinkId=58406) non è stato fornito un nome di cursore al passaggio 3.  
  
6.  Chiamare [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) per ottenere il numero di colonne (C) nel set di righe.  
  
     Utilizzare un'associazione per colonna.  
  
     \- - oppure -  
  
     Utilizzare un'associazione per riga.  
  
7.  Recuperare i set di righe dal cursore nel modo desiderato.  
  
8.  Chiamare [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) per determinare se è disponibile un altro set di risultati.  
  
    -   Se viene restituito SQL_SUCCESS, è disponibile un altro set di risultati.  
  
    -   Se viene restituito SQL_NO_DATA, non è più disponibile alcun set di risultati.  
  
    -   Se viene restituito SQL_SUCCESS_WITH_INFO o SQL_ERROR, chiamare [SQLGetDiagRec](http://go.microsoft.com/fwlink/?LinkId=58402) per determinare se è disponibile l'output da un'istruzione PRINT o RAISERROR.  
  
     Se si utilizzano parametri di istruzione associati per i parametri di output o il valore restituito di una stored procedure, utilizzare i dati disponibili nei buffer dei parametri associati.  
  
     Quando si utilizzano parametri associati, ogni chiamata a [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) o [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) eseguirà l'istruzione SQL S volte, in cui S è il numero di elementi nella matrice dei parametri associati. Di conseguenza, vi saranno S set di risultati da elaborare, in cui ogni set di risultati comprende tutti i set di risultati, i parametri di output e i codici restituiti utilizzati normalmente da una singola esecuzione dell'istruzione SQL.  
  
     Si noti che quando un set di risultati contiene righe di calcolo, ogni riga di calcolo viene resa disponibile come set di risultati distinto. Tali set di risultati di calcolo vengono intercalati all'interno delle normali righe e le suddividono in più set di risultati.  
  
9. Facoltativamente, è possibile chiamare [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) con SQL_UNBIND per rilasciare qualsiasi buffer delle colonne associate.  
  
10. Se è disponibile un altro set di risultati, andare al passaggio 6.  
  
     Nel passaggio 9 la chiamata a [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) in un set di risultati parzialmente elaborato cancella il resto del set di risultati. Un altro modo per cancellare un set di risultati parzialmente elaborato consiste nel chiamare [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
     È possibile controllare il tipo di cursore utilizzato impostando SQL_ATTR_CURSOR_TYPE e SQL_ATTR_CONCURRENCY oppure impostando SQL_ATTR_CURSOR_SENSITIVITY e SQL_ATTR_CURSOR_SCROLLABLE. È consigliabile non combinare i due metodi di definizione del comportamento del cursore.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle procedure per cursori &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)  
  
  