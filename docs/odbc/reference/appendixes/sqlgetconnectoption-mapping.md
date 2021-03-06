---
title: Mapping di SQLGetConnectOption | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8504709cb2cedb36c62bb9be74ffc8d12a4c811d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745789"
---
# <a name="sqlgetconnectoption-mapping"></a>Mapping di SQLGetConnectOption
Quando un'applicazione chiama **SQLGetConnectOption** tramite un'applicazione ODBC 3*x* driver, la chiamata a  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 viene eseguito il mapping come segue:  
  
-   Se *fOption* indica un'opzione di connessione definite da ODBC che restituisce una stringa, le chiamate di gestione Driver  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Se *fOption* indica un'opzione di connessione definite da ODBC che restituisce un valore integer a 32 bit, le chiamate di gestione Driver  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Se *fOption* indica un'opzione di istruzione definiti dal driver, le chiamate di gestione Driver  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 Nei tre casi precedenti, il *ConnectionHandle* argomento è impostato sul valore *hdbc*, il *attributo* argomento è impostato sul valore in *fOption* e il *ValuePtr* argomento è impostato sullo stesso valore come *il parametro pvParam*.  
  
 Per le opzioni di connessione di stringa definite da ODBC, gestione Driver imposta il *BufferLength* argomento nella chiamata a **SQLGetConnectAttr** alla lunghezza massima predefinita (SQL_MAX_OPTION_STRING_LENGTH); per un'opzione di connessione, non di tipo stringa *BufferLength* è impostato su 0.  
  
 Per un'applicazione ODBC 3 *. x* driver, gestione Driver non controlla se *opzione* compresa tra SQL_CONN_OPT_MIN e SQL_CONN_OPT_MAX, oppure è maggiore di SQL_CONNECT_OPT_DRVR_START. Il driver deve verificare la validità dei valori di opzione.
