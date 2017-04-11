---
title: "Configurazione di rete del server | Microsoft Docs"
ms.custom: ""
ms.date: "07/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Named Pipe [SQL Server], configurazione"
  - "connessioni [SQL Server], configurazione di rete del server"
  - "Motore di database [SQL Server], configurazioni di rete"
  - "configurazione di rete del server [SQL Server]"
  - "protocolli [SQL Server], scelta"
  - "porte [SQL Server], modifiche"
  - "configurazione server [SQL Server]"
ms.assetid: 890c09a1-6dad-4931-aceb-901c02ae34c5
caps.latest.revision: 50
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 50
---
# Configurazione di rete del server
  Le attività di configurazione di rete del server includono l'abilitazione dei protocolli, la modifica della porta o della pipe utilizzata da un protocollo, la configurazione della crittografia, la configurazione del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, le procedure per esporre o nascondere il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in rete e la registrazione del nome SPN. Nella maggior parte dei casi non è necessario modificare la configurazione di rete del server. Riconfigurare i protocolli di rete del server solo in presenza di requisiti speciali di rete.  
  
 La configurazione della rete per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguita tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzare l'utilità Configurazione di rete inclusa nei singoli prodotti.  
  
## Protocolli  
 Utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per abilitare o disabilitare i protocolli utilizzati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e per configurare le opzioni disponibili per i protocolli. È possibile abilitare più di un protocollo. È necessario abilitare tutti i protocolli che si desidera utilizzare con i client. Tutti i protocolli dispongono di uguale accesso al server. Per informazioni sui protocolli da usare, vedere [Abilitare o disabilitare un protocollo di rete del server](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) e [Configurazione dei protocolli di rete predefiniti di SQL Server](../../database-engine/configure-windows/default-sql-server-network-protocol-configuration.md).  
  
### Modifica di una porta  
 È possibile configurare il protocollo TCP/IP in attesa su una porta designata. Per impostazione predefinita, l'istanza predefinita del [!INCLUDE[ssDE](../../includes/ssde-md.md)] rimane in attesa sulla porta TCP 1433. Le istanze denominate del [!INCLUDE[ssDE](../../includes/ssde-md.md)] e di [!INCLUDE[ssEW](../../includes/ssew-md.md)] sono configurate per porte dinamiche. Questo significa che selezionano una porta disponibile quando viene avviato il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser facilita l'identificazione della porta alla connessione dei client.  
  
 Se configurata per le porte dinamiche, è possibile modificare la porta utilizzata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a ogni avvio. Se la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avviene tramite firewall, è necessario aprire la porta utilizzata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modo da utilizzare una porta specifica e configurare il firewall per consentire le comunicazioni con il server. Per altre informazioni, vedere [Configurare un server per l'attesa su una porta TCP specifica &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/configure a server to listen on a specific tcp port.md).  
  
### Modifica di una named pipe  
 È possibile configurare il protocollo Named Pipes per l'attesa su una named pipe designata. Per impostazione predefinita, l'istanza predefinita del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] resta in attesa sulla pipe \\\\.\pipe\sql\query per l'istanza predefinita e \\\\.\pipe\MSSQL$*\<nomeistanza>*\sql\query per un'istanza denominata. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] può restare in attesa solo su una named pipe, ma è possibile modificare il nome della pipe. Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser facilita l'identificazione della pipe alla connessione dei client. Per altre informazioni, vedere [Configurare un server per l'attesa su una pipe alternativa &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-an-alternate-pipe.md).  
  
## Forza crittografia  
 È possibile configurare il [!INCLUDE[ssDE](../../includes/ssde-md.md)] in modo da richiedere la crittografia durante le comunicazioni con le applicazioni client. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
## Protezione estesa per l'autenticazione  
 Il supporto per la protezione estesa per l'autenticazione mediante l'associazione di canale e l'associazione al servizio è disponibile per i sistemi operativi che supportano la protezione estesa. Per altre informazioni, vedere [Connettersi al motore di database mediante la protezione estesa](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md).  
  
## Autenticazione tramite Kerberos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta l'autenticazione Kerberos. Per altre informazioni, vedere [Registrare un nome dell'entità servizio per le connessioni Kerberos](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md) e [Microsoft Kerberos Configuration Manager per SQL Server](http://www.microsoft.com/download/details.aspx?id=39046).  
  
### Registrazione di un nome SPN  
 Nel servizio di autenticazione Kerberos viene utilizzato un nome SPN per autenticare un servizio. Per altre informazioni, vedere [Registrare un nome dell'entità servizio per le connessioni Kerberos](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).  
  
 È possibile utilizzare i nomi SPN anche per rendere più sicura l'autenticazione client quando si esegue la connessione con NTLM. Per altre informazioni, vedere [Connettersi al motore di database mediante la protezione estesa](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md).  
  
## Servizio SQL Server Browser  
 Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser viene eseguito sul server e consente ai computer client di individuare le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser non deve essere configurato ma solo eseguito in alcuni scenari di connessione. Per altre informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, vedere [Servizio SQL Server Browser &#40;motore di database e SSAS&#41;](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md)  
  
## Istanze nascoste di SQL Server  
 Durante l'esecuzione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser risponde alle query fornendo informazioni relative al nome, alla versione e alla connessione per ciascuna istanza installata. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]il flag **HideInstance** indica che la risposta restituita da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser non deve includere informazioni su questa istanza del server. Le applicazioni client possono comunque connettersi, purché dispongano delle informazioni necessarie per la connessione. Per altre informazioni, vedere [Nascondere un'istanza del motore di database di SQL Server](../../database-engine/configure-windows/hide-an-instance-of-sql-server-database-engine.md).  
  
## Contenuto correlato  
 [Configurazione di rete dei client](../../database-engine/configure-windows/client-network-configuration.md)  
  
 [Gestire il servizio Motore di database](../../database-engine/configure-windows/manage-the-database-engine-services.md)  
  
  