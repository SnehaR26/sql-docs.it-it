---
title: "Configurazione della trasformazione Comando OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "parametri [Integration Services]"
  - "Comando OLE DB - trasformazione"
ms.assetid: c800f167-3d2e-4c10-8ba3-a02f1872ccea
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# Configurazione della trasformazione Comando OLE DB
  È possibile aggiungere e configurare una trasformazione Comando OLE DB solo se il pacchetto include almeno un'attività Flusso di dati e un'origine, quale un'origine file flat o un'origine OLE DB. Questa trasformazione viene in genere utilizzata per l'esecuzione di query con parametri.  
  
### Per configurare la trasformazione Comando OLE DB  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di dati** e quindi, dalla **casella degli strumenti** trascinare la trasformazione Comando OLE DB sull'area di progettazione.  
  
4.  Connettere la trasformazione Comando OLE DB al flusso di dati trascinando un connettore, la freccia verde o la freccia rossa, da un'origine dei dati o una trasformazione precedente alla trasformazione Comando OLE DB.  
  
5.  Fare clic con il pulsante destro del mouse sul componente e scegliere Modifica o **Visualizza editor avanzato**.  
  
6.  Nella scheda **Gestioni connessioni** selezionare una gestione connessione OLE DB dall'elenco **Gestione connessione**. Per altre informazioni, vedere [Gestione connessione OLE DB](../../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
7.  Fare clic sulla scheda **Proprietà componente** e quindi sul pulsante con i puntini di sospensione **(...)** nella casella **SqlCommand**.  
  
8.  In **Editor valore stringa** digitare l'istruzione SQL con parametri usando un punto interrogativo (?) come indicatore per ogni parametro.  
  
9. Fare clic su **Aggiorna**. Quando si fa clic su **Aggiorna** la trasformazione crea una colonna per ogni parametro nella raccolta Colonne esterne e imposta la proprietà DBParamInfoFlags.  
  
10. Fare clic sulla scheda **Proprietà input e output**.  
  
11. Espandere **Input comando OLE DB** e quindi **Colonne esterne**.  
  
12. Verificare che in **Colonne esterne** sia elencata una colonna per ogni parametro nell'istruzione SQL. I nomi delle colonne sono **Param_0**, **Param_1** e così via.  
  
     Tali nomi non devono essere modificati. Se si modificano i nomi della colonna, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] genera un errore di convalida per la trasformazione Comando OLE DB.  
  
     Inoltre, non modificare il tipo di dati. La proprietà DataType di ogni colonna viene impostata sul tipo di dati corretto.  
  
13. Se in **Colonne esterne** non è elencata alcuna colonna, sarà necessario aggiungerle manualmente.  
  
    -   Fare clic su **Aggiungi colonna** una volta per ogni parametro nell'istruzione SQL.  
  
    -   Modificare i nomi delle colonne in **Param_0**, **Param_1** e così via.  
  
    -   Specificare un valore nella proprietà DBParamInfoFlags. Tale valore deve corrispondere a un valore dell'enumerazione OLE DB DBPARAMFLAGSENUM. Per ulteriori informazioni, vedere la documentazione di riferimento di OLE DB.  
  
    -   Specificare il tipo di dati della colonna e, a seconda del tipo di dati, specificarne anche la tabella codici, la lunghezza, la precisione e la scala.  
  
    -   Per eliminare un parametro non usato, selezionarlo in **Colonne esterne** e fare clic su **Rimuovi colonna**.  
  
    -   Fare clic su **Mapping colonne** ed eseguire il mapping delle colonne nell'elenco **Colonne di input disponibili** ai parametri nell'elenco **Colonne di destinazione disponibili**.  
  
14. Scegliere **OK**.  
  
15. Per salvare il pacchetto aggiornato, scegliere **Salva** dal menu **File**.  
  
## Vedere anche  
 [Trasformazione Comando OLE DB](../../../integration-services/data-flow/transformations/ole-db-command-transformation.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Percorsi in Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Attività Flusso di dati](../../../integration-services/control-flow/data-flow-task.md)  
  
  