---
title: MSSQLSERVER_21893 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 100edf017c864567cd8f7046ff4a7a76796aaf41
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775379"
---
# <a name="mssqlserver21893"></a>MSSQLSERVER_21893
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21893|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum21893|  
|Testo del messaggio|I sottoscrittori (%s) del server di pubblicazione originale '%s' non sembrano server remoti per il server di pubblicazione reindirizzato '%s.' Eseguire **sp_addlinkedserver** sul server di pubblicazione reindirizzato per aggiungere questi Sottoscrittori come server remoti.|  
  
## <a name="explanation"></a>Spiegazione  
**sp_validate_redirected_publisher** usa le tabelle di metadati della sottoscrizione del database del server di pubblicazione sul server remoto per identificare i Sottoscrittori associati e verifica che in master.dbo.sysservers siano presenti voci associate per i Sottoscrittori. Questo errore viene restituito se uno dei sottoscrittori identificato non è presente.  
  
Questo errore non è considerato un errore irreversibile. Gli agenti che rilevano questo errore lo registreranno come messaggio di errore informativo ma non termineranno, poiché un errore, per avere voci del sottoscrittore appropriate sul nuovo server di pubblicazione, ha un impatto limitato sulla replica. Senza una voce adatta per un Sottoscrittore in sysservers, è possibile che alcune attività di gestione delle sottoscrizioni non riescano se vengono eseguite tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Tuttavia, è possibile eseguire queste stesse attività correttamente eseguendo in modo esplicito le stored procedure di gestione.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire **sp_addlinkedserver** sul server di pubblicazione reindirizzato per tutti i Sottoscrittori identificati per aggiungerli come server remoti. Eseguire quindi **sp_serveroption** per impostare il bit del Sottoscrittore per il server.  
  
