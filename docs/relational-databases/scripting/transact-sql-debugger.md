---
title: Debugger Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, introduction
ms.assetid: 6e914699-0d85-46c2-aa2d-3e339ac2c4ce
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1aad3ad463e5addab11e77a829ec0377e6cc75c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836759"
---
# <a name="transact-sql-debugger"></a>Debugger Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] consente di individuare errori nel codice [!INCLUDE[tsql](../../includes/tsql-md.md)] esaminandone il comportamento in fase di esecuzione. Dopo avere impostato la finestra dell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] sulla modalità di debug, è possibile sospendere l'esecuzione di righe specifiche di codice e controllare le informazioni e i dati utilizzati o restituiti da tali istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
## <a name="stepping-through-transact-sql-code"></a>Esecuzione istruzione per istruzione del codice Transact-SQL  
 Il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] fornisce le seguenti opzioni che è possibile usare per spostarsi nel codice di [!INCLUDE[tsql](../../includes/tsql-md.md)] quando la finestra dell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] è in modalità di debug:  
  
-   Impostare i punti di interruzione su singole istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
     Un punto di interruzione specifica un punto in cui si desidera interrompere l'esecuzione per esaminare i dati. Quando viene avviato, il debugger sospende l'esecuzione in corrispondenza della prima riga di codice nella finestra dell'editor di query. Per proseguire l'esecuzione fino al primo punto di interruzione impostato, è possibile usare la funzionalità **Continua** . La funzionalità **Continua** può essere usata anche per procedere al successivo punto di interruzione da qualsiasi posizione in cui è stata attualmente messa in pausa la finestra. È possibile modificare i punti di interruzione per specificare alcune azioni, ad esempio le condizioni in base alle quali il punto deve interrompere l'esecuzione, le informazioni da visualizzare nella finestra di **output** e la modifica della posizione del punto di interruzione.  
  
-   Eseguire la successiva istruzione.  
  
     Questa opzione consente di spostarsi da un'istruzione alla successiva in un set di istruzioni e di osservare il comportamento di ognuna.  
  
-   Eseguire una chiamata o passare alla successiva chiamata a una stored procedure o una funzione.  
  
     Se si è sicuri che in una stored procedure non vi siano errori, è possibile superarla. La procedura viene eseguita completamente e i risultati vengono restituiti al codice.  
  
     Se si desidera eseguire il debug di una stored procedure o una funzione, è possibile eseguirlo nel modulo. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] apre una nuova finestra dell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] popolata con il codice sorgente per il modulo, imposta la finestra in modalità di debug, quindi sospende l'esecuzione della prima istruzione nel modulo. È possibile spostarsi quindi attraverso il codice del modulo, ad esempio, impostando dei punti di interruzione o avanzando nel codice.  
  
 Per altre informazioni sulle modalità con cui il debugger consente di spostarsi nel codice, vedere [Esecuzione istruzione per istruzione del codice Transact-SQL](../../relational-databases/scripting/step-through-transact-sql-code.md).  
  
## <a name="viewing-debugger-information"></a>Visualizzazione delle informazioni del debugger  
 Ogni volta che il debugger sospende l'esecuzione in corrispondenza di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] specifica, è possibile utilizzare le seguenti finestre del debugger per visualizzare lo stato corrente dell'esecuzione:  
  
-   **Variabili locali** ed **Espressione di controllo** In queste finestre vengono visualizzate le espressioni [!INCLUDE[tsql](../../includes/tsql-md.md)] attualmente allocate. Le espressioni sono clausole [!INCLUDE[tsql](../../includes/tsql-md.md)] che restituiscono una singola espressione scalare. Il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] supporta la visualizzazione di espressioni che fanno riferimento a variabili, parametri oppure alle funzioni predefinite [!INCLUDE[tsql](../../includes/tsql-md.md)] i cui nomi iniziano con @@. In queste finestre vengono inoltre visualizzati i valori dei dati che sono attualmente assegnati alle espressioni.  
  
-   **Controllo immediato.** Questa finestra visualizza il valore di un'espressione [!INCLUDE[tsql](../../includes/tsql-md.md)] e consente di salvare l'espressione in una finestra **Espressione di controllo** .  
  
-   **Punti di interruzione.** In questa finestra vengono visualizzati i punti di interruzione attualmente impostati ed è possibile gestirli.  
  
-   **Stack di chiamate.** In questa finestra viene visualizzato il percorso di esecuzione corrente. Questa finestra fornisce inoltre informazioni sul modo in cui l'esecuzione è passata dalla finestra dell'editor di query originale attraverso qualsiasi funzione, stored procedure o trigger per raggiungere il percorso di esecuzione corrente.  
  
-   **Output.** In questa finestra vengono visualizzati i vari messaggi e dati del programma, ad esempio i messaggi di sistema inviati dal debugger.  
  
-   **Risultati** ed **Messaggi** In queste schede della finestra dell'editor di query vengono visualizzati i risultati delle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] precedentemente eseguite.  
  
## <a name="transact-sql-debugger-tasks"></a>Attività del debugger Transact-SQL  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Descrive come configurare il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] per il debugging remoto.|[Configurare le regole del firewall prima di eseguire il debugger TSQL](../../relational-databases/scripting/configure-firewall-rules-before-running-the-tsql-debugger.md)|  
|Descrive come avviare, arrestare e controllare l'operazione del debugger.|[Esecuzione del debugger Transact-SQL](../../relational-databases/scripting/run-the-transact-sql-debugger.md)|  
|Descrive come utilizzare il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] per avanzare nel codice.|[Esecuzione istruzione per istruzione del codice Transact-SQL](../../relational-databases/scripting/step-through-transact-sql-code.md)|  
|Descrive come utilizzare il debugger per visualizzare dati [!INCLUDE[tsql](../../includes/tsql-md.md)] , ad esempio parametri e variabili, e informazioni sul sistema.|[Informazioni del debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Editor di query e di testo &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
