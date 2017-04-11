---
title: "Pianificazione di un&#39;installazione di SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "installazione di SQL Server, pianificazione"
ms.assetid: b1d56f2f-603f-48f2-b902-c715f14a6db9
caps.latest.revision: 36
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 36
---
# Pianificazione di un&#39;installazione di SQL Server
  Per installare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], effettuare le operazioni seguenti:  
  
-   Esaminare i requisiti di installazione, i controlli di configurazione del sistema e le considerazioni sulla sicurezza per un'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per installare o eseguire l'aggiornamento a una versione successiva. Prima dell'aggiornamento, vedere [Eseguire l'aggiornamento a SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md).  
  
-   Utilizzare le utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Indipendentemente dal metodo di installazione, è necessario confermare l'accettazione delle condizioni di licenza del software come utente singolo o per conto di un'entità, a meno che l'utilizzo del software non sia disciplinato da un contratto separato, ad esempio un contratto multilicenza [!INCLUDE[msCoName](../../includes/msconame-md.md)] o un contratto di terze parti con un fornitore di software indipendente o un OEM.  
  
 Le condizioni di licenza vengono visualizzate per la revisione e l'accettazione nell'interfaccia utente del programma di installazione. Le installazioni automatiche che utilizzano i parametri /Q o /QS devono includere il parametro /IAcceptSQLServerLicenseTerms. È possibile esaminare separatamente le condizioni di licenza alla pagina [Condizioni di Licenza Microsoft](http://go.microsoft.com/fwlink/?LinkID=148209).  
  
> [!NOTE]  
>  A seconda della modalità di ricezione del software, ad esempio attraverso un contratto multilicenza [!INCLUDE[msCoName](../../includes/msconame-md.md)], l'utilizzo del software potrebbe essere soggetto a condizioni aggiuntive.  
  
## Argomenti della sezione  
 [Novità relative all'installazione di SQL Server](../../sql-server/install/what-s-new-in-sql-server-installation.md)  
 In questo argomento vengono descritti i dettagli sulle caratteristiche di installazione nuove o migliorate disponibili in questa versione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)  
 In questo argomento vengono elencati i requisiti hardware e software minimi per l'installazione e l'esecuzione di un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 [Considerazioni sulla sicurezza per un'installazione di SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
 Questo argomento illustra alcune procedure consigliate per la sicurezza, da prendere in considerazione prima dell'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e dopo l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
 Nel presente argomento viene fornita la descrizione della configurazione predefinita dei servizi disponibili in questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e delle opzioni di configurazione per i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]che è possibile impostare durante e dopo l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Protocolli e librerie di rete](../../sql-server/install/network-protocols-and-network-libraries.md)  
 In questo argomento viene fornita la descrizione della configurazione predefinita dei protocolli di rete disponibili questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e delle opzioni di configurazione disponibili.  
  
 [Utilizzare più versioni e istanze di SQL Server](../../sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)  
 In questo argomento sono contenute le considerazioni relative alle installazioni di più versioni e istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Versioni in lingua locale di SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md)  
 In questo argomento vengono descritte le versioni localizzate di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## Sezioni correlate  
 [Installare SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016.md)  
 In questa sezione è contenuta una panoramica delle diverse opzioni disponibili per l'installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 [Installare le funzionalità di business intelligence di SQL Server 2016](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)  
 In questa sezione della documentazione relativa al programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene illustrata la modalità di installazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che fanno parte della piattaforma di Business Intelligence di Microsoft.  
  
 [Eseguire l'aggiornamento a SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
 Nella sezione vengono forniti cenni preliminari sull'aggiornamento delle istanze delle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 [Disinstallare SQL Server 2016](../../sql-server/install/uninstall-sql-server-2016.md)  
 Fare riferimento a questa sezione per disinstallare completamente un'istanza esistente di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e preparare il sistema in modo che sia possibile reinstallare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Installazione del cluster di failover di SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 In questa sezione della documentazione relativa al programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono descritte le modalità di installazione e configurazione del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Vedere anche  
 [Installazione di SQL Server 2016 dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [Soluzioni a disponibilità elevata &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Operazioni preliminari all'installazione del clustering di failover](../../sql-server/failover-clusters/install/before-installing-failover-clustering.md)   
 [Eseguire l'aggiornamento a SQL Server 2016 usando l'Installazione guidata &#40;programma di installazione&#41;](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md)  
  
  