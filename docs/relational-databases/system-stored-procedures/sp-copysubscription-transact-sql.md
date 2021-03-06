---
title: sp_copysubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_copysubscription
- sp_copysubscription_TSQL
helpviewer_keywords:
- sp_copysubscription
ms.assetid: 3c56cd62-2966-4e87-a986-44cb3fd0b760
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a0bb6f6614e1a19108faf2be780772508627af1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702379"
---
# <a name="spcopysubscription-transact-sql"></a>sp_copysubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  La funzionalità di sottoscrizione collegabile è deprecata e verrà rimossa a partire da una delle prossime versioni. Evitare di utilizzare questa funzionalità in un nuovo progetto di sviluppo. Nel caso di pubblicazioni di tipo merge partizionate mediante filtri con parametri, è consigliabile utilizzare la nuove funzionalità degli snapshot partizionati, che semplificano l'inizializzazione di un ampio numero di sottoscrizioni. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md). Per le pubblicazioni non partizionate, è possibile inizializzare una sottoscrizione con un backup. Per altre informazioni, vedere [Inizializzazione di una sottoscrizione transazionale senza uno snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 Copia un database di sottoscrizione che include sottoscrizioni pull, ma non push. È possibile copiare solo database a file singolo. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_copysubscription [ @filename = ] 'file_name'  
    [ , [ @temp_dir = ] 'temp_dir' ]  
    [ , [ @overwrite_existing_file = ] overwrite_existing_file]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@filename =**] **'***file_name***'**  
 Stringa che specifica il percorso completo, compreso il nome del file, in cui salvare una copia del file con estensione mdf. *nome del file* viene **nvarchar(260)**, non prevede alcun valore predefinito.  
  
 [  **@temp_dir=**] **'***temp_dir***'**  
 Nome della directory contenente i file temporanei. *temp_dir* viene **nvarchar(260)**, con un valore predefinito è NULL. Se NULL, il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà usata la directory dati predefinita. Nella directory deve essere disponibile spazio sufficiente per l'archiviazione di un file le cui dimensioni sono pari alla somma delle dimensioni di tutti i file di database del Sottoscrittore.  
  
 [  **@overwrite_existing_file=**] **'***overwrite_existing_file***'**  
 Flag booleano facoltativo che specifica se sovrascrivere un file esistente con lo stesso nome specificato nel **@filename**. *overwrite_existing_file*viene **bit**, il valore predefinito è **0**. Se **1**, sovrascrive il file specificato da **@filename**, se presente. Se **0**, la stored procedure ha esito negativo se il file esiste e il file non viene sovrascritto.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_copysubscription** viene utilizzato in tutti i tipi di replica per copiare un database di sottoscrizione in un file come alternativa all'applicazione di uno snapshot nel Sottoscrittore. Il database deve essere configurato in modo che supporti solo le sottoscrizioni pull. Gli utenti che dispongono delle autorizzazioni appropriate possono eseguire copie del database di sottoscrizione e quindi inviare tramite posta elettronica, copiare o trasferire il file ottenuto (con estensione msf) in un altro Sottoscrittore, dove è possibile collegarlo come sottoscrizione.  
  
 Le dimensioni del database di sottoscrizione copiato devono essere inferiori a 2 gigabyte (GB)  
  
 **sp_copysubscription** è supportata solo per i database con sottoscrizioni client e non può essere eseguita quando il database ha sottoscrizioni server.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_copysubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Posizioni alternative della cartella snapshot](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
