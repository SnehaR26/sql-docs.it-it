---
title: "Inizializzare azioni basate su modifiche dei valori di attributo (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regole business [Master Data Services], rilevamento delle modifiche agli attributi"
  - "gruppi rilevamento modifiche [Master Data Services], inizializzazione di azioni"
ms.assetid: 5e4402ce-31db-4774-a2a1-552335f87693
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Inizializzare azioni basate su modifiche dei valori di attributo (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] creare una regola di business per inizializzare azioni in base alle modifiche dei valori di attributo. Ad esempio, quando un valore di attributo specifico viene modificato, è necessario modificare un valore, inviare una notifica o avviare un flusso di lavoro esterno.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Gli attributi devono essere in un gruppo rilevamento modifiche. Per altre informazioni, vedere [Aggiungere attributi ad un gruppo rilevamento modifiche &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
### Per creare una regola business per inizializzare azioni basate su modifiche dei valori di attributo  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Dalla barra dei menu scegliere **Gestisci** e fare clic su **Regole business**.  
  
3.  Nella pagina **Manutenzione regola business** selezionare un modello dall'elenco **Modello**.  
  
4.  Dall'elenco **Entità** selezionare un'entità.  
  
5.  Dall'elenco **Tipo di membro** selezionare un tipo di membro a cui applicare la regola di business.  
  
6.  Dall'elenco **Attributo** selezionare un attributo o lasciare inalterata l'impostazione predefinita **Tutti**.  
  
7.  Fare clic su **Aggiungi regola di business**.  
  
8.  Fare clic su **Modifica regola business selezionata**.  
  
9. Nel riquadro **Componenti** espandere il nodo **Condizioni**.  
  
10. Nel nodo **Confronto valori** trascinare **è stato modificato** nell'etichetta **Condizioni** del riquadro **IF**.  
  
11. Nel riquadro **Modifica condizione** nella casella **Gruppo rilevamento modifiche** digitare il numero del gruppo di rilevamento delle modifiche assegnato come parte dei prerequisiti.  
  
12. Nel riquadro **Modifica condizione** fare clic su **Salva elemento**.  
  
13. Nel riquadro **Componenti** espandere il nodo **Azioni**.  
  
14. Fare clic su un'azione e trascinarla nell'etichetta **Azione** del riquadro **THEN**.  
  
15. Nel riquadro **Attributi** fare clic su un attributo e trascinarlo nell'etichetta **Seleziona attributo** del riquadro **Modifica azione**.  
  
16. Nel riquadro **Modifica azione** completare tutti i campi obbligatori.  
  
17. Nel riquadro **Modifica azione** fare clic su **Salva elemento**.  
  
18. Fare clic **Indietro**.  
  
19. Facoltativamente, nella pagina **Manutenzione regola business** per la riga che contiene la regola business fare doppio clic su una cella nella colonna **Nome**, **Descrizione** o **Notifica** per aggiornare il valore.  
  
    > [!NOTE]  
    >  Le notifiche vengono inviate soltanto per le regole che prevedono un'azione di convalida.  
  
20. Fare clic su **Pubblica regole business**.  
  
21. Nella finestra di dialogo di conferma fare clic su **OK**. Lo stato della regola viene modificato in **Attiva**.  
  
## Passaggi successivi  
  
-   Applicare regole business ai dati eseguendo una delle procedure riportate di seguito:  
  
    -   [Convalidare membri specifici rispetto a regole business &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Convalidare una versione usando le regole di business &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## Vedere anche  
 [Aggiungere attributi ad un gruppo rilevamento modifiche &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)   
 [Regole business &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  