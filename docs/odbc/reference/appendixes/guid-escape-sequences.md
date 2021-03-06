---
title: Le sequenze di Escape GUID | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf41671abc6393a18fad06e1debd297fed1f04c5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654981"
---
# <a name="guid-escape-sequences"></a>Sequenze di escape GUID
ODBC Usa sequenze di escape per i valori letterali GUID. La sintassi di questa sequenza di escape è come segue:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Note  
 Nella notazione BNF, la sintassi è come segue:  
  
 *ODBC-guid-escape* :: =  
     *Guid ODBC-esc-iniziatore* »*valore guid*' *ODBC-esc-carattere di terminazione*  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *ODBC-esc-carattere di terminazione* :: =}  
  
 *valore GUID* :: = *orologio di scarso valore guid-separatore orologio-medio-value. guid-separatore orologio di alto valore guid-separatore orologio-seq-value. guid-separatore nodo-valore*  
  
 *separatore di GUID* :: = -  
  
 *orologio-low-value* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *valore intermedio di clock* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *Clock rilevanza* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *orologio-seq-value* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *orologio-nodo-value* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; A &#124; B &#124; C &#124; 1!d &#124; E &#124; F  
  
 La sequenza di escape letterale GUID è supportata se il tipo di dati GUID è supportato dall'origine dati. Un'applicazione deve chiamare **SQLGetTypeInfo** per determinare se questo tipo di dati è supportato.
