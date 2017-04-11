---
title: "Editor attivit&#224; Inserimento bulk (pagina Opzioni) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.bulkinserttask.options.f1"
helpviewer_keywords: 
  - "Editor attività Inserimento bulk"
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# Editor attivit&#224; Inserimento bulk (pagina Opzioni)
  Utilizzare la pagina **Opzioni** della finestra di dialogo **Editor attività Inserimento bulk** per impostare le proprietà relative all'operazione di inserimento bulk. L'attività Inserimento bulk consente di copiare grandi quantità di dati all'interno di una vista o tabella di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Per altre informazioni sull'uso degli inserimenti di massa, vedere [Attività Inserimento bulk](../../integration-services/control-flow/bulk-insert-task.md) e [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
## Opzioni  
 **CodePage**  
 Consente di specificare la tabella codici dei dati contenuti nel file.  
  
 **DataFileType**  
 Consente di specificare il valore di tipo di dati da utilizzare nell'operazione di caricamento.  
  
 **BatchSize**  
 Consente di specificare il numero di righe di un batch. Il valore predefinito è l'intero file di dati. Se si imposta **BatchSize** su zero, i dati vengono caricati in un singolo batch.  
  
 **LastRow**  
 Consente di specificare l'ultima riga da copiare.  
  
 **FirstRow**  
 Consente di specificare la riga dalla quale iniziare la copia.  
  
 **Opzioni**  
 |Nome|Definizione|  
|----------|----------------|  
|**Vincoli CHECK**|Selezionare questa opzione per verificare i vincoli di colonna e tabella.|  
|**Mantieni valori Null**|Selezionare questa opzione per mantenere i valori Null durante l'operazione di inserimento bulk anziché inserire tutti i valori predefiniti per le colonne vuote.|  
|**Consenti IDENTITY_INSERT**|Selezionare questa opzione per inserire valori esistenti in una colonna Identity.|  
|**Blocco a livello di tabella**|Selezionare questa opzione per bloccare la tabella durante l'inserimento bulk.|  
|**Attive trigger**|Selezionare questa opzione per attivare tutti i trigger di eliminazione, aggiornamento o inserimento nella tabella.|  
  
 **SortedData**  
 Consente di specificare la clausola ORDER BY nell'istruzione di inserimento bulk. Il nome della colonna deve corrispondere a una colonna valida della tabella di destinazione. Il valore predefinito è **false**. Questo valore implica che i dati non vengono ordinati da una clausola ORDER BY.  
  
 **MaxErrors**  
 Consente di specificare il numero massimo di errori che possono verificarsi prima dell'annullamento dell'operazione di inserimento bulk. Un valore pari a 0 indica che è consentito un numero infinito di errori.  
  
> [!NOTE]  
>  Ogni riga che non è possibile importare tramite l'operazione di caricamento bulk viene considerata un errore.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Inserimento bulk &#40;pagina Generale&#41;](../../integration-services/control-flow/bulk-insert-task-editor-general-page.md)   
 [Editor attività Inserimento bulk &#40;pagina Connessione&#41;](../../integration-services/control-flow/bulk-insert-task-editor-connection-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  