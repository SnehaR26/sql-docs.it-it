---
title: "Editor gestione connessione SQL Server Compact Edition (pagina Tutte) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sqlmobileconnection.all.f1"
helpviewer_keywords: 
  - "Editor gestione connessione SQL Server Compact Edition"
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Editor gestione connessione SQL Server Compact Edition (pagina Tutte)
  Utilizzare la finestra di dialogo **Editor gestione connessione SQL Server Compact Edition** per specificare le proprietà di connessione a un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Per ulteriori informazioni sulla gestione connessione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Edition, vedere [Editor gestione connessione SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md).  
  
## Opzioni  
 **AutoShrink Threshold**  
 Consente di specificare la quantità di spazio libero in percentuale consentito nel database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact al raggiungimento della quale verrà avviata l'operazione di compattazione automatica.  
  
 **Default Lock Escalation**  
 Consente di specificare il numero di blocchi di database acquisiti dal database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact prima di tentare l'escalation.  
  
 **Default Lock Timeout**  
 Consente di specificare l'intervallo di tempo predefinito (in millisecondi) per cui una transazione deve rimanere in attesa di un blocco.  
  
 **Flush Interval**  
 Consente di specificare l'intervallo di tempo (in secondi) dopo il quale le transazioni completate devono essere scaricate su disco.  
  
 **Locale Identifier**  
 Consente di specificare l'ID delle impostazioni locali (LCID) del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Max Buffer Size**  
 Consente di specificare la quantità massima di memoria in KB usata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact al raggiungimento della quale viene eseguito lo scaricamento dei dati su disco.  
  
 **Max Database Size**  
 Consente di specificare le dimensioni massime in MB del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Mode**  
 Consente di specificare la modalità file in cui aprire il database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. Il valore predefinito di questa proprietà è **Read Write**.  
  
 Nella tabella seguente sono descritti i quattro valori disponibili per la proprietà Mode.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Sola lettura**|Imposta l'accesso di sola lettura al database.|  
|**Read Write**|Imposta l'autorizzazione di lettura/scrittura per il database.|  
|**Exclusive**|Imposta l'accesso esclusivo al database.|  
|**Shared Read**|Specifica che altri utenti possono accedere contemporaneamente in lettura al database.|  
  
 **Persist Security Info**  
 Consente di specificare se le informazioni di sicurezza vengono restituite all'interno della stringa di connessione. Il valore predefinito dell'opzione è **False**.  
  
 **Temp File Directory**  
 Consente di specificare il percorso del file di database temporaneo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Data Source**  
 Consente di specificare il nome del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Password**  
 Consente di immettere la password per il database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor gestione connessione SQL Server Compact Edition &#40;pagina Connessione&#41;](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  