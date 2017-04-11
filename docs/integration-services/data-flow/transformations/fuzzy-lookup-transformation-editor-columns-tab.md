---
title: "Editor trasformazione Ricerca fuzzy (scheda Colonne) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.fuzzylookuptransformation.columns.f1"
helpviewer_keywords: 
  - "Editor trasformazione Ricerca fuzzy"
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Editor trasformazione Ricerca fuzzy (scheda Colonne)
  Utilizzare la scheda **Colonne** della finestra di dialogo **Editor trasformazione Ricerca fuzzy** per impostare le proprietà delle colonne di input e output.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca fuzzy, vedere [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md).  
  
## Opzioni  
 **Colonne di input disponibili**  
 Trascinare le colonne di input per collegarle alle colonne di ricerca disponibili. Queste colonne devono disporre di tipi di dati supportati e corrispondenti. Selezionare una riga di mapping e fare clic con il pulsante destro del mouse per modificare i mapping nella finestra di dialogo [Crea relazioni](../../../integration-services/data-flow/transformations/create-relationships.md).  
  
 **Nome**  
 Consente di visualizzare i nomi delle colonne di input disponibili.  
  
 **Pass-through**  
 Consente di indicare l'inclusione delle colonne di input nell'output della trasformazione.  
  
 **Colonne di ricerca disponibili**  
 Utilizzare le caselle di controllo per selezionare le colonne su cui eseguire operazioni di ricerca fuzzy.  
  
 **Colonna di ricerca**  
 Selezionare le colonne di ricerca dall'elenco delle colonne della tabella di riferimento disponibili. Queste selezioni si rifletteranno nelle selezioni delle caselle di controllo nella tabella **Colonne di ricerca disponibili** . La selezione di una colonna nella tabella **Colonne di ricerca disponibili** comporta la creazione di una colonna di output contenente il valore della colonna della tabella di riferimento per ogni riga corrispondente restituita.  
  
 **Alias di output**  
 Consente di digitare un alias per l'output relativo a ogni colonna di ricerca. Per impostazione predefinita viene suggerito il nome della colonna di ricerca a cui è accodato un valore di indice numerico. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Ricerca fuzzy &#40;scheda Tabella di riferimento&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Editor trasformazione Ricerca fuzzy &#40;scheda Avanzate&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  