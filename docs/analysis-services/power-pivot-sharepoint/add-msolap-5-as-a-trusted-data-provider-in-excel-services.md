---
title: "Aggiungere MSOLAP.5 come provider di dati attendibile in Excel Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1f40fa4-de6d-41ee-8124-14b4d65988f5
caps.latest.revision: 6
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 6
---
# Aggiungere MSOLAP.5 come provider di dati attendibile in Excel Services
  MSOLAP.5 si riferisce al provider OLE DB di Analysis Services per SQL Server 2012. Excel Services deve considerare attendibile questo provider prima di effettuare la richiesta di connessione che comporta la disponibilità di dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in un server.  
  
 Se [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint è stato configurato usando lo strumento di configurazione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], MSOLAP.5 potrebbe già essere un provider attendibile perché lo strumento include un'azione che soddisfa questo requisito. Se tuttavia si usa PowerShell o Amministrazione centrale oppure se l'azione del provider attendibile è stata esclusa nello strumento di configurazione, il provider potrebbe essere mancante ed è quindi necessario aggiungerlo durante la configurazione della farm per l'accesso ai dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 È sufficiente eseguire questo passaggio una volta per ogni applicazione di servizio Excel Services.  
  
 Per ogni server fisico che gestisce una richiesta di dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], ad esempio un server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint o un server Excel Services, il provider OLE DB deve essere installato nel computer. Un'installazione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint include sempre il provider OLE DB, ma se Excel Services è in esecuzione in un computer su cui non è disponibile [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint, è necessario installare manualmente il provider. Per altre informazioni, vedere [Installazione del provider OLE DB di Analysis Services nei server di SharePoint](http://msdn.microsoft.com/it-it/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
## Aggiungere un provider attendibile a Excel Services  
  
1.  In Amministrazione centrale fare clic su **Gestisci applicazioni di servizio**, quindi fare clic sull'applicazione di servizio Excel Services.  
  
2.  Fare clic su **Provider di dati attendibili**.  
  
3.  Verificare che MSOLAP.5 sia visualizzato nell'elenco. A seconda di come è stato configurato [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint, MSOLAP.5 potrebbe già essere considerato attendibile.  
  
4.  Se non è elencato, fare clic su **Aggiungi provider di dati attendibile**.  
  
5.  In ID provider, digitare **MSOLAP.5**.  
  
6.  Per Tipo di provider, assicurarsi che sia selezionato OLE DB.  
  
7.  In Descrizione provider digitare **Provider Microsoft OLE DB per OLAP Services 11.0**.  
  
  