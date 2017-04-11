---
title: "Procedure consigliate per la sicurezza in database indipendenti | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "database indipendente, minacce"
ms.assetid: 026ca5fc-95da-46b6-b882-fa20f765b51d
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Procedure consigliate per la sicurezza in database indipendenti
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  I database indipendenti sono soggetti ad alcune minacce univoche che devono essere comprese e contrastate dagli amministratori di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. La maggior parte delle minacce è correlata al processo di autenticazione **USER WITH PASSWORD**, che sposta il limite di autenticazione dal livello [!INCLUDE[ssDE](../../includes/ssde-md.md)] al livello di database.  
  
## Minacce correlate agli utenti  
 Gli utenti di un database indipendente che hanno l'autorizzazione **ALTER ANY USER**, ad esempio i membri dei ruoli predefiniti del database **db_owner** e **db_securityadmin**, possono concedere l'accesso al database senza che l'amministratore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sia a conoscenza o abbia concesso l'autorizzazione. Quando si concede agli utenti l'accesso a un database indipendente, si aumenta la potenziale superficie di attacco all'intera istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È necessario che gli amministratori comprendano le implicazioni di questa delega del controllo di accesso e concedano con cautela l'autorizzazione **ALTER ANY USER** agli utenti del database indipendente. Tutti i proprietari del database hanno l'autorizzazione **ALTER ANY USER**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli amministratori devono sottoporre a un controllo periodico gli utenti di un database indipendente.  
  
### Accesso ad altri database con l'account Guest  
 Proprietari e utenti di database con l'autorizzazione **ALTER ANY USER** possono creare utenti del database indipendente. Dopo la connessione a un database indipendente in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un utente di questo database può accedere ad altri database del [!INCLUDE[ssDE](../../includes/ssde-md.md)], se in questi database è abilitato l'account **Guest**.  
  
### Creazione di un utente duplicato in un altro database  
 In alcune applicazioni potrebbe essere richiesto che un utente possa accedere a più database. Questo requisito può essere soddisfatto creando utenti identici del database indipendente in ogni database. Quando si crea il secondo utente con la password, utilizzare l'opzione SID. Nell'esempio seguente vengono creati due utenti identici in due database.  
  
```  
USE DB1;  
GO  
CREATE USER Carlo WITH PASSWORD = '<strong password>';   
-- Return the SID of the user  
SELECT SID FROM sys.database_principals WHERE name = 'Carlo';  
  
-- Change to the second database  
USE DB2;  
GO  
CREATE USER Carlo WITH PASSWORD = '<same password>', SID = <SID from DB1>;  
GO  
```  
  
 Per eseguire una query tra database, è necessario impostare l'opzione **TRUSTWORTHY** sul database chiamante. Se, ad esempio, l'utente (Carlo) definito in precedenza si trova in DB1, per eseguire `SELECT * FROM db2.dbo.Table1;` l'impostazione **TRUSTWORTHY** deve essere attiva per il database DB1. Eseguire il codice seguente per attivare l'impostazione **TRUSTWORTHY**.  
  
```  
ALTER DATABASE DB1 SET TRUSTWORTHY ON;  
```  
  
### Creazione di un utente che duplica un account di accesso  
 Se si crea un utente di database indipendente con password usando lo stesso nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e se l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si connette specificando il database indipendente come catalogo iniziale, non sarà possibile stabilire la connessione con l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La connessione sarà valutata come l'entità utente di database indipendente con password nel database indipendente anziché come utente basato sull'accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questo approccio potrebbe causare un attacco Denial of Service intenzionale o accidentale per l'accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Come procedura consigliata, è opportuno che i membri del ruolo predefinito del server **sysadmin** considerino la possibilità di connettersi sempre senza usare l'opzione relativa al catalogo iniziale. In questo modo l'account di accesso viene connesso al database master, evitando qualsiasi tentativo da parte del proprietario di un database di utilizzare l'accesso in modo improprio. L'amministratore potrà quindi passare al database indipendente con l'istruzione **USE***\<database>*. È anche possibile impostare il database indipendente come database predefinito dell'account di accesso, in modo da consentire il completamento dell'accesso al database **master** e il successivo trasferimento dell'account di accesso al database indipendente.  
  
