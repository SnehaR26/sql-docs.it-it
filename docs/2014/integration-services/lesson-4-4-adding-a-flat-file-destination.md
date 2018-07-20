---
title: 'Passaggio 4: Aggiunta di una destinazione file flat | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d30e1259da07f315b424747ad977917e8c68eb30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285476"
---
# <a name="step-4-adding-a-flat-file-destination"></a>Passaggio 4: Aggiunta di una destinazione file flat
  L'output degli errori della trasformazione Lookup Currency Key reindirizza alla trasformazione Script tutte le righe di dati in cui l'operazione di ricerca ha avuto esito negativo. Per migliorare le informazioni sugli errori, la trasformazione Script esegue uno script che ottiene la descrizione degli errori.  
  
 In questa attività, tutte queste informazioni sulle righe con esito negativo verranno salvate in un file delimitato per l'elaborazione in un momento successivo. Per salvare le righe con esito negativo, è necessario aggiungere e configurare una gestione connessione file flat per il file di testo che conterrà i dati degli errori e una destinazione file flat. Impostando le proprietà della gestione connessione file flat utilizzata dalla destinazione file flat è possibile specificare la modalità con cui la destinazione file flat deve formattare e scrivere il file di testo. Per altre informazioni, vedere [Gestione connessione file flat](connection-manager/file-connection-manager.md) e [Destinazione file flat](data-flow/flat-file-destination.md).  
  
### <a name="to-add-and-configure-a-flat-file-destination"></a>Per aggiungere e configurare una destinazione file flat  
  
1.  Fare clic sulla scheda **Flusso di dati** .  
  
2.  Nella **Casella degli strumenti SSIS**espandere **Altro**e trascinare **Destinazione file flat** sull'area di progettazione del flusso di dati. Posizionare la **Destinazione file flat** direttamente sotto la trasformazione **Get Error Description** (Ottieni descrizione errore).  
  
3.  Fare clic sulla trasformazione **Get Error Description** (Ottieni descrizione errore) e quindi trascinare la freccia verde sulla nuova **Destinazione file flat**.  
  
4.  Nell'area di progettazione **Flusso di dati** fare clic su **Destinazione file flat** nella trasformazione **Destinazione file flat** appena aggiunta e impostare il nome su **Righe con errori**.  
  
5.  Fare clic con il pulsante destro del mouse sulla trasformazione **Righe con errori** , scegliere **Modifica**e quindi in **Editor destinazione file flat**fare clic su **Nuovo**.  
  
6.  Nella finestra di dialogo **Formato file flat** verificare che sia stato selezionato **Delimitato** e quindi scegliere **OK**.  
  
7.  Nel **Editor gestione connessione File Flat**, nella **nome gestione connessione** nella casella `Error Data`.  
  
8.  Nella finestra di dialogo **Editor gestione connessione file flat** fare clic su **Sfoglia**e individuare la cartella in cui archiviare il file.  
  
9. Nel **aperto** della finestra di dialogo per **nome File**, tipo `ErrorOutput.txt`e quindi fare clic su **Open**.  
  
10. Nella finestra di dialogo **Editor gestione connessione file flat** verificare che nella casella **Impostazioni locali** sia presente Inglese (Stati Uniti) e che nella **Tabella codici** sia presente 1252 (ANSI -Latino I).  
  
11. Nel riquadro delle opzioni fare clic su **Colonne**.  
  
     Si noti che oltre alle colonne del file dei dati di origine sono presenti tre nuove colonne: ErrorCode, ErrorColumn e ErrorDescription. Queste colonne vengono generate dall'output degli errori della trasformazione Lookup Currency Key e dallo script nella trasformazione Get Error Description e possono essere utilizzate per la risoluzione dei problemi relativi alla riga con esito negativo.  
  
12. Fare clic su **OK**.  
  
13. In **Editor destinazione file flat**deselezionare la casella di controllo **Sovrascrivi dati nel file** .  
  
     La deselezione di questa casella di controllo mantiene gli errori per più esecuzioni del pacchetto.  
  
14. In **Editor destinazione file flat**fare clic su **Mapping** per verificare che tutte le colonne siano corrette. Facoltativamente è possibile rinominare le colonne nella destinazione.  
  
15. Fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 [Passaggio 5: Test del pacchetto creato nell'esercitazione della lezione 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  