---
title: Prerequisiti per la procedura dettagliata dell'analisi scientifica dei dati per SQL Server e R | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 08/23/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 0b0582b8-8843-4787-94a8-2e28bdc04fb2
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9d3a579f023a7e6d9805b934edc3f0e9e5ad5e8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="prerequisites-for-the-data-science-walkthrough-for-sql-server-and-r"></a>Prerequisiti per la procedura dettagliata dell'analisi scientifica dei dati per SQL Server e R

È consigliabile eseguire questa procedura dettagliata su un computer portatile o un altro computer che installate le librerie di Microsoft R. È necessario essere in grado di connettersi, nella stessa rete, a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer con servizi di machine learning e il linguaggio R abilitato.

È possibile eseguire la procedura dettagliata in un computer che dispone di entrambe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un ambiente di sviluppo di R, ma si sconsiglia di questa configurazione per un ambiente di produzione.

## <a name="install-machine-learning-for-sql-server"></a>Installare l'apprendimento di SQL Server

È necessario avere accesso a un'istanza di SQL Server con il supporto per R installato, utilizzando uno dei seguenti:

+ Per SQL Server 2017 di Machine Learning Services (In-Database)
+ SQL Server 2016 R Services

Per ulteriori informazioni, vedere [configurare SQL Server R Services (In-Database](../r/set-up-sql-server-r-services-in-database.md).

> [!IMPORTANT]
> Assicurarsi di usare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] o versione successiva. Le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supportano l'integrazione con R. Tuttavia, è possibile usare i database SQL precedenti come origine dati ODBC.

## <a name="install-an-r-development-environment"></a>Installare un ambiente di sviluppo di R

Per questa procedura dettagliata, è consigliabile utilizzare un ambiente di sviluppo R. Di seguito sono riportati alcuni suggerimenti:

- **Strumenti R per Visual Studio** (RTVS) è un plug-in che fornisce Intellisense, debug e il supporto per Microsoft R. È possibile utilizzarlo con R Server e servizi di SQL Server Machine Learning. Per scaricarlo, vedere [R Tools per Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx).

- **Microsoft R Client** è uno strumento di sviluppo leggero che supporta lo sviluppo in R con i pacchetti ScaleR. Per ottenerlo, vedere [Introduzione a Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started).

- **RStudio** è uno degli ambienti più diffusi per lo sviluppo di R. Per altre informazioni, vedere [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/).

    Non è possibile completare questa esercitazione Usa un'installazione generica di RStudio o un altro ambiente; è inoltre necessario installare i pacchetti R e librerie di connettività per Microsoft R Open. Per altre informazioni, vedere [Configurare un client per l'analisi scientifica dei dati](../r/set-up-a-data-science-client.md).

- Strumenti di base di R (R.exe, RTerm.exe, RScripts.exe) vengono installati anche per impostazione predefinita, quando si installa [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]. Se non si desidera installare un IDE, è possibile utilizzare questi strumenti.

## <a name="get-permissions-on-the-sql-server-instance-and-database"></a>Ottenere le autorizzazioni per l'istanza di SQL Server e database

Per connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire gli script e caricare i dati, è necessario disporre di un account di accesso valido nel server di database.  È possibile usare un account di accesso SQL o un'autenticazione integrata di Windows. Chiedere all'amministratore di database per configurare le autorizzazioni seguenti per l'account, nel database in cui si usano r:

- Creare database, tabelle, funzioni e stored procedure
- Scrivere dati nelle tabelle
- Possibilità di eseguire script R (`GRANT EXECUTE ANY EXTERNAL SCRIPT to <user>`)

Questa procedura dettagliata, abbiamo utilizzato l'account di accesso SQL **RTestUser**. È consigliabile in genere si utilizza l'autenticazione integrata di Windows, ma utilizzando l'account di accesso SQL è più semplice per alcuni scopi dimostrativi.

## <a name="change-list"></a>Elenco delle modifiche

+ In questo esempio è stato sviluppato utilizzando SQL Server 2016 R Services. Tuttavia, modifiche di rilievo introdotte nei componenti di Microsoft R per 2016 SP1. In particolare, il _varsToDrop_ e _varsToKeep_ parametri non sono supportati per le origini dati di SQL Server. Therefre, se è stata scaricata una versione dell'esercitazione precedente a SP1, non funzionerà con le compilazioni a SP1.

+ La versione corrente dell'esempio è stata testata mediante una build di versione non definitiva di SQL Server 2017 Machine Learning Services (RC1 e RC2). In generale, quasi tutti i passaggi devono essere eseguite senza modifica tra 2016 SP1 e 2017.

## <a name="next-lesson"></a>Lezione successiva

[Preparare i dati di utilizzo di PowerShell](/walkthrough-prepare-the-data.md)
