---
title: Determinazione del numero di righe interessate | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99e3676c3b73b177f5e6fc3acef0d93d55cce898
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626209"
---
# <a name="determining-the-number-of-affected-rows"></a>Determinazione del numero di righe interessate
Dopo che un'applicazione aggiorna, Elimina o inserisce righe, può chiamare **SQLRowCount** per determinare il numero di righe interessato. **SQLRowCount** restituisce questo valore se le righe sono state aggiornate, eliminate o inserite tramite l'esecuzione di un' **UPDATE**, **eliminare**, oppure **Inserisci** istruzione, tramite l'esecuzione di un oggetto posizionato aggiornare o eliminare istruzione o chiamando **SQLSetPos**.  
  
 Se viene eseguito un batch di istruzioni SQL, il conteggio delle righe interessate potrebbe essere un conteggio totale per tutte le istruzioni nel batch o singoli conteggi relativi a ogni istruzione nel batch. Per altre informazioni, vedere [batch di istruzioni SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) e [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Il numero di righe interessate viene restituito anche nel campo dell'intestazione diagnostica SQL_DIAG_ROW_COUNT nell'area di diagnostica associato all'handle di istruzione. Tuttavia, i dati in questo campo viene reimpostati dopo ogni funzione chiamato sullo stesso handle di istruzione, mentre il valore restituito da **SQLRowCount** rimane invariato fino a una chiamata a **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, o **SQLSetPos**.
