---
title: "Visualizzazione di un piano di esecuzione effettivo | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualizzazione dei piani di esecuzione"
  - "piani di esecuzione effettivi"
  - "visualizzazione dei piani di esecuzione"
  - "piani di esecuzione [SQL Server], visualizzazione"
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Visualizzazione di un piano di esecuzione effettivo
  In questo argomento viene descritto come generare piani di esecuzione grafici effettivi utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Alla generazione di piani di esecuzione effettivi vengono eseguite le query o i batch di comandi [!INCLUDE[tsql](../../includes/tsql-md.md)]. Il piano di esecuzione generato visualizza il piano di esecuzione query effettivo utilizzato da [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] per eseguire le query.  
  
 Per utilizzare questa funzionalità, gli utenti devono disporre delle autorizzazioni appropriate per eseguire le query [!INCLUDE[tsql](../../includes/tsql-md.md)] per le quali viene generato un piano di esecuzione grafico e dell'autorizzazione SHOWPLAN per tutti i database a cui fa riferimento la query.  
  
### Per includere un piano di esecuzione per una query durante l'esecuzione  
  
1.  Scegliere **Query del motore di database** nella barra degli strumenti [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per aprire una query esistente e visualizzare il piano di esecuzione stimato, è anche possibile fare clic sul pulsante **Apri file** della barra degli strumenti e trovare la query.  
  
2.  Immettere la query per quale si desidera visualizzare il piano di esecuzione effettivo.  
  
3.  Scegliere **Includi piano di esecuzione effettivo** dal menu **Query** oppure fare clic sul pulsante della barra degli strumenti **Includi piano di esecuzione effettivo**  
  
4.  Fare clic sul pulsante della barra degli strumenti **Esegui** per eseguire la query. Il piano usato da Query Optimizer viene visualizzato nella scheda **Piano di esecuzione** del riquadro dei risultati. Posizionando il puntatore del mouse sugli operatori logici e fisici è possibile visualizzare una descrizione comando contenente la descrizione e le proprietà degli operatori.  
  
     In alternativa, è possibile visualizzare le proprietà dell'operatore nella finestra Proprietà. Se la finestra Proprietà non è visibile, fare clic con il pulsante destro del mouse su un operatore e scegliere **Proprietà**. Selezionare un operatore e visualizzare le relative proprietà.  
  
5.  È possibile modificare la visualizzazione del piano di esecuzione facendo clic con il pulsante destro del mouse sul piano di esecuzione e scegliendo **Zoom avanti**, **Zoom indietro**, **Personalizza zoom** oppure **Adatta alla finestra**. Le opzioni **Zoom avanti** e **Zoom indietro** consentono rispettivamente di ingrandire e rimpicciolire il piano di esecuzione, mentre **Personalizza zoom** consente di definire un fattore di zoom personalizzato, ad esempio 80 percento. **Adatta alla finestra** consente di ingrandire il piano di esecuzione per adattarlo al riquadro dei risultati.  
  
  