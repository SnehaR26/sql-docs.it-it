---
title: Chiavi simmetriche nei database utente | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1b00f346f53bf0dced0da1182376d8575986e92a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165081"
---
# <a name="symmetric-keys-on-user-databases"></a>Chiavi simmetriche nei database utente
  Questa regola consente di controllare se le chiavi con lunghezza minore di 128 byte utilizzano l'algoritmo di crittografia RC2 o RC4.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Utilizzare la crittografia AES a 128 bit o maggiore per creare chiavi simmetriche per la crittografia dei dati. Se la crittografia AES non è supportata dal sistema operativo in uso, utilizzare 3DES.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Scelta di un algoritmo di crittografia](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
