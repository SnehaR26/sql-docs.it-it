---
title: 'Passaggio 2: Abilitazione e impostazione delle configurazioni dei pacchetti | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: be26ab7526d4ff270efc1ed11e592ad8552b0b22
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634769"
---
# <a name="lesson-5-2---enabling-and-configuring-package-configurations"></a>Lezione 5-2 - Abilitazione e impostazione delle configurazioni dei pacchetti
In questa attività si convertirà il progetto nel modello di distribuzione del pacchetto e si abiliteranno le configurazioni di pacchetto utilizzando la Configurazione guidata pacchetto. Questa procedura guidata consente di generare un file di configurazione XML contenente le impostazioni di configurazione per la proprietà **Directory** del contenitore Ciclo Foreach. Il valore della proprietà Directory è specificato da una variabile a livello di pacchetto che è possibile aggiornare in fase di esecuzione. Verrà inoltre popolata una cartella di dati di esempio da utilizzare durante il test.  
  
### <a name="to-create-a-new-package-level-variable-mapped-to-the-directory-property"></a>Per creare una nuova variabile a livello di pacchetto associata alla proprietà Directory  
  
1.  Fare clic sullo sfondo della scheda **Flusso di controllo** in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] . In questo modo viene impostato l'ambito del pacchetto per la variabile che verrà creata.  
  
2.  Scegliere [!INCLUDE[ssIS](../includes/ssis-md.md)] Variabili **dal menu**.  
  
3.  Nella finestra **Variabili** fare clic sull'icona Aggiungi variabile.  
  
4.  Nella casella **Nome** digitare **varFolderName**.  
  
    > [!IMPORTANT]  
    > Per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.  
  
5.  Verificare che in **Ambito** sia visualizzato il nome del pacchetto, Lesson 5.  
  
6.  Impostare su **String** il valore della casella `varFolderName` Tipo di dati **della variabile**.  
  
7.  Tornare alla scheda **Flusso di controllo** e fare doppio clic sul contenitore **Foreach File in Folder** .  
  
8.  Nella pagina **Raccolta** di **Editor ciclo Foreach**fare clic su **Espressioni**e quindi sul pulsante con i puntini di sospensione **(…)**.  
  
9. In **Editor espressioni di proprietà**fare clic nell'elenco **Proprietà** e selezionare **Directory**.  
  
10. Nella casella **Espressione** fare clic sul pulsante con i puntini di sospensione **(…)**.  
  
11. In **Generatore di espressioni**espandere la cartella Variabili e trascinare la variabile **User::varFolderName** nella casella **Espressione** .  
  
12. Fare clic su **OK** per chiudere **Generatore di espressioni**.  
  
13. Fare clic su **OK** per chiudere **Editor espressioni di proprietà**.  
  
14. Fare clic su **OK** per uscire da **Editor ciclo Foreach**.  
  
### <a name="to-enable-package-configurations"></a>Per abilitare le configurazioni dei pacchetti  
  
1.  Scegliere **Converti nel modello di distribuzione del pacchetto**dal menu **Progetto**.  
  
2.  Fare clic su **OK** nella richiesta di avviso e, una volta completata la conversione, scegliere **OK** nella finestra di dialogo **Converti nel modello di distribuzione del pacchetto** .  
  
3.  Fare clic sullo sfondo della scheda **Flusso di controllo** in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
4.  Scegliere **Configurazioni pacchetto** dal menu **SSIS**.  
  
5.  Nella finestra di dialogo **Libreria configurazioni pacchetto** selezionare **Abilita configurazioni pacchetto**e quindi fare clic su **Aggiungi**.  
  
6.  Nella pagina iniziale di Configurazione guidata pacchetto fare clic su **Avanti**.  
  
7.  Nella pagina **Selezione tipo di configurazione** verificare che l'opzione **Tipo configurazione** sia impostata su **File di configurazione XML**.  
  
8.  Nella pagina **Selezione tipo di configurazione** fare clic su **Sfoglia**.  
  
9. Per impostazione predefinita, nella finestra di dialogo **Selezionare il percorso del file di configurazione** verrà visualizzata la cartella del progetto.  
  
10. Nella finestra di dialogo **Selezionare il percorso del file di configurazione** digitare **SSISTutorial** nel campo **Nome file**e quindi fare clic su **Salva**.  
  
11. Nella pagina **Selezione tipo di configurazione** fare clic su **Avanti**.  
  
12. Nel riquadro **Oggetti** della pagina **Selezione proprietà da esportare** espandere **Variabili**, **varFolderName**, **Properties**e quindi selezionare **Value**.  
  
13. Nella pagina **Selezione proprietà da esportare** fare clic su **Avanti**.  
  
14. Nella pagina **Completamento procedura guidata** digitare un nome per la configurazione, ad esempio **SSIS Tutorial Directory configuration**. Si tratta del nome della configurazione visualizzato nella finestra di dialogo **Libreria configurazioni pacchetto** .  
  
15. Fare clic su **Fine**.  
  
16. Scegliere **Chiudi**.  
  
17. La procedura guidata consente di creare un file di configurazione denominato SSISTutorial.dtsConfig, che contiene le impostazioni di configurazione per il**valore** della variabile che imposta la proprietà **Directory** dell'enumeratore.  
  
    > [!NOTE]  
    > In un file di configurazione in genere sono incluse informazioni complesse sulle proprietà del pacchetto; tuttavia per questa esercitazione le uniche informazioni di configurazione saranno  
    > <Configuration ConfiguredType="Property"  
    > Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType\="String">  
    >  <ConfiguredValue>\<\/ConfiguredValue>  
    > \<\/Configuration>.  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a>Per creare e popolare una nuova cartella di dati di esempio  
  
1.  In Esplora risorse di Windows creare al livello di radice dell'unità disco (ad esempio C:\\) una nuova cartella denominata **New Sample Data**.  
  
2.  Individuare i file di esempio nel computer e copiare tre dei file nella cartella.  
  
3.  Incollare i file copiati nella cartella **New Sample Data** .  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 3: Modifica del valore di configurazione della proprietà Directory](../integration-services/lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
