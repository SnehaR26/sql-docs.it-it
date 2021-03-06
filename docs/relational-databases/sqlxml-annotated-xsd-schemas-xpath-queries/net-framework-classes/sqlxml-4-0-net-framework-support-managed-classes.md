---
title: Classi gestite SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b59a1f31f1dbf9e9ebb185b2ad0bb84ef66e52cc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617969"
---
# <a name="sqlxml-40-net-framework-support---managed-classes"></a>Supporto SQLXML 4.0 per .NET Framework - Classi gestite
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 supporta caratteristiche che consentono di scrivere applicazioni per accedere a dati XML da un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], trasferire i dati nell'ambiente [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, elaborare i dati e inviare gli aggiornamenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. 
  
  Le classi gestite [!INCLUDE[msCoName](../../../includes/msconame-md.md)] espongono la funzionalità di SQLXML 4.0 in [!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET Framework. Le classi gestite SQLXML consentono di scrivere un'applicazione C# per accedere ai dati XML da un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], portare i dati nell'ambiente .NET Framework, elaborare i dati e inviare nuovamente gli aggiornamenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come DiffGram per applicarli. Quando si applicano aggiornamenti a un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando le classi gestite SQLXML, è necessario utilizzare uno schema di mapping. Per un esempio funzionante, vedere [l'accesso a funzionalità SQLXML nell'ambiente .NET](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Per utilizzare le classi gestite SQLXML con SQLXML 4.0, è necessario installare Microsoft Visual Studio.  
  
> [!NOTE]  
>  .NET Framework include il provider di dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET. Tale provider può essere utilizzato per accedere a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dall'ambiente .NET. È tuttavia in grado di gestire solo query SQL tradizionali (ovvero query del database relazionale ad eccezione delle query FOR XML). Non è possibile eseguire modelli XML o query XPath sul lato server in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  

 Per informazioni sull'accesso e modifica dei dati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] all'interno di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework e sull'utilizzo di DiffGram per aggiornare i dati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabelle, vedere [l'accesso a funzionalità SQLXML nell'ambiente .NET](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
> [!NOTE]  
>  È anche possibile scrivere applicazioni [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio per eseguire il caricamento bulk di documenti XML utilizzando il caricamento bulk XML. Per altre informazioni, vedere [esecuzione di caricamento Bulk di dati di XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md). È necessario aggiungere all'applicazione un riferimento alla DLL del caricamento bulk XML (Xblkld4.dll). Si tratta di una DLL COM per la quale in Visual Studio .NET viene creata automaticamente la libreria di wrapper.  
  
  Questa sezione vengono fornite applicazioni di esempio che illustrano come usare il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] classi gestite SQLXML:  
 [Esecuzione di query SQL &#40;classi gestite SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md)  
  [Esecuzione di query SQL tramite il metodo ExecuteXMLReader](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [L'elaborazione di XML sul lato Client &#40;classi gestite SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [Esecuzione di query XPath &#40;classi gestite SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [Esecuzione di query XPath con spazi dei nomi &#40;classi gestite SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [Esecuzione di file modello con la proprietà CommandText](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [Esecuzione di file modello tramite la proprietà CommandStream](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [Applicare una trasformazione XSL &#40;classi gestite SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  

  
  
