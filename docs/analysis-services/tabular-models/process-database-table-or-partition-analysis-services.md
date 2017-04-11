---
title: "Elaborare database, tabelle o partizioni (Analysis Services) | Microsoft Docs"
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
  - "sql13.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1"
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 8
---
# Elaborare database, tabelle o partizioni (Analysis Services)
  Le attività di questo argomento descrivono come elaborare manualmente un database modello tabulare, una tabella o partizioni usando la finestra di dialogo **Elabora \<oggetto>** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Per altre informazioni sull'elaborazione di modelli tabulari, vedere [Elaborare dati &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/process-data-ssas-tabular.md).  
  
##  <a name="bkmk_process_tasks"></a> Attività  
  
###  <a name="bkmk_process_db"></a> Per elaborare un database  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fare clic con il pulsante destro del mouse sul database che si desidera elaborare, quindi scegliere **Elabora database**.  
  
2.  Nella finestra di dialogo **Elabora database** selezionare nella casella di riepilogo **Modalità** una delle modalità di elaborazione seguenti:  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Elaborazione predefinita**|Rileva lo stato di elaborazione degli oggetti di database e di eseguire l'elaborazione necessaria per restituire oggetti non elaborati o elaborati parzialmente in uno stato di elaborazione completa. Vengono caricati i dati per le tabelle vuote e le partizioni; vengono compilate o ricompilate (ricalcolate) le gerarchie, le colonne calcolate e le relazioni.|  
    |**Elaborazione completa**|Elabora un database e tutti gli oggetti in esso contenuti. Quando viene eseguita l'elaborazione completa per un oggetto che è stato già elaborato, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vengono eliminati tutti i dati dell'oggetto, quindi quest'ultimo viene elaborato. Questo tipo di elaborazione è necessario quando è stata apportata una modifica strutturale a un oggetto. Questa opzione richiede maggiori risorse.|  
    |**Elaborazione pulizia**|Rimuove tutti i dati da gli oggetti di database.|  
    |**Elabora ricalcolo**|Aggiorna e ricalcola gerarchie, relazioni e colonne calcolate.|  
  
3.  Nella colonna della casella di controllo **Elabora** selezionare le partizioni che si desidera elaborare con la modalità scelta, quindi fare clic su **OK**.  
  
###  <a name="bkmk_process_table"></a> Per elaborare una tabella  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], nel database modello tabulare contenente la tabella che si desidera elaborare, espandere il nodo **Tabelle**, quindi fare clic con il pulsante destro del mouse sulla tabella da elaborare e scegliere **Elabora tabella**.  
  
2.  Nella finestra di dialogo **Elabora tabella** selezionare nella casella di riepilogo **Modalità** una delle modalità di elaborazione seguenti:  
  
    |Modalità|Description|  
    |----------|-----------------|  
    |**Elaborazione predefinita**|Rilevare lo stato di elaborazione di un oggetto tabella ed esegue l'elaborazione necessaria per restituire oggetti non elaborati o elaborati parzialmente in uno stato di elaborazione completa. Vengono caricati i dati per le tabelle vuote e le partizioni; vengono compilate o ricompilate (ricalcolate) le gerarchie, le colonne calcolate e le relazioni.|  
    |**Elaborazione completa**|Elabora un oggetto tabella e tutti gli oggetti in esso contenuti. Quando viene eseguita l'elaborazione completa per un oggetto che è stato già elaborato, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vengono eliminati tutti i dati dell'oggetto, quindi quest'ultimo viene elaborato. Questo tipo di elaborazione è necessario quando è stata apportata una modifica strutturale a un oggetto. Questa opzione richiede maggiori risorse.|  
    |**Elaborare dati**|Carica i dati in una tabella senza ricompilare le gerarchie o le relazioni oppure ricalcolare le colonne calcolate e le misure.|  
    |**Elaborazione pulizia**|Rimuove tutti i dati da una tabella e qualsiasi partizione della tabella.|  
    |**Elabora deframmentazione**|Deframmenta gli indici di tabelle ausiliari.|  
  
3.  Nella colonna della casella di controllo della tabella verificare la tabella ed eventualmente selezionare tabelle aggiuntive che si desidera elaborare, quindi fare clic su **OK**.  
  
###  <a name="bkmk_process_partition"></a> Per elaborare una o più partizioni  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fare clic con il pulsante destro del mouse sulla tabella contenente le partizioni che si desidera elaborare, quindi scegliere **Partizioni**.  
  
2.  Nella finestra di dialogo **Partizioni** fare clic sul pulsante Elabora in **Partizioni**.  
  
3.  Nella casella di riepilogo **Modalità** della finestra di dialogo **Elabora partizione** selezionare una delle modalità di elaborazione seguenti:  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Elaborazione predefinita**|Rileva lo stato di elaborazione di un oggetto partizione ed esegue l'elaborazione necessaria per recapitare oggetti partizione non elaborati o elaborati parzialmente in uno stato di elaborazione completa. Vengono caricati i dati per le tabelle vuote e le partizioni; vengono compilate o ricompilate (ricalcolate) le gerarchie, le colonne calcolate e le relazioni.|  
    |**Elaborazione completa**|Elabora un oggetto partizione e tutti gli oggetti in esso contenuti. Quando viene eseguita l'elaborazione completa per un oggetto che è stato già elaborato, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vengono eliminati tutti i dati dell'oggetto, quindi quest'ultimo viene elaborato. Questo tipo di elaborazione è necessario quando è stata apportata una modifica strutturale a un oggetto.|  
    |**Elaborare dati**|Carica i dati in una partizione o in una tabella senza ricompilare le gerarchie o le relazioni oppure ricalcolare le colonne calcolate e le misure.|  
    |**Elaborazione pulizia**|Rimuove tutti i dati da una partizione.|  
    |**Elaborazione aggiunta**|Aggiornare in modo incrementale la partizione con i nuovi dati.|  
  
4.  Nella colonna della casella di controllo **Elabora** selezionare le partizioni che si desidera elaborare con la modalità scelta, quindi fare clic su **OK**.  
  
## Vedere anche  
 [Partizioni di modelli tabulari &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [Creare e gestire partizioni di modelli tabulari &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  