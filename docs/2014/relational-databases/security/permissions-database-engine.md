---
title: Autorizzazioni (motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseuser.permissions.database.f1--May use common.permissions
- sql12.swb.databaseuser.permissions.object.f1--May use common.permissions
helpviewer_keywords:
- REFERENCES permission
- permissions [SQL Server]
- security [SQL Server], permissions
- naming conventions [SQL Server]
ms.assetid: f28e3dea-24e6-4a81-877b-02ec4c7e36b9
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 21119211d750b8443d0f463e5b6dd3e407bd248b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141971"
---
# <a name="permissions-database-engine"></a>Autorizzazioni (Motore di database)
  Ogni entità a protezione diretta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dispone di autorizzazioni associate che possono essere concesse a un'entità. Questo argomento contiene informazioni sui seguenti aspetti:  
  
-   [Convenzioni di denominazione delle autorizzazioni](#_conventions)  
  
-   [Autorizzazioni correlate alle entità a protezione diretta specifiche](#_securables)  
  
-   [Autorizzazioni di SQL Server](#_permissions)  
  
-   [Algoritmo di controllo dell'autorizzazione](#_algorithm)  
  
-   [Esempi](#_examples)  
  
##  <a name="_conventions"></a> Convenzioni di denominazione delle autorizzazioni  
 Di seguito vengono descritte le convenzioni generali adottate per la denominazione delle autorizzazioni:  
  
-   CONTROL  
  
     Conferisce al beneficiario capacità da proprietario. In pratica il beneficiario dispone di tutte le autorizzazioni definite sull'entità a protezione diretta. Un'entità a cui è stata conferita un'autorizzazione CONTROL può a sua volta concedere autorizzazioni sull'entità a protezione diretta. Poiché il modello di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è di tipo gerarchico, un'autorizzazione CONTROL in un particolare ambito comprende implicitamente un'autorizzazione CONTROL su tutte le entità a protezione diretta comprese in tale ambito. Un'autorizzazione CONTROL su un database, ad esempio, implica tutte le autorizzazioni sul database, su tutti gli assembly del database, su tutti gli schemi del database e sugli oggetti contenuti in tutti gli schemi del database.  
  
-   ALTER  
  
     Conferisce la capacità di modificare le proprietà, eccetto il diritto di proprietà, di una particolare entità a protezione diretta. Quando viene concessa in un ambito, l'autorizzazione ALTER concede la capacità di modificare, creare o eliminare una qualsiasi entità a protezione diretta contenuta in tale ambito. Un'autorizzazione ALTER in uno schema, ad esempio, include la capacità di creare, modificare ed eliminare oggetti contenuti nello schema.  
  
-   ALTER ANY \<*Entità a protezione diretta del server*>, dove *Entità a protezione diretta del server* può essere qualsiasi entità a protezione diretta del server.  
  
     Conferisce la capacità di creare, modificare o eliminare singole istanze dell' *Entità a protezione diretta del server*. L'autorizzazione ALTER ANY LOGIN, ad esempio, conferisce la capacità di creare, modificare o eliminare un qualsiasi account di accesso nell'istanza.  
  
-   ALTER ANY \<*Entità a protezione diretta del database*>, dove *Entità a protezione diretta del database* può essere una qualsiasi entità a protezione diretta a livello del database.  
  
     Conferisce la capacità di creare, modificare o eliminare singole istanze dell' *Entità a protezione diretta del database*. L'autorizzazione ALTER ANY SCHEMA, ad esempio, conferisce la capacità di creare, modificare o eliminare un qualsiasi schema contenuto nel database.  
  
-   TAKE OWNERSHIP  
  
     Consente al beneficiario di prendere possesso dell'entità a protezione diretta sulla quale viene concessa questa autorizzazione.  
  
-   IMPERSONATE \<*Account di accesso*>  
  
     Consente al beneficiario di rappresentare l'account di accesso.  
  
-   IMPERSONATE \<*Utente*>  
  
     Consente al beneficiario di rappresentare l'utente.  
  
-   CREATE \<*Entità a protezione diretta del server*>  
  
     Conferisce al beneficiario la capacità di creare l' *Entità a protezione diretta del server*.  
  
-   CREATE \<*Entità a protezione diretta del database*>  
  
     Conferisce al beneficiario la capacità di creare l' *Entità a protezione diretta del database*.  
  
-   CREATE \<*Entità a protezione diretta contenuta in uno schema*>  
  
     Conferisce la capacità di creare un'entità a protezione diretta contenuta in uno schema. Per creare un'entità a protezione diretta in un particolare schema, è però necessario avere un'autorizzazione ALTER sullo schema.  
  
-   VIEW DEFINITION  
  
     Consente al beneficiario di accedere a metadati.  
  
-   REFERENCES  
  
     L'autorizzazione REFERENCES su una tabella è necessaria per creare un vincolo FOREIGN KEY che faccia riferimento alla tabella stessa.  
  
     L'autorizzazione REFERENCES è necessaria su un oggetto per creare FUNCTION o VIEW con la clausola `WITH SCHEMABINDING` che faccia riferimento all'oggetto stesso.  
  
## <a name="chart-of-sql-server-permissions"></a>Grafico delle autorizzazioni di SQL Server  
 Per un'anteprima di grandi dimensioni di tutte le autorizzazioni del [!INCLUDE[ssDE](../../includes/ssde-md.md)] in formato pdf, vedere [http://go.microsoft.com/fwlink/?LinkId=229142](http://go.microsoft.com/fwlink/?LinkId=229142).  
  
##  <a name="_securables"></a> Autorizzazioni applicabili a particolari entità a protezione diretta  
 Nella tabella seguente vengono elencati le classi principali di autorizzazione e i tipi di entità a protezione diretta a cui possono essere applicati.  
  
|Autorizzazione|Applicabile a|  
|----------------|----------------|  
|SELECT|Sinonimi<br /><br /> Tabelle e colonne<br /><br /> Funzioni con valori di tabella, [!INCLUDE[tsql](../../includes/tsql-md.md)] e Common Language Runtime (CLR), e colonne<br /><br /> Viste e colonne|  
|VIEW CHANGE TRACKING|Tabelle<br /><br /> Schemi|  
|UPDATE|Sinonimi<br /><br /> Tabelle e colonne<br /><br /> Viste e colonne<br /><br /> Oggetti sequenza|  
|REFERENCES|Funzioni scalari e di aggregazione ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Code di[!INCLUDE[ssSB](../../includes/sssb-md.md)] <br /><br /> Tabelle e colonne<br /><br /> Le funzioni con valori di tabella ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR) e colonne<br /><br /> Tipi<br /><br /> Viste e colonne<br /><br /> Oggetti sequenza|  
|INSERT|Sinonimi<br /><br /> Tabelle e colonne<br /><br /> Viste e colonne|  
|Elimina|Sinonimi<br /><br /> Tabelle e colonne<br /><br /> Viste e colonne|  
|EXECUTE|Procedure ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Funzioni scalari e di aggregazione ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Sinonimi<br /><br /> Tipi CLR|  
|RECEIVE|Code di[!INCLUDE[ssSB](../../includes/sssb-md.md)] |  
|VIEW DEFINITION|Gruppi di disponibilità<br /><br /> Procedure ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Code di[!INCLUDE[ssSB](../../includes/sssb-md.md)] <br /><br /> Funzioni scalari e di aggregazione ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Account di accesso, utenti e ruoli<br /><br /> Sinonimi<br /><br /> Tabelle<br /><br /> Le funzioni con valori di tabella ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Viste<br /><br /> Oggetti sequenza|  
|ALTER|Gruppi di disponibilità<br /><br /> Procedure ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Funzioni scalari e di aggregazione ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Oggetti sequenza<br /><br /> Account di accesso, utenti e ruoli<br /><br /> Code di[!INCLUDE[ssSB](../../includes/sssb-md.md)] <br /><br /> Tabelle<br /><br /> Le funzioni con valori di tabella ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Viste|  
|TAKE OWNERSHIP|Gruppi di disponibilità<br /><br /> Ruoli<br /><br /> Procedure ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Funzioni scalari e di aggregazione ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Ruoli del server<br /><br /> Sinonimi<br /><br /> Tabelle<br /><br /> Le funzioni con valori di tabella ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Viste<br /><br /> Oggetti sequenza|  
|CONTROL|Gruppi di disponibilità<br /><br /> Procedure ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Funzioni scalari e di aggregazione ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Account di accesso, utenti e ruoli<br /><br /> Code di[!INCLUDE[ssSB](../../includes/sssb-md.md)] <br /><br /> Sinonimi<br /><br /> Tabelle<br /><br /> Le funzioni con valori di tabella ([!INCLUDE[tsql](../../includes/tsql-md.md)] e CLR)<br /><br /> Viste<br /><br /> Oggetti sequenza|  
|IMPERSONATE|Account di accesso e utenti|  
  
> [!CAUTION]  
>  Le autorizzazioni predefinite concesso a oggetti di sistema durante l'installazione vengono valutati attentamente per individuare possibili minacce e non è quindi necessario modificarli per implementare misure di protezione avanzata dell'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Eventuali modifiche alle autorizzazioni per gli oggetti di sistema possono limitare o compromettere la funzionalità e potrebbero lasciare l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uno stato non supportato.  
  
##  <a name="_permissions"></a> SQL Server e le autorizzazioni di Database SQL  
 La tabella seguente contiene un elenco completo delle autorizzazioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le autorizzazioni del[!INCLUDE[ssSDS](../../includes/sssds-md.md)] sono disponibili solo per entità a protezione diretta supportate. Non è possibile concedere autorizzazioni a livello di server in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], tuttavia in alcuni casi sono disponibili invece autorizzazioni di database.  
  
|Entità a protezione diretta di base|Autorizzazioni di granularità sull'entità a protezione diretta di base|Codice tipo di autorizzazione|Entità a protezione diretta contenente l'entità a protezione diretta di base|Autorizzazione sull'entità a protezione diretta contenente che implica un'autorizzazione di granularità sull'entità a protezione diretta di base|  
|--------------------|--------------------------------------------|--------------------------|--------------------------------------------|------------------------------------------------------------------------------------------|  
|APPLICATION ROLE|ALTER|AL|DATABASE|ALTER ANY APPLICATION ROLE|  
|APPLICATION ROLE|CONTROL|CL|DATABASE|CONTROL|  
|APPLICATION ROLE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ASSEMBLY|ALTER|AL|DATABASE|ALTER ANY ASSEMBLY|  
|ASSEMBLY|CONTROL|CL|DATABASE|CONTROL|  
|ASSEMBLY|REFERENCES|RF|DATABASE|REFERENCES|  
|ASSEMBLY|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|ASSEMBLY|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ASYMMETRIC KEY|ALTER|AL|DATABASE|ALTER ANY ASYMMETRIC KEY|  
|ASYMMETRIC KEY|CONTROL|CL|DATABASE|CONTROL|  
|ASYMMETRIC KEY|REFERENCES|RF|DATABASE|REFERENCES|  
|ASYMMETRIC KEY|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|ASYMMETRIC KEY|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|AVAILABILITY GROUP|ALTER|AL|SERVER|ALTER ANY AVAILABILITY GROUP|  
|AVAILABILITY GROUP|CONTROL|CL|SERVER|CONTROL SERVER|  
|AVAILABILITY GROUP|TAKE OWNERSHIP|TO|SERVER|CONTROL SERVER|  
|AVAILABILITY GROUP|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|CERTIFICATE|ALTER|AL|DATABASE|ALTER ANY CERTIFICATE|  
|CERTIFICATE|CONTROL|CL|DATABASE|CONTROL|  
|CERTIFICATE|REFERENCES|RF|DATABASE|REFERENCES|  
|CERTIFICATE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|CERTIFICATE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|CONTRACT|ALTER|AL|DATABASE|ALTER ANY CONTRACT|  
|CONTRACT|CONTROL|CL|DATABASE|CONTROL|  
|CONTRACT|REFERENCES|RF|DATABASE|REFERENCES|  
|CONTRACT|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|CONTRACT|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|DATABASE|ALTER|AL|SERVER|ALTER ANY DATABASE|  
|DATABASE|ALTER ANY APPLICATION ROLE|ALAR|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ASSEMBLY|ALAS|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ASYMMETRIC KEY|ALAK|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY CERTIFICATE|ALCF|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY CONTRACT|ALSC|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY DATABASE AUDIT|ALDA|SERVER|ALTER ANY SERVER AUDIT|  
|DATABASE|ALTER ANY DATABASE DDL TRIGGER|ALTG|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY DATABASE EVENT NOTIFICATION|ALED|SERVER|ALTER ANY EVENT NOTIFICATION|  
|DATABASE|ALTER ANY DATABASE EVENT SESSION|AADS<br /><br /> Nota: Si applica solo ai [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|SERVER|ALTER ANY EVENT SESSION|  
|DATABASE|ALTER ANY DATASPACE|ALDS|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY FULLTEXT CATALOG|ALFT|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY MESSAGE TYPE|ALMT|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY REMOTE SERVICE BINDING|ALSB|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ROLE|ALRL|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ROUTE|ALRT|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SCHEMA|ALSM|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SECURITY POLICY|ALSP<br /><br /> Nota: Si applica solo ai [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SERVICE|ALSV|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SYMMETRIC KEY|ALSK|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY USER|ALUS|SERVER|CONTROL SERVER|  
|DATABASE|AUTHENTICATE|AUTH|SERVER|AUTHENTICATE SERVER|  
|DATABASE|BACKUP DATABASE|BADB|SERVER|CONTROL SERVER|  
|DATABASE|BACKUP LOG|BALO|SERVER|CONTROL SERVER|  
|DATABASE|CHECKPOINT|CP|SERVER|CONTROL SERVER|  
|DATABASE|CONNECT|CO|SERVER|CONTROL SERVER|  
|DATABASE|CONNECT REPLICATION|CORP|SERVER|CONTROL SERVER|  
|DATABASE|CONTROL|CL|SERVER|CONTROL SERVER|  
|DATABASE|CREATE AGGREGATE|CRAG|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ASSEMBLY|CRAS|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ASYMMETRIC KEY|CRAK|SERVER|CONTROL SERVER|  
|DATABASE|CREATE CERTIFICATE|CRCF|SERVER|CONTROL SERVER|  
|DATABASE|CREATE CONTRACT|CRSC|SERVER|CONTROL SERVER|  
|DATABASE|CREATE DATABASE|CRDB|SERVER|CREATE ANY DATABASE|  
|DATABASE|CREATE DATABASE DDL EVENT NOTIFICATION|CRED|SERVER|CREATE DDL EVENT NOTIFICATION|  
|DATABASE|CREATE DEFAULT|CRDF|SERVER|CONTROL SERVER|  
|DATABASE|CREATE FULLTEXT CATALOG|CRFT|SERVER|CONTROL SERVER|  
|DATABASE|CREATE FUNCTION|CRFN|SERVER|CONTROL SERVER|  
|DATABASE|CREATE MESSAGE TYPE|CRMT|SERVER|CONTROL SERVER|  
|DATABASE|CREATE PROCEDURE|CRPR|SERVER|CONTROL SERVER|  
|DATABASE|CREATE QUEUE|CRQU|SERVER|CONTROL SERVER|  
|DATABASE|CREATE REMOTE SERVICE BINDING|CRSB|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ROLE|CRRL|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ROUTE|CRRT|SERVER|CONTROL SERVER|  
|DATABASE|CREATE RULE|CRRU|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SCHEMA|CRSM|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SERVICE|CRSV|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SYMMETRIC KEY|CRSK|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SYNONYM|CRSN|SERVER|CONTROL SERVER|  
|DATABASE|CREATE TABLE|CRTB|SERVER|CONTROL SERVER|  
|DATABASE|CREATE TYPE|CRTY|SERVER|CONTROL SERVER|  
|DATABASE|CREATE VIEW|CRVW|SERVER|CONTROL SERVER|  
|DATABASE|CREATE XML SCHEMA COLLECTION|CRXS|SERVER|CONTROL SERVER|  
|DATABASE|Elimina|DL|SERVER|CONTROL SERVER|  
|DATABASE|EXECUTE|EX|SERVER|CONTROL SERVER|  
|DATABASE|INSERT|IN|SERVER|CONTROL SERVER|  
|DATABASE|KILL DATABASE CONNECTION|KIDC<br /><br /> Nota: Si applica solo ai [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Usare ALTER ANY CONNECTION in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|SERVER|ALTER ANY CONNECTION|  
|DATABASE|REFERENCES|RF|SERVER|CONTROL SERVER|  
|DATABASE|SELECT|SL|SERVER|CONTROL SERVER|  
|DATABASE|SHOWPLAN|SPLN|SERVER|ALTER TRACE|  
|DATABASE|SUBSCRIBE QUERY NOTIFICATIONS|SUQN|SERVER|CONTROL SERVER|  
|DATABASE|TAKE OWNERSHIP|TO|SERVER|CONTROL SERVER|  
|DATABASE|UPDATE|UP|SERVER|CONTROL SERVER|  
|DATABASE|VIEW DATABASE STATE|VWDS|SERVER|VIEW SERVER STATE|  
|DATABASE|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|ENDPOINT|ALTER|AL|SERVER|ALTER ANY ENDPOINT|  
|ENDPOINT|CONNECT|CO|SERVER|CONTROL SERVER|  
|ENDPOINT|CONTROL|CL|SERVER|CONTROL SERVER|  
|ENDPOINT|TAKE OWNERSHIP|TO|SERVER|CONTROL SERVER|  
|ENDPOINT|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|FULLTEXT CATALOG|ALTER|AL|DATABASE|ALTER ANY FULLTEXT CATALOG|  
|FULLTEXT CATALOG|CONTROL|CL|DATABASE|CONTROL|  
|FULLTEXT CATALOG|REFERENCES|RF|DATABASE|REFERENCES|  
|FULLTEXT CATALOG|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|FULLTEXT CATALOG|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|FULLTEXT STOPLIST|ALTER|AL|DATABASE|ALTER ANY FULLTEXT CATALOG|  
|FULLTEXT STOPLIST|CONTROL|CL|DATABASE|CONTROL|  
|FULLTEXT STOPLIST|REFERENCES|RF|DATABASE|REFERENCES|  
|FULLTEXT STOPLIST|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|FULLTEXT STOPLIST|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|Account di accesso|ALTER|AL|SERVER|ALTER ANY LOGIN|  
|Account di accesso|CONTROL|CL|SERVER|CONTROL SERVER|  
|Account di accesso|IMPERSONATE|IM|SERVER|CONTROL SERVER|  
|Account di accesso|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|MESSAGE TYPE|ALTER|AL|DATABASE|ALTER ANY MESSAGE TYPE|  
|MESSAGE TYPE|CONTROL|CL|DATABASE|CONTROL|  
|MESSAGE TYPE|REFERENCES|RF|DATABASE|REFERENCES|  
|MESSAGE TYPE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|MESSAGE TYPE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|OBJECT|ALTER|AL|SCHEMA|ALTER|  
|OBJECT|CONTROL|CL|SCHEMA|CONTROL|  
|OBJECT|DELETE|DL|SCHEMA|Elimina|  
|OBJECT|EXECUTE|EX|SCHEMA|EXECUTE|  
|OBJECT|INSERT|IN|SCHEMA|INSERT|  
|OBJECT|RECEIVE|RC|SCHEMA|CONTROL|  
|OBJECT|REFERENCES|RF|SCHEMA|REFERENCES|  
|OBJECT|SELECT|SL|SCHEMA|SELECT|  
|OBJECT|TAKE OWNERSHIP|TO|SCHEMA|CONTROL|  
|OBJECT|UPDATE|UP|SCHEMA|UPDATE|  
|OBJECT|VIEW CHANGE TRACKING|VWCT|SCHEMA|VIEW CHANGE TRACKING|  
|OBJECT|VIEW DEFINITION|VW|SCHEMA|VIEW DEFINITION|  
|REMOTE SERVICE BINDING|ALTER|AL|DATABASE|ALTER ANY REMOTE SERVICE BINDING|  
|REMOTE SERVICE BINDING|CONTROL|CL|DATABASE|CONTROL|  
|REMOTE SERVICE BINDING|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|REMOTE SERVICE BINDING|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ROLE|ALTER|AL|DATABASE|ALTER ANY ROLE|  
|ROLE|CONTROL|CL|DATABASE|CONTROL|  
|ROLE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|ROLE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ROUTE|ALTER|AL|DATABASE|ALTER ANY ROUTE|  
|ROUTE|CONTROL|CL|DATABASE|CONTROL|  
|ROUTE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|ROUTE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|SEARCH PROPERTY LIST|ALTER|AL|SERVER|ALTER ANY FULLTEXT CATALOG|  
|SEARCH PROPERTY LIST|CONTROL|CL|SERVER|CONTROL|  
|SEARCH PROPERTY LIST|REFERENCES|RF|SERVER|REFERENCES|  
|SEARCH PROPERTY LIST|TAKE OWNERSHIP|TO|SERVER|CONTROL|  
|SEARCH PROPERTY LIST|VIEW DEFINITION|VW|SERVER|VIEW DEFINITION|  
|SCHEMA|ALTER|AL|DATABASE|ALTER ANY SCHEMA|  
|SCHEMA|CONTROL|CL|DATABASE|CONTROL|  
|SCHEMA|CREATE SEQUENCE|CRSO|DATABASE|CONTROL|  
|SCHEMA|Elimina|DL|DATABASE|Elimina|  
|SCHEMA|EXECUTE|EX|DATABASE|EXECUTE|  
|SCHEMA|INSERT|IN|DATABASE|INSERT|  
|SCHEMA|REFERENCES|RF|DATABASE|REFERENCES|  
|SCHEMA|SELECT|SL|DATABASE|SELECT|  
|SCHEMA|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|SCHEMA|UPDATE|UP|DATABASE|UPDATE|  
|SCHEMA|VIEW CHANGE TRACKING|VWCT|DATABASE|VIEW CHANGE TRACKING|  
|SCHEMA|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|SERVER|ADMINISTER BULK OPERATIONS|ADBO|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY CONNECTION|ALCO|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY CREDENTIAL|ALCD|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY DATABASE|ALDB|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY ENDPOINT|ALHE|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY EVENT NOTIFICATION|ALES|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY EVENT SESSION|AAES|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY LINKED SERVER|ALLS|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY LOGIN|ALLG|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY SERVER AUDIT|ALAA|Non applicabile|Non applicabile|  
|SERVER|ALTER ANY SERVER ROLE|ALSR|Non applicabile|Non applicabile|  
|SERVER|ALTER AVAILABILITY GROUP|ALAG|Non applicabile|Non applicabile|  
|SERVER|ALTER RESOURCES|ALRS|Non applicabile|Non applicabile|  
|SERVER|ALTER SERVER STATE|ALSS|Non applicabile|Non applicabile|  
|SERVER|ALTER SETTINGS|ALST|Non applicabile|Non applicabile|  
|SERVER|ALTER TRACE|ALTR|Non applicabile|Non applicabile|  
|SERVER|AUTHENTICATE SERVER|AUTH|Non applicabile|Non applicabile|  
|SERVER|CONNECT ANY DATABASE|CADB|Non applicabile|Non applicabile|  
|SERVER|CONNECT SQL|COSQ|Non applicabile|Non applicabile|  
|SERVER|CONTROL SERVER|CL|Non applicabile|Non applicabile|  
|SERVER|CREATE ANY DATABASE|CRDB|Non applicabile|Non applicabile|  
|SERVER|CREATE AVAILABILTITY GROUP|CRAC|Non applicabile|Non applicabile|  
|SERVER|CREATE DDL EVENT NOTIFICATION|CRDE|Non applicabile|Non applicabile|  
|SERVER|CREATE ENDPOINT|CRHE|Non applicabile|Non applicabile|  
|SERVER|CREATE SERVER ROLE|CRSR|Non applicabile|Non applicabile|  
|SERVER|CREATE TRACE EVENT NOTIFICATION|CRTE|Non applicabile|Non applicabile|  
|SERVER|EXTERNAL ACCESS ASSEMBLY|XA|Non applicabile|Non applicabile|  
|SERVER|IMPERSONATE ANY LOGIN|IAL|Non applicabile|Non applicabile|  
|SERVER|SELECT ALL USER SECURABLES|SUS|Non applicabile|Non applicabile|  
|SERVER|SHUTDOWN|SHDN|Non applicabile|Non applicabile|  
|SERVER|UNSAFE ASSEMBLY|XU|Non applicabile|Non applicabile|  
|SERVER|VIEW ANY DATABASE|VWDB|Non applicabile|Non applicabile|  
|SERVER|VIEW ANY DEFINITION|VWAD|Non applicabile|Non applicabile|  
|SERVER|VIEW SERVER STATE|VWSS|Non applicabile|Non applicabile|  
|SERVER ROLE|ALTER|AL|SERVER|ALTER ANY SERVER ROLE|  
|SERVER ROLE|CONTROL|CL|SERVER|CONTROL SERVER|  
|SERVER ROLE|TAKE OWNERSHIP|TO|SERVER|CONTROL SERVER|  
|SERVER ROLE|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|SERVICE|ALTER|AL|DATABASE|ALTER ANY SERVICE|  
|SERVICE|CONTROL|CL|DATABASE|CONTROL|  
|SERVICE|SEND|SN|DATABASE|CONTROL|  
|SERVICE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|SERVICE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|SYMMETRIC KEY|ALTER|AL|DATABASE|ALTER ANY SYMMETRIC KEY|  
|SYMMETRIC KEY|CONTROL|CL|DATABASE|CONTROL|  
|SYMMETRIC KEY|REFERENCES|RF|DATABASE|REFERENCES|  
|SYMMETRIC KEY|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|SYMMETRIC KEY|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|TYPE|CONTROL|CL|SCHEMA|CONTROL|  
|TYPE|EXECUTE|EX|SCHEMA|EXECUTE|  
|TYPE|REFERENCES|RF|SCHEMA|REFERENCES|  
|TYPE|TAKE OWNERSHIP|TO|SCHEMA|CONTROL|  
|TYPE|VIEW DEFINITION|VW|SCHEMA|VIEW DEFINITION|  
|Utente|ALTER|AL|DATABASE|ALTER ANY USER|  
|Utente|CONTROL|CL|DATABASE|CONTROL|  
|Utente|IMPERSONATE|IM|DATABASE|CONTROL|  
|Utente|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|XML SCHEMA COLLECTION|ALTER|AL|SCHEMA|ALTER|  
|XML SCHEMA COLLECTION|CONTROL|CL|SCHEMA|CONTROL|  
|XML SCHEMA COLLECTION|EXECUTE|EX|SCHEMA|EXECUTE|  
|XML SCHEMA COLLECTION|REFERENCES|RF|SCHEMA|REFERENCES|  
|XML SCHEMA COLLECTION|TAKE OWNERSHIP|TO|SCHEMA|CONTROL|  
|XML SCHEMA COLLECTION|VIEW DEFINITION|VW|SCHEMA|VIEW DEFINITION|  
  
##  <a name="_algorithm"></a> Riepilogo delle informazioni sull'algoritmo di controllo delle autorizzazioni  
 Il controllo delle autorizzazioni può essere complesso. L'algoritmo di controllo delle autorizzazioni include le appartenenze a gruppi sovrapposti e il concatenamento di proprietà, nonché autorizzazioni esplicite e implicite. È inoltre possibile che le autorizzazioni per le classi di entità a protezione diretta contenenti l'entità a protezione diretta abbiano impatto su tale algoritmo. Il processo generale dell'algoritmo consiste nel raccogliere tutte le autorizzazioni rilevanti. Se non viene individuato alcun blocco DENY, l'algoritmo cerca un'istruzione GRANT che fornisce accesso sufficiente. L'algoritmo contiene tre elementi fondamentali, ovvero il **contesto di sicurezza**, lo **spazio di autorizzazione**e l' **autorizzazione necessaria**.  
  
> [!NOTE]  
>  Non è possibile concedere, negare o revocare autorizzazioni a sa, dbo, proprietari di entità, information_schema, sys o all'utente corrente.  
  
-   **Contesto di sicurezza**  
  
     Gruppo di entità che fornisce le autorizzazioni per il controllo dell'accesso. Tali autorizzazioni sono correlate all'utente o all'account di accesso corrente, a meno che l'utente o l'account di accesso del contesto di sicurezza non sia stato modificato tramite l'istruzione EXECUTE AS. Il contesto di sicurezza include le seguenti entità:  
  
    -   Account di accesso  
  
    -   Utente  
  
    -   Appartenenze a ruoli  
  
    -   Appartenenze a gruppi di Windows  
  
    -   Se si usano la firma del modulo, qualsiasi account utente o di accesso tiene conto del certificato usato per firmare il modulo attualmente eseguito dall'utente e delle appartenenze a ruoli associate di tale entità.  
  
-   **Spazio di autorizzazione**  
  
     L'entità a protezione diretta e qualsiasi classe di entità a protezione diretta in cui è contenuta. Ad esempio, una tabella (entità a protezione diretta) è contenuta nella classe di entità a protezione diretta dello schema e nella classe di entità a protezione diretta del database. Sull'accesso possono influire le autorizzazioni a livello di tabella, schema, database e server. Per altre informazioni, vedere [Gerarchia delle autorizzazioni &#40;motore di database&#41;](permissions-hierarchy-database-engine.md).  
  
-   **Autorizzazione necessaria**  
  
     Il tipo di autorizzazione richiesto. Ad esempio, INSERT, UPDATE, DELETE SELECT, EXECUTE ALTER, CONTROL e così via.  
  
     L'accesso può richiedere più autorizzazioni, come negli esempi seguenti:  
  
    -   Una stored procedure può richiedere sia l'autorizzazione EXECUTE per la stored procedure, sia l'autorizzazione INSERT per varie tabelle a cui la stored procedure fa riferimento.  
  
    -   Una vista a gestione dinamica può richiedere entrambe le autorizzazioni VIEW SERVER STATE e SELECT per la vista.  
  
### <a name="general-steps-of-the-algorithm"></a>Passaggi generali dell'algoritmo  
 I passaggi precisi usati dall'algoritmo per determinare se consentire l'accesso a un'entità a protezione diretta possono variare in base alle entità e alle entità a protezione diretta coinvolte. L'algoritmo, tuttavia, effettua i passaggi generali indicati di seguito:  
  
1.  Ignora il controllo delle autorizzazioni se l'account di accesso è un membro del ruolo predefinito del server sysadmin o se l'utente è l'utente dbo nel database corrente.  
  
2.  Consente l'accesso se il concatenamento della proprietà è applicabile e il controllo dell'accesso sul primo oggetto nella catena ha superato il controllo della sicurezza.  
  
3.  Aggrega le identità del modulo firmato a livello di database e a livello di server associate al chiamante per creare il **contesto di scurezza**.  
  
4.  Per il **contesto di sicurezza**raccoglie tutte le autorizzazioni concesse o negate per lo **spazio di autorizzazione**. È possibile dichiarare l'autorizzazione in modo esplicito come GRANT, GRANT WITH GRANT o DENY oppure usare autorizzazioni GRANT o DENY implicite o effettive. L'autorizzazione CONTROL per uno schema implica ad esempio l'autorizzazione CONTROL per una tabella, così come l'autorizzazione CONTROL per una tabella implica l'autorizzazione SELECT. Se è stata pertanto concessa l'autorizzazione CONTROL per lo schema, viene concessa anche l'autorizzazione SELECT per la tabella. Se l'autorizzazione CONTROL è stata negata per la tabella, viene negata anche l'autorizzazione SELECT per la tabella.  
  
    > [!NOTE]  
    >  Un'autorizzazione GRANT a livello di colonna esegue l'override di un'autorizzazione DENY a livello di oggetto.  
  
5.  Identifica l' **autorizzazione necessaria**.  
  
6.  Restituisce un esito negativo per il controllo delle autorizzazioni se l' **autorizzazione necessaria** è negata in modo diretto o implicito per un'identità nel **contesto di sicurezza** degli oggetti nello **spazio di autorizzazione**.  
  
7.  Restituisce un esito positivo per il controllo delle autorizzazioni se l' **autorizzazione necessaria** non è stata negata e se l' **autorizzazione necessaria** contiene un'autorizzazione GRANT o GRANT WITH GRANT concessa in modo diretto o implicito per un'identità nel **contesto di sicurezza** di un oggetto nello **spazio di autorizzazione**.  
  
##  <a name="_examples"></a> Esempi  
 Negli esempi inclusi in questa sezione viene illustrato come recuperare le informazioni sulle autorizzazioni.  
  
### <a name="a-returning-the-complete-list-of-grantable-permissions"></a>A. A. Restituzione dell'elenco completo delle autorizzazioni che è possibile concedere  
 L'istruzione seguente restituisce tutte le autorizzazioni del [!INCLUDE[ssDE](../../includes/ssde-md.md)] tramite la funzione `fn_builtin_permissions` . Per altre informazioni, vedere [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql).  
  
```  
SELECT * FROM fn_builtin_permissions(default);  
GO  
```  
  
### <a name="b-returning-the-permissions-on-a-particular-class-of-objects"></a>B. B. Restituzione delle autorizzazioni per una classe di oggetti specifica  
 Nell'esempio seguente viene usata la funzione `fn_builtin_permissions` per visualizzare tutte le autorizzazioni disponibili per una categoria di entità a protezione diretta. Nell'esempio vengono restituite le autorizzazioni per gli assembly.  
  
```  
SELECT * FROM fn_builtin_permissions('assembly');  
GO    
```  
  
### <a name="c-returning-the-permissions-granted-to-the-executing-principal-on-an-object"></a>C. C. Restituzione delle autorizzazioni concesse all'entità di esecuzione per un oggetto  
 Nell'esempio seguente viene usata la funzione `fn_my_permissions` per restituire un elenco delle autorizzazioni valide assegnate all'entità chiamante per un'entità a protezione diretta specificata. Nell'esempio vengono restituite le autorizzazioni per un oggetto denominato `Orders55`. Per altre informazioni, vedere [sys.fn_my_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-my-permissions-transact-sql).  
  
```  
SELECT * FROM fn_my_permissions('Orders55', 'object');  
GO  
```  
  
### <a name="d-returning-the-permissions-applicable-to-a-specified-object"></a>D. D. Restituzione delle autorizzazioni applicabili a un oggetto specificato  
 Nell'esempio seguente vengono restituite le autorizzazioni applicabili a un oggetto denominato `Yttrium`. Si noti che la funzione predefinita `OBJECT_ID` viene usata per recuperare l'ID dell'oggetto `Yttrium`.  
  
```  
SELECT * FROM sys.database_permissions   
    WHERE major_id = OBJECT_ID('Yttrium');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia delle autorizzazioni &#40;Motore di database&#41;](permissions-hierarchy-database-engine.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)  
  
  
