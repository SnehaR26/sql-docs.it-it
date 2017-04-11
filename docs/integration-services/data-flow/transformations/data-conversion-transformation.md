---
title: "Trasformazione Conversione dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dataconversiontrans.f1"
helpviewer_keywords: 
  - "conversione di tipi di dati [Integration Services]"
  - "Conversione dati - trasformazione"
  - "tipo di dati [Integration Services], conversione"
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
caps.latest.revision: 53
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 53
---
# Trasformazione Conversione dati
  La trasformazione Conversione dati converte i dati in una colonna di input in un tipo di dati diverso e quindi li copia in una nuova colonna di output. Un pacchetto può ad esempio estrarre dati da più origini e quindi utilizzare questa trasformazione per convertire le colonne nel tipo di dati richiesto dall'archivio dati di destinazione. È possibile applicare più conversioni a una singola colonna di input.  
  
 Tramite questa trasformazione un pacchetto può eseguire i tipi di conversioni dei dati seguenti:  
  
-   Modifica del tipo di dati. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../../integration-services/data-flow/integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Se i dati da convertire hanno tipo di dati date o datetime, per la data nella colonna di output verrà utilizzato il formato ISO anche se le impostazioni locali specificano un formato diverso.  
  
-   Impostazione della lunghezza di colonna dei dati stringa, nonché della scala e della precisione dei dati numerici. Per altre informazioni, vedere [Precisione, scala e lunghezza &#40;Transact-SQL&#41;](../../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
-   Impostazione di una tabella codici. Per altre informazioni, vedere [Comparing String Data](../../../integration-services/data-flow/comparing-string-data.md).  
  
    > [!NOTE]  
    >  È possibile copiare dati tra colonne con un tipo di dati string solo se le due colonne utilizzano la stessa tabella codici.  
  
 Se la lunghezza di una colonna di output con dati di tipo string è minore di quella della colonna di input corrispondente, i dati di output verranno troncati. Per altre informazioni, vedere [Gestione degli errori nei dati](../../../integration-services/data-flow/error-handling-in-data.md).  
  
 Questa trasformazione include un input, un output e un output degli errori.  
  
## Attività correlate  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice. Per informazioni sull'utilizzo della trasformazione Conversione dati in Progettazione SSIS, vedere [Conversione di dati in un tipo di dati diverso utilizzando la trasformazione Conversione dati](../../../integration-services/data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md) e [Editor trasformazione Conversione dati](../../../integration-services/data-flow/transformations/data-conversion-transformation-editor.md). Per informazioni sull'impostazione delle proprietà di questa trasformazione a livello di programmazione, vedere [Proprietà comuni](../Topic/Common%20Properties.md) e [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
## Contenuto correlato  
 Intervento nel blog sul [confronto delle prestazioni tra le tecniche di conversione dei tipi di dati in SSIS 2008](http://go.microsoft.com/fwlink/?LinkId=220823)su blogs.msdn.com.  
  
## Vedere anche  
 [Analisi veloce](../Topic/Fast%20Parse.md)   
 [Flusso di dati](../../../integration-services/data-flow/data-flow.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  