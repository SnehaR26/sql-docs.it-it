---
title: Configurare un Server di Report per il recapito tramite posta elettronica (Gestione configurazione SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], distributing
- report servers [Reporting Services], e-mail delivery
- remote SMTP service [Reporting Services]
- distributing reports [Reporting Services], e-mail
- CDO
- Collaboration Data Objects
- SMTP settings [Reporting Services]
- e-mail [Reporting Services]
- sending reports
- mail [Reporting Services]
- local SMTP service [Reporting Services]
ms.assetid: b838f970-d11a-4239-b164-8d11f4581d83
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 275503157f0bfbc004463f3bc567cfbef4a3fc41
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117051"
---
# <a name="configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager"></a>Configurare un server di report per il recapito tramite posta elettronica (Gestione configurazione SSRS)
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è disponibile un'estensione per il recapito tramite posta elettronica che consente di distribuire report tramite posta elettronica. A seconda di come viene definita la sottoscrizione tramite posta elettronica, un recapito può essere costituito da una notifica, un collegamento, un allegato o un report incorporato. L'estensione per il recapito tramite posta elettronica può essere utilizzata con la tecnologia del server di posta elettronica esistente. Il server di posta elettronica deve essere un server SMTP o un server di inoltro. Il server di report si connette a un server SMTP tramite librerie Collaboration Data Objects, o CDO, (cdosys.dll) fornite dal sistema operativo.  
  
 Per impostazione predefinita, l'estensione per il recapito tramite posta elettronica del server di report non è configurata. Per configurare al minimo l'estensione, è necessario utilizzare Gestione configurazione Reporting Services. Per impostare le proprietà avanzate, è necessario modificare il file `RSReportServer.config` . Se non è possibile configurare il server di report per utilizzare questa estensione, è possibile invece recapitare i report in una cartella condivisa. Per ulteriori informazioni, vedere [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md).  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modalità nativa|  
  
 
  
##  <a name="bkmk_configuration_requirements"></a> Requisiti di configurazione  
  
