---
title: Individuare testo, numeri o date in un report | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- searching reports
ms.assetid: 309dffe5-00f5-404f-bb63-9e6046253ae0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d17541a43178f7ebe5161904266087096844b680
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620989"
---
# <a name="find-text-numbers-or-dates-in-a-report"></a>Individuare testo, numeri o date in un report
  È possibile cercare contenuto in un report digitando la parola o la frase che si desidera trovare (la lunghezza massima di un termine di ricerca è 256 caratteri). La ricerca è una tecnica di navigazione in cui viene trovato un valore corrispondente a un criterio nel report e la selezione viene spostata sulla parte del report che contiene tale valore.  
  
 La ricerca viene eseguita senza distinzione tra maiuscole e minuscole a partire dall'inizio della pagina o della sezione attualmente selezionata. Viene incluso nella ricerca solo il contenuto visibile nel report. Se il report contiene aree che è possibile espandere o comprimere, durante la ricerca i valori che si trovano nell'area compressa verranno ignorati. È possibile ricercare solo testo, numeri o date presenti nel report corrente. Se per l'esplorazione dei dati si utilizza un report click-through generato automaticamente, non sarà possibile ricercare un termine individuato in un report generato in precedenza, né utilizzare la ricerca per individuare un termine che potrebbe trovarsi in un report a un livello inferiore nel percorso dei dati.  
  
 Il valore su cui si desidera basare la ricerca deve essere digitato esattamente come si prevede che compaia nel report. Non immettere domande, ad esempio "qual è il profitto medio per questo mese?", a meno che non si supponga che tutte le parole della frase siano presenti nel report.  
  
 È possibile ricercare un solo termine o valore alla volta. Non è possibile utilizzare operatori di ricerca (ad esempio OR o AND), né simboli o caratteri jolly. Non è possibile eseguire ricerche incrociate su uno specifico insieme di dati, ad esempio la ricerca delle vendite nette di un particolare prodotto per un mese specifico. Per eseguire analisi di questo tipo, creare o utilizzare report click-through tramite Generatore report.  
  
 Le impostazioni di sicurezza del modello e del database che limitano l'accesso ai dati del report vengono applicate anche alle operazioni di ricerca. Se si cerca un valore in un report click-through che utilizza un modello come origine dei dati, ma non si ha accesso a parte del modello, i dati corrispondenti a tale parte del modello verranno esclusi dalla ricerca.  
  
### <a name="to-find-data-in-a-report"></a>Per ricercare dati in un report  
  
1.  quindi aprirlo.  
  
2.  Sulla barra degli strumenti per i report immettere il testo, il numero o la data da trovare.  
  
     Se la barra degli strumenti per i report non è visualizzata, significa che è stata nascosta intenzionalmente e non è possibile utilizzarne le caratteristiche. La visibilità di tale barra degli strumenti è determinata dalle proprietà della web part Visualizzatore report.  
  
3.  Fare clic su **Trova**.  
  
4.  Per cercare le occorrenze successive dello stesso valore, fare clic su **Avanti**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere la Web part Visualizzatore report a una pagina Web &#40;Reporting Services in modalità integrata SharePoint&#41;](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)  
  
  
