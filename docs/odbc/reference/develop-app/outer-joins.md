---
title: Outer join | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd35a8bd0e2a9280d16614a3979dc2af05487e42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47619609"
---
# <a name="outer-joins"></a>Outer join
ODBC supporta SQL-92 a sinistra, la sintassi di right e full outer join. La sequenza di escape per gli outer join  
  
 **{GU** *outer-join * * *}**  
  
 in cui *outer join* è  
  
 *riferimento alla tabella* {**LEFT &#124; RIGHT &#124; completo} OUTER JOIN** {*riferimento alla tabella* &#124; *outer join*} **via**  *condizione di ricerca*  
  
 *riferimento alla tabella* specifica un nome di tabella, e *condizione di ricerca* specifica la condizione di join tra il *riferimenti alla tabella*.  
  
 Una richiesta di outer join deve essere visualizzati dopo il **FROM** (parola chiave) e prima di **in cui** clausola (se presente). Per informazioni complete sulla sintassi, vedere [Outer Join sequenza di Escape](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) nell'appendice c: SQL grammatica.  
  
 Le istruzioni SQL seguenti, ad esempio, creano lo stesso set di risultati che elenca tutti i clienti e mostra che ha gli ordini aperti. La prima istruzione Usa la sintassi di escape-sequence. La seconda istruzione viene utilizzata la sintassi nativa per Oracle e non è interoperativa.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Per determinare i tipi di outer join che supporta un'origine dati e i driver, un'applicazione chiama **SQLGetInfo** con il SQL_OJ_CAPABILITIES flag. I tipi di outer join che potrebbero essere supportati sono sinistro, destro, completo o outer join; nidificati outer join in cui i nomi di colonna nel **via** clausola non è lo stesso ordine i nomi di tabella corrispondente nella **OUTER JOIN** clausola; gli inner join in combinazione con outer join; e gli outer join con qualsiasi operatore di confronto ODBC. Se il tipo di informazioni SQL_OJ_CAPABILITIES restituisce 0, non esiste una clausola outer join è supportata.