-   La funzionalità di recapito tramite posta elettronica del server di report viene implementata in oggetti CDO (Collaboration Data Objects) e per essa è richiesto un server SMTP (Simple Mail Transfer Protocol) locale o remoto o un server d'inoltro SMTP. SMTP non è supportato in tutti i sistemi operativi Windows. Se si utilizza l'edizione basata su Itanium di Windows Server 2008, SMTP non è supportato. Per ulteriori informazioni sulle opzioni di configurazione disponibili tramite CDO, vedere la pagina relativa alla [coclasse Configuration](http://go.microsoft.com/fwlink/?LinkId=98237) nel sito Web MSDN.  
  
-   L'account del servizio del server di report deve disporre dell'autorizzazione necessaria per inviare messaggi di posta elettronica nel server SMTP.  
  
-   L'estensione per il recapito tramite posta elettronica utilizza la codifica UTF-8 negli allegati di posta elettronica. Non è possibile modificare la codifica. L'estensione per il rendering HTML supporta solo la codifica UTF-8.  
  
> [!NOTE]  
>  L'estensione predefinita per il recapito tramite posta elettronica non supporta la firma digitale e la crittografia dei messaggi in uscita.  
  
 
  
##  <a name="bkmk_configure_for_local_or_remote_SMTP"></a> Configurazione di un Server di Report per il servizio SMTP locale o remoto  
 È possibile utilizzare un servizio SMTP locale o un server SMTP remoto o un server d'inoltro per supportare il recapito tramite posta elettronica. Se si ha accesso a un server SMTP remoto esistente, è consigliabile utilizzarlo. Se non esiste alcun server SMTP disponibile o se in seguito vengono generati errori di recapito dei report che possono essere attribuiti a errori di connessione del computer, utilizzare un servizio SMTP locale. Più avanti in questo argomento vengono forniti dettagli sulla configurazione di un server di report per un servizio locale o remoto.  
  
  
  
##  <a name="bkmk_setting_email_delivery"></a> Impostazione delle opzioni di configurazione per il recapito tramite posta elettronica  
 Prima di poter utilizzare il recapito tramite posta elettronica di Server report, è necessario impostare valori di configurazione che offrano informazioni sul server SMTP da utilizzare.  
  
 Per configurare un server di report per il recapito tramite posta elettronica, eseguire le operazioni seguenti:  
  
-   Utilizzare Gestione configurazione Reporting Services se si specifica soltanto un server SMTP e un account utente con autorizzazione a inviare posta elettronica. Si tratta delle impostazioni minime necessarie per la configurazione dell'estensione per il recapito tramite posta elettronica di Server report. Per altre informazioni, vedere [impostazioni di posta elettronica - Configuration Manager &#40;modalità nativa SSRS&#41; ](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) e [recapito tramite posta elettronica in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   Utilizzare un editor di testo per specificare impostazioni aggiuntive nel file RSreportserver.config (facoltativo). Questo file contiene tutte le impostazioni di configurazione per il recapito tramite posta elettronica del server di report. È necessario specificare impostazioni aggiuntive in questi file se si utilizza un server SMTP locale o se il recapito tramite posta elettronica è limitato a host specifici. Per altre informazioni sulla ricerca e la modifica dei file di configurazione, vedere [modificare un File di configurazione di Reporting Services &#40;RSReportServer. config&#41; ](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) nella documentazione Online di SQL Server.  
  
> [!NOTE]  
>  Le impostazioni della posta elettronica del server di report sono basate su CDO. Per ulteriori informazioni su impostazioni specifiche, fare riferimento alla documentazione di CDO.  
  

  
##  <a name="bkmk_example_config_file"></a> Configurazione di posta elettronica Server di Report di esempio  
 Nell'esempio seguente vengono illustrate le impostazioni nel file RSreportserver.config per un server SMTP remoto. Per informazioni su come le descrizioni delle impostazioni e i valori validi, vedere [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione in linea o la documentazione di CDO.  
  
```  
<RSEmailDPConfiguration>  
     <SMTPServer>mySMTPServer.Adventure-Works.com</SMTPServer>  
     <SMTPServerPort></SMTPServerPort>  
     <SMTPAccountName></SMTPAccountName>  
     <SMTPConnectionTimeout></SMTPConnectionTimeout>  
     <SMTPServerPickupDirectory></SMTPServerPickupDirectory>  
     <SMTPUseSSL></SMTPUseSSL>  
     <SendUsing>2</SendUsing>  
     <SMTPAuthenticate></SMTPAuthenticate>  
     <From>my-rs-email-account@Adventure-Works.com</From>  
     <EmbeddedRenderFormats>  
          <RenderingExtension>MHTML</RenderingExtension>  
     </EmbeddedRenderFormats>  
     <PrivilegedUserRenderFormats></PrivilegedUserRenderFormats>  
     <ExcludedRenderFormats>  
          <RenderingExtension>HTMLOWC</RenderingExtension>  
          <RenderingExtension>NULL</RenderingExtension>  
     </ExcludedRenderFormats>  
     <SendEmailToUserAlias>True</SendEmailToUserAlias>  
     <DefaultHostName></DefaultHostName>  
     <PermittedHosts>  
          <HostName>Adventure-Works.com</HostName>  
          <HostName>hotmail.com</HostName>  
     </PermittedHosts>  
</RSEmailDPConfiguration>  
```  
  

  
##  <a name="bkmk_setting_TO_field"></a> Opzioni di configurazione per l'impostazione di a: campo di un messaggio  
 Le sottoscrizioni definite dall'utente create in base alle autorizzazioni concesse dall'attività **Gestione di sottoscrizioni individuali** contengono un nome utente preimpostato che si basa sull'account utente di dominio. Quando l'utente crea la sottoscrizione, l'indirizzo del nome del destinatario incluso nel campo **A:** viene immesso automaticamente in base all'account utente di dominio della persona che crea la sottoscrizione.  
  
 Se si utilizza un server SMTP o un server d'inoltro che utilizza account di posta elettronica diversi dall'account utente di dominio, il recapito del report non riuscirà quando il server SMTP tenterà di recapitare il report a tale utente.  
  
 Per ovviare a questo problema, è possibile modificare le impostazioni di configurazione che consentono agli utenti di immettere un nome nel campo **A:**  
  
1.  Aprire RSReportServer.config con un editor di testo.  
  
2.  Impostare `SendEmailToUserAlias` a `False`.  
  
3.  Impostare `DefaultHostName` al sistema DNS (Domain Name) nome o indirizzo IP del server SMTP o del server d'inoltro.  
  
4.  Salvare il file.  
  
  
  
##  <a name="bkmk_options_remote_SMTP"></a> Opzioni di configurazione per il servizio SMTP remoto  
 La connessione tra il server di report e un server SMTP o un server d'inoltro viene determinata tramite le impostazioni di configurazione seguenti:  
  
-   `SendUsing` Specifica un metodo per l'invio di messaggi. È possibile scegliere tra un servizio SMTP di rete o una directory di prelievo del servizio SMTP locale. Per utilizzare un servizio SMTP remoto, questo valore deve essere impostato su **2** nel file RSReportServer.config.  
  
-   `SMTPServer` Specifica il server SMTP remoto o server d'inoltro. Questo valore è obbligatorio se si utilizza un server SMTP remoto o un server d'inoltro.  
  
-   `From` Imposta il valore visualizzato nei **da:** riga del messaggio di posta elettronica. Questo valore è obbligatorio se si utilizza un server SMTP remoto o un server d'inoltro.  
  
 Tra gli altri valori utilizzati per il servizio SMTP remoto sono inclusi quelli indicati di seguito. Si noti che non è necessario specificare tali valori, a meno che non si desideri ignorare i valori predefiniti.  
  
-   **SMTPServerPort** è configurato per la porta 25.  
  
-   **SMTPAuthenticate** specifica il modo in cui il server di report si connette a un server SMTP remoto. Il valore predefinito è 0, ovvero nessuna autenticazione. In questo caso, la connessione viene stabilita tramite l'accesso anonimo. In base alla configurazione del dominio, potrebbe essere necessario che il server di report e il server SMTP siano membri dello stesso dominio.  
  
     Per inviare messaggi di posta elettronica a liste di distribuzione limitate, ad esempio liste di distribuzione in cui si accettano i messaggi in arrivo solo da account autenticati, impostare **SMTPAuthenticate** su **2**.  
  

  
##  <a name="bkmk_options_local_SMTP"></a> Opzioni di configurazione per il servizio SMTP locale  
 La configurazione di un servizio SMTP locale è utile se si desidera testare o risolvere i problemi di recapito tramite posta elettronica del server di report. Il servizio SMTP locale non è attivato per impostazione predefinita. Per istruzioni su come abilitarlo, vedere [configurare un Server di Report per il recapito tramite posta elettronica (Gestione configurazione SSRS)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) e [impostazioni di posta elettronica - Configuration Manager &#40;modalità nativa SSRS&#41; ](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) .  
  
 La connessione tra il server di report e un server SMTP locale o un server d'inoltro viene determinata tramite le impostazioni di configurazione seguenti:  
  
-   `SendUsing` è impostato su **1**.  
  
-   **SMTPServerPickupDirectory** è impostato su una cartella nell'unità locale.  
  
    > [!NOTE]  
    >  Assicurarsi che non si imposta `SMTPServer` se si usa un server SMTP locale.  
  
-   `From` Imposta il valore visualizzato nei **da:** riga del messaggio di posta elettronica. Questo valore è obbligatorio.  
  
 
  
##  <a name="bkmk_use_configuration_manager"></a> Per configurare posta elettronica di server di report tramite Gestione configurazione Reporting Services  
  
1.  Verificare che il servizio Windows ReportServer disponga delle autorizzazioni `Send As` sul server SMTP.  
  
2.  Avviare Gestione configurazione Reporting Services e connettersi all'istanza del server di report.  
  
3.  Nella pagina Impostazioni posta elettronica immettere il nome del server SMTP. Questo valore può corrispondere a un indirizzo IP, un nome UNC di un computer dell'Intranet aziendale o un nome di dominio completo.  
  
4.  In **Indirizzo mittente**immettere il nome di un account autorizzato a inviare messaggi di posta elettronica dal server SMTP.  
  
5.  Fare clic su **Applica**.  
  

  
##  <a name="bkmk_confiugre_remote_SMTP"></a> Per configurare un servizio SMTP remoto per il server di report  
  
1.  Verificare che il servizio Windows ReportServer disponga delle autorizzazioni `Send As` sul server SMTP.  
  
2.  Aprire il file RSReportServer.config in un editor di testo.  
  
3.  Verificare che <`UrlRoot`> è impostato per l'indirizzo URL del server di report. Questo valore viene impostato quando si configura il server di report e quindi dovrebbe essere già inserito. In caso contrario, digitare l'indirizzo URL del server di report.  
  
4.  Nella sezione Delivery individuare la voce <`ReportServerEmail`>.  
  
5.  In <`SMTPServer`> digitare il nome del server SMTP. Questo valore può corrispondere a un indirizzo IP, un nome UNC di un computer dell'Intranet aziendale o un nome di dominio completo.  
  
6.  Verificare che <`SendUsing`> sia impostato su 2. Se è impostato un valore diverso, il server di report non è configurato per l'utilizzo di un servizio SMTP remoto.  
  
7.  In <`From`>, digitare il nome di un account che dispone dell'autorizzazione per l'invio di posta elettronica dal server SMTP.  
  
8.  Salvare il file.  
  
     Il server di report utilizzerà automaticamente le nuove impostazioni e non sarà necessario riavviare il servizio. È possibile specificare impostazioni SMTP aggiuntive per configurare ulteriormente la modalità di utilizzo del server SMTP per il recapito tramite posta elettronica del server di report. Per altre informazioni, vedere [configurare un Server di Report per il recapito tramite posta elettronica](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) e [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione Online.  
  

  
##  <a name="bkmk_confiugre_local_SMTP"></a> Per configurare un servizio SMTP locale per il server di report  
  
1.  Nel Pannello di controllo fare clic su **Installazione applicazioni**.  
  
2.  Fare clic su **Installazione componenti di Windows** per avviare l'Aggiunta guidata componenti di Windows.  
  
3.  Selezionare **Server applicazioni** e fare clic su **Dettagli**.  
  
4.  Selezionare **IIS (Internet Information Services)** e fare clic su **Dettagli**.  
  
5.  Selezionare la casella di controllo **Servizio SMTP** e fare clic su **OK**.  
  
6.  In Aggiunta guidata componenti di Windows fare clic su **Avanti**. Scegliere **Fine**.  
  
7.  Nella console **Servizi** verificare che il servizio sia in esecuzione.  
  
8.  Aprire il file **RSReportServer.config** in un editor di testo.  
  
9. Verificare che `<UrlRoot>` sia impostato sull'indirizzo URL del server di report. Questo valore viene impostato quando si configura il server di report e quindi dovrebbe essere già inserito. In caso contrario, digitare l'indirizzo URL del server di report.  
  
10. Nella sezione relativa al recapito individuare `<ReportServerEmail>.`  
  
11. In `<SMTPServer>`cancellare tutti i valori eventualmente presenti per questa impostazione ma non eliminare i tag.  
  
12. Impostare `<SendUsing>` su 1. Se è impostato un valore diverso, il server di report non è configurato per l'utilizzo di un servizio SMTP locale.  
  
13. Impostare `<SMTPServerPickupDirectory>` su una cartella nell'unità locale.  
  
14. Impostare `<From>` su un account autorizzato a inviare messaggi di posta elettronica dal server SMTP.  
  
15. Salvare il file.  
  
 
  
## <a name="see-also"></a>Vedere anche  
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
