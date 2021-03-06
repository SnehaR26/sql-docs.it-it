---
title: Notificare lo stato di un processo a un operatore | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7762daa362b73f981603f7d32a41b8084327e1f8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185321"
---
# <a name="notify-an-operator-of-job-status"></a>Notify an Operator of Job Status
  In questo argomento si illustra come impostare opzioni di notifica in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o SQL Server Management Objects, in modo che tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sia possibile inviare notifiche agli operatori relative ai processi.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per notificare lo stato di un processo a un operatore mediante:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-notify-an-operator-of-job-status"></a>Per notificare lo stato di un processo a un operatore  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**e **Processi**, fare clic con il pulsante destro del mouse sul processo che si vuole modificare e scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà processo** selezionare la pagina **Notifiche** .  
  
4.  Se si vuole inviare una notifica a un operatore tramite posta elettronica, selezionare la casella **Posta elettronica**, selezionare un operatore nell'elenco e scegliere una delle opzioni seguenti:  
  
    -   **In caso di esito positivo processo** per inviare la notifica all'operatore se il processo è stato completato correttamente.  
  
    -   **In caso di esito negativo processo** per inviare all'operatore una notifica del completamento non riuscito del processo.  
  
    -   **Al termine del processo** per inviare la notifica all'operatore indipendentemente dallo stato di completamento.  
  
5.  Se si desidera inviare una notifica a un operatore tramite cercapersone, selezionare la casella **Cercapersone**, selezionare un operatore nell'elenco e quindi scegliere una delle opzioni seguenti:  
  
    -   **In caso di esito positivo processo** per inviare la notifica all'operatore se il processo è stato completato correttamente.  
  
    -   **In caso di esito negativo processo** per inviare all'operatore una notifica del completamento non riuscito del processo.  
  
    -   **Al termine del processo** per inviare la notifica all'operatore indipendentemente dallo stato di completamento.  
  
6.  Se si desidera inviare una notifica a un operatore tramite Net Send, selezionare la casella **Net Send**, selezionare un operatore nell'elenco e quindi scegliere una delle opzioni seguenti:  
  
    -   **In caso di esito positivo processo** per inviare la notifica all'operatore se il processo è stato completato correttamente.  
  
    -   **In caso di esito negativo processo** per inviare all'operatore una notifica del completamento non riuscito del processo.  
  
    -   **Al termine del processo** per inviare la notifica all'operatore indipendentemente dallo stato di completamento.  
  
##  <a name="TSQL"></a> Uso di Transact-SQL  
  
#### <a name="to-notify-an-operator-of-job-status"></a>Per notificare lo stato di un processo a un operatore  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that François Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'François Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).  
  
##  <a name="SMO"></a> Utilizzo di SQL Server Management Objects  
 **Per notificare lo stato di un processo a un operatore**  
  
 Usare il `Job` classe utilizzando un linguaggio di programmazione desiderato, ad esempio Visual Basic, Visual c# o PowerShell. Per altre informazioni, vedere [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
