---
title: Entità (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], about entities
- entities [Master Data Services]
ms.assetid: 0af057d5-6b73-472b-99eb-9f5eb61a9b5b
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 97a3fe9e9552170332e6be0d5cf5a3cb8541fe9b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072911"
---
# <a name="entities-master-data-services"></a>Entità (Master Data Services)
  Le entità sono oggetti contenuti nei modelli [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Ogni entità contiene membri che sono le righe dei dati master gestiti.  
  
## <a name="how-many-entities-are-appropriate"></a>Numero di entità appropriate  
 I modelli possono contenere tutte le entità che si desidera gestire. Ogni entità deve raggruppare un tipo di dati simile. Ad esempio, potrebbe essere necessaria un'entità per tutti gli account aziendali o un'entità per l'elenco principale di dipendenti.  
  
 Sono in genere disponibili una o più entità centrali importanti per l'azienda, alle quali sono correlati altri oggetti nel modello. Ad esempio, in un modello Product è possibile disporre di un'entità centrale denominata Product e di entità denominate Subcategory e Category alle quali è correlata l'entità Product. Tuttavia, non è necessario disporre di un'entità centrale. A seconda delle necessità, è possibile disporre di diverse entità che sono ritenute della stessa importanza.  
  
## <a name="how-entities-relate-to-other-model-objects"></a>Correlazione tra entità e gli altri oggetti modello  
 Un'entità può essere considerata come una tabella che contiene dati master, dove le righe rappresentano i membri e le colonne rappresentano gli attributi.  
  
 ![Entità Master Data Services rappresentata come tabella](../../2014/master-data-services/media/mds-conc-entity-table.gif "Entità Master Data Services rappresentata come tabella")  
  
 Popolare l'entità con un elenco di dati master che si desidera gestire.  
  
 Le entità possono essere utilizzate per compilare gerarchie derivate, che sono gerarchie basate su livelli in base a più entità. Per altre informazioni, vedere [Gerarchie derivate &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).  
  
 Le entità inoltre possono essere abilitate a contenere gerarchie esplicite (strutture incomplete basate su una sola entità) e raccolte (uniche combinazioni di subset di membri). Per altre informazioni, vedere [Gerarchie esplicite &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) e [Raccolte &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md).  
  
## <a name="using-entities-as-constrained-lists"></a>Utilizzo di entità come elenchi vincolati  
 Quando gli utenti stanno assegnando gli attributi ai membri in un'entità, è possibile sceglierli da un elenco di valori vincolato. A tale scopo, utilizzare un'entità per popolare l'elenco di valori per l'attributo. Questa caratteristica è nota come attributo basato su dominio. Per altre informazioni, vedere [Attributi basati su dominio &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).  
  
## <a name="base-entities"></a>Entità di base  
 Un'entità di base rappresenta un punto di partenza per gli utenti, durante lo spostamento tra oggetti nel modello. Un'entità di base determina il layout dello schermo quando un utente apre l'area funzionale **Visualizzatore** e fa clic su **Visualizzatore** sulla barra dei menu. Per specificare un'entità come entità di base, passare all'area funzionale **Amministrazione sistema** . Nella pagina **Vista modello** trascinare l'entità dal controllo albero sulla destra sul nome del modello nel controllo albero sulla sinistra.  
  
## <a name="entity-security"></a>Sicurezza dell'entità  
 È possibile concedere agli utenti l'autorizzazione per un'entità che include oggetti modello correlati. Per altre informazioni, vedere [Autorizzazioni per le entità &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md).  
  
## <a name="entity-examples"></a>Esempi di entità  
 Nell'esempio seguente viene illustrata un'entità che dispone degli attributi Name, Code, Subcategory, StandardCost, ListPrice e FilePhoto. Tali attributi descrivono i membri. Ogni membro viene rappresentato da una singola riga di valori di attributo.  
  
 ![Tabella dell'entità prodotto bicicletta](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Tabella dell'entità prodotto bicicletta")  
  
 Nel seguente esempio, l'entità Product è l'entità centrale. L'entità Subcategory è un attributo basato su dominio dell'entità Product. L'entità Category è un attributo basato su dominio dell'entità Subcategory. StandardCost e ListPrice sono attributi in formato libero dell'entità Product mentre FilePhoto è un attributo di file dell'entità Product.  
  
 ![Struttura ad albero dell'entità prodotto](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Struttura ad albero dell'entità prodotto")  
  
> [!NOTE]  
>  Si tratta di un esempio basato sull'interfaccia utente di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . La struttura ad albero gerarchica mostra le relazioni tra le entità e gli attributi basati su dominio. Lo scopo è illustrare le relazioni anziché rappresentare i livelli di importanza.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare una nuova entità.|[Creare un'entità &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)|  
|Specificare che un'entità può contenere attributi, gerarchie esplicite e raccolte.|[Abilitare un'entità per gerarchie esplicite e raccolte di &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|Modificare il nome di un'entità esistente.|[Modificare un nome di entità &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md)|  
|Eliminare un'entità esistente.|[Eliminare un'entità &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-entity-master-data-services.md)|  
|Assegnare autorizzazioni alle entità.|[Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Modelli &#40;Master Data Services&#41;](../../2014/master-data-services/models-master-data-services.md)  
  
-   [I membri &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)  
  
-   [Gli attributi &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
