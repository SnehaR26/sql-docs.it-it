---
title: "Configurazione di un server per l&#39;attesa su una pipe alternativa (Gestione configurazione SQL Server) | Microsoft Docs"
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
  - "Named Pipe [SQL Server], configurazione"
  - "attesa [SQL Server], pipe"
  - "pipe [SQL Server], alternative"
  - "pipe alternative [SQL Server]"
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Configurazione di un server per l&#39;attesa su una pipe alternativa (Gestione configurazione SQL Server)
  In questo argomento viene illustrato come configurare un server per l'ascolto su una pipe alternativa in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando Gestione configurazione SQL Server. Per impostazione predefinita, l'istanza predefinita di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] è in attesa sulla named pipe \\\\.\pipe\sql\query. Le istanze denominate del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] e [!INCLUDE[ssEW](../../includes/ssew-md.md)] sono in attesa su altre pipe.  
  
 È possibile connettersi a una named pipe specifica mediante un'applicazione client in tre modi differenti:  
  
-   Avviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser sul server.  
  
-   Creare un alias nel client, specificando la named pipe.  
  
-   Programmare il client affinché si connetta utilizzando una stringa di connessione personalizzata.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di Gestione configurazione SQL Server  
  
#### Per configurare l'utilizzo della named pipe mediante il Motore di database di SQL Server  
  
1.  Nel riquadro della console di Gestione configurazione SQL Server, espandere **Configurazione di rete SQL Server** e **Protocolli per** *\<nome istanza>*.  
  
2.  Nel riquadro dei dettagli fare clic con il pulsante destro del mouse su **Named pipe**, quindi scegliere **Proprietà**.  
  
3.  Nel riquadro **Nome pipe** della scheda **Protocollo** , specificare la pipe su cui si desidera che il [!INCLUDE[ssDE](../../includes/ssde-md.md)] sia in attesa e quindi fare clic su **OK**.  
  
4.  Nel riquadro della console fare clic su **Servizi di SQL Server**.  
  
5.  Nel riquadro dei dettagli fare clic con il pulsante destro del mouse su **SQL Server (**\<nome istanza>**)** e scegliere **Riavvia**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà arrestato e riavviato.  
  
 Quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in attesa su una pipe alternativa, è possibile connettersi a una named pipe specifica mediante un'applicazione client in tre modi differenti:  
  
-   Avviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser sul server.  
  
-   Creare un alias nel client, specificando la named pipe.  
  
-   Programmare il client affinché si connetta utilizzando una stringa di connessione personalizzata.  
  
## Vedere anche  
 [Creare o eliminare un alias server per l'uso da parte di un client &#40;Gestione configurazione SQL Server Manager&#41;](../../database-engine/configure-windows/create or delete a server alias for use by a client.md)   
 [Configurazione di rete del server](../../database-engine/configure-windows/server-network-configuration.md)  
  
  