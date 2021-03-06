---
title: Funzione SQLGetConfigMode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1148ab38f7d389c3fe78a09a646a9cbdec0bb723
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755789"
---
# <a name="sqlgetconfigmode-function"></a>Funzione SQLGetConfigMode
**Conformità**  
 Versione introdotta: ODBC 3.0  
  
 **Riepilogo**  
 **SQLGetConfigMode** recupera la modalità di configurazione che indica se la voce ini Elenca i valori DSN è nelle informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Argomenti  
 *pwConfigMode*  
 [Output] Puntatore al buffer che contiene la modalità di configurazione. (Vedere "Commenti".) Il valore in  *\*pwConfigMode* può essere:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetConfigMode** FALSO, restituisce un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* i valori che possono essere restituiti da **SQLInstallerError** e illustra ognuna nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione non è stato possibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 Questa funzione viene utilizzata per determinare la posizione di voce ini Elenca i valori DSN nelle informazioni di sistema. Se  *\*pwConfigMode* è ODBC_USER_DSN, il DSN è un DSN utente e la funzione legge dalla voce ini in HKEY_CURRENT_USER. Se si tratta ODBC_SYSTEM_DSN, il DSN è un DSN di sistema e la funzione legge dalla voce ini in HKEY_LOCAL_MACHINE. Se si tratta ODBC_BOTH_DSN, viene eseguito un tentativo di HKEY_CURRENT_USER e in caso contrario, viene usato HKEY_LOCAL_MACHINE.  
  
 Per impostazione predefinita **SQLGetConfigMode** restituisce ODBC_BOTH_DSN. Quando viene creato un DSN utente o un DSN di sistema da una chiamata a **SQLConfigDataSource**, la funzione imposta la modalità di configurazione su ODBC_USER_DSN o ODBC_SYSTEM_DSN per distinguere i DSN di sistema e utente durante la modifica di un DSN. Prima della restituzione, **SQLConfigDataSource** ODBC_BOTH_DSN Reimposta la modalità di configurazione.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Impostazione della modalità di configurazione|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