-   Come procedura consigliata, evitare di creare utenti del database indipendente con password con lo stesso nome degli accessi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Se l'account di accesso duplicato è disponibile, connettersi al database **master** senza specificare un catalogo iniziale, quindi eseguire il comando **USE** per passare al database indipendente.  
  
-   Quando sono presenti database indipendenti, gli utenti di database non indipendenti devono connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)] senza utilizzare un catalogo iniziale oppure specificando il nome di un database non indipendente come catalogo iniziale. In questo modo si eviterà di stabilire la connessione al database indipendente, che è meno soggetto al controllo diretto degli amministratori di [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
### Aumento del livello di accesso mediante la modifica dello stato di indipendenza di un database  
 Gli account di accesso che dispongono dell'autorizzazione **ALTER ANY DATABASE**, ad esempio i membri del ruolo predefinito del server **dbcreator**, e gli utenti di un database non indipendente che dispongono dell'autorizzazione **CONTROL DATABASE**, ad esempio i membri del ruolo predefinito del database **db_owner**, possono modificare l'impostazione di indipendenza di un database. Se tale impostazione viene modificata da **NONE** a **PARTIAL** o a **FULL**, l'accesso utente può essere concesso creando utenti del database indipendente con password. In questo modo potrebbe essere consentito l'accesso senza che gli amministratori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne siano a conoscenza o abbiano concesso l'autorizzazione. Per evitare che un database sia indipendente, impostare l'opzione **contained database authentication** del [!INCLUDE[ssDE](../../includes/ssde-md.md)] su 0. Per impedire connessioni da parte degli utenti del database indipendente con password a determinati database indipendenti, utilizzare trigger di accesso per annullare i tentativi di accesso da parte di tali utenti.  
  
### Collegamento di un database indipendente  
 Mediante il collegamento di un database indipendente, un amministratore potrebbe concedere a utenti indesiderati l'accesso all'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Un amministratore che voglia evitare questo rischio può portare il database online in modalità **RESTRICTED_USER**, in modo da impedire l'autenticazione per gli utenti del database indipendente con password. Solo le entità autorizzate tramite account di accesso potranno accedere a [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Gli utenti vengono creati utilizzando i requisiti per le password validi al momento della creazione e le password non vengono verificate di nuovo quando si collega il database. Collegando un database indipendente che supporta password vulnerabili a un sistema con criteri password più severi, un amministratore potrebbe consentire l'utilizzo di password che non soddisfano i criteri password correnti nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] collegato. Gli amministratori possono evitare di mantenere le password vulnerabili richiedendo la reimpostazione di tutte le password per il database collegato.  
  
### Criteri password  
 Le password in un database possono essere obbligatoriamente di tipo complesso, ma non possono essere protette da criteri password attendibili. Utilizzare, quando possibile, l'autenticazione di Windows per sfruttare i criteri password più estesi disponibili in Windows.  
  
### Autenticazione Kerberos  
 Gli utenti del database indipendente con password non possono utilizzare l'autenticazione Kerberos. Quando possibile, utilizzare l'autenticazione di Windows per sfruttare le funzionalità di Windows, ad esempio Kerberos.  
  
### Attacco con dizionario offline  
 Gli hash delle password per gli utenti del database indipendente con password vengono archiviati nel database indipendente. Chiunque disponga dell'accesso ai file di database potrebbe effettuare un attacco con dizionario nei confronti degli utenti del database indipendente con password in un sistema non controllato. Per contrastare questa minaccia, limitare l'accesso ai file di database o consentire connessioni ai database indipendenti solo utilizzando l'autenticazione di Windows.  
  
## Escape di un database indipendente  
 Se un database è parzialmente indipendente, gli amministratori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dovranno controllare periodicamente le funzionalità di utenti e moduli nei database indipendenti.  
  
## Denial of Service tramite AUTO_CLOSE  
 Evitare di configurare la chiusura automatica di database indipendenti. Se viene chiuso, l'apertura del database per autenticare un utente utilizza risorse aggiuntive e potrebbe contribuire a un attacco Denial of Service.  
  
## Vedere anche  
 [Database indipendenti](../../relational-databases/databases/contained-databases.md)   
 [Migrazione in un database parzialmente indipendente](../../relational-databases/databases/migrate-to-a-partially-contained-database.md)  
  
  