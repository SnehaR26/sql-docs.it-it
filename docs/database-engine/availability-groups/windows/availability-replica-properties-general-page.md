---
title: Proprietà replica di disponibilità (Pagina Generale) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.availabilityreplicaproperties.general.f1
ms.assetid: 8318fefb-e045-4fab-8507-e1951fc7cec6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 54105086ff43e11f703df1da6da6c8dba75f0dad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611126"
---
# <a name="availability-replica-properties-general-page"></a>Proprietà replica di disponibilità (Pagina Generale)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Usare questa finestra di dialogo per visualizzare le proprietà di una replica di disponibilità.  
  
## <a name="task-list"></a>Elenco attività  
 **Per visualizzare le proprietà della replica di disponibilità**  
  
-   [Visualizzare le proprietà della replica di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-replica-properties-sql-server.md)  
  
-   [Usare il dashboard Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Nome del gruppo di disponibilità**  
 Nome del gruppo di disponibilità. Si tratta di un nome specificato dall'utente che deve essere univoco all'interno del cluster di failover di Windows Server (WSFC).  
  
 **Istanza del server**  
 Nome del server dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che ospita la replica corrente e, per un'istanza non predefinita, il nome dell'istanza.  
  
 **Ruolo**  
 **Primaria**  
 Attualmente la replica primaria.  
  
 **Secondari**  
 Attualmente una replica secondaria.  
  
 **Risoluzione**  
 È in corso la risoluzione del ruolo della replica nel ruolo primario o secondario.  
  
 **Modalità di disponibilità**  
 Modalità di disponibilità della replica. I valori possibili sono:  
  
 **Commit asincrono**  
 La replica primaria può eseguire il commit delle transazioni senza attendere che la replica secondaria salvi il log su disco.  
  
 **Commit sincrono**  
 La replica primaria attende che la replica secondaria salvi la transazione su disco prima di eseguirne il commit.  
  
 Per altre informazioni, vedere [Modalità di disponibilità &#40;gruppi di disponibilità Always On&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).  
  
 **Failover mode**  
 Modalità di failover della replica. I valori possibili sono:  
  
 **Automatico**  
 Failover automatico. La replica è una destinazione per i failover automatici. Questa opzione è supportata solo se la modalità di disponibilità è impostata sul commit sincrono.  
  
 **Manuale**  
 Failover manuale. Il failover della replica può essere eseguito solo manualmente dall'amministratore di database.  
  
 **Connessioni nel ruolo primario**  
 Tipo di connessioni client supportate quando la replica detiene il ruolo primario.  
  
 **Consenti tutte le connessioni**  
 Sono consentite tutte le connessioni ai database nella replica primaria. Si tratta dell'impostazione predefinita.  
  
 **Consenti connessioni in lettura/scrittura**  
 Non sono consentite le connessioni in cui la proprietà di connessione Finalità dell'applicazione è impostata su **ReadOnly** . Se la proprietà Finalità dell'applicazione è impostata su **ReadWrite** o se tale proprietà non è impostata, la connessione è consentita.  
  
 **Secondario leggibile**  
 Specifica se una replica di disponibilità che esegue il ruolo secondario, ovvero una replica secondaria, può accettare connessioni dai client. I valori possibili sono:  
  
 **No**  
 Non sono consentite connessioni dirette ai database secondari di questa replica. I database non sono disponibili per l'accesso in lettura. Si tratta dell'impostazione predefinita.  
  
 **Solo con finalità di lettura**  
 Sono consentite solo connessioni dirette di sola lettura ai database secondari di questa replica. Il database o i database secondari sono tutti disponibili per l'accesso in lettura.  
  
 **Sì**  
 Sono consentite tutte le connessioni ai database secondari di questa replica, ma solo per l'accesso in lettura. Il database o i database secondari sono tutti disponibili per l'accesso in lettura.  
  
 Per altre informazioni, vedere [Repliche secondarie attive: Repliche secondarie leggibili &#40;Gruppi di disponibilità AlwaysOn&#41;](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 **Timeout sessione (secondi)**  
 Periodo di timeout in secondi. Il periodo di timeout è il tempo di attesa massimo rispettato dalla replica per la ricezione di un messaggio da un'altra replica, prima di considerare la connessione tra la replica primaria e secondaria non riuscita. Il timeout della sessione rileva se le repliche secondarie sono connesse alla replica primaria. Se viene rilevata una connessione non riuscita con una replica secondaria, la replica primaria considera la replica secondaria come NOT_SYNCHRONIZED. Se viene rilevata una connessione non riuscita con una replica primaria, una replica secondaria tenta di riconnettersi.  
  
> [!NOTE]  
>  I timeout della sessione non provocano failover automatici.  
  
 **URL endpoint**  
 Rappresentazione di stringa dell'endpoint del mirroring di database specificato dall'utente usato dalle connessioni tra repliche primarie e secondarie per la sincronizzazione dei dati. Per informazioni sulla sintassi degli URL dell'endpoint, vedere [Specificare l'URL dell'endpoint quando si aggiunge o si modifica una replica di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
