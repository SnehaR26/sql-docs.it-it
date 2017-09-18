---
title: "Proprietà personalizzate ADO NET | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e062a9ab-1e6b-4061-845a-4f8a0552b09d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e16ce0117e36cfd15f8f1cde1bb8c7ce9ac2df55
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="ado-net-custom-properties"></a>Proprietà personalizzate ADO NET
  **Proprietà personalizzate delle origini**  
  
 L'origine ADO NET include sia proprietà personalizzate sia le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate dell'origine ADO.NET. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|CommandTimeout|String|Valore che specifica il numero di secondi di attesa prima che si verifichi il timeout del comando SQL. Il valore 0 indica che non è impostato alcun timeout del comando.|  
|SqlCommand|String|Istruzione SQL utilizzata dall'origine ADO.NET per l'estrazione dei dati.<br /><br /> Durante il caricamento del pacchetto, è possibile aggiornare dinamicamente la proprietà con l'istruzione SQL che verrà utilizzata dall'origine ADO.NET. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md) e [Utilizzo delle espressioni di proprietà nei pacchetti](../../integration-services/expressions/use-property-expressions-in-packages.md).|  
|AllowImplicitStringConversion|Boolean|Valore che indica se si verificano le condizioni seguenti:<br /><br /> - Nessuna generazione di un errore di convalida in caso di mancata corrispondenza tra i tipi di metadati esterni e i tipi stringa delle colonne di output (DT_WSTR o DT_NTEXT).<br /><br /> - Conversione implicita dei tipi di metadati esterni nel tipo di dati stringa usato dalla colonna di output.<br /><br /> <br /><br /> Il valore predefinito è TRUE.<br /><br /> Per altre informazioni, vedere [Origine ADO NET](../../integration-services/data-flow/ado-net-source.md).|  
  
 L'output e le colonne di output dell'origine ADO.NET non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Origine ADO NET](../../integration-services/data-flow/ado-net-source.md).  
  
 **Proprietà personalizzate delle destinazioni**  
  
 La destinazione [!INCLUDE[vstecado](../../includes/vstecado-md.md)] include sia proprietà personalizzate che le proprietà comuni a tutti i componenti flusso di dati.  
  
 La tabella seguente descrive le proprietà personalizzate della destinazione [!INCLUDE[vstecado](../../includes/vstecado-md.md)] . Tutte le proprietà sono di lettura/scrittura. Tali proprietà non sono disponibili in **Editor di destinazione ADO.NET**, ma possono essere impostate tramite **Editor avanzato**.  
  
|Proprietà|Tipo di dati|Description|  
|--------------|---------------|-----------------|  
|BatchSize|Valore intero|Numero di righe in un batch inviato al server. Il valore **0** indica che le dimensioni del batch corrispondono alle dimensioni del buffer interno. Il valore predefinito di questa proprietà è **0**.|  
|CommandTimeout|Valore intero|Numero massimo di secondi durante i quali è possibile eseguire il comando SQL prima del timeout. Il valore **0** corrisponde a un intervallo infinito. Il valore predefinito di questa proprietà è **0**.|  
|TableOrViewName|String|Nome della tabella o vista di destinazione.|  
  
 Per altre informazioni, vedere [Destinazione ADO NET](../../integration-services/data-flow/ado-net-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  