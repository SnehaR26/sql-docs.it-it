---
title: Metodo SetStartMode (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetStartMode Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 289317a56c1a48b69b500758fbbb47e57b8a49e6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112099"
---
# <a name="setstartmode-method-sqlservice-class"></a>Metodo SetStartMode (classe SqlService)
  Modifica la modalità di avvio dell'istanza del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.SetStartMode(  
StartMode  
)  
  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SqlService](sqlservice-class.md) che rappresenta il servizio.  
  
#### <a name="parameters"></a>Parametri  
 *StartMode*  
 Valore `uint32` che specifica la modalità di avvio dell'istanza del servizio.  
  
 I valori validi sono i seguenti:  
  
 Valore = 0. Boot: driver di dispositivo avviato dal caricatore del sistema operativo. Questo valore è valido solo per i servizi del driver.  
  
 Valore = 1. System: driver di dispositivo avviato dal metodo `IoInitSystem`. Questo valore è valido solo per i servizi del driver.  
  
 Valore = 2. Automatic: servizio da avviare automaticamente da Gestione controllo servizi durante l'avvio del sistema.  
  
 Valore = 3. Manual: servizio da avviare da Gestione computer quando un processo chiama il metodo `StartService`.  
  
 Valore = 4. Disabled: impossibile avviare il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore `uint32` che è 0 se il servizio è stato modificato correttamente 0 1 se la richiesta non è supportata. Qualsiasi altro numero indica un errore.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
