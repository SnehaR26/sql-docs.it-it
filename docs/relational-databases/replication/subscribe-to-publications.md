---
title: "Sottoscrizione delle pubblicazioni | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.conc.subtopubs.f1"
helpviewer_keywords: 
  - "sottoscrizioni [replica di SQL Server], informazioni sulle sottoscrizioni"
  - "sottoscrizioni pull [replica di SQL Server]"
  - "sottoscrizioni [replica di SQL Server]"
  - "sottoscrizioni push [replica di SQL Server], informazioni sulle sottoscrizioni push"
  - "sottoscrizione della replica di tipo merge [replica di SQL Server]"
  - "sottoscrizione della replica di tipo merge [replica di SQL Server], informazioni sulla sottoscrizione"
  - "pubblicazioni [replica di SQL Server], sottoscrizione"
  - "sottoscrizioni push [replica di SQL Server]"
  - "sottoscrizioni pull [replica di SQL Server], informazioni sulle sottoscrizioni pull"
  - "replica snapshot [SQL Server], sottoscrizione"
  - "replica transazionale, sottoscrizione"
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Sottoscrizione delle pubblicazioni
  Una sottoscrizione è la richiesta di una copia di dati o di oggetti di database in una pubblicazione. Una sottoscrizione definisce quale pubblicazione verrà ricevuta, insieme alla posizione e al momento in cui verrà ricevuta. Quando si pianificano le sottoscrizioni, è necessario decidere dove si desidera eseguire l'elaborazione dell'agente. La posizione di esecuzione dell'agente varia in base al tipo di sottoscrizione selezionato. In una sottoscrizione push, l'agente di merge o l'agente di distribuzione viene eseguito nel server di distribuzione, mentre in una sottoscrizione pull gli agenti vengono eseguiti nei Sottoscrittori. Dopo la creazione di una sottoscrizione non è più possibile modificarne il tipo.  
  
|Sottoscrizione|Caratteristiche|Situazioni in cui utilizzarla|  
|------------------|---------------------|--------------|  
|Sottoscrizione push|Nelle sottoscrizioni push il server di pubblicazione propaga le modifiche a un Sottoscrittore senza che il Sottoscrittore ne faccia richiesta. È possibile inviare le modifiche ai Sottoscrittori su richiesta, in modo continuato o in base a una pianificazione definita. L'agente di distribuzione o l'agente di merge viene eseguito nel server di distribuzione.|I dati vengono sincronizzati in modo continuato o in modo ricorrente in base a una pianificazione specifica.<br /><br /> Le pubblicazioni richiedono lo spostamento dei dati quasi in tempo reale.<br /><br /> In un server di distribuzione l'aumento dell'overhead del processore non compromette le prestazioni.<br /><br /> Generalmente utilizzato con la replica snapshot e transazionale.|  
|Sottoscrizione pull|Tramite le sottoscrizioni pull il Sottoscrittore richiede le modifiche eseguite nel server di pubblicazione. Le sottoscrizioni pull consentono al Sottoscrittore di stabilire quando sincronizzare le modifiche apportate ai dati. L'agente di distribuzione o l'agente di merge viene eseguito nel Sottoscrittore.|I dati vengono sincronizzati su richiesta o in base a una pianificazione anziché in modo continuo.<br /><br /> Alla pubblicazione è associato un numero elevato di Sottoscrittori e/o l'esecuzione di tutti gli agenti nel server di distribuzione richiederebbe un numero di risorse eccessivo.<br /><br /> I Sottoscrittori sono autonomi, scollegati e/o mobili. I Sottoscrittori determinano quando eseguire la connessione e quando sincronizzare le modifiche.<br /><br /> Generalmente utilizzato con la replica di tipo merge.|  
  
## Tipi di sottoscrizione della replica di tipo merge  
 Tutti i tipi di replica consentono le sottoscrizioni push e pull. Per la replica di tipo merge vengono usati due termini aggiuntivi per distinguere le sottoscrizioni: sottoscrizioni client e sottoscrizioni server. Le sottoscrizioni client e server possono essere entrambe utilizzate con le sottoscrizioni push e pull. Le sottoscrizioni client sono appropriate per la maggior parte dei Sottoscrittori, mentre le sottoscrizioni server sono generalmente utilizzate per i Sottoscrittori che ripubblicano i dati in altri Sottoscrittori. La scelta del tipo di sottoscrizione influisce anche sulla risoluzione dei conflitti.  
  
## Sottoscrittori non SQL Server  
 Nei sistemi Oracle e IBM DB2 è possibile sottoscrivere pubblicazioni snapshot e transazionali mediante le sottoscrizioni push. Per ulteriori informazioni, vedere [sottoscrittori Non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
## Creazione di sottoscrizioni  
 Per creare una sottoscrizione, è necessario specificare le seguenti informazioni:  
  
-   Nome della pubblicazione.  
  
-   Nome del Sottoscrittore e database di sottoscrizione.  
  
-   Se l'agente di distribuzione o l'agente di merge viene eseguito nel server di distribuzione o nel Sottoscrittore.  
  
-   Se l'agente di distribuzione o di merge viene eseguito in modo continuato, in base a una pianificazione specifica oppure solo su richiesta.  
  
-   Se l'agente di snapshot deve creare uno snapshot iniziale per la sottoscrizione e l'agente di distribuzione o di merge deve applicare lo snapshot al Sottoscrittore.  
  
-   Account utilizzati per eseguire l'agente di distribuzione o di merge.  
  
-   Per la replica di tipo merge, il tipo di sottoscrizione: server o client.  
  
 **Per creare una sottoscrizione push**  
  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)  
  
 **Per visualizzare o modificare le proprietà di sottoscrizione push**  
  
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)  
  
 **Per eliminare una sottoscrizione push**  
  
 [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md)  
  
> [!NOTE]  
>  Se si elimina una sottoscrizione non si rimuovono gli oggetti pubblicati dal Sottoscrittore.  
  
 **Per creare una sottoscrizione pull**  
  
 [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)  
  
 **Per visualizzare o modificare le proprietà di sottoscrizione pull**  
  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)  
  
 **Per eliminare una sottoscrizione pull**  
  
 [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md)  
  
## Vedere anche  
 [Sicurezza del Sottoscrittore](../../relational-databases/replication/security/secure-the-subscriber.md)   
 [Scadenza e disattivazione delle sottoscrizioni](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  