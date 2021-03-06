---
title: Opzione di configurazione del server clr enabled | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a796426f02c2ad9c0878c212c51eb0e90cfce8bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219377"
---
# <a name="clr-enabled-server-configuration-option"></a>Opzione di configurazione del server clr enabled
  Utilizzare l'opzione clr enabled per specificare se gli assembly utente possono essere eseguiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'opzione clr enabled restituisce i valori riportati di seguito.  
  
|valore|Description|  
|-----------|-----------------|  
|0|Esecuzione degli assembly non consentita in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|1|Esecuzione degli assembly consentita in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 I server WOW64 devono essere riavviati prima che le modifiche apportate a questa impostazione diventino effettive. Il riavvio non è necessario per altri tipi di server.  
  
> [!NOTE]  
>  Quando si esegue RECONFIGURE e il valore dell'opzione clr enabled viene modificato da 1 a 0, vengono scaricati immediatamente tutti i domini applicazione contenenti assembly utente.  
  
> [!NOTE]  
>  L'esecuzione di CLR (Common Language Runtime) non è supportata nell'ambito dell'opzione lightweight pooling. Disabilitare una delle due opzioni, "clr enabled" o "lightweight pooling". Le funzionalità che si basano su CLR e che non funzionano correttamente in modalità fiber includono il `hierarchy` tipo di dati, replica e la gestione basata su criteri.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene prima visualizzata l'impostazione corrente dell'opzione clr enabled, quindi abilitata l'opzione impostandone il valore su 1. Per disabilitare l'opzione, impostare il valore su 0.  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzione di configurazione del server lightweight pooling](lightweight-pooling-server-configuration-option.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Opzione di configurazione del server lightweight pooling](lightweight-pooling-server-configuration-option.md)  
  
  
