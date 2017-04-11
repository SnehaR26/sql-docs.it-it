---
title: "Panoramica: Importazione di dati da tabelle (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "processo di gestione temporanea [Master Data Services], informazioni"
  - "importazione di dati [Master Data Services]"
  - "processo di gestione temporanea [Master Data Services]"
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
caps.latest.revision: 21
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 21
---
# Panoramica: Importazione di dati da tabelle (Master Data Services)
  Dopo aver creato un modello per i dati in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], è possibile iniziare ad aggiungere dati e ad apportarvi modifiche.   È possibile usare stored procedure, tabelle di gestione temporanea e Gestione dati master di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Per istruzioni su come aggiungere e modificare i dati, vedere [Importare dati dalle tabelle &#40;Master Data Services&#41;](../master-data-services/import-data-from-tables-master-data-services.md).  
  
> [!NOTE]  
>  È anche possibile usare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] per aggiungere dati al repository MDS (database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]) da Excel. Per altre informazioni, vedere [Panoramica: Importazione di dati da Excel &#40;componente aggiuntivo MDS per Excel&#41;](../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).  
  
 Quando si aggiungono e si modificano i dati, è possibile:  
  
-   Caricare e aggiornare membri e aggiornare valori di attributo  
  
-   Disattivare ed eliminare membri  
  
-   Spostare membri della gerarchia esplicita  
  
 Le principali attività correlate all'aggiunta e all'aggiornamento dei dati sono le seguenti.  
  
1.  Caricare i dati nelle tabelle di gestione temporanea del database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Caricare i dati dalle tabelle di gestione temporanea nelle tabelle di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] appropriate.  
  
     Per caricare i dati, si usano stored procedure di gestione temporanea oppure [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
> [!NOTE]  
>  In [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] il supporto per i processi di gestione temporanea di [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] è deprecato.  
  
## Disattivazione ed eliminazione di membri (MDS)  
 La disattivazione implica che è possibile riattivare il membro. Se si riattiva un membro, i relativi attributi e l'appartenenza a gerarchie e raccolte vengono ripristinati. Tutte le transazioni precedenti rimangono intatte. Le transazioni di disattivazione sono visibili agli amministratori nell'area funzionale **Gestione versioni** di Gestione dati master.  
  
 L'eliminazione implica l'eliminazione in modo permanente del membro dal sistema. Tutte le transazioni per i membri, tutte le relazioni e tutti gli attributi vengono eliminati in modo definitivo.  
  
> [!NOTE]  
>  Non è possibile usare la gestione temporanea per la riattivazione dei membri. È necessario eseguire l'operazione manualmente in Gestione dati master. Per altre informazioni, vedere [Riattivare un membro o una raccolta &#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md).  
>   
>  Non è possibile usare la gestione temporanea per l'eliminazione o la disattivazione di raccolte. Per altre informazioni sulla disattivazione manuale delle raccolte, vedere [Eliminare un membro o una raccolta &#40;Master Data Services&#41;](../master-data-services/delete-a-member-or-collection-master-data-services.md).  
  
## Spostamento di membri di gerarchie esplicite (MDS)  
 Quando si cambia in blocco la posizione di membri in gerarchie esplicite, è possibile specificare le designazioni seguenti.  
  
-   Un membro consolidato come padre di un membro consolidato.  
  
-   Un membro consolidato come padre di un membro foglia.  
  
-   Un membro foglia come elemento di pari livello di un membro foglia o consolidato.  
  
-   Un membro consolidato come elemento di pari livello di un membro foglia o consolidato.  
  
## Stored procedure e tabelle di gestione temporanea (MDS)  
 Il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] include i tipi di tabelle di gestione temporanea seguenti che è possibile popolare con i dati personali.  
  
-   [Tabella di gestione temporanea dei membri foglia &#40;Master Data Services&#41;](../master-data-services/leaf-member-staging-table-master-data-services.md)  
  
-   [Tabella di gestione temporanea di membri consolidati &#40;Master Data Services&#41;](../master-data-services/consolidated-member-staging-table-master-data-services.md)  
  
-   [Tabella di gestione temporanea delle relazioni &#40;Master Data Services&#41;](../master-data-services/relationship-staging-table-master-data-services.md)  
  
 Per ogni entità del modello esiste una tabella di gestione temporanea. Il nome della tabella indica l'entità corrispondente e il tipo di entità, ad esempio membro foglia. La figura seguente mostra le tabelle di gestione temporanea per le entità currency, customer e product.  
  
 ![Staging Tables in MDS database](../master-data-services/media/mds-staging-tables.png "Staging Tables in MDS database")  
  
 Il nome della tabella viene specificato quando si crea un'entità e non può essere modificato. Se nel nome della tabella di gestione temporanea è contenuto _1 o un altro numero, un'altra tabella con tale nome era già presente al momento della creazione dell'entità.  
  
 In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] sono inclusi i tipi di stored procedure di gestione temporanea seguenti.  
  
-   stg.udp_\<name>_Leaf  
  
-   stg.udp_\<name>_Consolidated  
  
-   stg.udp_\<name>_Relationship  
  
 Per ogni entità nel modello esistono tre stored procedure corrispondenti alle tabelle di gestione temporanea di membri foglia, membri consolidati e relazioni.  La figura seguente mostra le stored procedure di gestione temporanea per le entità currency, customer e product.  
  
 ![Staging stored procedures in the MDS database](../master-data-services/media/mds-staging-storedprocedures.png "Staging stored procedures in the MDS database")  
  
 Per altre informazioni sulle stored procedure, vedere [Stored procedure di gestione temporanea &#40;Master Data Services&#41;](../master-data-services/staging-stored-procedure-master-data-services.md).  
  
## Registrazione delle transazioni (MDS)  
 Tutte le transazioni, che si verificano durante l'importazione o l'aggiornamento di dati o relazioni, possono essere registrate. Un'opzione nella stored procedure consente questa registrazione. Se si inizia il processo di gestione temporanea con [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], non viene eseguita alcuna registrazione.  
  
 In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]l'impostazione **Registra transazioni di gestione temporanea** non viene applicata a questo metodo di gestione temporanea dei dati.  
  
## Contenuto correlato  
  
-   [Convalida &#40;Master Data Services&#41;](../master-data-services/validation-master-data-services.md)  
  
-   [Regole di business &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  