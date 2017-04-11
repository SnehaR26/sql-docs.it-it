---
title: "Gestione dei pacchetti (servizio SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti di SQL Server Integration Services, gestione"
  - "pacchetti [Integration Services], gestione"
  - "pacchetti di Integration Services, gestione"
  - "archiviazione di pacchetti"
  - "Pacchetti archiviati - cartella"
  - "pacchetti correnti"
  - "Pacchetti in esecuzione - cartella"
  - "informazioni sullo stato [Integration Services]"
  - "pacchetti SSIS, gestione"
  - "archivio [Integration Services]"
  - "monitoraggio [Integration Services], pacchetti"
  - "servizio Integration Services, gestione di pacchetti"
  - "servizi [Integration Services], gestione di pacchetti"
ms.assetid: 0261ed9e-3b01-4e37-a9d4-d039c41029b6
caps.latest.revision: 59
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 57
---
# Gestione dei pacchetti (servizio SSIS)
  La gestione dei pacchetti implica attività come le seguenti:  
  
-   Monitoraggio dei pacchetti in esecuzione  
  
-   Gestione dell'archiviazione di pacchetti  
  
-   Importazione ed esportazione di pacchetti  
  
> [!IMPORTANT]  
>  In questo argomento viene illustrato il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , un servizio Windows per la gestione dei pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] supporta il servizio per la compatibilità con le versioni precedenti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], è possibile gestire oggetti come i pacchetti del server Integration Services.  
  
## Archivio pacchetti  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include due cartelle di livello principale per l'accesso ai pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ovvero **Pacchetti in esecuzione** e **Pacchetti archiviati**. La cartella **Pacchetti in esecuzione** include i pacchetti in esecuzione nel server. La cartella **Pacchetti archiviati** include i pacchetti che vengono salvati nell'archivio pacchetti. Questi sono gli unici pacchetti gestiti dal servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. L'archivio pacchetti può includere sia il database msdb sia le cartelle del file system elencate nel file di configurazione per il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Il file di configurazione specifica le cartelle msdb e del file system da gestire. Possono inoltre essere presenti pacchetti archiviati in un'altra posizione nel file system non gestiti dal servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 I pacchetti salvati in msdb sono archiviati in una tabella denominata sysssispackages. Quando si salvano i pacchetti in msdb, è inoltre possibile raggrupparli in cartelle logiche. L'uso di cartelle logiche può essere utile per organizzare i pacchetti in base allo scopo o per filtrarli nella tabella sysssispackages. È possibile creare nuove cartelle logiche usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per impostazione predefinita, le cartelle logiche aggiunte a msdb vengono incluse automaticamente nell'archivio pacchetti.  
  
 Le cartelle logiche create per raggruppare i pacchetti in msdb sono rappresentate da righe nella tabella sysssispackagefolders di msdb. Le colonne folderid e parentfolderid di sysssispackagefolders definiscono la gerarchia delle cartelle. Le cartelle logiche radice di msdb corrispondono alle righe di sysssispackagefolders contenenti valori Null nella colonna parentfolderid. Per altre informazioni, vedere [sysssispackages &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysssispackages-transact-sql.md) e [sysssispackagefolders &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysssispackagefolders-transact-sql.md).  
  
 Quando si apre [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e ci si connette a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vengono visualizzate le cartelle di msdb gestite dal servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] elencate nella cartella Pacchetti archiviati. Se il file di configurazione specifica cartelle del file system radice, nella cartella Pacchetti archiviati sono elencati anche i pacchetti salvati nel file system in tali cartelle e in tutte le sottocartelle.  
  
 È possibile archiviare pacchetti in qualunque cartella del file system, ma non verranno elencati nelle sottocartelle della cartella **Pacchetti archiviati** a meno che non si aggiunga la cartella all'elenco di cartelle nel file di configurazione per l'archivio pacchetti. Per altre informazioni sul file di configurazione, vedere [Configurazione del servizio Integration Services &#40;SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
 La cartella **Pacchetti in esecuzione** non contiene alcuna sottocartella e non è estensibile.  
  
 Per impostazione predefinita, la cartella **Pacchetti archiviati** contiene due sottocartelle, ovvero **File System** e **MSDB**. La cartella **File System** include i pacchetti che vengono salvati nel file system. La posizione di tali file è specificata nel file di configurazione per il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. La cartella predefinita è Packages, inclusa in %Programmi%\Microsoft SQL Server\100\DTS. La cartella **MSDB** include i pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che sono stati salvati nel database msdb di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel server. La tabella sysssispackages contiene i pacchetti salvati in msdb.  
  
 Per visualizzare un elenco dei pacchetti presenti nell'archivio pacchetti, è necessario aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e connettersi a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per altre informazioni, vedere [Visualizzare pacchetti di Integration Services in SQL Server Management Studio &#40;servizio SSIS&#41;](../../integration-services/service/view-integration-services-packages-in-sql-server-management-studio-ssis-service.md).  
  
## Monitoraggio dei pacchetti in esecuzione  
 La cartella **Pacchetti in esecuzione** include i pacchetti attualmente in esecuzione. Per visualizzare informazioni sui pacchetti indicati nella pagina **Riepilogo** di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], fare clic sulla cartella **Pacchetti in esecuzione**. Nella pagina **Riepilogo** verranno visualizzate informazioni come la durata di esecuzione dei pacchetti. Per visualizzare informazioni aggiornate, aggiornare la cartella.  
  
 Per visualizzare informazioni su un singolo pacchetto indicato nella pagina **Riepilogo**, fare clic sul pacchetto. Nella pagina **Riepilogo** vengono visualizzate informazioni come la versione e la descrizione del pacchetto.  
  
 Per arrestare un pacchetto in esecuzione dalla cartella **Pacchetti in esecuzione**, fare clic con il pulsante destro del mouse sul pacchetto e quindi scegliere **Arresta**.  
  
