---
title: "Aggiungere file di dati o file di log a un database | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "log [SQL Server], file"
  - "aggiunta di file di dati"
  - "aggiunta di file"
  - "aggiunta di file di log"
  - "aggiunte di file [SQL Server], passaggi"
  - "file [SQL Server], aggiunta"
  - "aggiunte di dati [SQL Server]"
ms.assetid: 8ead516a-1334-4f40-84b2-509d0a8ffa45
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Aggiungere file di dati o file di log a un database
  In questo argomento si descrive come aggiungere file di dati o di log a un database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per aggiungere file di dati o file di log a un database utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Non è possibile aggiungere o rimuovere un file durante l'esecuzione di un'istruzione BACKUP.  
  
-   Per ogni database è possibile specificare un massimo di 32.767 file e 32.767 filegroup.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per aggiungere file di dati o file di log a un database  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , quindi espandere questa istanza.  
  
2.  Espandere **Databases**, fare clic con il pulsante destro del mouse sul database dal quale aggiungere i file e quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà database** selezionare la pagina **File** .  
  
4.  Per aggiungere un file di dati o di log delle transazioni, fare clic su **Aggiungi**.  
  
5.  Nella griglia **File di database** immettere un nome logico per il file. Il nome deve essere univoco all'interno del database.  
  
6.  Selezionare il tipo di file, dati oppure log.  
  
7.  Per un file di dati, selezionare il filegroup nel quale includere il file dall'elenco, oppure selezionare **<nuovo filegroup>\>** per creare un nuovo filegroup. Non è possibile inserire log delle transazioni nei filegroup.  
  
8.  Specificare le dimensioni iniziali del file. Creare file di dati delle dimensioni maggiori possibili, corrispondenti alla quantità massima di dati che si prevede di includere nel database.  
  
9. Per specificare le modalità di aumento delle dimensioni del file, fare clic su **...** nella colonna **Aumento automatico**. Selezionare una delle seguenti opzioni:  
  
    1.  Per consentire l'aumento del file attualmente selezionato qualora sia necessario un maggiore spazio per i dati, selezionare la casella di controllo **Abilita aumento automatico dimensioni** e quindi selezionare una delle opzioni seguenti:  
  
    2.  Per fare in modo che le dimensioni del file aumentino a incrementi fissi, selezionare **In megabyte** e specificare un valore.  
  
    3.  Per fare in modo che le dimensioni del file aumentino di una quantità pari a una percentuale delle dimensioni correnti del file, selezionare **In percentuale** e specificare un valore.  
  
10. Per specificare il limite delle dimensioni del file, impostare le opzioni seguenti nel modo desiderato:  
  
    1.  Per specificare le dimensioni massime che possono essere raggiunte dal file, selezionare **Limite aumento in MB** e specificare un valore.  
  
    2.  Per fare in modo che le dimensioni del file aumentino secondo le necessità, selezionare **Aumento illimitato**.  
  
    3.  Per impedire che il file aumenti, deselezionare la casella di controllo **Abilita aumento automatico dimensioni** . Le dimensioni del file non aumenteranno oltre il valore specificato nella colonna **Dimensioni iniziali (MB)**.  
  
    > [!NOTE]  
    >  Le dimensioni massime del database sono comunque determinate dalla quantità di spazio disponibile su disco e dalle limitazioni previste dalla licenza della versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uso.  
  
11. Specificare il percorso per la posizione del file. È necessario che il percorso specificato sia esistente prima dell'aggiunta del file.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, i dati e i log delle transazioni vengono inseriti sulla stessa unità e sullo stesso percorso per sistemi a unità singola, ma questa procedura potrebbe non essere ottimale per ambienti di produzione. Per altre informazioni, vedere [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md).  
  
12. Scegliere **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per aggiungere file di dati o file di log a un database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. Nell'esempio si aggiunge un filegroup con due file a un database. Inoltre, si crea il filegroup `Test1FG1` nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] e si aggiungono due file da 5 MB al filegroup.  
  
 [!code-sql[DatabaseDDL#AlterDatabase2](../../relational-databases/databases/codesnippet/tsql/add-data-or-log-files-to_1.sql)]  
  
 Per altri esempi, vedere [Opzioni per file e filegroup ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md).  
  
## Vedere anche  
 [Filegroup e file di database](../../relational-databases/databases/database-files-and-filegroups.md)   
 [Eliminare file di dati o file di log da un database](../../relational-databases/databases/delete-data-or-log-files-from-a-database.md)   
 [Aumentare le dimensioni di un database](../../relational-databases/databases/increase-the-size-of-a-database.md)  
  
  