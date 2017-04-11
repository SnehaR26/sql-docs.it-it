---
title: "Compilazione di sottocubi in MDX (MDX) | Microsoft Docs"
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
helpviewer_keywords: 
  - "query [MDX] sottocubi"
  - "sottocubi [MDX]"
  - "viste filtrate [MDX]"
  - "MDX [Analysis Services], sottocubi"
  - "espressioni multidimensionali [Analysis Services], sottocubi"
  - "CREATE SUBCUBE - istruzione"
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
caps.latest.revision: 31
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 31
---
# Compilazione di sottocubi in MDX (MDX)
  Un sottocubo è un subset di un cubo che rappresenta una vista filtrata dei dati sottostanti. Riducendo il cubo a un sottocubo, è possibile migliorare le prestazioni delle query.  
  
 Per definire un sottocubo, è possibile usare l'istruzione [CREATE SUBCUBE](../Topic/CREATE%20SUBCUBE%20Statement%20\(MDX\).md), come descritto in questo argomento.  
  
## Sintassi di CREATE SUBCUBE  
 Per creare un sottocubo, utilizzare la sintassi seguente:  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 La sintassi di CREATE SUBCUBE è piuttosto semplice. Il parametro *Subcube_Identifier* identifica il cubo su cui sarà basato il sottocubo. Il parametro *Subcube_Expression* seleziona la parte del cubo che costituirà il sottocubo  
  
 Dopo la creazione del sottocubo, quest'ultimo diventerà il contesto di tutte le query MDX fino alla chiusura della sessione o all'esecuzione dell'istruzione [DROP SUBCUBE](../Topic/DROP%20SUBCUBE%20Statement%20\(MDX\).md).  
  
### Contenuto di un sottocubo  
 Anche se è piuttosto semplice da utilizzare, l'istruzione CREATE SUBCUBE in sé non indica esplicitamente tutti i membri che faranno parte del sottocubo. Nella definizione di un sottocubo valgono le regole seguenti:  
  
-   Se si include il membro **(All)** (Tutti) di una gerarchia, verranno inclusi tutti i membri della gerarchia.  
  
-   Se si include un membro, verranno inclusi tutti i predecessori e i discendenti di tale membro.  
  
-   Se si includono tutti i membri di un livello, verranno inclusi tutti i membri della gerarchia. I membri di altre gerarchie che non corrispondono a membri del livello (ad esempio, una gerarchia sbilanciata come nel caso di una città per cui non esistono clienti) verranno esclusi.  
  
-   Un sottocubo contiene sempre tutti i membri **(All)** (Tutti) del cubo.  
  
 I valori di aggregazione inclusi nel sottocubo verranno inoltre totalizzati visivamente. Si consideri ad esempio un sottocubo contenente `USA`, `WA` e `OR`. Il valore di aggregazione di `USA` sarà costituito dalla somma di `{WA,OR}`, perché `WA` e `OR` sono gli unici stati definiti dal sottocubo. Tutti gli altri stati verranno ignorati.  
  
 I riferimenti espliciti alle celle esterne al sottocubo restituiscono inoltre valori di cella che vengono valutati nel contesto dell'intero cubo. Si immagini ad esempio di creare un sottocubo limitato all'anno corrente. Si usa quindi la funzione [ParallelPeriod](../../../mdx/parallelperiod-mdx.md) per confrontare l'anno corrente con quello precedente. La differenza tra tali valori verrà restituita anche se il valore dell'anno precedente è esterno al sottocubo.  
  
 Infine, se il contesto originale non viene sovrascritto, le funzioni sui set valutate in una sub-SELECT verranno valutate nel contesto della sub-SELECT. Se il contesto viene sovrascritto, le funzioni sui set verranno valutate nel contesto dell'intero cubo.  
  
## Esempio di CREATE SUBCUBE  
 Nell'esempio seguente viene creato un sottocubo che restringe il cubo Budget ai soli conti 4200 e 4300:  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 Poiché è stato creato un sottocubo per la sessione, tutte le query successive verranno eseguite sul sottocubo, non sull'intero cubo. Se ad esempio si esegue la query seguente, verranno restituiti solo membri dei conti 4200 e 4300.  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## Vedere anche  
 [Definizione del contesto di cubo in una query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)   
 [Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  