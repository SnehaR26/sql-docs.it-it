---
title: Impostare l'arresto dell'esecuzione del processo (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 935a54d1f3b7606ac4f761e9e49953edfd7f77e6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091991"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Set Job Execution Shutdown (SQL Server Management Studio)
  In questo argomento viene illustrata la procedura di impostazione del periodo di attesa di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prima di terminare l'esecuzione dei processi, trascorso il quale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stesso viene interrotto in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per impostare il tempo di arresto per un processo di SQL Server Agent utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per impostazione predefinita, i membri del ruolo predefinito del server **sysadmin** possono impostare il periodo di attesa di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prima di terminare l'esecuzione dei processi, trascorso il quale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stesso viene interrotto. Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-set-job-execution-shutdown"></a>Per impostare l'arresto dell'esecuzione del processo  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server in cui si desidera impostare un intervallo per l'arresto dell'esecuzione del processo.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent** e scegliere **Proprietà**.  
  
3.  In **Selezione pagina**selezionare **Sistema processi**.  
  
4.  Impostare l'opzione **Intervallo di time-out chiusura** (in secondi) per aumentare o ridurre l'intervallo di time-out di chiusura. Questo valore determina l'intervallo di attesa del completamento dell'esecuzione dei processi da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, trascorso il quale viene interrotto anche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
  
