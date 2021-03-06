---
title: Contenuto del modello di data mining per i modelli di Clustering (Analysis Services - Data Mining) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3344fbcd8a1a31f0bb98a8a1702f1535eb831b3d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34019168"
---
# <a name="mining-model-content-for-clustering-models-analysis-services---data-mining"></a>Contenuto dei modelli di data mining per i modelli di clustering (Analysis Services - Data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In questo argomento viene descritto il contenuto dei modelli di data mining specifico per i modelli che utilizzano l'algoritmo Microsoft Clustering. Per una spiegazione generale del contenuto del modello di data mining valida per tutti i tipi di modello, vedere [Mining Model Content &#40;Analysis Services - Data Mining&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="understanding-the-structure-of-a-clustering-model"></a>Informazioni sulla struttura di un modello di clustering  
 Un modello di clustering ha una struttura semplice. Ogni modello include un singolo nodo padre che rappresenta il modello e i relativi metadati e ogni nodo padre è associato a un elenco semplice di cluster (NODE_TYPE = 5). Questa organizzazione è illustrata nell'immagine seguente.  
  
 ![struttura del contenuto del modello per il clustering](../../analysis-services/data-mining/media/modelcontentstructure-clust.gif "struttura del contenuto del modello per il clustering")  
  
 Ogni nodo figlio rappresenta un singolo cluster e contiene statistiche dettagliate sugli attributi dei relativi case, tra cui un conteggio del numero di case nel cluster e la distribuzione di valori che distinguono un cluster dagli altri.  
  
> [!NOTE]  
>  Non è necessario scorrere i nodi per ottenere un conteggio o una descrizione dei cluster; anche il nodo padre del modello contiene un conteggio e un elenco dei cluster.  
  
 Il nodo padre contiene statistiche utili che descrivono la distribuzione effettiva di tutti i case di training. Queste statistiche si trovano nella colonna della tabella nidificata, NODE_DISTRIBUTION. Ad esempio, nella tabella seguente sono illustrate diverse righe della tabella NODE_DISTRIBUTION che descrivono la distribuzione di dati demografici dei clienti per il modello di clustering `TM_Clustering`creato nell' [Esercitazione di base sul data mining](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c):  
  
|ATTRIBUTE_NAME|ATTRIBUTE_VALUE|Supporto|PROBABILITY|VARIANCE|VALUE_TYPE|  
|---------------------|---------------------|-------------|-----------------|--------------|-----------------|  
|Age|Missing|0|0|0|1 (Mancante)|  
|Age|44.9016152716593|12939|1|125.663453102554|3 (Continuo)|  
|Gender|Missing|0|0|0|1 (Mancante)|  
|Gender|F|6350|0.490764355823479|0|4 (discreto)|  
|Gender|M|6589|0.509235644176521|0|4 (discreto)|  
  
 Da questi risultati emerge che sono stati utilizzati 12939 case per compilare il modello, che il rapporto tra maschi e femmine è approssimativamente 50-50 e che l'età media è 44 anni. Le statistiche descrittive variano a seconda che l'attributo riportato sia un tipo di dati numerico continuo, ad esempio l'età, o un tipo di valore discreto, ad esempio il sesso. Le misure statistiche *media* e *varianza* vengono calcolate per i tipi di dati continui, mentre *probabilità* e *supporto* vengono calcolate per i tipi di dati discreti.  
  
