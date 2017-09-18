---
title: Limitazioni di istruzione UPDATE | Documenti Microsoft
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
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 828fc042a4184bfedccf7c26210f899c1d73f2a4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="update-statement-limitations"></a>Limitazioni di istruzione di aggiornamento
Per il driver Paradox aggiornare una tabella, la tabella deve includere un indice univoco (chiave primaria). Quando si utilizza il driver Paradox senza implementare Borland Database Engine, non è possibile aggiornare una tabella di Paradox.  
  
 Non è supportata dal driver del testo.  
  
 Quando viene utilizzato il driver per Microsoft Excel, è possibile aggiornare i valori, ma non può essere eliminata una riga da una tabella in base a un foglio di calcolo di Microsoft Excel. Di conseguenza, l'istruzione UPDATE non è considerata ufficialmente supportata dal driver Microsoft Excel. Solo l'istruzione INSERT è considerato supportato.