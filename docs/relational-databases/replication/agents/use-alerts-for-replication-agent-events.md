---
title: "Utilizzare gli avvisi per gli eventi degli agenti di replica | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualizzazione di avvisi"
  - "Agente di lettura coda, avvisi"
  - "avvisi [replica di SQL Server]"
  - "avvisi di replica predefiniti [replica di SQL Server]"
  - "Agente di lettura log, avvisi"
  - "Agente di distribuzione, avvisi"
  - "Avvisi agente, avvisi"
  - "agenti [replica di SQL Server], avvisi"
  - "visualizzazione di avvisi"
  - "Agente snapshot, avvisi"
ms.assetid: 8c42e523-7020-471d-8977-a0bd044b9471
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Utilizzare gli avvisi per gli eventi degli agenti di replica
  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent consentono di monitorare gli eventi, ad esempio gli eventi dell'agente di replica, utilizzare gli avvisi. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent consente di monitorare il registro applicazioni di Windows per gli eventi che sono associate agli avvisi. Se si verifica un evento di questo tipo, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent risponde automaticamente eseguendo un'attività definita dall'utente e/o inviando un messaggio di posta elettronica o tramite cercapersone a un operatore specificato. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] include un set di avvisi predefiniti per gli agenti di replica che è possibile configurare per eseguire un'attività e/o notificare un operatore. Per ulteriori informazioni sulla definizione di un'attività da eseguire, vedere la sezione "Risposte automatiche a un avviso" in questo argomento.  
  
 Quando un computer viene configurato come server di distribuzione, vengono installati gli avvisi seguenti:  
  
|ID del messaggio|Avviso predefinito|Condizione che genera l'avviso|Inserimento di informazioni aggiuntive in msdb..sysreplicationalerts|  
|----------------|----------------------|-----------------------------------------|-----------------------------------------------------------------|  
|14150|**Replica: operazione dell'agente riuscita**|La chiusura dell'agente è stata completata correttamente.|Sì|  
|14151|**Replica: errore dell'agente**|Si è verificato un errore durante la chiusura dell'agente.|Sì|  
|14152|**Replica: nuovo tentativo dell'agente**|La chiusura dell'agente avviene in seguito al tentativo non riuscito di ripetere un'operazione. In questo caso, l'agente rileva un errore quale la non disponibilità del server, un deadlock, un errore di connessione o un errore di timeout.|Sì|  
|14157|**Replica: eliminata sottoscrizione scaduta**|La sottoscrizione scaduta è stata eliminata.|No|  
|20572|**Replica: la sottoscrizione è stata reinizializzata dopo l'errore di convalida**|Il processo di risposta "Reinizializzazione delle sottoscrizioni con errori di convalida dei dati" reinizializza una sottoscrizione correttamente.|No|  
|20574|**Replica: la convalida dei dati nel Sottoscrittore non è riuscita**|La convalida dei dati dell'agente di distribuzione o di merge non è riuscita.|Sì|  
|20575|**Replica: la convalida dei dati nel Sottoscrittore è riuscita**|La convalida dei dati dell'agente di distribuzione o di merge ha avuto esito positivo.|Sì|  
|20578|**Replica: arresto dell'agente personalizzato**|||  
|22815|**Avviso di rilevamento dei conflitti peer-to-peer**|L'agente di distribuzione ha rilevato un conflitto durante il tentativo di applicare una modifica a un nodo peer-to-peer.|Sì|  
  
 In aggiunta a questi avvisi, in Monitoraggio replica è disponibile un set di avvisi relativi allo stato e alle prestazioni. Per ulteriori informazioni, vedere [impostare soglie e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md). È inoltre possibile definire avvisi per altri eventi di replica utilizzando l'infrastruttura degli avvisi di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [creare un evento definito dall'utente](../../../ssms/agent/create-a-user-defined-event.md).  
  
 **Per configurare gli avvisi predefiniti della replica**  
  
