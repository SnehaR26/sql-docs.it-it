---
title: Proprietà dinamica (ADO) prompt | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc11f2691613848865219f80b82a7d082803fa04
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752349"
---
# <a name="prompt-property-dynamic-ado"></a>Proprietà dinamica Prompt (ADO)
Specifica se il provider OLE DB deve richiedere all'utente le informazioni di inizializzazione.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta e restituisce un [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md) valore.  
  
## <a name="remarks"></a>Note  
 **Messaggio di richiesta** è una proprietà dinamica, che possono essere aggiunti al [Connection](../../../ado/reference/ado-api/connection-object-ado.md) dell'oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta in base al provider OLE DB. Per richiedere le informazioni sull'inizializzazione, i provider OLE DB in genere visualizzerà una finestra di dialogo per l'utente.  
  
 Proprietà dinamiche di un' [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto vengono perse quando il **connessione** viene chiuso. Il **dei messaggi di richiesta** proprietà deve essere reimpostata prima di riaprire il **connessione** per utilizzare un valore diverso da quello predefinito.  
  
> [!NOTE]
>  Non si specifica che il provider deve richiedere all'utente in scenari in cui l'utente non sarà in grado di rispondere alla finestra di dialogo. Ad esempio, l'utente non sarà in grado di rispondere se l'applicazione è in esecuzione in un sistema server invece che sul client dell'utente, o se l'applicazione è in esecuzione in un sistema senza utente connesso. In questi casi, l'applicazione attende una risposta per un periodo illimitato e sembra bloccarsi.  
  
## <a name="usage"></a>Utilizzo  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
