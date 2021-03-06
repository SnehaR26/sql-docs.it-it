---
title: Cancel (metodo) (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Cancel method [RDS]
ms.assetid: 560b5b3d-fba9-4275-8920-9c3e186134f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be5ff99397e73f1098f4c11b57a636b08bfa5921
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747319"
---
# <a name="cancel-method-rds"></a>Metodo Cancel (Servizi Desktop remoto)
Annulla l'esecuzione di un'in sospeso, chiamata asincrona al metodo.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più incluse nel sistema operativo Windows (vedere Windows 8 e [indicazioni sulla compatibilità di Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). I componenti client di servizi desktop remoto verranno rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che usano servizi desktop remoto devono eseguire la migrazione a [di WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RDS.DataControl.Cancel  
```  
  
## <a name="remarks"></a>Note  
 Quando si chiama **annullare**, [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) viene impostata automaticamente **adcReadyStateLoaded**e il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sarà vuoto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo Cancel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Metodo Cancel (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Metodo CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Metodo CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Metodo CancelUpdate (Servizi Desktop remoto)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Proprietà ExecuteOptions (Servizi Desktop remoto)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


