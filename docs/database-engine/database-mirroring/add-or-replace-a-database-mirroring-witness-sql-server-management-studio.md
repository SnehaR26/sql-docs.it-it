---
title: Aggiungere o sostituire un server di controllo del mirroring del database (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- database mirroring [SQL Server], witness
ms.assetid: 4b5ecffd-f025-4ab7-b69d-8958c6477127
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 54aa90739bb6f2d5d89afe33b6237b00a6c81a84
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628039"
---
# <a name="add-or-replace-a-database-mirroring-witness-sql-server-management-studio"></a>Aggiunta o sostituzione di un server di controllo del mirroring del database (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Se gli endpoint del mirroring del database utilizzano l'autenticazione di Windows, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per aggiungere o sostituire un server di controllo del mirroring. L'aggiunta di un server di controllo del mirroring in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] comporta l'attivazione della modalità a sicurezza elevata con failover automatico.  
  
> [!NOTE]  
>  È consigliabile che il server di controllo del mirroring si trovi in un computer separato dagli altri due partner. L'account di servizio utilizzato dal server di controllo del mirroring deve trovarsi nello stesso dominio degli account di servizio utilizzati dalle istanze del server principale e del server mirror oppure in un dominio trusted.  
  
### <a name="to-add-or-replace-a-witness"></a>Per aggiungere o sostituire un server di controllo del mirroring  
  
1.  Dopo aver attivato la connessione all'istanza del server principale, in Esplora oggetti fare clic sul nome del server per espandere l'albero.  
  
2.  Espandere **Database**e selezionare il database principale della sessione in cui si intende aggiungere o sostituire un server di controllo del mirroring.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività**e quindi fare clic su **Server mirror**. Viene visualizzata la pagina **Mirroring** della finestra di dialogo **Proprietà database** .  
  
4.  Fare clic su **Configura sicurezza**.  
  
5.  Se viene visualizzata la schermata iniziale di **Configurazione guidata sicurezza mirroring del database** , fare clic su **Avanti**.  
  
6.  Nella finestra di dialogo **Aggiunta server di controllo del mirroring** fare clic su **Sì**e quindi su **Avanti**.  
  
7.  Nella finestra di dialogo **Selezione dei server da configurare** viene automaticamente selezionata la casella di controllo **Istanza server di controllo del mirroring** . Scegliere **Avanti**.  
  
8.  Nella finestra di dialogo **Istanza server principale** mantenere la porta e l'endpoint esistenti. Scegliere **Avanti**.  
  
9. Nella finestra di dialogo **Istanza server di controllo del mirroring** fare clic su **Connetti**.  
  
10. Nella finestra di dialogo **Connetti al server** specificare l'istanza del server di controllo del mirroring nel campo **Nome server** e usare l'autenticazione di Windows (impostazione predefinita). Fare clic su **Connetti**.  
  
11. Dopo avere stabilito la connessione, nella finestra di dialogo **Istanza server di controllo del mirroring** vengono visualizzati la porta di attesa e l'endpoint del mirroring del database dell'istanza del server di controllo del mirroring. Scegliere **Avanti**.  
  
12. Nella finestra di dialogo **Account di servizio** sono contenuti i campi per gli account di servizio del dominio delle istanze dei server principale, mirror e di controllo del mirroring.  
  
    -   Se le istanze del server utilizzano tutte lo stesso account di servizio, lasciare i campi vuoti.  
  
    -   Se l'istanza del server di controllo del mirroring usa un account di servizio diverso da uno degli altri partner, immettere il nome dell'account nei campi **Server principale**, **Server mirror**e **Server di controllo del mirroring** :  
  
         *DOMAINNAME* **\\** *nome utente*  
  
         Il nome del dominio deve essere scritto in lettere maiuscole.  
  
     Scegliere **Avanti**.  
  
13. Nella schermata di riepilogo **Completare la procedura guidata** verificare, facoltativamente, la configurazione del server di controllo del mirroring e quindi fare clic su **Fine**.  
  
14. Al termine, verrà nuovamente visualizzata la finestra di dialogo **Proprietà database** nel cui campo **Server di controllo del mirroring** verrà visualizzato l'indirizzo di rete del server di controllo del mirroring. Viene inoltre selezionata automaticamente l'opzione **Protezione elevata con failover automatico (sincrona)** necessaria con un server di controllo del mirroring.  
  
     Per abilitare il server di controllo del mirroring e impostare la sessione sulla modalità di protezione elevata con failover automatico, fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Server di controllo del mirroring del database](../../database-engine/database-mirroring/database-mirroring-witness.md)   
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Proprietà del database &#40;Pagina Mirroring&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)   
 [Server di controllo del mirroring del database](../../database-engine/database-mirroring/database-mirroring-witness.md)  
  
  
