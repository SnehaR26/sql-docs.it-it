---
title: "Servizio SharePoint di Reporting Services e applicazioni di servizio | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 501aa9ee-8c13-458c-bf6f-24e00c82681b
caps.latest.revision: 10
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 10
---
# Servizio SharePoint di Reporting Services e applicazioni di servizio
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è basata sull'architettura del servizio SharePoint e prevede l'utilizzo di un servizio SharePoint e di applicazioni di servizio uno-a-molti. Creando un'applicazione di servizio si rende disponibile il servizio e si genera il database dell'applicazione di servizio. È possibile creare più applicazioni di servizio Reporting Services, tuttavia un'unica applicazione di servizio è sufficiente per la maggior parte degli scenari di distribuzione.  
  
 In questo argomento vengono illustrate le informazioni seguenti:  
  
-   [Creazione di un'applicazione di servizio Reporting Services](#bkmk_createapp)  
  
-   [Modifica delle associazioni dell'applicazione di servizio con un gruppo di proxy](#bkmk_associations)  
  
-   [Modificare le proprietà dell'applicazione di servizio](#bkmk_editserviceapplication)  
  
-   [Per creare un'applicazione di servizio Reporting Services utilizzando PowerShell](#bkmk_powershell_create_ssrs_serviceapp)  
  
-   [Attività correlate](#bkmk_related)  
  
##  <a name="bkmk_createapp"></a> Creazione di un'applicazione di servizio Reporting Services  
 Per creare applicazioni di servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , è possibile utilizzare Amministrazione centrale SharePoint o script di PowerShell. Per altre informazioni sull'uso di Amministrazione centrale SharePoint, vedere la sezione "Creare un'applicazione di servizio Reporting Services" in [Installare la modalità SharePoint di Reporting Services per SharePoint 2010](http://msdn.microsoft.com/it-it/47efa72e-1735-4387-8485-f8994fb08c8c). Per uno script di PowerShell di esempio per la creazione di applicazioni di servizio, vedere la sezione relativa a PowerShell più avanti in questo argomento.  
  
##  <a name="bkmk_associations"></a> Modifica delle associazioni dell'applicazione di servizio con un gruppo di proxy  
 Nella pagina Nuova per la creazione di un'applicazione di servizio è contenuta la sezione **Associazione applicazione Web**. Questa sezione consente di associare l'applicazione di servizio quando viene creata. Utilizzare i passaggi seguenti per modificare l'associazione e assegnare una configurazione personalizzata all'applicazione di servizio. Lo stesso processo generale può inoltre essere utilizzato per aggiungere il proxy al gruppo predefinito anziché modificare l'associazione dell'applicazione di servizio a un gruppo personalizzato.  
  
1.  In Gestione applicazioni di Amministrazione centrale SharePoint fare clic su **Configura associazioni applicazione di servizio**.  
  
2.  Nella pagina Associazioni applicazione di servizio modificare la visualizzazione in **Applicazioni di servizio**.  
  
3.  Trovare e fare clic sul nome della nuova applicazione di servizio di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . È possibile fare clic anche sull' **impostazione predefinita** del nome del gruppo proxy di applicazione per aggiungere il proxy per impostare il gruppo piuttosto che completare i passaggi seguenti.  
  
4.  Nella casella di selezione **Modifica il gruppo di connessioni seguente** scegliere **Personalizza**.  
  
5.  Selezionare la casella relativa al proxy e fare clic su **OK**.  
  
##  <a name="bkmk_editserviceapplication"></a> Modificare le proprietà dell'applicazione di servizio  
 È possibile riaprire la pagina delle proprietà dell'applicazione di servizio per modificare le proprietà.  
  
1.  Nel gruppo Gestione applicazioni di Amministrazione centrale SharePoint fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Selezionare l'applicazione di servizio facendo clic sul tipo di colonna per selezionare l'intera riga. Se si fa clic sul nome dell'applicazione, viene aperta la pagina delle opzioni di gestione per il servizio anziché le proprietà dell'applicazione di servizio.  
  
3.  Nella barra multifunzione relativa alle applicazioni di servizio fare clic su **Proprietà**.  
  
##  <a name="bkmk_powershell_create_ssrs_serviceapp"></a> Per creare un'applicazione di servizio Reporting Services utilizzando PowerShell  
 È possibile utilizzare PowerShell per creare l'applicazione di servizio e il proxy. Nell'esempio sottostante si presuppone che si conosca quale pool di applicazioni si desidera configurare affinché venga utilizzato dall'applicazione di servizio.  
  
1.  Aggiungere l'oggetto del pool di applicazioni del nome del pool di applicazioni a una variabile che viene passata in Nuova azione.  
  
    ```  
    $appPoolName = get-spserviceapplicationpool “<application pool name>”  
    ```  
  
2.  Creare l'applicazione di servizio con un nome e il nome del pool di applicazioni forniti.  
  
    ```  
    New-SPRSServiceApplication –Name ‘MyServiceApplication’ –ApplicationPool $appPoolName –DatabaseName ‘MyServiceApplicationDatabase’ –DatabaseServer ‘<Server Name>’  
    ```  
  
3.  Ottenere il nuovo oggetto dell'applicazione di servizio e inoltrare tramite pipe l'oggetto nella pipe del nuovo cmdlet del proxy.  
  
    ```  
    Get-SPRSServiceApplication –name MyServiceApplication | New-SPRSServiceApplicationProxy “MyServiceApplicationProxy”  
    ```  
  
##  <a name="bkmk_related"></a> Attività correlate  
  
|Attività|Collegamento|  
|----------|----------|  
|Gestire le impostazioni dell'applicazione di servizio.|[Gestire un'applicazione di servizio SharePoint di Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)|  
|Eseguire il backup e il ripristino dell'applicazione di servizio e dei componenti correlati, quali chiavi di crittografia e proxy.|[Eseguire il backup e il ripristino di applicazioni di servizio SharePoint di Reporting Services](../../reporting-services/report-server-sharepoint/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  
  
  