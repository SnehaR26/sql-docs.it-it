---
title: Mapping di SQLBindParam | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26f9bdc0564b98132bb5ec413c99917e78e4d62e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855179"
---
# <a name="sqlbindparam-mapping"></a>Mapping di SQLBindParam
**SQLBindParam** non può essere chiamato deprecato perché non vi era presente in ODBC; tuttavia, ancora rappresenta funzionalità duplicate, è necessario esportarlo perché le applicazioni ISO e conforme a Open gruppo verranno utilizzato Gestione Driver. In quanto **SQLBindParameter** contiene tutte le funzionalità di **SQLBindParam**, **SQLBindParam** verrà mappato in cima **SQLBindParameter** (quando il driver sottostante è un'applicazione ODBC 3*x* driver). Un'applicazione ODBC 3 *. x* driver non è necessario implementare **SQLBindParam**.  
  
## <a name="remarks"></a>Note  
 Quando la chiamata seguente a **SQLBindParam** viene eseguito:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 le chiamate di gestione Driver **SQLBindParameter** nel driver come indicato di seguito:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Visualizzare [le informazioni ODBC 64-Bit](../../../odbc/reference/odbc-64-bit-information.md), se l'applicazione verrà eseguita in un sistema operativo a 64 bit.  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di funzioni deprecate](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
