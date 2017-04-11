---
title: "Backup e ripristino di indici e cataloghi full-text | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "indici full-text [SQL Server], backup"
  - "ricerca full-text [SQL Server], backup e ripristino"
  - "recupero [ricerca full-text]"
  - "backup [SQL Server], indici full-text"
  - "indici full-text [SQL Server], ripristino"
  - "operazioni di ripristino [ricerca full-text]"
ms.assetid: 6a4080d9-e43f-4b7b-a1da-bebf654c1194
caps.latest.revision: 62
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 61
---
# Backup e ripristino di indici e cataloghi full-text
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In questo argomento viene illustrato come eseguire il backup e il ripristino di indici full-text creati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il catalogo full-text è un concetto logico e non è contenuto in un filegroup. Pertanto, per eseguire il backup di un catalogo full-text in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario identificare ogni filegroup che contiene un indice full-text appartenente al catalogo, quindi eseguirne il backup uno alla volta.  
  
> [!IMPORTANT]  
>  È possibile importare cataloghi full-text quando si aggiorna un database di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Ogni catalogo full-text importato è un file di database nel proprio filegroup. Per eseguire il backup di un catalogo importato, eseguire il backup del relativo filegroup. Per altre informazioni, vedere [Backup e ripristino di cataloghi full-text](http://go.microsoft.com/fwlink/?LinkID=121052) nella documentazione online di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
##  <a name="backingup"></a> Backup degli indici full-text di un catalogo full-text  
  
###  <a name="Find_FTIs_of_a_Catalog"></a> Individuazione degli indici full-text di un catalogo full-text  
 È possibile recuperare le proprietà degli indici full-text usando l'istruzione [SELECT](../../t-sql/queries/select-transact-sql.md) seguente che consente di selezionare le colonne dalle viste del catalogo [sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md) e [sys.fulltext_catalogs](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @TableID int;  
SET @TableID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product'));  
SELECT object_name(@TableID), i.is_enabled, i.change_tracking_state,   
   i.has_crawl_completed, i.crawl_type, c.name as fulltext_catalog_name   
   FROM sys.fulltext_indexes i, sys.fulltext_catalogs c   
   WHERE i.fulltext_catalog_id = c.fulltext_catalog_id;  
GO  
```  
  
 [Contenuto dell'argomento](#top)  
  
###  <a name="Find_FG_of_FTI"></a> Individuazione del filegroup o del file che contiene un indice full-text  
 Quando viene creato, l'indice full-text viene inserito in una delle posizioni seguenti:  
  
-   Filegroup specificato dall'utente.  
  
-   Lo stesso filegroup della vista o della tabella di base, per una tabella non partizionata.  
  
-   Filegroup primario, per una tabella partizionata.  
  
> [!NOTE]  
>  Per informazioni sulla creazione di un indice full-text, vedere [Creare e gestire indici full-text](../../relational-databases/search/create-and-manage-full-text-indexes.md) e [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
 Per trovare il filegroup dell'indice full-text in una tabella o vista, usare la query seguente, dove *object_name* rappresenta il nome della tabella o della vista:  
  
```  
SELECT name FROM sys.filegroups f, sys.fulltext_indexes i   
   WHERE f.data_space_id = i.data_space_id   
      and i.object_id = object_id('object_name');  
GO  
  
```  
  
 [Contenuto dell'argomento](#top)  
  
###  <a name="Back_up_FTIs_of_FTC"></a> Backup dei filegroup che contengono gli indici full-text  
 Dopo avere trovato i filegroup che contengono gli indici di un catalogo full-text, è necessario eseguire il backup di ognuno. Durante il processo di backup non è consentito eliminare o aggiungere cataloghi full-text.  
  
 Il primo backup di un filegroup deve essere un backup di file completo. Dopo avere creato un backup di file completo per un filegroup, è possibile eseguire il backup delle sole modifiche avvenute in un filegroup creando una serie di uno o più backup di file differenziali basati sul backup di file completo.  
  
 **Per eseguire il backup di file e filegroup**  
  
-   [Eseguire il backup di file e filegroup &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md)  
  
-   [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)  
  
 [Contenuto dell'argomento](#top)  
  
##  <a name="Restore_FTI"></a> Ripristino di un indice full-text  
 Il ripristino del backup di un filegroup include il ripristino dei file di indice full-text e degli altri file nel filegroup. Per impostazione predefinita, il filegroup viene ripristinato nel percorso del disco in cui è stato eseguito il backup.  
  
 Se alla creazione del backup era online una tabella indicizzata full-text con un popolamento in corso, quest'ultimo verrà ripreso dopo il ripristino.  
  
 **Per ripristinare un filegroup**  
  
-   [Ripristinare file e filegroup &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [Ripristinare file e filegroup sovrascrivendo file esistenti &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [Ripristinare i file in una nuova posizione &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
 [Contenuto dell'argomento](#top)  
  
## Vedere anche  
 [Gestione e monitoraggio della ricerca full-text per un'istanza del server](../../relational-databases/search/manage-and-monitor-full-text-search-for-a-server-instance.md)   
 [Aggiornamento della ricerca full-text](../../relational-databases/search/upgrade-full-text-search.md)  
  
  