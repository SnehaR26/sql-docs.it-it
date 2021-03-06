---
title: Cenni preliminari sulla sicurezza (Data Mining) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8cf7958cdde480bf48c26dfed7e3056385439a4d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34016888"
---
# <a name="security-overview-data-mining"></a>Panoramica della sicurezza (data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Il processo di protezione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] avviene su più livelli. È necessario proteggere ogni istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e le relative origini dati in modo che solo gli utenti autorizzati dispongano di autorizzazioni di lettura o di lettura/scrittura per le dimensioni, i modelli di data mining e le origini dati selezionati. È inoltre necessario proteggere le origini dati sottostanti per evitare che utenti non autorizzati danneggino le informazioni aziendali riservate. Il processo di protezione di un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è descritto negli argomenti seguenti.  
  
##  <a name="bkmk_Architecture"></a> Architettura di sicurezza  
 Per ulteriori informazioni sull'architettura di sicurezza di base di un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], incluso il modo in cui in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene utilizzata l'autenticazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows per autenticare l'accesso utente, vedere le risorse seguenti.  
  
-   [Ruoli di sicurezza & #40; Analysis Services - dati multidimensionali & #41;](../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
-   [Proprietà di sicurezza](../../analysis-services/server-properties/security-properties.md)  
  
-   [Configurare gli account del servizio & #40; Analysis Services & #41;](../../analysis-services/instances/configure-service-accounts-analysis-services.md)  
  
-   [Per l'autorizzazione di accesso per gli oggetti e operazioni & #40; Analysis Services & #41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)  
  
##  <a name="bkmk_Logon"></a> Configurazione dell'account di accesso per Analysis Services  
 È necessario selezionare un account di accesso appropriato per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e specificare le autorizzazioni per questo account. È necessario verificare che l'account di accesso di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] disponga solo delle autorizzazioni necessarie per eseguire determinate attività, incluse le autorizzazioni appropriate per le origini dati sottostanti.  
  
 Per data mining è necessario un diverso set di autorizzazioni per compilare ed elaborare i modelli necessari per la visualizzazione o l'esecuzione di query sui modelli. L'esecuzione di stime su un modello è simile all'esecuzione di query con la differenza che non vengono richieste autorizzazioni amministrative.  
  
##  <a name="bkmk_Instance"></a> Sicurezza di un'istanza di Analysis Services  
 È quindi necessario proteggere il computer di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , il sistema operativo Windows nel computer di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e le origini dei dati usate da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
##  <a name="bkmk_Access"></a> Configurazione dell'accesso ad Analysis Services  
 Quando si configurano e si definiscono gli utenti autorizzati per un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è necessario determinare gli utenti a cui è inoltre necessario concedere le autorizzazioni per l'amministrazione di oggetti di database specifici, gli utenti che possono visualizzare la definizione di oggetti o esplorare i modelli e gli utenti che possono accedere direttamente alle origini dati.  
  
##  <a name="bkmk_DMspecial"></a> Considerazioni speciali per data mining  
 Per consentire a un analista o a uno sviluppatore di creare modelli di data mining ed eseguirne il test, è necessario concedergli le autorizzazioni amministrative per il database in cui sono archiviati i modelli di data mining. Di conseguenza, l'analista o lo sviluppatore di data mining può potenzialmente creare o eliminare gli altri oggetti che non sono correlati al data mining, inclusi gli oggetti di data mining creati e utilizzati da altri analisti o sviluppatori o oggetti OLAP che non sono inclusi nella soluzione di data mining.  
  
 Pertanto, quando si crea una soluzione per data mining, è necessario bilanciare le esigenze dell'analista o dello sviluppatore di sviluppare e ottimizzare i modelli, nonché di eseguirne il test, con le esigenze di altri utenti e adottare misure per proteggere gli oggetti di database esistenti. Un possibile approccio è creare un database separato dedicato al data mining o creare database separati per ogni analista.  
  
 Anche se la creazione di modelli richiede il massimo livello di autorizzazioni, è possibile controllare l'accesso degli utenti ai modelli di data mining per le altre operazioni, ad esempio l'elaborazione, l'esplorazione o l'esecuzione di query, mediante la sicurezza basata sui ruoli. Quando si crea un ruolo, si impostano le autorizzazioni specifiche per gli oggetti di data mining. Qualsiasi utente che è membro di un ruolo dispone automaticamente di tutte le autorizzazioni associate a quel ruolo.  
  
 Ai modelli di data mining inoltre fanno spesso riferimento origini dati contenenti informazioni riservate. Se la struttura di data mining e il modello di data mining sono stati configurati per consentire agli utenti di eseguire il drill-through dal modello ai dati della struttura, è necessario adottare le dovute precauzioni per mascherare le informazioni riservate o limitare gli utenti che dispongono dell'accesso ai dati sottostanti.  
  
 Se si utilizzano pacchetti di Integration Services per pulire i dati, aggiornare modelli di data mining o eseguire stime, è necessario assicurarsi che il servizio Integration Services disponga delle autorizzazioni appropriate per il database in cui è archiviato il modello e delle autorizzazioni appropriate per i dati di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Ruoli e autorizzazioni & #40; Analysis Services & #41;](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
