---
title: 'Passaggio 2: Aggiunta e configurazione della registrazione | Documenti Microsoft'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 56105f3f-e500-4669-8c8e-acf434527727
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 37702c62d20217d11785351b69252e08f03c0985
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-3-2---adding-and-configuring-logging"></a>Lezione 3-2: aggiunta e configurazione della registrazione
In questa attività verrà abilitata la registrazione per il flusso di dati del pacchetto Lesson 3.dtsx. Successivamente un provider di log per file di testo verrà configurato in modo da registrare gli eventi PipelineExecutionPlan e PipelineExecuteTrees. Il provider di log per file di testo crea log facili da visualizzare e da spostare. La semplicità di questi file di log li rende particolarmente utili nella fase di test di base di un pacchetto. Le voci di log possono essere visualizzate anche nella finestra Registra eventi di Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
### <a name="to-add-logging-to-the-package"></a>Per aggiungere le funzionalità di registrazione al pacchetto  
  
1.  Scegliere **Registrazione** dal menu **SSIS**.  
  
2.  Nel riquadro **Contenitori** della finestra di dialogo **Configura log SSIS** verificare che sia selezionato l'oggetto in prima posizione, che rappresenta il pacchetto della lezione 3.  
  
3.  Nella casella **Tipo provider** della scheda **Provider e log** selezionare **Provider di log SSIS per file di testo**e quindi fare clic su **Aggiungi**.  
  
    Integration Services consente di aggiungere un nuovo provider di log per file di testo al pacchetto con il nome predefinito **Provider di log SSIS per file di testo**. È ora possibile configurare il nuovo provider di log.  
  
4.  Nella colonna **Nome** digitare **Lesson 3 Log File**.  
  
5.  Facoltativamente, modificare la **Descrizione**.  
  
6.  Nella colonna **Configurazione** fare clic su **<New Connection>** per specificare la destinazione nella quale verranno scritte le informazioni sulla registrazione.  
  
    Nella finestra di dialogo **Editor gestione connessione file** per **Tipo di utilizzo**selezionare **Crea file**e quindi fare clic su **Sfoglia**. Per impostazione predefinita, la finestra di dialogo **Seleziona file** apre la cartella di progetto; tuttavia è possibile salvare le informazioni sulla registrazione in qualsiasi posizione.  
  
7.  Nella casella **Nome file** della finestra di dialogo **Seleziona file** digitare **TutorialLog.log**e quindi fare clic su **Apri**.  
  
8.  Fare clic su **OK** per chiudere la finestra di dialogo **Editor gestione connessione file** .  
  
9. Nel riquadro **Contenitori** espandere tutti i nodi della gerarchia del contenitore del pacchetto e quindi deselezionare tutte le caselle di controllo, compresa **Extract Sample Currency Data** . Selezionare quindi la casella di controllo **Extract Sample Currency Data** per ottenere solo gli eventi relativi a tale nodo.  
  
    > [!IMPORTANT]  
    > Se la casella di controllo **Extract Sample Currency Data** risulta non disponibile anziché selezionata, l'attività usa le impostazioni log del contenitore padre e non è possibile attivare gli eventi specifici dell'attività.  
  
10. Nella colonna **Eventi** della scheda **Dettagli** selezionare gli eventi **PipelineExecutionPlan** e **PipelineExecutionTrees** .  
  
11. Fare clic su **Avanzate** per controllare i dettagli che verranno scritti nel log per ogni evento. Per impostazione predefinita, tutte le categorie delle informazioni vengono automaticamente selezionate per gli eventi specificati.  
  
12. Fare clic su **Standard** per nascondere le categorie delle informazioni.  
  
13. Nella colonna **Nome** della scheda **Provider e log** selezionare **Lesson 3 Log File**. Dopo aver creato un provider di log per il pacchetto, è possibile disabilitare temporaneamente la registrazione senza la necessità di eliminarlo e ricrearlo.  
  
14. Scegliere **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
[Passaggio 3: Test del pacchetto creato nella lezione 3 dell'esercitazione](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
