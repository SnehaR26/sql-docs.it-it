---
title: "Credenziali Oracle per l&#39;esecuzione di script | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Credenziali Oracle per l&#39;esecuzione di script
  Per eseguire lo script di registrazione supplementare di Oracle da CDC Designer Console, vengono richieste le credenziali dell'utente Oracle che esegue lo script. Per eseguire questo script, l'utente Oracle deve disporre dell'autorizzazione ALTER TABLE per tutte le tabelle da acquisire e dell'autorizzazione SELECT per la vista DBA_LOG_GROUPS.  
  
## Elenco attività  
 Immettere quanto segue nella finestra di dialogo:  
  
 **Autenticazione**  
  
 Selezionare una delle opzioni seguenti:  
  
-   **Windows Authentication**: selezionare questa opzione per utilizzare le credenziali del dominio Windows correnti. È possibile utilizzare questa opzione solo se il database Oracle è configurato per l'utilizzo dell'autenticazione di Windows.  
  
-   **Oracle Authentication**: se si seleziona questa opzione, è necessario digitare il **nome utente** e la **password** dell'utente nel database Oracle di origine a cui si effettua la connessione.  
  
## Vedere anche  
 [Procedura di gestione di un'istanza di CDC](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [Rivedere e generare script di registrazione supplementare](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  