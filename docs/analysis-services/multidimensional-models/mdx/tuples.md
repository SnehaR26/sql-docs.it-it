---
title: "Tuple | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35b629ae-b1ef-44b1-b556-96956aeb56e7
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 7
---
# Tuple
  Una tupla consente di identificare in modo univoco una sezione di dati di un cubo. La tupla viene creata da una combinazione di membri di dimensione, finché non esistono due o più membri che appartengono alla medesima gerarchia.  
  
## Membri dell'attributo impliciti o predefiniti in una tupla  
 Quando si definisce una tupla in una query o espressione MDX, non è necessario includere in modo esplicito il membro dell'attributo di ogni gerarchia dell'attributo. Se un membro di una gerarchia dell'attributo non viene incluso in una query o espressione in modo esplicito, il membro predefinito della gerarchia dell'attributo è il membro dell'attributo incluso nella tupla in modo implicito. Se non altrimenti definito in modo esplicito in un cubo, il membro predefinito per ogni gerarchia dell'attributo è il membro (Totale), se esistente. Se non esiste un membro (Totale) all'interno di una gerarchia dell'attributo, il membro predefinito è un membro del livello principale della gerarchia dell'attributo. La misura predefinita è la prima misura specificata nel cubo, a meno che non venga definita in modo esplicito una misura predefinita. Per altre informazioni, vedere [Definire un membro predefinito](../../../analysis-services/multidimensional-models/define-a-default-member.md) e [DefaultMember &#40;MDX&#41;](../../../mdx/defaultmember-mdx.md).  
  
 La tupla seguente identifica ad esempio una singola cella nel database Adventure Works definendo in modo esplicito un solo membro della dimensione Measures.  
  
```  
(Measures.[Reseller Sales Amount])  
```  
  
 Nell'esempio precedente viene identificata in modo univoco la cella costituita dal membro Reseller Sales Amount della dimensione Measures e dal membro predefinito di ogni gerarchia dell'attributo del cubo. Il membro predefinito è il membro (Totale) per ogni gerarchia dell'attributo diversa dalla gerarchia dell'attributo Destination Currency. Il membro predefinito per la gerarchia Destination Currency, è il membro US Dollar. Questo membro predefinito viene definito nello script MDX del cubo Adventure Works.  
  
> [!IMPORTANT]  
>  Il membro di una gerarchia dell'attributo in una tupla viene influenzato anche dalle relazioni definite tra gli attributi all'interno di una dimensione.  
  
 Nella query seguente viene restituito il valore della cella a cui fa riferimento la tupla specificata nell'esempio precedente, ($80,450.596.98).  
  
```  
SELECT   
Measures.[Reseller Sales Amount] ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Quando in una query si specifica un asse per un set (in questo caso costituito da una sola tupla), è necessario specificare innanzitutto un set per l'asse delle colonne prima di specificare un set per l'asse delle righe. L'asse delle colonne è inoltre noto come *Axis(0)* o semplicemente *0*. Per altre informazioni, vedere [Query MDX di base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-query-mdx.md).  
  
### Tuple come riferimenti a valori o al membro  
 È inoltre possibile usare una tupla in una query per restituire il valore della cella a cui fa riferimento la tupla, come nell'esempio precedente, oppure è possibile usarla in un'espressione per fare riferimento in modo esplicito ai membri specificati nella tupla. La query o l'espressione consente di impiegare funzioni che restituiscono o usano le tuple. Una tupla può essere usata per fare riferimento al valore della cella specificata dalla tupla o per specificare una combinazione di membri quando viene usata in una funzione.  
  
### Dimensionalità della tupla  
 Per *dimensionalità* di una tupla si intende la sequenza o l'ordine dei membri nella tupla. Dal momento che i membri impliciti ricorrono sempre nello stesso ordine, la dimensionalità viene spesso considerata in relazione ai membri della tupla definiti in modo esplicito. L'ordinamento dei membri della tupla è importante quando si definisce un set di tuple. Nell'esempio seguente vengono inclusi due membri di una tupla nell'asse delle colonne.  
  
```  
SELECT   
([Measures].[Reseller Sales Amount],[Date].[Calendar Year].[CY 2004]) ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Quando si specifica in modo esplicito un membro in una tupla da più di una dimensione, è necessario includere l'intera tupla tra parentesi. Quando si specifica un solo membro in una tupla, le parentesi sono facoltative.  
  
 La tupla nella query dell'esempio precedente specifica la restituzione della cella del cubo nel punto di intersezione tra la misura Reseller Sales Amount della dimensione Measures e il membro CY 2004 della gerarchia dell'attributo Calendar Year nella dimensione Date.  
  
> [!NOTE]  
>  È possibile fare riferimento a un membro dell'attributo tramite il nome o la chiave del membro. Nell'esempio precedente, è possibile sostituire il riferimento a [CY 2004] con &[2004].  
  
## Vedere anche  
 [Concetti chiave di MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [Spazio del cubo](../../../analysis-services/multidimensional-models/mdx/cube-space.md)   
 [Auto Exist](../../../analysis-services/multidimensional-models/mdx/autoexists.md)   
 [Utilizzo di membri, tuple e set &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)  
  
  