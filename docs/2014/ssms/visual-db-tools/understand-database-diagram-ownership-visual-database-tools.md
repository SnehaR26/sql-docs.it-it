---
title: Informazioni sulla proprietà dei diagrammi di database (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0fef70305887b7d0b2d5face1dc31a2e7ea451c6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102451"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Informazioni sulla proprietà dei diagrammi di database (Visual Database Tools)
  Per poter utilizzare la Progettazione diagrammi di database, è necessario che un membro del ruolo db_owner (un ruolo dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) ne effettui preventivamente la configurazione per il controllo dell'accesso ai diagrammi. Ciascun diagramma ha un solo proprietario, ovvero l'utente che lo ha creato. Per altre informazioni sull'impostazione dei diagrammi, vedere [Set Up Database Diagram Designer &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 In relazione alla proprietà dei diagrammi, tenere presente quanto segue:  
  
-   Benché un diagramma possa essere creato da qualsiasi utente che dispone di accesso a un database, potrà essere visualizzato solo dall'utente che lo ha creato e dai membri del ruolo db_owner.  
  
-   La proprietà dei diagrammi può essere trasferita solo ai membri del ruolo db_owner e soltanto se il proprietario precedente è stato rimosso dal database.  
  
-   Se il proprietario di un diagramma viene rimosso dal database, il diagramma rimarrà all'interno del database finché un membro del ruolo db_owner non tenterà di aprirlo. A questo punto, il membro del ruolo db_owner potrà scegliere di subentrare come proprietario del diagramma.  
  
## <a name="see-also"></a>Vedere anche  
 [Usare diagrammi di Database &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md)   
 [Impostazione di Progettazione diagrammi di database &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
