---
title: Trasformazione multicast | Documenti Microsoft
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
- sql13.dts.designer.multicasttrans.f1
- sql13.dts.designer.multicasttransformation.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4b557efa62075f7b88e6b70cf5950546444b95d8
ms.openlocfilehash: bd3eee42fbb204a9ca1e806d273b7c09a86c87d2
ms.contentlocale: it-it
ms.lasthandoff: 08/19/2017

---
# <a name="multicast-transformation"></a>Multicast - trasformazione
  La trasformazione Multicast distribuisce il proprio input a uno o più output. Questa trasformazione è simile alla trasformazione Suddivisione condizionale. Entrambe le trasformazioni dirigono uno stesso input verso più output, ma la trasformazione Multicast dirige tutte le righe verso tutti gli output, mentre la trasformazione Suddivisione condizionale dirige una riga a un singolo output. Per altre informazioni, vedere [Trasformazione Suddivisione condizionale](../../../integration-services/data-flow/transformations/conditional-split-transformation.md).  
  
 Per configurare la trasformazione Multicast, è necessario aggiungere gli output.  
  
 Tramite la trasformazione Multicast un pacchetto può creare copie logiche dei dati. Questa funzionalità è utile quando il pacchetto deve applicare più set di trasformazioni agli stessi dati. È ad esempio possibile aggregare una copia dei dati e caricare nella relativa destinazione solo le informazioni di riepilogo, mentre un'altra copia dei dati viene estesa con valori di ricerca e colonne derivate prima di caricarla nella relativa destinazione.  
  
 Questa trasformazione include un input e più output. Non supporta un output degli errori.  
  
## <a name="configuration-of-the-multicast-transformation"></a>Configurazione della trasformazione Multicast  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per informazioni sulle proprietà che è possibile impostare a livello di codice, vedere [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796).  
  
## <a name="related-tasks"></a>Attività correlate  
 Per informazioni su come impostare le proprietà del componente, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="multicast-transformation-editor"></a>Editor trasformazione Multicast
  Utilizzare la finestra di dialogo **Editor trasformazione Multicast** per visualizzare e impostare le proprietà per ogni output della trasformazione.  
  
### <a name="options"></a>Opzioni  
 **Output**  
 Selezionare un output a sinistra per visualizzare le proprietà corrispondenti nella tabella a destra.  
  
 **Proprietà**  
 Tutte le proprietà di output elencate sono di sola lettura, ad eccezione di **Nome** e **Descrizione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Flusso di dati](../../../integration-services/data-flow/data-flow.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  