---
title: Funzione LocalDBStartInstance | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- LocalDBStartInstance
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: cb325f5d-10ee-4a56-ba28-db0074ab3926
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e95a20d3984d6f32a4ba78155edb116e4cb9cc32
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818619"
---
# <a name="localdbstartinstance-function"></a>Funzione LocalDBStartInstance
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Avvia l'istanza specificata del database locale di SQL Server Express.  
  
 **File di intestazione:** SQLNCLI. h  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT LocalDBStartInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           LPWSTR wszSqlConnection,   
           LPDWORD lpcchSqlConnection   
);  
```  
  
## <a name="parameters"></a>Parametri  
 *pInstanceName*  
 [Input] Nome dell'istanza del database locale da avviare.  
  
 *dwFlags*  
 [Input] Riservato per utilizzi futuri. Deve essere impostato attualmente su 0.  
  
 *wszSqlConnection*  
 [Output] Buffer per archiviare la stringa di connessione nell'istanza del database locale.  
  
 *lpcchSqlConnection*  
 [Input/Output] Contiene la dimensione di input il *wszSqlConnection* buffer in caratteri, inclusi gli spazi vuoti finali. In fase di output, se le dimensioni del buffer specificate sono troppo piccole, nel parametro sono contenute le dimensioni del buffer richieste in caratteri, inclusi gli spazi vuoti finali.  
  
## <a name="returns"></a>Valori di codice restituiti  
 S_OK  
 Funzione completata.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 Database locale di SQL Server Express non installato nel computer.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Uno o più parametri di input specificati non validi.  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 Nome dell'stanza specificata non valido.  
  
 [LOCALDB_ERROR_UNKNOWN_INSTANCE](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-instance.md)  
 Istanza inesistente.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../../relational-databases/express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Il buffer specificato *wszSqlConnection* è troppo piccolo.  
  
 [LOCALDB_ERROR_WAIT_TIMEOUT](../../relational-databases/express-localdb-error-messages/localdb-error-wait-timeout.md)  
 Timeout durante il tentativo di acquisizione dei blocchi di sincronizzazione.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../../relational-databases/express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Percorso di archiviazione richiesto per l'istanza più lungo di MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 Impossibile recuperare una cartella del profilo utente.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 Impossibile accedere alla cartella di un'istanza.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Impossibile accedere al Registro di sistema di un'istanza.  
  
 [LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 Impossibile modificare il Registro di sistema di un'istanza.  
  
 [LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-create-sql-process.md)  
 Impossibile creare un processo per SQL Server.  
  
 [LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 Avviato processo di SQL Server ma tale operazione non è stata completata.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../../relational-databases/express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Configurazione di un'istanza danneggiata.  
  
 [LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-auto-instance-create-failed.md)  
 Impossibile creare un'istanza automatica. Per informazioni sugli errori, vedere il registro eventi applicazioni di Windows.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Errore imprevisto. Per informazioni, vedere il registro eventi.  
  
## <a name="details"></a>Dettagli  
 Sia l'argomento di buffer di connessione (*wszSqlConnection*) e l'argomento di dimensione del buffer di connessione (*lpcchSqlConnection*) sono facoltativi. Nella tabella seguente vengono mostrate le opzioni per l'utilizzo di questi argomenti e dei relativi risultati.  
  
|Buffer|Dimensioni del buffer|Spiegazione|Azione|  
|------------|-----------------|---------------|------------|  
|NULL|NULL|L'utente desidera avviare l'istanza e non necessita di un nome della pipe.|Viene avviata un'istanza. Non viene restituita alcuna pipe né le dimensioni del buffer richieste.|  
|NULL|Presente|L'utente richiede le dimensioni del buffer di output. Nella chiamata successiva probabilmente l'utente richiederà un avvio effettivo.|Vengono restituite le dimensioni del buffer richieste (nessun avvio né restituzione di pipe). Il risultato è S_OK.|  
|Presente|NULL|Non consentito. Input non corretto.|Il risultato restituito è LOCALDB_ERROR_INVALID_PARAMETER.|  
|Presente|Presente|L'utente desidera avviare l'istanza e necessita del nome della pipe per la connessione a quest'ultima dopo il relativo avvio.|Vengono controllate le dimensioni del buffer, viene avviata l'istanza e viene restituito il nome della pipe nel buffer. <br />Tramite l'argomento relativo alle dimensioni del buffer viene restituita la lunghezza della stringa "server=", senza includere valori Null di terminazione.|  
  
 Per un esempio di codice che utilizza l'API LocalDB, vedere [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulla versione e intestazione di SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
