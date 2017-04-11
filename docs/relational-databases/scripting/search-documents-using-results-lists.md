---
title: "Ricerca nei documenti utilizzando gli elenchi dei risultati | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ricerche [SQL Server Management Studio], elenchi di risultati"
  - "ricerche con elenchi di risultati [SQL Server Management Studio]"
  - "ricerche [SQL Server Management Studio], più file"
  - "Editor di query [SQL Server Management Studio], ricerca in più file"
ms.assetid: 275e1b6c-fbd0-4408-af77-35903f90657c
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Ricerca nei documenti utilizzando gli elenchi dei risultati
  Nella finestra di dialogo **Trova e sostituisci** è possibile eseguire ricerche e sostituzioni di testo in tutti i file di un progetto o di una soluzione o in una cartella di file system, anche se i file non sono aperti in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Le corrispondenze delle ricerche eseguite con la finestra di dialogo **Trova e sostituisci** vengono visualizzate nelle finestre Risultati ricerca 1 e Risultati ricerca 2, in cui è possibile vedere il testo esatto dalla riga contenente la corrispondenza.  
  
### Per eseguire la ricerca in più file  
  
1.  Scegliere **Trova e sostituisci** dal menu **Modifica** e fare clic su **Cerca nei file**.  
  
2.  Nella casella di testo **Trova** immettere il testo da cercare.  
  
3.  Nell'elenco **Cerca in** fare clic su **Tutti i documenti aperti**, **Progetto corrente**, **Intera soluzione** o digitare un percorso di directory.  
  
4.  Nell'elenco **Tipi di file** selezionare uno dei set di estensioni di file elencati o immettere le estensioni relative ai tipi di file su cui eseguire la ricerca separandole da un punto e virgola. Usare \*.\* per eseguire la ricerca in tutti i file della directory indicata nell'elenco a discesa **Cerca in**.  
  
5.  Selezionare altre opzioni di ricerca per definire ulteriormente la precisione della ricerca.  
  
6.  Fare clic su **Trova** per iniziare la ricerca.  
  
 Per impostazione predefinita, le corrispondenze della ricerca vengono riportate nella finestra Risultati ricerca 1. È possibile esplorare le corrispondenze della ricerca facendo doppio clic su ogni voce della finestra Risultati ricerca 1. Per visualizzare i risultati della ricerca in una nuova finestra, selezionare **Visualizza in Risultati ricerca 2**.  
  
#### Per eseguire sostituzioni in più file o cartelle  
  
1.  Scegliere **Trova e sostituisci** dal menu **Modifica** e fare clic su **Sostituisci nei file**.  
  
2.  Nella casella di testo **Trova** immettere il testo da cercare.  
  
3.  Nella casella di testo **Sostituisci con** immettere il testo con cui sostituire il testo trovato.  
  
4.  Nell'elenco **Cerca in** fare clic su **Tutti i documenti aperti**, **Progetto corrente**, **Intera soluzione** o digitare un percorso di directory.  
  
5.  Fare clic su **Sostituisci** per sostituire la corrispondenza di ricerca corrente con il testo contenuto nella casella **Sostituisci con**. Fare clic su **Trova successivo** per ignorare una corrispondenza e su **Ignora file** per ignorare un intero file.  
  
     \- - oppure -  
  
     Scegliere **Sostituisci tutto** per sostituire tutte le corrispondenze di ricerca con il testo contenuto nella casella **Sostituisci con**. Selezionare **Non chiudere i file modificati con Sostituisci tutto** se si vuole annullare alcune delle sostituzioni eseguite in un'altra sessione.  
  
    > [!NOTE]  
    >  **Sostituisci tutto** consente di sostituire tutte le corrispondenze di ricerca comprese quelle dei file ignorati con **Ignora file** o **Trova successivo**. È possibile usare **Annulla** solo per le sostituzioni eseguite nei file rimasti aperti dopo l'operazione di sostituzione.  
  
 Per impostazione predefinita, le informazioni di sostituzione vengono visualizzate nella finestra Risultati ricerca 1. È possibile esplorare le sostituzioni facendo doppio clic su ogni voce della finestra Risultati ricerca 1.  
  
## Vedere anche  
 [Ricerca e sostituzione](../../relational-databases/scripting/search-and-replace.md)   
 [Ricerca interattiva all'interno di documenti](../../relational-databases/scripting/search-documents-interactively.md)   
 [Testo di ricerca con caratteri jolly](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [Testo di ricerca con espressioni regolari](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  