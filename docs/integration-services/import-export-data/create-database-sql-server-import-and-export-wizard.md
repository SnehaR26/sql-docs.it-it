---
title: "Crea database (Importazione/Esportazione guidata SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.createdatabase.f1"
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
caps.latest.revision: 54
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 52
---
# Crea database (Importazione/Esportazione guidata SQL Server)
Se si seleziona **Nuovo** nella pagina **Scegliere una destinazione** per creare un nuovo database di destinazione SQL Server, l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza la finestra di dialogo **Crea database**. In questa pagina è possibile specificare un nome per il nuovo database. Facoltativamente è possibile modificare le impostazioni per la dimensione iniziale e l'aumento automatico del nuovo database e il relativo file di log. 

> [!NOTE] Per maggiori informazioni sull'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE DATABASE e non sulla finestra di dialogo **Creazione database** di Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [CREATE DATABASE &#40;Transact-SQL di SQL Server&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  

## <a name="screen-shot-of-the-create-database-page"></a>Screenshot della pagina Crea database  
L'immagine riportata di seguito illustra la finestra di dialogo **Creazione database** della procedura guidata.  

Questa finestra di dialogo della procedura guidata offre solo un subset delle opzioni disponibili per la creazione di un nuovo database di SQL Server. Per visualizzare e configurare tutte le opzioni di un nuovo database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], usare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per creare o configurare il database. 

![Create database page of the Import and Export Wizard](../../integration-services/import-export-data/media/create-database.png "Create database page of the Import and Export Wizard")  

## <a name="provide-a-name-for-the-new-database"></a>Specificare un nome per il nuovo database  
**Nome**  
 Consente di specificare un nome univoco per il database di SQL Server di destinazione. Accertarsi di rispettare le convenzioni di denominazione dei database di SQL Server.  
  
-   Il nome del database deve essere univoco in un'istanza di SQL Server.  
  
-   Il nome del database può essere composto da un massimo di 123 caratteri. (In questo modo sono consentiti 5 caratteri per i suffissi che SQL Server aggiunge al file di dati e al file di log, fino a un massimo di 128 caratteri.)  
  
-   Il nome del database deve essere conforme alle regole per gli identificatori di SQL Server. Ecco i requisiti più importanti.  
  
    -   Il primo carattere deve essere una lettera, un carattere di sottolineatura (_), il simbolo di chiocciola (@), o il simbolo di cancelletto (#).  
  
    -   I caratteri successivi possono essere lettere, numeri, il simbolo di chiocciola, il simbolo di dollaro ($), il simbolo di cancelletto o il carattere di sottolineatura.  
  
    -   Non è possibile usare spazi o altri caratteri speciali.  
  
Per informazioni dettagliate su questi requisiti, vedere [Identificatori del database](../../relational-databases/databases/database-identifiers.md).  

## <a name="optionally-specify-data-file-and-log-file-options"></a>Facoltativamente specificare le opzioni del file di dati e del file di log

> [!TIP] È necessario specificare un nome per il nuovo database nel campo **Nome**, ma in genere è possibile lasciare inalterati i valori predefiniti delle altre impostazioni per la dimensione e l'aumento delle dimensioni del file.
>
> Per altre informazioni sulle opzioni per le dimensioni di file visualizzati in questa pagina, vedere [CREATE DATABASE &#40;Transact-SQL di SQL Server&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md). 

### <a name="data-file-options"></a>Opzioni del file di dati  
 **Dimensioni iniziali**  
 Consente di specificare il numero di megabyte per le dimensioni iniziali del file di dati.  
  
 **Aumento dimensioni non consentito**  
 Consente di indicare se le dimensioni del file di dati possono eccedere le dimensioni iniziali specificate.  
  
 **Aumento dimensioni in percentuale**  
 Consente di specificare che le dimensioni del file di dati possono aumentare in base a un valore percentuale.  
  
 **Aumento dimensioni in MB**  
 Consente di specificare che le dimensioni del file di dati possono aumentare in base a un numero di megabyte.  
  
### <a name="log-file-options"></a>Opzioni del file di log  
 **Dimensioni iniziali**  
 Consente di specificare il numero di megabyte per le dimensioni iniziali del file di log.  
  
 **Aumento dimensioni non consentito**  
 Consente di indicare se le dimensioni del file di log possono eccedere le dimensioni iniziali specificate.  
  
 **Aumento dimensioni in percentuale**  
 Consente di specificare che le dimensioni del file di log possono aumentare in base a un valore percentuale.  
  
 **Aumento dimensioni in MB**  
 Consente di specificare che le dimensioni del file di log possono aumentare in base a un numero di megabyte.  
  
## <a name="whats-next"></a>Operazioni successive  
 Dopo aver specificato un nome per il nuovo database che verrà creato dalla procedura guidata e dopo aver fatto clic su **OK**, la finestra di dialogo **Creazione database** si chiude e verrà visualizzata nuovamente la pagina **Scegliere una destinazione**. Per altre informazioni, vedere [Scelta destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).  