> [!NOTE]  
>  La varianza rappresenta la varianza totale per il cluster. Se il valore relativo alla varianza è piccolo, significa che la maggior parte dei valori della colonna sono relativamente vicini alla media. Per ottenere la deviazione standard, calcolare la radice quadrata della varianza.  
  
 Si noti che per ogni attributo è presente un tipo di valore **Missing** che indica il numero di case in cui i dati per tale attributo sono mancanti. I dati mancanti possono essere significativi e influiscono sui calcoli in vari modi, a seconda del tipo di dati. Per altre informazioni, vedere [Valori mancanti &#40; Analysis Services - Data mining&#41;](../../analysis-services/data-mining/missing-values-analysis-services-data-mining.md).  
  
## <a name="model-content-for-a-clustering-model"></a>Contenuto di un modello di clustering  
 In questa sezione vengono forniti dettagli ed esempi relativi solo alle colonne del contenuto dei modelli di data mining pertinenti per i modelli di clustering.  
  
 Per informazioni sulle colonne generiche del set di righe dello schema, ad esempio MODEL_CATALOG e MODEL_NAME, vedere [Mining Model Content &#40;Analysis Services - Data Mining&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
 MODEL_CATALOG  
 Nome del database in cui è archiviato il modello.  
  
 MODEL_NAME  
 Nome del modello.  
  
 ATTRIBUTE_NAME  
 Sempre vuota nei modelli di clustering perché non è disponibile alcun attributo stimabile nel modello.  
  
 NODE_NAME  
 Sempre uguale a NODE_UNIQUE_NAME.  
  
 NODE_UNIQUE_NAME  
 Identificatore univoco del nodo all'interno del modello. Questo valore non può essere modificato.  
  
 NODE_TYPE  
 Un modello di clustering restituisce i tipi di nodo seguenti:  
  
|ID e nome del nodo|Description|  
|----------------------|-----------------|  
|1 (Model)|Nodo radice per il modello.|  
|5 (Cluster)|Contiene un conteggio dei case nel cluster, le caratteristiche dei case nel cluster e statistiche che descrivono i valori nel cluster.|  
  
 NODE_CAPTION  
 Nome descrittivo a scopo di visualizzazione. Quando si crea un modello, il valore di NODE_UNIQUE_NAME viene automaticamente utilizzato come didascalia. Tuttavia, è possibile modificare il valore di NODE_CAPTION per aggiornare il nome visualizzato per il cluster, a livello di programmazione o tramite il visualizzatore.  
  
> [!NOTE]  
>  Quando si rielabora il modello, tutte le modifiche dei nomi verranno sovrascritte dai nuovi valori. Non è possibile impostare come persistenti i nomi nel modello né effettuare il rilevamento delle modifiche nell'appartenenza al cluster tra versioni diverse di un modello.  
  
 CHILDREN_CARDINALITY  
 Stima del numero di nodi figlio del nodo.  
  
 **Nodo padre** Indica il numero di cluster nel modello.  
  
 **Nodi del cluster** Sempre 0.  
  
 PARENT_UNIQUE_NAME  
 Nome univoco dell'elemento padre del nodo.  
  
 **Nodo padre** Sempre NULL.  
  
 **Nodi del cluster** Solitamente 000.  
  
 NODE_DESCRIPTION  
 Descrizione del nodo.  
  
 **Nodo padre** Sempre **(All)**.  
  
 **Nodi del cluster** Elenco delimitato da virgole degli attributi principali che distinguono il cluster dagli altri.  
  
 NODE_RULE  
 Opzione non utilizzata per i modelli di clustering.  
  
 MARGINAL_RULE  
 Opzione non utilizzata per i modelli di clustering.  
  
 NODE_PROBABILITY  
 Probabilità associata a questo nodo. **Nodo padre** Sempre 1.  
  
 **Nodi del cluster** La probabilità rappresenta la probabilità composta degli attributi, con alcuni adattamenti a seconda dell'algoritmo usato per creare il modello di clustering.  
  
 MARGINAL_PROBABILITY  
 Probabilità di raggiungere il nodo dal nodo padre. In un modello di clustering la probabilità marginale corrisponde sempre alla probabilità del nodo.  
  
 NODE_DISTRIBUTION  
 Tabella contenente l'istogramma delle probabilità del nodo.  
  
 **Nodo padre** Vedere l'introduzione di questo argomento.  
  
 **Nodi del cluster** Rappresenta la distribuzione di attributi e valori per i case inclusi nel cluster.  
  
 NODE_SUPPORT  
 Numero di case che supportano il nodo. **Nodo padre** Indica il numero di case di training per l'intero modello.  
  
 **Nodi del cluster** Indica la dimensione del cluster come numero di case.  
  
 **Nota** Se il modello usa il clustering K-medie, ogni case può appartenere a un unico cluster. Se invece il modello utilizza il clustering EM, ogni case può appartenere a cluster diversi e gli viene assegnata una distanza ponderata per ogni cluster cui appartiene. Pertanto, per i modelli EM la somma del supporto per un singolo cluster è maggiore del supporto per il modello complessivo.  
  
 MSOLAP_MODEL_COLUMN  
 Opzione non utilizzata per i modelli di clustering.  
  
 MSOLAP_NODE_SCORE  
 Visualizza un punteggio associato al nodo.  
  
 **Nodo padre** Punteggio BIC (Bayesian Information Criterion) per il modello di clustering.  
  
 **Nodi del cluster** Sempre 0.  
  
 MSOLAP_NODE_SHORT_CAPTION  
 Etichetta utilizzata a scopo di visualizzazione. Questa didascalia non può essere modificata.  
  
 **Nodo padre** Tipo di modello: modello di cluster  
  
 **Nodi del cluster** Nome del cluster. Esempio: Cluster 1.  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] offre più metodi per la creazione di un modello di clustering. Se non si conosce il metodo impiegato per creare il modello in uso, è possibile recuperare a livello di programmazione i metadati del modello, utilizzando un client ADOMD o AMO oppure eseguendo una query sul set di righe dello schema di data mining. Per altre informazioni, vedere [Eseguire query sui parametri usati per creare un modello di data mining](../../analysis-services/data-mining/query-the-parameters-used-to-create-a-mining-model.md).  
  
> [!NOTE]  
>  La struttura e il contenuto del modello rimangono invariati, indipendentemente dal metodo di clustering o dai parametri utilizzati.  
  
## <a name="see-also"></a>Vedere anche  
 [Contenuto del modello di data mining & #40; Analysis Services - Data Mining & #41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)   
 [Visualizzatori modello di Data Mining](../../analysis-services/data-mining/data-mining-model-viewers.md)   
 [Algoritmo Microsoft Clustering](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)   
 [Query di Data Mining](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
