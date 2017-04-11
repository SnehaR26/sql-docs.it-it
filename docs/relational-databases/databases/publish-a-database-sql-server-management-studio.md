---
title: "Pubblicazione di un database (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98b2914e-7147-40af-ba7d-87253bbe8bf9
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Pubblicazione di un database (SQL Server Management Studio)
  È possibile utilizzare la procedura guidata **Genera e pubblica script** per pubblicare un database intero o singoli oggetti di database in un provider di hosting Web remoto.  
  
> [!NOTE]  
>  La funzionalità descritta in questo argomento era fornita da Pubblicazione guidata database. Poiché la funzionalità di pubblicazione è stata aggiunta alla procedura guidata Genera e pubblica script, la procedura Pubblicazione guidata database non è più supportata.  
  
## Procedura guidata Genera e pubblica script  
 La procedura guidata Genera e pubblica script consente di pubblicare un database oppure oggetti di database selezionati su un provider di hosting Web. Un provider di hosting Web di SQL Server è un'interfaccia di connettività a un servizio Web. Il servizio Web viene creato tramite il progetto Database Publishing Service in SQL Server Hosting Toolkit su CodePlex. Il servizio Web facilita la pubblicazione nel servizio dei database dei clienti dell'hoster Web tramite la procedura guidata Genera e pubblica script. Per altre informazioni sul download di SQL Server Hosting Toolkit, vedere [Database Publishing Services di SQL Server](http://go.microsoft.com/fwlink/?LinkId=142025).  
  
 È inoltre possibile utilizzare la procedura guidata Genera e pubblica script per creare uno script per il trasferimento di un database.  
  
#### Per pubblicare un database su un servizio Web  
  
1.  In Esplora oggetti, espandere **Database**, fare clic con il pulsante destro del mouse su un database, scegliere **Attività**, quindi fare clic su **Genera e pubblica script**. Per creare script per gli oggetti di database da pubblicare, seguire i passaggi della procedura guidata.  
  
2.  Nella pagina **Seleziona oggetti** selezionare gli oggetti da pubblicare sul servizio di hosting Web.  
  
3.  Nella pagina **Imposta opzioni di generazione script** selezionare **Pubblica su servizio Web**.  
  
    1.  Nella casella **Provider** specificare il provider per il servizio Web. Se non è stato configurato un provider di hosting Web, selezionare **Gestisci provider** e utilizzare la finestra di dialogo **Gestisci provider** per configurare un provider per il servizio Web.  
  
    2.  Per specificare opzioni di pubblicazione avanzate, selezionare il pulsante **Avanzate** nella sezione **Pubblica su servizio Web** .  
  
4.  Controllare le selezioni effettuate nella pagina **Riepilogo** . Fare clic su **Indietro** per modificare le selezioni. Fare clic su **Avanti** per pubblicare gli oggetti selezionati.  
  
5.  Monitorare lo stato di pubblicazione nella pagina **Salva o pubblica script** .  
  
## Vedere anche  
 [Generazione di script &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/generate-scripts-sql-server-management-studio.md)   
 [Copia di database in altri server](../../relational-databases/databases/copy-databases-to-other-servers.md)  
  
  