## Gestione di archivi pacchetti  
 Per organizzare i pacchetti, è possibile aggiungere cartelle personalizzate alle cartelle degli archivi pacchetti radice elencate nel file di configurazione del servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per impostazione predefinita, le cartelle radice sono **File System** e **MSDB**. Si supponga, ad esempio, di voler aggiungere nella cartella **File System** la cartella **Pulitura dati** contenente tutti i pacchetti usati per la pulitura di dati. A tale scopo è possibile aggiungere cartelle personalizzate alle cartelle personalizzate in modo da creare una gerarchia di cartelle nidificate in base alle specifiche esigenze. È possibile eliminare e rinominare le cartelle personalizzate, ma non le cartelle radice specificate nel file di configurazione. Per aggiornare le cartelle radice di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è necessario aggiornare il file di configurazione.  
  
 Per altre informazioni, vedere [Configurazione del servizio Integration Services &#40;servizio SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
## Importazione ed esportazione di pacchetti  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] I pacchetti possono essere salvati nel database msdb o nel file system. Per copiare un pacchetto da un archivio all'altro, è necessario utilizzare la funzionalità di importazione o esportazione di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. È inoltre possibile importare un pacchetto nello stesso tipo di archivio e modificare il nome del pacchetto in modo da crearne una copia. Per importare ed esportare pacchetti, è anche possibile usare l'utilità del prompt dei comandi **dtutil** (dtutil.exe).  
  
 Per altre informazioni, vedere [dtutil Utility](../../integration-services/dtutil-utility.md).  
  
## Attività correlate  
  
-   [Importare ed esportare pacchetti &#40;servizio SSIS&#41;](../../integration-services/service/import-and-export-packages-ssis-service.md)  
  
-   [Visualizzare pacchetti di Integration Services in SQL Server Management Studio &#40;servizio SSIS&#41;](../../integration-services/service/view-integration-services-packages-in-sql-server-management-studio-ssis-service.md)  
  
## Vedere anche  
 [Servizio Integration Services &#40;servizio SSIS&#41;](../../integration-services/service/integration-services-service-ssis-service.md)  
  
  