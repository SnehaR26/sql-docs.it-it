---
title: Union All Transformation | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.unionalltrans.f1
- sql13.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4b557efa62075f7b88e6b70cf5950546444b95d8
ms.openlocfilehash: e947aa8b3d079830b9433ba1b01450fda699904a
ms.contentlocale: it-it
ms.lasthandoff: 08/19/2017

---
# <a name="union-all-transformation"></a>Unione input multipli - trasformazione
  La trasformazione Unione input multipli consente di combinare più input in un unico output. È ad esempio possibile utilizzare gli output di cinque diverse origini file flat come input per la trasformazione Unione input multipli e combinarli in un singolo output.  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Gli input della trasformazione vengono aggiunti all'output della trasformazione uno dopo l'altro, senza riordinare le righe. Se il pacchetto richiede un output ordinato, sarà necessario utilizzare la trasformazione Unione anziché la trasformazione Unione input multipli.  
  
 L'output della trasformazione Unione input multipli viene creato a partire dal primo input connesso alla trasformazione. Sulle colonne negli input connessi successivamente alla trasformazione viene eseguito il mapping a quelle dell'output della trasformazione.  
  
 Per unire gli input è necessario eseguire il mapping delle relative colonne alle colonne nell'output. È necessario eseguire il mapping di almeno una colonna di input a ogni colonna di output. Il mapping tra due colonne può essere eseguito solo se i relativi metadati corrispondono. Le colonne sulle quali viene eseguito il mapping devono ad esempio avere lo stesso tipo di dati.  
  
 Se le colonne sulle quali viene eseguito il mapping contengono dati stringa e la lunghezza della colonna di output è inferiore a quella della colonna di input, la lunghezza della colonna di output verrà aumentata automaticamente in modo che possa contenere la colonna di input. Le colonne di input sulle quali non viene eseguito il mapping a colonne di output vengono impostate su valori Null nelle colonne di output.  
  
 Questa trasformazione include più input e un output. Non supporta un output degli errori.  
  
## <a name="configuration-of-the-union-all-transformation"></a>Configurazione della trasformazione Unione input multipli  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare a livello di codice, vedere [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796).  
  
 Per ulteriori informazioni sulle procedure per l'impostazione delle proprietà, fare clic su uno degli argomenti seguenti:  
  
-   [Impostare le proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## <a name="union-all-transformation-editor"></a>Editor trasformazione Unione input multipli
  Utilizzare la finestra di dialogo **Editor trasformazione Unione input multipli** per unire diversi set di righe di input in un unico set di righe di output. Includendo la trasformazione Unione input multipli in un flusso di dati è possibile unire dati tratti da più flussi di dati, creare set di dati complessi nidificando più trasformazioni Unione input multipli e unire nuovamente le righe dopo la correzione degli errori nei dati.  
  
### <a name="options"></a>Opzioni  
 **Nome colonna di output**  
 Consente di digitare un alias per ogni colonna. Per impostazione predefinita, viene suggerito il nome della colonna del primo input, ovvero l'input di riferimento. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Input unione input multipli 1**  
 Consente di selezionare nell'elenco di colonne di input disponibili nel primo input, ovvero l'input di riferimento. I metadati delle colonne mappate devono corrispondere.  
  
 **Input unione input multipli n**  
 Consente di selezionare nell'elenco di colonne di input disponibili nel secondo input e negli input aggiuntivi. I metadati delle colonne mappate devono corrispondere.  
  
## <a name="related-tasks"></a>Attività correlate  
 [Unione di dati tramite la trasformazione Unione input multipli](../../../integration-services/data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)  
  
  