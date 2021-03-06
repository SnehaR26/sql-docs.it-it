---
title: Identificatori (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ca1a3bd1754659548f6d1bc23764fd167006974a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37978605"
---
# <a name="identifiers-dmx"></a>Identificatori (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Tutti gli oggetti nel [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] deve avere un identificatore. Il nome di un oggetto ne costituisce l'identificatore. Sono dotati di identificatori anche i server, i database e gli oggetti di database quali origini dei dati, viste origine dati, cubi, dimensioni, modelli di data mining e così via.  
  
 In DMX (Data Mining Extensions) esistono due classi di identificatori:  
  
-   [Identificatori regolari](#RegularIdentifiers)  
  
-   [Identificatori delimitati](#DelimitedIdentifiers)  
  
 L'identificatore di un oggetto viene creato al momento della sua definizione e viene quindi utilizzato per farvi riferimento. Gli identificatori devono contenere al massimo 100 caratteri.  
  
##  <a name="RegularIdentifiers"></a> Identificatori regolari  
 Gli identificatori regolari in DMX sono conformi alle regole di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per il formato degli identificatori. In DMX gli identificatori regolari non richiedono delimitatori. Di seguito è riportato un esempio di istruzione DMX che utilizza un identificatore regolare, non delimitato:  
  
```  
SELECT * FROM Clustering.CONTENT;  
```  
  
### <a name="rules-for-regular-identifiers"></a>Regole relative agli identificatori regolari  
 Le regole per il formato degli identificatori regolari sono riportate di seguito:  
  
1.  Il primo carattere di un identificatore regolare deve essere uno dei seguenti:  
  
    -   Una lettera definita dallo Standard Unicode 2.0. che include i caratteri latini da A a Z (maiuscoli e minuscoli) oltre ai caratteri lettera di altre lingue.  
  
    -   Un carattere di sottolineatura (_).  
  
2.  I caratteri successivi possono essere:  
  
    -   Lettere definite nello Standard Unicode 2.0.  
  
    -   Numeri decimali inclusi nell'alfabeto Latino di base o in altri alfabeti nazionali.  
  
    -   Un carattere di sottolineatura (_).  
  
3.  L'identificatore non deve coincidere con una parola riservata DMX. In DMX per le parole riservate non viene fatta distinzione tra maiuscole e minuscole. Per altre informazioni, vedere [parole chiave riservate &#40;DMX&#41;](../dmx/reserved-keywords-dmx.md).  
  
4.  Gli identificatori non possono contenere spazi o caratteri speciali incorporati.  
  
 Se in un'istruzione DMX si utilizza un identificatore che non rispetta queste regole, sarà necessario racchiuderlo tra parentesi quadre.  
  
##  <a name="DelimitedIdentifiers"></a> Identificatori delimitati  
 Gli identificatori delimitati sono racchiusi tra parentesi quadre ([ ]).  Di seguito è riportato un esempio di istruzione DMX con un identificatore delimitato conforme alle regole indicate.  
  
```  
SELECT * FROM [Marketing_Clusters].CONTENT;  
```  
  
 Un identificatore non conforme alle regole deve essere sempre delimitato. Di seguito è riportato un esempio di istruzione DMX con un identificatore delimitato che contiene uno spazio:  
  
```  
SELECT * FROM [Targeted Mailing].CONTENT;  
```  
  
 È necessario utilizzare gli identificatori delimitati nelle situazioni seguenti:  
  
-   Quando si utilizzano parole riservate come nomi di oggetti o parti di nomi di oggetti.  
  
     È consigliabile evitare di utilizzare parole chiave riservate come nomi di oggetti. I database aggiornati da versioni precedenti di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] possono contenere identificatori che includono parole che non erano riservate nelle versioni precedenti di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ma che sono parole riservate[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Per fare riferimento a oggetti di questo tipo, è possibile utilizzare un identificatore delimitato finché non sarà possibile modificare il nome dell'oggetto.  
  
-   Quando si utilizzano caratteri non elencati come identificatori qualificati.  
  
     In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] è possibile utilizzare qualsiasi carattere della tabella codici corrente negli identificatori delimitati. L'utilizzo indiscriminato di caratteri speciali nei nomi degli oggetti può tuttavia rendere più difficile la lettura e la gestione delle istruzioni DMX.  
  
### <a name="rules-for-delimited-identifiers"></a>Regole relative agli identificatori delimitati  
 Le regole per il formato degli identificatori delimitati sono riportate di seguito:  
  
1.  Gli identificatori delimitati possono essere composti dallo stesso numero di caratteri degli identificatori regolari (da 1 a 100 caratteri, esclusi i caratteri di delimitazione).  
  
2.  Il corpo di un identificatore può contenere qualsiasi combinazione di caratteri utilizzati nella tabella codici corrente, inclusi i caratteri di delimitazione stessi. Se il corpo dell'identificatore contiene caratteri di delimitazione, sarà necessaria una gestione particolare:  
  
    -   Se il corpo dell'identificatore contiene una parentesi quadra aperta ([), non saranno necessarie operazioni di gestione aggiuntive.  
  
    -   Se il corpo dell'identificatore contiene una parentesi quadra chiusa (]), sarà necessario specificare due parentesi quadre chiuse (]]) per rappresentarla nella tabella codici.  
  
### <a name="delimiting-identifiers-with-multiple-parts"></a>Identificatori delimitati composti da più parti  
 Quando si utilizzano nomi di oggetti qualificati può essere necessario delimitare più identificatori che compongono il nome dell'oggetto. Tali identificatori devono essere delimitati singolarmente.  
  
## <a name="see-also"></a>Vedere anche  
 [Le estensioni di Data Mining di dati &#40;DMX&#41; riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; gli elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; riferimento alle funzioni](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; riferimento alle istruzioni](../dmx/data-mining-extensions-dmx-statements.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
