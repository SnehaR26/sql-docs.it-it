---
title: Catalog. environment_references (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: efec53ef-3e5a-4b76-b71d-a0cf9e11ac00
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ee6f15af7a5384fea850aa67c7b5a95483530740
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogenvironmentreferences-ssisdb-database"></a>catalog.environment_references (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Consente di visualizzare i riferimenti all'ambiente per tutti i progetti di **SSISDB** catalogo.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|reference_id|**bigint**|Identificatore (ID) univoco del riferimento.|  
|project_id|**bigint**|ID univoco del progetto.|  
|reference_type|**Char (1)**|Viene indicato se l'ambiente può essere individuato nella stessa cartella del progetto (riferimento relativo) o in una cartella diversa (riferimento assoluto). Quando il valore è `R`, l'ambiente viene individuato tramite un riferimento relativo. Quando il valore è `A`, l'ambiente viene individuato tramite un riferimento assoluto.|  
|environment_folder_name|**sysname**|Nome della cartella se l'ambiente viene individuato tramite un riferimento assoluto.|  
|environment_name|**sysname**|Nome dell'ambiente a cui fa riferimento il progetto.|  
|validation_status|**Char (1)**|Stato della convalida.|  
|last_validation_time|**datatimeoffset(7)**|Ora dell'ultima convalida.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista viene visualizzata una riga per ogni riferimento all'ambiente nel catalogo.  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per il progetto corrispondente  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server.  
  
> [!NOTE]  
>  Se si dispone dell'autorizzazione READ per un progetto, si dispone anche dell'autorizzazione READ per tutti i pacchetti e i riferimenti all'ambiente associati a tale progetto. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
## <a name="remarks"></a>Osservazioni  
 Un progetto può disporre di riferimenti all'ambiente relativi o assoluti. I riferimenti relativi fanno riferimento all'ambiente in base al nome. Per tali riferimenti è necessario che l'ambiente si trovi nella stessa cartella del progetto. I riferimenti assoluti fanno riferimento all'ambiente in base al nome e alla cartella e possono fare riferimento ad ambienti che si trovano in una cartella di destinazione diversa da quella del progetto. Un progetto può fare riferimento a più ambienti.  
  
  