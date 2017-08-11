---
title: Utilizzare SQL Server Management Studio per la gestione di SQL Server in Linux | Documenti Microsoft
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 07/19/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: b2fcf858-21c3-462a-8d49-50c85647d092
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 1b16a5e8168f18a3e687fdf0249f93cd3549f27d
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="use-sql-server-management-studio-on-windows-to-manage-sql-server-on-linux"></a>Utilizzare SQL Server Management Studio in Windows per la gestione di SQL Server in Linux

Questo argomento vengono presentate [SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/en-us/library/hh213248.aspx) e viene descritto un paio di attività comuni. SQL Server Management Studio è un'applicazione Windows, pertanto utilizzare SQL Server Management Studio, quando si dispone di un computer Windows in grado di connettersi a un'istanza remota di SQL Server in Linux.

[SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/en-us/library/hh213248.aspx) fa parte di un gruppo di strumenti SQL che offerte Microsoft gratuitamente alle proprie esigenze di sviluppo e gestione. SQL Server Management Studio è un ambiente integrato per accedere, configurare, gestire, amministrare e sviluppare tutti i componenti di SQL Server in esecuzione in locale o nel cloud, Linux, Windows o Docker macOS e Database SQL di Azure e Azure SQL Data Warehouse. SSMS integra un'ampia gamma di strumenti grafici con numerosi editor di script avanzati per fornire l'accesso a SQL Server a sviluppatori e amministratori di tutti i livelli di.

SQL Server Management Studio offre un'ampia gamma di funzionalità di sviluppo e gestione per SQL Server, inclusi gli strumenti per:
- configurare, monitorare e amministrare una o più istanze di SQL Server
- distribuire, monitorare e aggiornare i componenti di livello dati, ad esempio database e i data warehouse
- backup e ripristino di database
- compilare ed eseguire script e query T-SQL e risultati
- Genera script T-SQL per gli oggetti di database
- Consente di visualizzare e modificare i dati nel database
- progettare visivamente query T-SQL e gli oggetti di database, ad esempio viste, tabelle e stored procedure

Vedere [usare SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/ms174173.aspx) per ulteriori informazioni.

## <a name="install-the-newest-version-of-sql-server-management-studio-ssms"></a>Installare la versione più recente di SQL Server Management Studio (SSMS)

Quando si utilizza SQL Server, è consigliabile utilizzare sempre la versione più recente di SQL Server Management Studio (SSMS). La versione più recente di SQL Server Management Studio viene aggiornata continuamente, ottimizzazione e attualmente funziona con SQL Server Linux su 2017. Per scaricare e installare la versione più recente, vedere [scaricare SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx). Per rimanere aggiornati, la versione più recente di SSMS chiede di quando è disponibile una nuova versione disponibile per il download. 

## <a name="before-you-begin"></a>Operazioni preliminari
- Vedere [utilizzare SQL Server Management Studio in Windows per connettersi a SQL Server in Linux](sql-server-linux-develop-use-ssms.md) per informazioni su come connettersi ed eseguire una Query tramite SQL Server Management Studio
- Lettura di [problemi noti](sql-server-linux-release-notes.md) per SQL Server 2017 RC2 in Linux

## <a name="create-and-manage-databases"></a>Creare e gestire i database
Durante la connessione al *master* database, è possibile creare database sul server e modificare o eliminare i database esistenti. I passaggi seguenti viene descritto come eseguire più comuni attività di gestione di database tramite Management Studio. Per eseguire queste attività, assicurarsi che si è connessi al *master* database con l'account di accesso dell'entità a livello di server creati quando si configura SQL Server 2017 RC2 in Linux.

### <a name="create-a-new-database"></a>Creare un nuovo database

1. Avviare SQL Server Management Studio e connettersi al server in SQL Server 2017 RC2 in Linux

2. In Esplora oggetti fare clic su di *database* cartella e quindi fare clic su * Nuovo Database... "

3. Nel *Nuovo Database* finestra di dialogo immettere un nome per il nuovo database e quindi fare clic su *OK*

Il nuovo database viene creato correttamente nel server. Se si preferisce creare un nuovo database utilizzando T-SQL, vedere [CREATE DATABASE (SQL Server Transact-SQL)](https://msdn.microsoft.com/en-us/library/ms176061.aspx).

### <a name="drop-a-database"></a>Eliminare un database

1. Avviare SQL Server Management Studio e connettersi al server in SQL Server 2017 RC2 in Linux

2. In Esplora oggetti espandere il *database* cartella per visualizzare un elenco di tutti i database nel server.

3. In Esplora oggetti fare clic sul database che si desidera eliminare e quindi fare clic su *eliminare*

4. Nel *Elimina oggetto* finestra di dialogo, controllo *Chiudi connessioni esistenti* e quindi fare clic su *OK*

Il database viene eliminato correttamente dal server. Se si preferisce eliminare un database utilizzando T-SQL, vedere [DROP DATABASE (SQL Server Transact-SQL)](https://msdn.microsoft.com/en-us/library/ms178613.aspx).

## <a name="use-activity-monitor-to-see-information-about-sql-server-activity"></a>Utilizzare Monitoraggio attività per visualizzare informazioni sulle attività di SQL Server

Il [Monitoraggio attività](https://msdn.microsoft.com/en-us/library/hh212951.aspx) strumento è incorporato in SQL Server Management Studio (SSMS) e Visualizza informazioni sui processi di SQL Server e come questi processi influiscono sull'istanza corrente di SQL Server.

1. Avviare SQL Server Management Studio e connettersi al server in SQL Server 2017 RC2 in Linux

2. In Esplora oggetti, fare doppio clic su di *server* nodo e quindi fare clic su *Monitoraggio attività*

Monitoraggio attività Mostra i riquadri espandibili e comprimibili con le seguenti informazioni:
- Panoramica
- Processi
- Attesa di risorse
- I/o File di dati
- Query recenti con costo elevato
- Query con costo elevato Active

Quando un riquadro è espanso, Monitoraggio attività esegue una query di istanza per ottenere informazioni. Quando un riquadro è compresso, significa che tutte le relative attività di query sono arrestate. È possibile espandere uno o più riquadri contemporaneamente per visualizzare diversi tipi di attività sull'istanza.

## <a name="see-also"></a>Vedere anche
- [Utilizzo di SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/ms174173.aspx)
- [Esportare e importare un database con SSMS](sql-server-linux-migrate-ssms.md)
- [Esercitazione su SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/bb934498.aspx)
- [Esercitazione: Scrittura di istruzioni Transact-SQL](https://msdn.microsoft.com/en-us/library/ms365303.aspx)
- [Monitoraggio delle prestazioni e dell'attività del server](https://msdn.microsoft.com/en-us/library/ms191511.aspx)
