---
title: Omissione di valori per gli oggetti del servizio Web facoltativi | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8ce8a1662a57a4273e6449ecb94a410cd4dd798f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192811"
---
# <a name="omitting-values-for-optional-web-service-objects"></a>Omissione di valori per gli oggetti del servizio Web facoltativi
  Alle proprietà di diversi tipi complessi del servizio Web ReportServer è associata una proprietà nota come proprietà Specified. Il nome della proprietà è costituito dal nome della proprietà originale con l'aggiunta della parola "Specified". La presenza di questa proprietà indica che, a volte, è possibile omettere un valore per la proprietà originale. Si tratta di un risultato diretto della conversione da WSDL (Web Service Description Language) a una classe proxy [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Ad esempio, alla proprietà del servizio Web <xref:ReportService2010.DataSourceDefinition.Enabled%2A> del tipo complesso <xref:ReportService2010.DataSourceDefinition> è associata una proprietà denominata <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>. Se si compila un'applicazione e non si desidera impostare un valore per la proprietà <xref:ReportService2010.DataSourceDefinition.Enabled%2A>, non è necessario fornire un valore per <xref:ReportService2010.DataSourceDefinition.Enabled%2A>; verrà utilizzato il valore predefinito `true`. È tuttavia necessario impostare ancora <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> su `false`. Se si fornisce un valore per la proprietà <xref:ReportService2010.DataSourceDefinition.Enabled%2A>, è necessario impostare <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> su `true`. È il caso delle proprietà scrivibili. Per le proprietà di sola lettura, non è necessaria alcuna azione.  
  
> [!IMPORTANT]  
>  La mancata definizione di una proprietà con la tecnica indicata in precedenza può causare un comportamento imprevedibile del servizio Web.  
  
 I tipi di dati che generalmente richiedono la gestione della proprietà Specified aggiuntiva sono `Boolean`, `DateTime`, e `Enumeration`.  
  
 Per un esempio, vedere il metodo <xref:ReportService2010.ReportingService2010.CreateDataSource%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni tramite servizio Web e .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Guida di riferimento tecnico &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  
