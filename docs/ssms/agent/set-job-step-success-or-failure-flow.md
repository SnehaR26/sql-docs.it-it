---
title: Impostare il flusso di interventi in caso di esito positivo o negativo del passaggio di processo | Microsoft Docs
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
- SQL Server Agent jobs, action flow logic
- successful jobs [SQL Server]
- failed jobs [SQL Server]
- jobs [SQL Server Agent], action flow logic
ms.assetid: 23041ccf-8a07-41d3-85b9-c449a54b7e1e
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f88c9c3b52f96ecba89570480cb5195a93b1eea3
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="set-job-step-success-or-failure-flow"></a>Set Job Step Success or Failure Flow
Quando si creano processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , è possibile specificare le azioni che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dovrà intraprendere in caso di errore durante l'esecuzione del processo. Determinare l'azione che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dovrà eseguire in caso di esito positivo o negativo di ogni passaggio di processo. Attenersi quindi alla procedura riportata di seguito per configurare la logica del flusso di azioni del passaggio di processo utilizzando [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per impostare il flusso di interventi in caso di esito positivo o negativo del passaggio di processo utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a>Per impostare il flusso di interventi in caso di esito positivo o negativo del passaggio di processo  
  
1.  In **Esplora oggetti**espandere **SQL Server Agent**e quindi **Processi**.  
  
2.  Fare clic con il pulsante destro del mouse sul processo da modificare e scegliere **Proprietà**.  
  
3.  Selezionare la pagina **Passaggi** , fare clic su un passaggio e quindi su **Modifica**.  
  
4.  Nella finestra di dialogo **Proprietà passaggio processo** selezionare la pagina **Avanzate** .  
  
5.  Nella finestra di dialogo **Azione in caso di esito positivo**fare clic sull'azione da eseguire se il passaggio del processo viene eseguito correttamente.  
  
6.  Nella casella **Numero tentativi** immettere un valore compreso tra 0 e 9999 per indicare il numero di ripetizioni desiderate del passaggio prima di stabilirne l'esito negativo. Se è stato immesso un valore maggiore di 0 nella casella **Numero tentativi** , immettere nella casella **Intervallo tra i tentativi (minuti)** un numero compreso tra 1 e 9999 per indicare i minuti che devono intercorrere tra due tentativi di esecuzione del passaggio del processo.  
  
7.  Nell'elenco **In caso di esito negativo** selezionare l'azione da eseguire in caso di esito negativo del passaggio.  
  
8.  Se il processo è uno script [!INCLUDE[tsql](../../includes/tsql_md.md)] , è possibile scegliere una delle opzioni seguenti:  
  
    -   Nella casella **File di output** immettere il nome di un file di output in cui scrivere l'output dello script. Per impostazione predefinita il file viene sovrascritto a ogni esecuzione del passaggio processo. Per evitarlo, selezionare **Accoda output a file esistente**.  
  
    -   Selezionare **Registra nella tabella** per registrare il passaggio processo in una tabella di database. Per impostazione predefinita il contenuto della tabella viene sovrascritto a ogni esecuzione del passaggio processo. Per evitarlo, selezionare **Accoda output a voce esistente nella tabella**. Dopo l'esecuzione del passaggio processo, è possibile visualizzare il contenuto della tabella facendo clic su **Visualizza**.  
  
    -   Selezionare **Includi output passaggio nella cronologia** se si desidera includere l'output nella cronologia dei passaggi. L'output verrà visualizzato solo se non si sono verificati errori. È inoltre possibile che l'output sia troncato.  
  
9. Se l'elenco **Esegui come utente** è disponibile selezionare l'account proxy account con le credenziali che verranno utilizzate dal processo.  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a>Per impostare il flusso di interventi in caso di esito positivo o negativo del passaggio di processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @on_success_action = 1;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per impostare il flusso di interventi in caso di esito positivo o negativo del passaggio di processo**  
  
Usare la classe **JobStep** con un linguaggio di programmazione a scelta, ad esempio Visual Basic, Visual C# o PowerShell. Per altre informazioni, vedere [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
