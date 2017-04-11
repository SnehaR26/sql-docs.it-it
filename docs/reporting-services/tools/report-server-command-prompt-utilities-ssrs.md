---
title: "Utilit&#224; della riga di comando del server di report (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rsconfig - utilità"
  - "componenti [Reporting Services], utilità della riga di comando"
  - "rs - utilità"
  - "utilità del prompt dei comandi [Reporting Services]"
  - "rskeymgmt - utilità"
ms.assetid: 68f2f9f4-f894-40ff-a71c-f9756bf4b68c
caps.latest.revision: 48
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 48
---
# Utilit&#224; della riga di comando del server di report (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] include diverse utilità della riga di comando che è possibile usare per gestire un server di report. Tali utilità vengono installate automaticamente al momento dell'installazione di un server di report.  
  
|Nome|File di comando|Modalità di distribuzione supportata|Description|  
|----------|------------------|-------------------------------|-----------------|  
|Utilità RSS|rs.exe|Modalità nativa e modalità SharePoint. Nella versione [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] è stato introdotto il supporto per la modalità SharePoint.|L'[utilità rs](../../reporting-services/tools/rs-exe-utility-ssrs.md) è un host di script che è possibile usare per l'esecuzione di operazioni inserite nello script. Questo strumento consente di eseguire script di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] per la copia di dati tra database del server di report, la pubblicazione di report, la creazione di elementi in un database del server di report e altro ancora. Per sapere di più sull'uso di script per gestire un server, vedere [Utilizzare script per l'esecuzione di attività di distribuzione e di amministrazione](../../reporting-services/tools/script-deployment-and-administrative-tasks.md).|  
|Cmdlet di PowerShell||Solo SharePoint|Per un elenco dei cmdlet di PowerShell, vedere [PowerShell cmdlets for Reporting Services SharePoint Mode](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) (Cmdlet di PowerShell per la modalità SharePoint di Reporting Services).|  
|Utilità Rsconfig|rsconfig.exe|Solo nativa|L'[utilità rsconfig](../../reporting-services/tools/rsconfig-utility-ssrs.md) consente di configurare e gestire una connessione del server di report al database del server di report. È inoltre possibile utilizzarla per specificare un account utente per l'elaborazione automatica dei report. Per altre informazioni, vedere [Reporting Services Report Server &#40;Native Mode&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md). Per sapere di più sulla configurazione della connessione, vedere [Configurare una connessione del database del server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md).|  
|Utilità rskeymgmt|rskeymgmt.exe|Solo nativa|L'[utilità rskeymgmt](../../reporting-services/tools/rskeymgmt-utility-ssrs.md) è uno strumento di gestione delle chiavi di crittografia. È possibile utilizzarla per eseguire il backup, applicare, ricreare ed eliminare chiavi simmetriche. Questo strumento può inoltre essere utilizzato per associare un'istanza del server di report a un database del server di report condiviso e in operazioni di recupero del database. È possibile riutilizzare un database esistente in una nuova installazione applicando una copia di backup della chiave simmetrica. Nel caso non sia possibile recuperare le chiavi, questo strumento consente di eliminare il contenuto crittografato non più utilizzabile. Per sapere di più sulla gestione delle chiavi e sull'archiviazione dei dati sensibili, vedere [Archiviare i dati crittografati del server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/store-encrypted-report-server-data-ssrs-configuration-manager.md) e [Configurare e gestire chiavi di crittografia &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-and-manage-encryption-keys-ssrs-configuration-manager.md).|  
  
> [!NOTE]  
>  Se si preferisce uno strumento con interfaccia utente grafica, è possibile usare Gestione configurazione Reporting Services anziché **rsconfig** e **rskeymgmt**.  
  
## Vedere anche  
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Strumenti di Reporting Services](../../reporting-services/tools/reporting-services-tools.md)   
 [Reporting Services Report Server &#40;Native Mode&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)  
  
  