---
title: "Nuovo profilo agente | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.profiles.newperfprofile.f1"
helpviewer_keywords: 
  - "Nuovo profilo agente - finestra di dialogo"
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Nuovo profilo agente
  La finestra di dialogo **Nuovo profilo agente** consente di creare un nuovo profilo. I nuovi profili sono sempre basati su profili esistenti, ma possono essere modificati in base ai requisiti delle applicazioni. Dopo aver creato un profilo, è possibile applicarlo a processi agente esistenti e creati in un secondo momento nella finestra di dialogo **Profili agente** . I valori dei parametri dell'agente possono essere modificati nel \<**AgentProfileName > proprietà** la finestra di dialogo.  
  
## Opzioni  
 **Nome**  
 Consente di immettere un nome per il profilo.  
  
 **Descrizione**  
 Consente di immettere una descrizione per il profilo.  
  
 **Parametro**  
 I parametri degli agenti inclusi nel profilo. Il profilo su cui è basato il nuovo profilo non contiene necessariamente un valore per ogni parametro. Per visualizzare tutti i parametri validi per un determinato agente, deselezionare la casella di controllo **Mostra solo i parametri utilizzati in questo profilo** . Per una descrizione dei singoli parametri, vedere:  
  
-   [Agente snapshot repliche](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Agente lettura log repliche](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Agente distribuzione repliche](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Agente merge repliche](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Agente di lettura coda repliche](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 **Valore predefinito**  
 Il valore predefinito per ogni parametro degli agenti.  
  
 **Valore**  
 Il valore specificato per il parametro nel profilo su cui è basato il nuovo profilo. Modificare questo campo per qualsiasi valore di parametro che si desidera modificare.  
  
 **Mostra solo i parametri utilizzati in questo profilo**  
 Deselezionare questa casella di controllo per mostrare tutti i parametri validi per un determinato agente.  
  
## Vedere anche  
 [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Profili degli agenti di replica](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  