---
title: Quali sono le novità nel sistema di piattaforma Analitica – un warehouse dati di tipo scale-out
description: Vedere novità Microsoft® Analitica Platform System, uno strumento di scalabilità orizzontale in locale che ospita MPP SQL Server Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: bc9b0e8b89fb7fd6e507e9e615190fef21a94466
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461106"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Quali sono le novità nel sistema di piattaforma Analitica, di un data warehouse di tipo scale-out MPP
Vedere Novità gli ultimi aggiornamenti di Appliance per Microsoft® Analitica piattaforma di strumenti analitici. I punti di accesso è un'appliance di scalabilità orizzontale in locale che ospita MPP SQL Server Parallel Data Warehouse. 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"
<a name="h2-aps-cu7.1"></a>
## <a name="aps-cu71"></a>APS CU7.1
Data di rilascio - luglio 2018

### <a name="dbcc-commands-do-not-consume-concurrency-slots-behavior-change"></a>Comandi DBCC non usano gli slot di concorrenza (modifica del comportamento)
I punti di accesso supporta un subset T-SQL [comandi DBCC](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-transact-sql) , ad esempio [DBCC DROPCLEANBUFFERS](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql). In precedenza, questi comandi richiederebbe una [slot di concorrenza](https://docs.microsoft.com/sql/analytics-platform-system/workload-management?view=aps-pdw-2016-au7#concurrency-slots) riducendo il numero di caricamenti/le query utente che potrebbero essere eseguite. Il `DBCC` comandi vengono ora eseguiti in una coda locale che non usano uno slot di concorrenza utente miglioramento complessivo delle prestazioni di esecuzione di query.

### <a name="replaces-some-metadata-calls-with-catalog-objects"></a>Sostituisce alcune chiamate di metadati con oggetti del catalogo
Utilizzando oggetti del catalogo per le chiamate di metadati anziché utilizzare SMO è stato illustrato il miglioramento delle prestazioni nella piattaforma di strumenti analitici. A partire da CU7.1, alcune di queste chiamate metadati ora di usare oggetti del catalogo per impostazione predefinita. Questo comportamento può essere disattivato dagli [opzione della funzionalità](appliance-feature-switch.md) se i clienti che usano query sui metadati eventuali problemi.

### <a name="bug-fixes"></a>Correzioni di bug
È stato aggiornato a SQL Server 2016 SP2 CU2 con CU7.1 APS. L'aggiornamento risolve alcuni problemi descritti di seguito.

| Title | Description |
|:---|:---|
| **Potenziali deadlock di motore di tuple di tupla** |L'aggiornamento consente di risolvere una possibilità lungo discusso di deadlock distribuita tupla e transazione mover thread in background. Dopo aver installato CU7.1, i clienti che hanno utilizzato TF634 per arrestare il processo tuple-mover come parametro di avvio di SQL Server o il flag di traccia globale possono rimuoverla. | 
| **Alcune query lag/lead ha esito negativo** |Alcune query sulle tabelle di indice ColumnStore cluster con le funzioni lag/lead annidati che verrebbe errore è stato corretto con questo aggiornamento. | 


<a name="h2-aps-au7"></a>
## <a name="aps-au7"></a>APS AU7
Data di rilascio: maggio 2018

APS 2016 è un prerequisito per l'aggiornamento a AU7. Di seguito sono nuove funzionalità di piattaforma di strumenti analitici AU7:

### <a name="auto-create-and-auto-update-statistics"></a>Crea automaticamente e l'aggiornamento automatico statistiche
APS AU7 crea e aggiorna le statistiche automaticamente, per impostazione predefinita. Per aggiornare le impostazioni delle statistiche, gli amministratori possono utilizzare una nuova voce di menu funzionalità commutatore nel [Configuration Manager](appliance-configuration.md#CMTasks). Il [opzione della funzionalità](appliance-feature-switch.md) controlla il auto-create, l'aggiornamento automatico e il comportamento di aggiornamento asincrono delle statistiche. È anche possibile aggiornare le statistiche con il [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) istruzione.

### <a name="t-sql"></a>T-SQL
Selezionare @var è ora supportato. Per altre informazioni, vedere [selezionare variabile locale] (/ sql/t-sql/language-elements/select-local-variable-transact-sql) 

Hint per la query HASH e gruppo sono ora supportati. Per altre informazioni, vedere [Hints(Transact-SQL) - Query] (/ / t-sql/query/hint-transact-sql-query sql)

### <a name="feature-switch"></a>Opzione della funzionalità
APS AU7 introduce funzionalità commutatore in [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled e DmsProcessStopMessageTimeoutInSeconds sono ora opzioni configurabili che possono essere modificate dagli amministratori.

### <a name="known-issues"></a>Problemi noti
Software AU7 APS, viene fornito un aggiornamento del BIOS Intel che consente di risolvere un problema designato come *attacchi al canale laterale dell'esecuzione speculativa*. Gli attacchi tendere a sfruttare cosiddetti *vulnerabilità Spectre e Meltdown*. Anche se incluso nel pacchetto insieme ai punti di accesso, l'aggiornamento del BIOS viene installato manualmente e non come parte dell'installazione del software AU7 APS.

Si consiglia di tutti i clienti per installare il BIOS aggiornato. Microsoft è misurato l'effetto del Kernel virtuale indirizzo Shadowing (KVAS), Kernel pagina tabella di riferimento indiretto si esegue e mitigazione indiretta stima ramo (IBP) in vari carichi di lavoro SQL nei diversi ambienti. Le misurazioni TransportCredentialOnly una riduzione significativa delle alcuni carichi di lavoro. In base ai risultati, è consigliabile testare l'effetto sulle prestazioni dell'abilitazione dell'aggiornamento del BIOS prima di distribuirli in un ambiente di produzione. Vedere le indicazioni di SQL Server [qui](https://support.microsoft.com/en-us/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"
<a name="h2-aps-au6"></a>
## <a name="aps-2016"></a>APS 2016
Questa sezione viene descritto le nuove funzionalità per APS 2016 AU6.

### <a name="sql-server-2016"></a>SQL Server 2016

APS AU6 viene eseguito nell'ultima versione di SQL Server 2016 e Usa il livello di compatibilità database 130 predefinito. SQL Server 2016 consente il supporto per le nuove funzionalità, ad esempio:

- Indici secondari per gli indici columnstore cluster.
- Protocollo Kerberos per PolyBase.

### <a name="t-sql"></a>T-SQL
APS AU6 supporta questi miglioramenti di compatibilità di T-SQL.  Questi elementi del linguaggio aggiuntive rendono più semplice eseguire la migrazione da SQL Server e altre origini dati. 

- [Regole di confronto SQL a livello di colonna][] sono ora supportati, oltre alle regole di confronto di Windows.
- [Indici non cluster in indici columnstore cluster][] migliorare le prestazioni delle query che cercano valori specifici in corrispondenza dell'indice columnstore cluster. 
- [SELECT...INTO][] 
- [sp_spaceused()][] consente di visualizzare lo spazio su disco usato o riservato in una tabella o database.
- [Tabelle estese in larghezza][] supporto equivale a SQL Server 2016. Il precedente limite di 32 KB per le dimensioni di riga non esiste più. 

**Tipi di dati**

- [Varchar (max)][], [nvarchar (max)][] e [varbinary (max)][]. Questi tipi di dati LOB hanno una dimensione massima di 2 GB. Per caricare questi oggetti di uso [utilità bcp][]. Polybase e dwloader non attualmente supportano questi tipi di dati. 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [NUMERIC][] e tipi di dati decimale.

**Funzioni finestra**

- [ROWS o RANGE][] nella clausola OVER dell'istruzione SELECT.
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

**Funzioni di sicurezza**

- [CHECKSUM()][] e [BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

**Funzioni aggiuntive**

- [NEWID()][]
- [RAND()][]

### <a name="polybasehadoop-enhancements"></a>Miglioramenti di PolyBase/Hadoop

- Compatibilità con Hortonworks HDP 2.4 e 2.5 HDP
- Supporto per Kerberos tramite le credenziali con ambito database
- Supporto di credenziali con i BLOB di archiviazione di Azure

### <a name="install-and-upgrade-enhancements"></a>Miglioramenti di aggiornamento e installazione

**Gli aggiornamenti di architettura Enterprise** l'aggiornamento all'appliance esistente a AU6 APS viene installato il firmware più recente e gli aggiornamenti dei driver, che includono correzioni della sicurezza. 

Una nuova appliance da HPE o DELL include tutti gli aggiornamenti più recenti plus:

- Supporto per processori di ultima generazione (Broadwell)
- Aggiornamento di moduli DIMM DDR4
- Miglioramento della velocità effettiva DIMM

**Integrazione di**

- Completamente il supporto del nome di dominio completo (FQDN) rende possibile configurare un trust di dominio per l'appliance. 
- Per usare FQDN, è necessario eseguire un aggiornamento completo e acconsenti esplicitamente durante l'aggiornamento. 

**Tempi di inattività ridotti** installazione o l'aggiornamento a AU6 APS risulta più rapida e richiede tempi di inattività inferiori rispetto alle versioni precedenti. Per ridurre i tempi di inattività, l'installazione o l'aggiornamento: 

 - Semplifica ottenuto applicando gli aggiornamenti di WSUS mediante un'immagine che contiene tutti gli aggiornamenti a giugno 2016
 - Si applica gli aggiornamenti della sicurezza con gli aggiornamenti firmware e driver
 - Inserisce i hotfix più recenti e l'utilità di verifica di appliance (PAV) nell'appliance in modo che siano pronti per l'installazione senza la necessità di eseguirne il download.

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[Regole di confronto SQL a livello di colonna]: ~/relational-databases/collations/collation-and-unicode-support.md

[Indici non cluster in indici columnstore cluster]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR (MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR (MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY (MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[SELECT...INTO]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Tabelle estese in larghezza]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[Utilità bcp]:/sql/tools/bcp-utility
[UNIQUEIDENTIFIER]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[NUMERIC]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[ROWS o RANGE]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[CHECKSUM()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[NEWID()]:/sql/t-sql/functions/newid-transact-sql
[RAND()]:/sql/t-sql/functions/rand-transact-sql


  

  


