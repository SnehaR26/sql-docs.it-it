---
title: Identificatore Case | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c55118fa47337425e715a8b3d6409525668e383f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="identifier-case"></a>Identificatore Case
In istruzioni SQL e gli argomenti di funzione di catalogo, identificatori e gli identificatori tra virgolette possono essere distinzione maiuscole/minuscole o non, che un'applicazione può determinare chiamando **SQLGetInfo** e SQL_IDENTIFIER_CASE SQL_QUOTED_ Opzioni IDENTIFIER_CASE.  
  
 Ognuna di queste opzioni con quattro valori restituiti possibili: uno che informa che l'identificatore o identificatore delimitato case è sensibile e tre che informa che non è sensibile. I tre valori che non fanno distinzione tra maiuscole e descrivono ulteriormente il caso in cui gli identificatori vengono archiviati nel catalogo di sistema. Come gli identificatori vengono archiviati nel catalogo di sistema sono rilevanti solo per scopi di visualizzazione, ad esempio quando un'applicazione consente di visualizzare i risultati di una funzione di catalogo. viene modificata la distinzione maiuscole/minuscole degli identificatori.