---
title: "Genera filtri | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.generatefilters.f1"
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Genera filtri
  La finestra di dialogo **Genera filtri** consente di definire un filtro di riga in una tabella in una pubblicazione di tipo merge. Durante la replica, il filtro viene esteso automaticamente alle altre tabelle correlate tramite relazioni di chiave esterna. Se ad esempio si definisce un filtro in una tabella clienti in modo che contenga solo dati su clienti francesi, la replica estenderà tale filtro affinché nelle tabelle degli ordini e dei dettagli ordine correlate vengano incluse solo informazioni relative ai clienti francesi.  
  
## Opzioni  
 Questa finestra di dialogo prevede un processo in tre passaggi per la creazione di un filtro di riga in una tabella. Il filtro viene quindi esteso alle tabelle correlate a quella su cui viene applicato il filtro tramite relazioni di chiave esterna e primaria. Si supponga ad esempio di disporre delle tre tabelle **Cliente**, **IntestazioneOrdineVendita**e **DettagliOrdineVendita**, in cui **Cliente** è correlata a **IntestazioneOrdineVendita**e **IntestazioneOrdineVendita** è correlata a **DettagliOrdineVendita**. Se si applica un filtro di riga a **Cliente**, la replica estenderà tale filtro a **IntestazioneOrdineVendita** e a **DettagliOrdineVendita**.  
  
1.  **Selezionare la tabella da filtrare.**  
  
     Selezionare una tabella dall'elenco a discesa. Le tabelle verranno visualizzate nella casella di riepilogo solo se sono state selezionate nella pagina **Articoli** .  
  
2.  **Completare l'istruzione per il filtro per identificare le righe della tabella che verranno ricevute dai Sottoscrittori.**  
  
     Consente di definire una nuova istruzione per il filtro. Nella casella di riepilogo **Colonne** vengono elencate tutte le colonne in fase di pubblicazione appartenenti alla tabella selezionata in **Selezionare la tabella da filtrare**. L'area di testo **Istruzione per il filtro** contiene il testo predefinito, nel formato seguente:  
  
     `SELECT <published_columns> FROM [tableowner].[tablename] WHERE`  
  
     Questo testo non può essere modificato. Digitare la clausola di filtro dopo la parola chiave WHERE utilizzando la sintassi [!INCLUDE[tsql](../../includes/tsql-md.md)] standard.  
  
    > [!IMPORTANT]  
    >  Per motivi relativi alle prestazioni, è consigliabile evitare di applicare funzioni ai nomi di colonna nelle clausole di filtro di riga con parametri, come `LEFT([MyColumn]) = SUSER_SNAME()`. Se si usano HOST_NAME in una clausola di filtro e si sostituisce il valore HOST_NAME, può essere necessario convertire i tipi di dati tramite l'istruzione CONVERT. Per ulteriori informazioni sulle procedure consigliate in questo caso, vedere la sezione "Si esegue l'override del valore di HOST_NAME ()" nell'argomento [i filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
3.  **Specificare se i dati di questa tabella dovranno essere inviati a una o più sottoscrizioni.**  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. La replica di tipo merge consente di specificare il tipo di partizioni più adatte ai dati e all'applicazione. Se si seleziona **Una riga di questa tabella verrà inviata a una sola sottoscrizione**, viene impostata l'opzione relativa alle partizioni non sovrapposte della replica di tipo merge. Le partizioni non sovrapposte vengono utilizzate insieme alle partizioni pre-calcolate per migliorare le prestazioni per ridurre il costo di caricamento associato alle partizioni pre-calcolate. Il vantaggio a livello di prestazioni delle partizioni non sovrapposte è più evidente quando i filtri con parametri e i filtri join utilizzati sono più complessi. Se si seleziona questa opzione è necessario, tuttavia, verificare che i dati vengano partizionati in modo che una riga non possa essere replicata in più Sottoscrittori. Per altre informazioni, vedere la sezione relativa all'impostazione delle opzioni delle partizioni nell'argomento [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 Dopo aver aggiunto un filtro, fare clic su **OK** per chiudere la finestra di dialogo. Il filtro specificato viene analizzato ed eseguito sulla tabella nella clausola SELECT. Se nell'istruzione di filtro sono presenti errori di sintassi o di altro tipo, verrà visualizzato un apposito messaggio di notifica e sarà possibile modificare l'istruzione.  
  
 Al termine dell'analisi dell'istruzione, la replica creerà i filtri join necessari. Se non è stato ancora configurato il server di distribuzione per il server di pubblicazione su cui viene eseguita la procedura guidata, verrà chiesto di eseguire tale operazione.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Filtro dei dati pubblicati](../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtri join](../../relational-databases/replication/merge/join-filters.md)   
 [Filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  