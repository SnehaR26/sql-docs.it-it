---
title: Formato di File di Output XML (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6644b8da77f8ebb6e4e8d6b6fc23ce5d9e356dd6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48070831"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Formato del file di output XML (ssbdiagnose)
  L'utilità **ssbdiagnose** restituisce un file di output in formato XML quando viene eseguita con l'opzione **-XML** . Nel file di output XML vengono elencate informazioni di intestazione e gli errori rilevati nella configurazione o nella conversazione di [!INCLUDE[ssSB](../../includes/sssb-md.md)] analizzata. È possibile scrivere un'applicazione per analizzare o generare un report relativo agli errori elencati nel file. In alternativa, è possibile visualizzare il file XML in un editor XML generico, ad esempio XML Notepad.  
  
 Un file di output di **ssbdiangose** contiene un elemento radice DiagnosticInformation con due tipi di figlio:  
  
-   Un elemento Banner con le informazioni di intestazione.  
  
-   Un elemento Issue per ogni problema segnalato da **ssbdiagnose**.  
  
## <a name="diagnosticinformation-root-element"></a>Elemento radice DiagnosticInformation  
  
-   [Elemento DiagnosticInformation &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Elemento Banner  
  
-   [Elemento banner &#40;ssbdiagnose&#41;](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Elemento Issue  
  
-   [Elemento Issue &#40;ssbdiagnose&#41;](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità ssbdiagnose &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  
