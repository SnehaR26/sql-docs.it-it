---
title: "Passaggio 4: Aggiunta di un'attività Flusso di dati al pacchetto | Microsoft Docs"
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f42cdf02129bcd10b373f28e8a35544d3b9906a4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855829"
---
# <a name="lesson-1-4---adding-a-data-flow-task-to-the-package"></a>Lezione 1-4 - Aggiunta di un'attività Flusso di dati al pacchetto
Dopo aver creato le gestioni connessioni per i dati di origine e di destinazione, l'operazione successiva consiste nell'aggiunta di un'attività Flusso di dati al pacchetto. L'attività Flusso di dati incapsula il motore del flusso di dati che gestisce lo spostamento dei dati tra origini e destinazioni, offrendo funzionalità di trasformazione, pulitura e modifica dei dati durante lo spostamento. Nell'attività Flusso di dati avviene gran parte del lavoro di un processo ETL (Extract, Transform and Load).  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separa il flusso di dati dal flusso di controllo.  
  
### <a name="to-add-a-data-flow-task"></a>Per aggiungere un'attività Flusso di dati  
  
1.  Fare clic sulla scheda **Flusso di controllo** .  
  
2.  Nella **Casella degli strumenti SSIS**espandere **Preferiti**, quindi trascinare un' **Attività Flusso di dati** sulla superficie di progettazione della scheda **Flusso di controllo** .  
  
    > [!NOTE]  
    > Se la Casella degli strumenti SSIS non è disponibile, selezionare SSIS nel menu principale, quindi Casella degli strumenti SSIS per visualizzare la casella degli strumenti in questione.  
  
3.  Nella superficie di progettazione **Flusso di controllo** fare clic con il pulsante destro del mouse sull' **Attività Flusso di dati**appena aggiunta, fare clic su **Rinomina**e modificare il nome in **Extract Sample Currency Data**.  
  
    È consigliabile fornire nomi univoci a tutti i componenti aggiunti a una superficie di progettazione. Per facilità d'uso e manutenzione, i nomi dovrebbero descrivere la funzione svolta da ogni componente. Se vengono applicate queste linee guida per la denominazione, i pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] avranno un nome descrittivo. Come descrizione dei pacchetti è inoltre possibile utilizzare le annotazioni. Per altre informazioni sulle annotazioni, vedere [Utilizzo di annotazioni nei pacchetti](../integration-services/use-annotations-in-packages.md).  
  
4.  Fare clic con il pulsante destro del mouse sull'attività Flusso di dati, scegliere **Proprietà**e verificare che la proprietà **LocaleID** sia impostata su **Inglese (Stati Uniti)** nella finestra Proprietà.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 5: Aggiunta e configurazione dell'origine file flat](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a>Vedere anche  
[Attività Flusso di dati](../integration-services/control-flow/data-flow-task.md)  
  
  
  
