---
title: "DDL FileTable, funzioni, stored Procedure e viste | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FileTable [SQL Server], oggetti di database"
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# DDL FileTable, funzioni, stored Procedure e viste
  Vengono elencate le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] e gli oggetti di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aggiunti o modificati per supportare la funzionalità FileTable in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La colonna Stato nelle tabelle seguenti indica se l'elemento è nuovo in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o è presente nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ma è stato modificato in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] per supportare la ricerca semantica.  
  
 Per l'elenco di istruzioni e oggetti di database che supportano FILESTREAM, vedere [FILESTREAM DDL, Functions, Stored Procedures, and Views](../../relational-databases/blob/filestream-ddl-functions-stored-procedures-and-views.md).  
  
##  <a name="ddl"></a> Istruzioni Transact-SQL DDL (Data Definition Language)  
  
|Oggetto|Stato|Ulteriori informazioni|  
|------------|------------|----------------------|  
|[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)<br /><br /> [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)|Modificato|[Abilitazione dei prerequisiti per la tabella FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)<br /><br /> [Gestione di tabelle FileTable](../../relational-databases/blob/manage-filetables.md)|  
|[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)|Modificato|[Creare, modificare e rilasciare FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)<br /><br /> [Gestione di tabelle FileTable](../../relational-databases/blob/manage-filetables.md)|  
|[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)|Modificato|[Abilitazione dei prerequisiti per la tabella FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)|  
|[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)|Modificato|[Creare, modificare e rilasciare FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)|  
|[RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)<br /><br /> [Argomenti RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20Arguments%20\(Transact-SQL\).md)|Modificato||  
  
##  <a name="func"></a> Funzioni  
  
|Oggetto|Stato|Ulteriori informazioni|  
|------------|------------|----------------------|  
|[FileTableRootPath &#40;Transact-SQL&#41;](../../relational-databases/system-functions/filetablerootpath-transact-sql.md)|**Aggiunto**|[Utilizzare directory e percorsi in FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
|[GetFileNamespacePath &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getfilenamespacepath-transact-sql.md)|**Aggiunto**|[Utilizzare directory e percorsi in FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
|[GetPathLocator &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getpathlocator-transact-sql.md)|**Aggiunto**|[Utilizzare directory e percorsi in FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
  
##  <a name="sproc"></a> Stored procedure  
  
|Oggetto|Stato|Ulteriori informazioni|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../Topic/sp_kill_filestream_non_transacted_handles%20\(Transact-SQL\).md)|**Aggiunto**|[Gestione di tabelle FileTable](../../relational-databases/blob/manage-filetables.md)|  
  
##  <a name="cv"></a> Viste del catalogo  
  
|Oggetto|Stato|Ulteriori informazioni|  
|------------|------------|----------------------|  
|[sys.database_filestream_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)|**Aggiunto**|[Abilitazione dei prerequisiti per la tabella FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)|  
|[sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql.md)|**Aggiunto**|[Creare, modificare e rilasciare FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)<br /><br /> [Gestione di tabelle FileTable](../../relational-databases/blob/manage-filetables.md)|  
|[sys.filetables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetables-transact-sql.md)|**Aggiunto**|[Gestione di tabelle FileTable](../../relational-databases/blob/manage-filetables.md)|  
|[sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)|Modificato|[Gestione di tabelle FileTable](../../relational-databases/blob/manage-filetables.md)|  
  
##  <a name="dmv"></a> DMV  
  
|Oggetto|Stato|Ulteriori informazioni|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)|**Aggiunto**|[Gestione di tabelle FileTable](../../relational-databases/blob/manage-filetables.md)|  
  
## Vedere anche  
 [Gestione di tabelle FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  