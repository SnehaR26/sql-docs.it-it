---
title: "Configurare le impostazioni avanzate per i file di log DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "file di log, impostazioni avanzate"
  - "DQS - file di log, impostazioni avanzate"
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Configurare le impostazioni avanzate per i file di log DQS
  In questo argomento viene descritto come configurare le impostazioni avanzate per i file di log del [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] e del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], ad esempio come impostare il limite delle dimensioni dei file mobili per i file di log, il modello del timestamp degli eventi e così via.  
  
> [!NOTE]  
>  Queste attività non possono essere eseguite mediante il [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] e sono destinate solo agli utenti avanzati.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
  
-   Per modificare le impostazioni di configurazione nella tabella A_CONFIGURATION del database DQS_MAIN, è necessario che l'account utente di Windows sia membro del ruolo predefinito del server sysadmin nell'istanza di SQL Server.  
  
-   Per configurare le impostazioni di registrazione del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], è necessario avere eseguito l'accesso come membro del gruppo Administrators al computer in cui si modifica il file DQLog.Client.xml.  
  
##  <a name="DQSServer"></a> Configurare le impostazioni di log del server Data Quality  
 Il [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] le impostazioni del registro sono presenti in un formato XML nel **valore** colonna il **ServerLogging** riga nella tabella A_CONFIGURATION del database DQS_MAIN. Per visualizzare le informazioni di configurazione, è possibile eseguire la query SQL seguente:  
  
```  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
```  
  
 È necessario aggiornare le informazioni appropriate nella **valore** colonna il **ServerLogging** riga per modificare le impostazioni di configurazione per [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] registrazione. In questo esempio verranno aggiornate le impostazioni di log del [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] per impostare il limite delle dimensioni dei file mobili su 25000 KB (il valore predefinito è 20000 KB).  
  
1.  Avviare Microsoft SQL Server Management Studio e connettersi all'istanza di SQL Server appropriata.  
  
2.  In Esplora oggetti, fare doppio clic su server e quindi fare clic su **Nuova Query**.  
  
3.  Nella finestra dell'editor di query copiare le istruzioni SQL seguenti:  
  
    ```  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  Premere F5 per eseguire le istruzioni. Esaminare il riquadro dei risultati ** ** per verificare che le istruzioni siano state eseguite correttamente.  
  
5.  Per applicare le modifiche apportate alla configurazione della registrazione del [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], è necessario eseguire le istruzioni Transact-SQL seguenti. Aprire una nuova finestra dell'editor di query e incollare le istruzioni Transact-SQL seguenti:  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
  
    ```  
  
6.  Premere F5 per eseguire le istruzioni. Esaminare il riquadro dei risultati ** ** per verificare che le istruzioni siano state eseguite correttamente.  
  
> [!NOTE]  
>  Il [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] configurazione delle impostazioni di registrazione è generati dinamicamente e archiviati i database DQS_MAIN. File di log, in genere disponibile in C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Log se è installata l'istanza predefinita di SQL Server. Tuttavia, le modifiche effettuate direttamente in questo file non vengono conservate e vengono sovrascritte dalle impostazioni di configurazione nella tabella A_CONFIGURATION del database DQS_MAIN.  
  
##  <a name="DQSClient"></a> Configurare le impostazioni di log del client Data Quality  
 Il [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] file di configurazione impostazioni di log, DQLog.Client.xml, è disponibile in genere in C:\Program Files\Microsoft SQL Server\130\Tools\Binn\DQ\config. Il contenuto del file XML è simile al file XML modificato precedentemente per le impostazioni di configurazione di log del [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]. Per configurare le impostazioni di log del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]:  
  
1.  Eseguire un qualsiasi strumento di modifica dei file XML o Blocco note come amministratore.  
  
2.  Aprire il file DQLog.Client.xml nello strumento o in Blocco note.  
  
3.  Apportare le modifiche necessarie e salvare il file per applicare le nuove modifiche di registrazione.  
  
## Vedere anche  
 [Configure Severity Levels for DQS Log Files](../data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  