---
title: Programmazione di SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, about SQL Server Native Client
- SQL Server Native Client, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
- data access [SQL Server Native Client]
- SQL Server Native Client
- SQLNCLI
- native data access [SQL Server Native Client]
ms.assetid: 14ba2cb1-a424-4e4d-b224-0bf1015ab801
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6b5b8e1f8d3c27552033b014347108ebbedba75e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708589"
---
# <a name="sql-server-native-client-programming"></a>Programmazione in SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client è un'API (Application Programming Interface) di accesso ai dati autonoma utilizzata sia in OLE DB sia in ODBC, introdotta in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client combina il provider OLE DB per SQL Server e il driver ODBC per SQL Server in una sola DLL (libreria di collegamento dinamico) nativa. Fornisce inoltre nuove funzionalità che estendono quelle fornite da Windows Data Access Components (Windows DAC, applicazione livello dati, precedentemente noto come Microsoft Data Access Components o MDAC). È possibile utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client per creare nuove applicazioni o per migliorare applicazioni esistenti al fine di sfruttare le nuove caratteristiche di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ad esempio MARS (Multiple Active Result Set), tipi di dati definiti dall'utente (UDT), notifica delle query, isolamento dello snapshot e supporto del tipo di dati XML.  
  
> [!NOTE]  
>  Per un elenco delle differenze tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client e Windows DAC, oltre a informazioni sui problemi da considerare prima di aggiornare un'applicazione Windows DAC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, vedere [aggiornamento di un'applicazione a SQL Server Native Client da MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
 Il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client viene sempre utilizzato in combinazione con Gestione driver ODBC fornito con Windows DAC (applicazione livello dati). Il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client può essere utilizzato con i servizi principali OLE DB forniti con Windows DAC (applicazione livello dati), ma non si tratta di un requisito obbligatorio. La scelta di utilizzare o meno i servizi di base dipende dai requisiti dell'applicazione specifica (ad esempio se è richiesto il pool di connessioni).  
  
 Le applicazioni dati oggetto ADO (ActiveX) possono usare la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client, ma è consigliabile utilizzare ADO in combinazione con il **DataTypeCompatibility** (parola chiave di stringa di connessione o relativo corrispondente **DataSource** proprietà). Quando si utilizza il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, le applicazioni ADO possono sfruttare le nuove caratteristiche introdotte in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] disponibili tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client attraverso le parole chiave delle stringhe di connessione o le proprietà OLE DB o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per altre informazioni sull'uso di queste caratteristiche con ADO, vedere [utilizzo di ADO con SQL Server Native Client](../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client è stato progettato come metodo semplificato per ottenere l'accesso ai dati nativo in SQL Server tramite OLE DB o ODBC. La semplicità è data dalla combinazione delle tecnologie OLE DB e ODBC in un'unica libreria e dalla possibilità di sviluppare nuove caratteristiche di accesso ai dati, elaborate senza modificare i componenti Windows DAC (applicazione livello dati) esistenti, facenti ora parte della piattaforma Microsoft Windows.  
  
 Benché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utilizzi componenti di Windows DAC (applicazione livello dati), non dipende in modo esplicito da una determinata versione di Windows DAC. È possibile utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client con la versione di Windows DAC (applicazione livello dati) installata con qualsiasi sistema operativo supportato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [SQL Server Native Client](../../relational-databases/native-client/sql-server-native-client.md)  
 Vengono elencate le nuove importanti funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [Quando usare SQL Server Native Client](../../relational-databases/native-client/when-to-use-sql-server-native-client.md)  
 Viene illustrato in che modo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client si integra con le tecnologie di accesso ai dati di Microsoft, viene presentato un confronto con Windows DAC (applicazione livello dati) e ADO.NET e vengono fornite informazioni utili per decidere quale tecnologia di accesso ai dati utilizzare.  
  
 [Funzionalità di SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
 Vengono descritte le caratteristiche supportate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [Compilazione di applicazioni con SQL Server Native Client](../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
 Viene presentata una panoramica dello sviluppo con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, incluse le differenze rispetto a Windows DAC (applicazione livello dati), i componenti utilizzati e la modalità di utilizzo di ADO con questo prodotto.  
  
 Vengono inoltre illustrate le operazioni di installazione e di distribuzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, inclusa la modalità di ridistribuzione della libreria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [Requisiti di sistema per SQL Server Native Client](../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
 Vengono presentate le risorse di sistema necessarie per utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
 Vengono fornite informazioni sull'utilizzo del provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
 Vengono fornite informazioni sull'utilizzo del driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [Ricerca di altre informazioni su SQL Server Native Client](../../relational-databases/native-client/finding-more-sql-server-native-client-information.md)  
 Vengono fornite risorse aggiuntive su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, tra cui collegamenti a risorse esterne e istruzioni per ottenere assistenza.  
  
 [Errori di SQL Server Native Client](http://msdn.microsoft.com/library/ebd0e9a8-5fe5-4b15-9a44-2f131a13c186)  
 Contiene argomenti sugli errori di runtime associati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiornamento di un'applicazione da SQL Server 2005 Native Client](../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md)   
 [Procedure relative a ODBC](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Procedure relative a OLE DB](../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
