---
title: I provider OLE DB (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 6e0488c3-934d-4976-99dc-65c580dc7a3c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b3f4f1d4efed51a8f9e3b5eaf3bd4a2c7f385e75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613809"
---
# <a name="ole-db-providers-ado"></a>Provider OLE DB (ADO)
OLE DB definisce un set di interfacce COM per offrire ad applicazioni con accesso uniforme ai dati archiviati in diverse origini di informazioni. Questo approccio consente a un'origine dati condividere i propri dati tramite le interfacce che supportano la quantità di funzionalità DBMS appropriato per l'origine dati. Per impostazione predefinita, l'architettura ad alte prestazioni di OLE DB è basata sul relativo uso di un modello di servizi basati su componenti e flessibile. Evitando che un numero predefinito di livelli intermedi tra l'applicazione e i dati, OLE DB richiede solo il numero di componenti necessari per completare un'attività particolare.  
  
 Ad esempio, si supponga che un utente desidera eseguire una query. Esaminare gli scenari seguenti:  
  
-   I dati si trovano in un database relazionale per il quale esiste attualmente esiste un driver ODBC, ma nessun provider OLE DB nativo: l'applicazione utilizza ADO per comunicare con il Provider OLE DB per ODBC, che carica quindi il driver ODBC appropriato. Il driver passa l'istruzione SQL per il sistema DBMS, che recupera i dati.  
  
-   I dati risiedono in Microsoft SQL Server per cui è disponibile un provider OLE DB nativo: l'applicazione utilizza ADO per comunicare direttamente con il Provider OLE DB per Microsoft SQL Server. Non sono necessari intermediari.  
  
-   I dati risiedono in Microsoft Exchange Server, per il quale non esiste un provider OLE DB, ma che non espone un motore di elaborazione delle query SQL: l'applicazione utilizza ADO per comunicare con il Provider OLE DB per Microsoft Exchange e si avvale di un processore di query di OLE DB componente per la gestione delle query.  
  
-   I dati si trovano nel file system NTFS Microsoft sotto forma di documenti: accesso ai dati tramite un provider OLE DB nativo su servizio di indicizzazione Microsoft, che indicizza il contenuto e le proprietà dei documenti nel file system per consentire a contenuti efficiente esegue la ricerca.  
  
 In tutti gli esempi precedenti, l'applicazione può eseguire una query dei dati. Con un numero minimo di componenti vengano soddisfatte le esigenze dell'utente. In ogni caso, i componenti aggiuntivi vengono utilizzati solo se necessario, e vengono richiamati solo i componenti necessari. Il caricamento su richiesta di componenti riutilizzabili e condivisibili favorisce notevolmente ad alte prestazioni quando si utilizza OLE DB.  
  
 I provider possono essere suddivise in due categorie: quelli che forniscono i dati e quelli che forniscono servizi. Un provider di dati possiede i propri dati e la espone in formato tabulare per l'applicazione. Un provider di servizi è incluso un servizio tramite producono e usano i dati, in modo da integrare le funzionalità nelle applicazioni ADO. Un provider di servizi possa anche essere definito come un componente del servizio, che deve funzionare in combinazione con altri provider di servizi o componenti.  
  
 ADO fornisce un coerente, interfaccia di livello superiore per i vari provider OLE DB.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Provider di dati](../../../ado/guide/data/data-providers.md)  
  
-   [Provider di servizi e componenti](../../../ado/guide/data/service-providers-and-components.md)
