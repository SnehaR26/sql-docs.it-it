---
title: "Importazione ed esportazione delle informazioni | Microsoft Docs"
ms.custom: ""
ms.date: "07/31/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# Importazione ed esportazione delle informazioni
  È possibile creare le Knowledge Base e i domini direttamente nell'applicazione [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] oppure è possibile importare le informazioni in una Knowledge Base o esportarle da essa. Nell'applicazione [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] è possibile utilizzare un file di dati per le operazioni di importazione ed esportazione o un file di Excel per le operazioni di importazione. Il file di dati utilizzato è un file crittografato creato da [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) con un'estensione DQS. I file creati da Microsoft Excel potranno presentare l'estensione xlsx, xls o csv. Queste operazioni offrono una maggiore flessibilità nella compilazione e nella condivisione delle informazioni utilizzate per eseguire la pulizia dei dati e la corrispondenza.  
  
> [!IMPORTANT]  
>  È possibile esportare *tutti* le knowledge base di [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] a un file di backup DQS (con estensione dqsb) alla volta eseguendo il file DQSInstaller.exe dal prompt dei comandi. Analogamente, è possibile importare *tutti* le knowledge base in DQS una backup di file (con estensione dqsb) per il [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] contemporaneamente eseguendo il file DQSInstaller.exe dal prompt dei comandi. Per informazioni su questa operazione, vedere [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) nella Guida all'installazione di DQS.  
  
## Argomenti della sezione  
 È possibile eseguire le operazioni di importazione ed esportazione seguenti:  
  
|||  
|-|-|  
|Esportare un dominio di una Knowledge Base in un file di dati DQS|[Export a Domain to a .dqs File](../data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|Importare un dominio da un file di dati DQS in una Knowledge Base esistente|[Import a Domain from a .dqs File](../data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|Esportare un'intera Knowledge Base in un file di dati DQS|[Export a Knowledge Base to a .dqs File](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|Importare un'intera Knowledge Base in un file di dati DQS|[Import a Knowledge Base from a .dqs File](../data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|Importare i valori da un file di Excel in un dominio|[Importare i valori da un file di Excel in un dominio](../data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|Importare i domini da un file di Excel in una Knowledge Base|[Import Domains from an Excel File in Knowledge Discovery](../data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|Importare le informazioni raccolte durante la pulizia in una Knowledge Base|[Import Cleansing Project Values into a Domain](../data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Compilazione di una Knowledge Base eseguendo l'individuazione delle informazioni e gestendo queste ultime in modo interattivo|[Compilazione di una Knowledge Base](../data-quality-services/building-a-knowledge-base.md)|  
|Creazione di un singolo dominio e aggiunta di informazioni al dominio.|[Gestione di un dominio](../data-quality-services/managing-a-domain.md)|  
|Creazione di un dominio composito e aggiunta di informazioni al dominio.|[Gestione di un dominio composito](../data-quality-services/managing-a-composite-domain.md)|  
  
  