---
title: "Modificare una connessione all&#39;origine dati esistente (SSAS tabulare) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.selexistconn.f1"
ms.assetid: 97e63f18-a01d-4c91-a411-e7e6d40a0647
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# Modificare una connessione all&#39;origine dati esistente (SSAS tabulare)
  In questo argomento viene descritto come modificare le proprietà di una connessione all'origine dati esistente in un modello tabulare.  
  
 Dopo aver creato una connessione a un'origine dati esterna, è possibile modificarla in un secondo momento nei modi seguenti:  
  
-   È possibile modificare le informazioni di connessione, inclusi il file, il feed o il database utilizzato come origine, le rispettive proprietà o le altre opzioni di connessione specifiche del provider.  
  
-   È possibile modificare i mapping di colonne e tabelle e rimuovere i riferimenti alle colonne che non vengono più utilizzate.  
  
-   È possibile modificare le tabelle, le viste o le colonne ottenute dall'origine dati esterna.  
  
## Modificare una connessione  
 In questa procedura viene descritto come modificare una connessione all'origine dati di un database. Alcune opzioni per l'utilizzo delle origini dati differiscono in base al tipo di origine dati; tuttavia, si dovrebbe essere in grado di identificare facilmente tali differenze.  
  
#### Per modificare l'origine dati esterna utilizzata da una connessione corrente  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]scegliere **Connessioni esistenti** dal menu **Modello**.  
  
2.  Selezionare la connessione all'origine dati che si desidera modificare, quindi fare clic su **Modifica**.  
  
3.  Nella finestra di dialogo **Modifica connessione** fare clic su **Sfoglia** per individuare un altro database dello stesso tipo ma con un nome o un percorso diverso.  
  
     Appena si modifica il file di database, viene visualizzato un messaggio che indica la necessità di salvare e aggiornare le tabelle per visualizzare i nuovi dati.  
  
4.  Fare clic su **Salva**, quindi su **Chiudi**.  
  
5.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]fare clic su **Modello**, selezionare **Elabora**, quindi scegliere **Elabora tutto**.  
  
     Le tabelle vengono elaborate nuovamente utilizzando la nuova origine dati ma con le selezioni dei dati originali.  
  
    > [!NOTE]  
    >  Se nella nuova origine dati sono incluse le tabelle aggiuntive che non erano presenti nell'origine dati originale, è necessario aprire nuovamente la connessione modificata e aggiungere le tabelle.  
  
## Modificare i mapping (associazioni) di tabelle e colonne  
 In questa procedura viene descritto come modificare i mapping dopo avere modificato un'origine dati.  
  
#### Per modificare i mapping delle colonne quando viene modificata un'origine dati  
  
1.  In Progettazione modelli selezionare una tabella.  
  
2.  Fare clic sul menu **Tabella** , quindi scegliere **Proprietà tabella**.  
  
     Il nome della tabella selezionata viene visualizzato nella casella **Nome tabella** . Nella casella **Nome origine** è presente il nome della tabella dell'origine dati esterna. Se le colonne sono denominate in modo diverso nell'origine e nel modello, è possibile attivare alternativamente i due set di nomi di colonna selezionando le opzioni **Origine** o **Modello**.  
  
3.  Per modificare la tabella utilizzata come origine dati, per **Nome origine**selezionare una tabella diversa da quella corrente.  
  
4.  Modificare i mapping delle colonne, se necessario:  
  
    1.  Per aggiungere colonne che sono presenti nell'origine ma non nel modello, selezionare la casella di controllo accanto al nome della colonna.  
  
         I dati effettivi verranno caricati nel modello al successivo aggiornamento.  
  
    2.  Se alcune colonne nel modello non sono più disponibili nell'origine dati corrente, viene visualizzato un messaggio nell'area di notifica in cui sono elencate le colonne non valide. Non è necessario eseguire altre operazioni.  
  
5.  Fare clic su **Salva** per applicare le modifiche al modello.  
  
     Quando si salva il set corrente di proprietà della tabella, è possibile che venga visualizzato un messaggio che indica la necessità di elaborare le tabelle. Fare clic su **Elabora** per caricare dati aggiornati nel modello.  
  
## Vedere anche  
 [Elaborare dati &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/process-data-ssas-tabular.md)   
 [Origini dati supportate &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  