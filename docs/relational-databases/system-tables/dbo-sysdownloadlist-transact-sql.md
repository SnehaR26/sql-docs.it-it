---
title: dbo.sysdownloadlist (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysdownloadlist
- sysdownloadlist_TSQL
- dbo.sysdownloadlist_TSQL
- sysdownloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sysdownloadlist system table
ms.assetid: 71087a4c-e829-488e-aa7d-a9476e2b4779
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d0568403cb7f5bdf48d9be33e1b40f0be3fc1c33
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745086"
---
# <a name="dbosysdownloadlist-transact-sql"></a>dbo.sysdownloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Include la coda delle istruzioni di download per tutti i server di destinazione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Colonna Identity che indica la sequenza di inserimento naturale delle righe.|  
|**source_server**|**sysname**|Nome del server di origine.|  
|**operation_code**|**tinyint**|Codice operativo per il processo:<br /><br /> **1** = I COMPONENTI AGGIUNTIVI (INSERT)<br /><br /> **2** = UPD (AGGIORNAMENTO)<br /><br /> **3** = CANC (ELIMINA)<br /><br /> **4** = AVVIO<br /><br /> **5** = STOP|  
|**object_type**|**tinyint**|Codice del tipo di oggetto.|  
|**object_id** <sup>1</sup>|**uniqueidentifier**|Numero di identificazione dell'oggetto.|  
|**target_server**|**sysname**|Nome del server di destinazione.|  
|**error_message**|**nvarchar(1024)**|Messaggio di errore restituito se nel server di destinazione viene rilevato un errore durante l'elaborazione di una determinata riga|  
|**date_posted**|**datetime**|Giorno e ora in cui il processo è stato inviato al server di destinazione.|  
|**date_downloaded**|**datetime**|Giorno e ora in cui è stato eseguito l'ultimo download del processo.|  
|**status**|**tinyint**|Stato del processo:<br /><br /> **0** = non ancora scaricato<br /><br /> **1** = scaricato correttamente|  
|**deleted_object_name**|**sysname**|Nome dell'oggetto eliminato.|  
  
 <sup>1</sup> il **object_id** colonna può essere un valore di **-1**, che corrisponde a un valore se tutti i **operation_code** colonna è un valore di eliminazione.  
  
  
