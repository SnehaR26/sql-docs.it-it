---
title: Esportare un report tramite l'accesso con URL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b90f1ad3e67aafa2ee8b967f8a04ddb16daf4e53
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132907"
---
# <a name="export-a-report-using-url-access"></a>Esportare un report tramite l'accesso con URL
  È facoltativamente possibile specificare il formato in cui eseguire il rendering di un report utilizzando il *rs: Format* parametro. Ad esempio per ottenere una copia PDF di un report direttamente da un server di report in modalità nativa:  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 Da un server di report in modalità integrata SharePoint:  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 I valori validi per questo parametro sono basati sulle estensioni per il rendering di report installate nel server di report a cui si sta effettuando l'accesso. Le estensioni comuni sono HTML4.0, MHTML, IMAGE, EXCEL, WORD, CSV, PDF, XML e NULL. Se un'estensione per il rendering specificata non è installata nel server di report, il rendering del report non viene eseguito e un errore viene generato e visualizzato nel browser.  
  
 Se non si include il parametro *Format* come parte dell'URL, il server di report rileva il browser ed esegue il rendering del report nel formato HTML appropriato.  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso con URL &#40;SSRS&#41;](url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](url-access-parameter-reference.md)  
  
  
