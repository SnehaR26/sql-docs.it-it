---
title: Connessione a SQL Server per l'eliminazione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f347a4866a7b6566ae2f0759813ac99d7977f058
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48143811"
---
# <a name="connection-to-sql-server-for-delete"></a>Connessione a SQL Server per l'eliminazione
  Quando si tenta di eliminare un'istanza di Oracle CDC con un account di accesso senza un ruolo del database che include autorizzazione di scrittura (ad esempio il ruolo **db_owner**) per il database MSXDBCDC, viene visualizzata la finestra di dialogo Connetti a SQL Server.  
  
 In questa finestra di dialogo è necessario immettere le credenziali per un account di accesso con autorizzazione di scrittura per il database MSXDBCDC, ad esempio il ruolo del database **db_owner** , per eliminare l'istanza di Oracle CDC.  
  
 Immettere le informazioni riportate di seguito nella finestra di dialogo Connect to SQL Server.  
  
 **Nome server**  
 Digitare il nome del server in cui si trova [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Autenticazione**  
 Selezionare una delle opzioni seguenti:  
  
-   **Autenticazione di Windows**  
  
-   **Autenticazione di SQL Server**: se si seleziona questa opzione, è necessario digitare **Login** e **Password** per l'utente nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui si esegue la connessione.  
  
 **Opzioni**  
 Fare clic sulla freccia per visualizzare le opzioni disponibili da configurare. È possibile scegliere di non modificare il valore predefinito per queste opzioni. Sono disponibili le opzioni seguenti:  
  
-   **Timeout connessione**: digitare il tempo, in secondi, di attesa del programma per la connessione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da stabilire prima che venga generato un errore di timeout. Il valore predefinito è **15**.  
  
-   **Timeout esecuzione**: digitare il tempo, in secondi, di attesa del programma per l'esecuzione del comando SQL da terminare prima che venga generato un errore di timeout. Il valore predefinito è **30**.  
  
-   **Crittografa connessione**: selezionare **Crittografa connessione** per assicurare che la connessione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da stabilire venga crittografata per garantire la privacy.  
  
-   **Advanced**: fare clic su **Advanced** e digitare eventuali proprietà di connessione aggiuntive nella finestra di dialogo Advanced Connection Properties, se necessario.  
  
## <a name="see-also"></a>Vedere anche  
 [Autorizzazioni necessarie per la connessione a SQL per il servizio CDC](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
