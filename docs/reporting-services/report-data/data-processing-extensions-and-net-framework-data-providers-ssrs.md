---
title: "Estensioni per l&#39;elaborazione dati e provider di dati .NET Framework (SSRS) | Microsoft Docs"
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
  - "report [Reporting Services], dati"
  - "estensioni per l'elaborazione dati [Reporting Services]"
  - "provider di dati [Reporting Services]"
  - "recupero di dati [Reporting Services]"
  - "Reporting Services, origini dati"
  - "dati del report [Generatore report], accesso"
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 19
---
# Estensioni per l&#39;elaborazione dati e provider di dati .NET Framework (SSRS)
  Un'estensione per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è un componente installato con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], progettato per recuperare i dati da un tipo specifico di origine dati e offrire funzionalità aggiuntive per supportare la progettazione e l'elaborazione dei report. Un provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] è un componente reso disponibile da [!INCLUDE[msCoName](../../includes/msconame-md.md)] o da terze parti in grado di supportare le interfacce <xref:System.Data> che consentono di recuperare e modificare i dati da un tipo specifico di origine dati.  
  
## Informazioni sulle estensioni per l'elaborazione dei dati  
 L'estensione per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supporta un subset delle interfacce <xref:System.Data>. Le estensioni per l'elaborazione dati richiedono soltanto l'accesso in lettura all'origine dati, pertanto le interfacce per scrivere e aggiornare non sono implementate. Ogni estensione per l'elaborazione dati può fornire caratteristiche personalizzate per supportare l'elaborazione del report. Un'estensione per l'elaborazione dati potrebbe supportare ad esempio i tipi di caratteristiche seguenti:  
  
-   Gestione di credenziali separatamente dalla stringa di connessione  
  
-   Supporto di parametri multivalore  
  
-   Recupero di aggregazioni server calcolate nell'origine dati  
  
-   Recupero di proprietà e valori dei dati dall'origine dati  
  
## Informazioni sui provider di dati  
 Un provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (talvolta noto anche come driver) supporta un set standard di interfacce <xref:System.Data> per la lettura, la scrittura e l'aggiornamento di dati in un'origine dati. I provider di dati possono essere utilizzati quando non sono disponibili estensioni per l'elaborazione dati per un determinato tipo di origine dati. Sono disponibili numerosi provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] standard di terze parti.  
  
 Poiché [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è provvisto di un'architettura di provider di dati estensibile, è possibile compilare estensioni per l'elaborazione dati personalizzate con funzionalità aggiuntive offerte dalle estensioni di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Per ulteriori informazioni, vedere [Implementing a Data Processing Extension](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md). Per le estensioni per l'elaborazione dati di terze parti, vedere la documentazione fornita con le stesse.  
  
> [!NOTE]  
>  Per poter accedere ai dati di un'origine dati mediante un provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] o un'estensione per l'elaborazione dati personalizzata, è necessario che questi ultimi vengano installati e registrati. L'estensione per l'elaborazione dati deve essere installata e registrata nel client per la gestione dei report per creare il report e nel server di report per visualizzare il report pubblicato. Non tutti i provider di dati vengono progettati per il funzionamento in un ambiente server. Per altre informazioni, vedere [Registrare un provider di dati .NET Framework standard &#40;SSRS&#41;](../../reporting-services/report-data/register-a-standard-net-framework-data-provider-ssrs.md) e [Distribuzione di un'estensione per l'elaborazione dati](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md).  
  
## Vedere anche  
 [Cenni preliminari sulle estensioni per l'elaborazione dati](../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)   
 [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  