-   [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: [Configure Predefined Replication Alerts &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/administration/configure-predefined-replication-alerts-sql-server-management-studio.md)  
  
## Visualizzazione diretta del registro applicazioni  
 Per visualizzare il registro applicazioni di Windows, utilizzare il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visualizzatore eventi di Windows. Il registro applicazioni contiene messaggi di errore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nonché messaggi per molte altre attività eseguite nel computer. Diversamente dal log degli errori di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a ogni avvio di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non viene creato un nuovo registro applicazioni (durante ogni sessione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono scritti nuovi eventi in un registro applicazioni esistente). È tuttavia possibile specificare il periodo di memorizzazione degli eventi registrati. Quando si visualizza il registro applicazioni di Windows, è possibile filtrarlo per eventi specifici. Per ulteriori informazioni, vedere la documentazione di Windows.  
  
## Risposte automatiche a un avviso  
 La replica include un processo di risposta per le sottoscrizioni con errore di convalida dei dati nonché una struttura per la creazione di ulteriori risposte automatiche agli avvisi. Il processo di risposta denominato **reinizializzazione delle sottoscrizioni con errori di convalida dei dati** e viene archiviato nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] agente **processi** cartella [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Per informazioni sull'abilitazione di questo processo di risposta, vedere [Configura avvisi di replica predefiniti & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/administration/configure-predefined-replication-alerts-sql-server-management-studio.md). Se la convalida degli articoli di una pubblicazione transazionale non riesce, il processo di risposta reinizializza solo gli articoli con errore. Se la convalida degli articoli di una pubblicazione di tipo merge non riesce, il processo di risposta reinizializza tutti gli articoli della pubblicazione.  
  
### Struttura per le risposte automatiche  
 Quando viene generato un avviso, le informazioni necessarie per comprenderne le causa e determinare l'intervento appropriato in genere sono contenute nel messaggio di avviso stesso. L'analisi di queste informazioni può essere soggetta a errori e richiedere tempi lunghi. La replica semplifica l'automatizzazione delle risposte da fornire informazioni aggiuntive sull'avviso nel **sysreplicationalerts** tabella di sistema; le informazioni fornite sono già analizzate in un formato facilmente utilizzato in programmi personalizzati.  
  
 Ad esempio, se i dati di **Sales. SalesOrderHeader** tabella nel server di sottoscrizione non viene convalidato, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] il messaggio di avviso 20574 per avvisare, segnala all'utente di tale errore. Il messaggio viene visualizzato sarà: "Sottoscrittore 'A', sottoscrizione per l'articolo 'SalesOrderHeader' della pubblicazione 'MyPublication' non è riuscita la convalida dei dati."  
  
 Se si crea una risposta in base al messaggio, è necessario analizzare in modo manuale il nome del Sottoscrittore, il nome dell'articolo, il nome della pubblicazione e l'errore indicato nel messaggio. Tuttavia, poiché l'agente di distribuzione e l'agente di Merge scrivono le stesse informazioni per **sysreplicationalerts** (insieme a dettagli quali il tipo di agente, l'ora dell'avviso, database di pubblicazione, database sottoscrittore e il tipo di pubblicazione) è possibile eseguire il processo di risposta direttamente query le informazioni dalla tabella. Anche se la riga esatta non può essere associata a un'istanza specifica dell'avviso, la tabella contiene un **stato** colonna, che può essere utilizzato per tenere traccia delle voci elaborate. Le voci di questa tabella sono disponibili per l'intero periodo di memorizzazione della cronologia.  
  
 Se, ad esempio, si desidera creare un processo di risposta in [!INCLUDE[tsql](../../../includes/tsql-md.md)] che elabori il messaggio di avviso 20574, è possibile utilizzare la logica seguente:  
  
```  
declare @publisher sysname, @publisher_db sysname, @publication sysname, @publication_type int, @article sysname, @subscriber sysname, @subscriber_db sysname, @alert_id int  
declare hc cursor local for select publisher, publisher_db, publication, publication_type, article, subscriber,   
  subscriber_db, alert_id from   
  msdb..sysreplicationalerts where  
  alert_error_code = 20574 and status = 0  
  for read only  
open hc  
fetch hc into  @publisher, @publisher_db, @publication, @publication_type, @article, @subscriber, @subscriber_db, @alert_id  
while (@@fetch_status <> -1)  
begin  
/* Do custom work  */  
/* Update status to 1, which means the alert has been serviced. This prevents subsequent runs of this job from doing this again */  
update msdb..sysreplicationalerts set status = 1 where alert_id = @alert_id  
 fetch hc into  @publisher, @publisher_db, @publication, @publication_type, @article, @subscriber, @subscriber_db, @alert_id  
end  
close hc  
deallocate hc  
```  
  
## Vedere anche  
 [Amministrazione dell'agente di replica](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Procedure consigliate per l'amministrazione della replica](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Monitoraggio & #40; Replica & #41;](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  