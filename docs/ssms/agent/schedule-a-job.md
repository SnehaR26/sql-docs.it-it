---
title: Pianificare un processo | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 86798cd5e3705ea8f5a575df76d245bf41e625d8
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="schedule-a-job"></a>Pianificare un processo
In questo argomento viene descritto come pianificare un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
-   **Prima di iniziare:** ,  
  
    [Security](#Security)  
  
-   **Per pianificare un processo utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a>Per creare e collegare una pianificazione a un processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**, espandere **Processi**, fare clic con il pulsante destro del mouse sul processo che si vuole pianificare e scegliere **Proprietà**.  
  
3.  Selezionare la pagina **Pianificazioni** e quindi fare clic su **Nuovo**.  
  
4.  Nella casella **Nome** digitare un nome per la nuova pianificazione.  
  
5.  Deselezionare la casella di controllo **Abilitata** se non si desidera attivare la pianificazione subito dopo la relativa creazione.  
  
6.  Per **Tipo pianificazione**, selezionare una delle opzioni seguenti:  
  
    -   Fare clic su **Avvia automaticamente all'avvio di SQL Server Agent** per avviare il processo all'avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
    -   Fare clic su **Avvia quando la CPU diventa inattiva** per avviare il processo quando la CPU raggiunge una condizione di inattività.  
  
    -   Fare clic su **Periodica** se si desidera eseguire ripetutamente una pianificazione. Per impostare la pianificazione periodica, completare i gruppi **Frequenza**, **Frequenza giornaliera**e **Durata** della finestra di dialogo.  
  
    -   Fare clic su **Singola occorrenza** se si desidera che la pianificazione venga eseguita una sola volta. Per impostare la pianificazione di tipo **Singola occorrenza** , completare il gruppo **Singola occorrenza** nella finestra di dialogo.  
  
#### <a name="to-attach-a-schedule-to-a-job"></a>Per collegare una pianificazione a un processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**, espandere **Processi**, fare clic con il pulsante destro del mouse sul processo che si vuole pianificare e scegliere **Proprietà**.  
  
3.  Selezionare la pagina **Pianificazioni** , quindi fare clic su **Seleziona**.  
  
4.  Selezionare la pianificazione da collegare, quindi scegliere **OK**.  
  
5.  Nella finestra di dialogo **Proprietà processo** , fare doppio clic sulla pianificazione collegata.  
  
6.  Verificare che l'opzione **Data inizio** sia impostata correttamente. In caso contrario, impostare la data desiderata per l'avvio della pianificazione, quindi fare clic su **OK**.  
  
7.  Nella finestra di dialogo **Proprietà processo** scegliere **OK**.  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-schedule-a-job"></a>Per pianificare un processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_add_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7) e [sp_attach_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/80c80eaf-cf23-4ed8-b8dd-65fe59830dd1).  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
Usare la classe **JobSchedule** tramite un linguaggio di programmazione a scelta, ad esempio Visual Basic, Visual C# o PowerShell. Per altre informazioni, vedere[SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
