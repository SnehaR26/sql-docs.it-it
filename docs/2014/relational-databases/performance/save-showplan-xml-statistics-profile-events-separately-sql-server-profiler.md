---
title: Salvare la classe di eventi Showplan XML Statistics Profile Events in file distinti (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: df393f13-d538-4d94-8155-9c2fdf5f755d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 511769ec59b62cef75ffde7f0226fe89b3970bc1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198291"
---
# <a name="save-showplan-xml-statistics-profile-events-separately-sql-server-profiler"></a>Salvataggio della classe di eventi Showplan XML Statistics Profile Events in file distinti (SQL Server Profiler)
  Questo argomento descrive la procedura da seguire per salvare gli eventi **Showplan XML Statistics Profile** acquisiti in tracce in file SQLPlan distinti tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. È possibile aprire i file di eventi **Showplan XML Statistics Profile** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]per visualizzare graficamente il piano di esecuzione di ogni evento.  
  
### <a name="to-save-showplan-xml-statistics-events-separately"></a>Per salvare eventi Showplan XML Statistics Profile in file distinti  
  
1.  Scegliere **Nuova traccia** dal menu **File**e quindi connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia** .  
  
    > [!NOTE]  
    >  Se l'opzione **Avvia traccia non appena viene stabilita una connessione**è selezionata, la finestra di dialogo **Proprietà traccia**non viene visualizzata e viene invece avviata la traccia. Per disabilitare questa impostazione, scegliere **Opzioni**dal menu **Strumenti**e deselezionare la casella di controllo **Avvia traccia non appena viene stabilita una connessione** .  
  
2.  Nella finestra di dialogo **Proprietà traccia** digitare un nome per la traccia nella casella **Nome traccia** .  
  
3.  Nell'elenco **Modello** selezionare un modello di traccia su cui basare la traccia oppure selezionare **Vuoto** se non si desidera utilizzare alcun modello.  
  
4.  Eseguire una delle operazioni seguenti:  
  
    -   Fare clic su**Salva nel file**per acquisire la traccia in un file. Specificare un valore per l'opzione **Dimensioni massime del file**.  
  
         Facoltativamente selezionare le caselle di controllo **Consenti rollover dei file** e **Dati di traccia elaborati dal server**.  
  
    -   Fare clic su**Salva nella tabella** per acquisire la traccia in una tabella del database.  
  
         Facoltativamente selezionare la casella di controllo **Numero massimo di righe**e specificare un valore.  
  
5.  Facoltativamente selezionare la casella di controllo **Data e ora di arresto della traccia** e specificare la data e l'ora di arresto desiderate.  
  
6.  Fare clic sulla scheda **Selezione eventi**.  
  
7.  Nella colonna di dati **Events**espandere la categoria di eventi **Performance**e quindi selezionare la casella di controllo **Showplan XML Statistics Profile**. Se la categoria di eventi **Performance** non è visualizzata, selezionare la casella di controllo **Mostra tutti gli eventi** .  
  
     La scheda **Impostazioni estrazione eventi**viene aggiunta alla finestra di dialogo **Proprietà traccia**.  
  
8.  Scegliere **Impostazioni estrazione event**selezionare la casella di controllo **Salva eventi Showplan XML separatamente**.  
  
9. Nella finestra di dialogo **Salva con nome** immettere un nome per il file in cui archiviare gli eventi **Showplan XML Statistics Profile** .  
  
10. Fare clic su **Tutti i batch in un singolo file** per salvare tutti gli eventi **Showplan XML Statistics Profile** in un unico file XML oppure fare clic su **Crea un file distinto per ogni singolo batch Showplan XML**per creare un nuovo file XML per ogni evento **Showplan XML Statistics Profile** .  
  
11. Per visualizzare il file di eventi **Showplan XML Statistics Profile** in SQL Server Management Studio, scegliere **Apri** dal menu **File**e quindi fare clic su **File**. Spostarsi sulla directory in cui è stato salvato il file o i file di eventi **Showplan XML Statistics Profile** , selezionare il file desiderato e quindi aprirlo. I file di eventi**Showplan XML Statistics Profile** sono contraddistinti dall'estensione SQLPlan.  
  
## <a name="see-also"></a>Vedere anche  
 [Analizzare query con risultati SHOWPLAN in SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
