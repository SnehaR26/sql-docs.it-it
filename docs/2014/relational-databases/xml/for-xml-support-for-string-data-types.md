---
title: Supporto di FOR XML per i tipi di dati stringa | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- strings [SQL Server], XML
ms.assetid: bf069da8-de1e-44d2-a1fb-ade383076ac1
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3b81ccaf551f1d2a6d2a3edb106f45b8f9aa606f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329321"
---
# <a name="for-xml-support-for-string-data-types"></a>Supporto di FOR XML per i tipi di dati stringa
  Il codice XML generato dagli spazi vuoti FOR XML nei dati viene sostituito con delle entità.  
  
 Nell'esempio seguente viene creata la tabella **T** e vengono inseriti dati di esempio che includono i caratteri di avanzamento riga, ritorno a capo e tabulazione. L'istruzione SELECT recupera i dati dalla tabella.  
  
```  
CREATE TABLE T  
(  
  c1 int identity primary key,  
  c2 varchar(100)  
);  
go  
  
INSERT T (c2) VALUES ('Special character 0xD for carriage return ' + convert(varchar(10), 0xD) + ' after carriage return');  
INSERT T (c2) VALUES ('Special character 0x9 for tab ' + convert(varchar(10), 0x9) + ' after tab' );  
INSERT T (c2) VALUES ('Special character 0xA for line feed ' + convert(varchar(10), 0xA) + ' after line feed');  
go  
SELECT *   
FROM T  
FOR XML AUTO;  
go  
```  
  
 Risultato:  
  
```  
 <T c1="1" c2="Special character 0xD for carriage return   
 after carriage return" />  
 <T c1="2" c2="Special character 0x9 for tab     after tab" />  
 <T c1="3" c2="Special character 0xA for line feed   
after line feed" />  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il carattere di ritorno a capo nella prima riga viene sostituito con l'entità &#xD.  
  
-   Il carattere di tabulazione nella seconda riga viene sostituito con l'entità &#x09.  
  
-   Il carattere di avanzamento riga nella terza riga viene sostituito con l'entità &#xA.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di FOR XML per vari tipi di dati di SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  