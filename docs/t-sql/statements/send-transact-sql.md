---
title: SEND (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SEND_ON_CONVERSATION_TSQL
- ON_CONVERSATION_TSQL
- SEND
- SEND_TSQL
- SEND ON CONVERSATION
- ON CONVERSATION
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker], message sending
- SEND statement
- messages [Service Broker], sending
- sending messages
ms.assetid: b6e66aeb-1714-4c2b-b7c2-d386d77b0d46
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 73a1c310ce9f18dee10e3cd78003e90468b98122
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607711"
---
# <a name="send-transact-sql"></a>SEND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Invia un messaggio, utilizzando una o più conversazioni già esistenti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SEND  
   ON CONVERSATION [(]conversation_handle [,.. @conversation_handle_n][)]  
   [ MESSAGE TYPE message_type_name ]  
   [ ( message_body_expression ) ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 ON CONVERSATION *conversation_handle [.. @conversation_handle_n]*  
 Specifica le conversazioni a cui appartiene il messaggio. *conversation_handle* deve contenere un identificatore di conversazione valido. Impossibile utilizzare più di una volta lo stesso handle di conversazione.  
  
 MESSAGE TYPE *message_type_name*  
 Specifica il tipo di messaggio del messaggio inviato. Questo tipo di messaggio deve essere incluso nei contratti di servizio utilizzati da queste conversazioni. I contratti devono consentire al tipo di messaggio di essere inviato da questo lato della conversazione. Ad esempio, i servizi di destinazione delle conversazioni possono soltanto inviare messaggi specificati nel contratto come SENT BY TARGET o SENT BY ANY. Se questa clausola viene omessa, il messaggio sarà del tipo DEFAULT.  
  
 *message_body_expression*  
 Fornisce un'espressione che rappresenta il corpo del messaggio. *message_body_expression* è facoltativo. Se però *message_body_expression* è presente, l'espressione deve essere di un tipo convertibile in **varbinary(max)**. L'espressione non può essere NULL. Se questa clausola viene omessa, il corpo del messaggio sarà vuoto.  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]  
>  Se l'istruzione SEND non è la prima istruzione in un batch o in una stored procedure, l'istruzione precedente deve terminare con un punto e virgola (;).  
  
 L'istruzione SEND trasmette un messaggio dai servizi su un lato di una o più conversazioni di [!INCLUDE[ssSB](../../includes/sssb-md.md)] ai servizi sull'altro lato di tali conversazioni. L'istruzione RECEIVE viene quindi utilizzata per recuperare il messaggio inviato dalle code associate ai servizi di destinazione.  
  
 Gli handle di conversazione forniti alla clausola ON CONVERSATION derivano da una delle tre origini seguenti:  
  
-   Quando viene inviato un messaggio non in risposta a un messaggio ricevuto da un altro servizio, utilizzare l'handle di conversazione restituito dall'istruzione BEGIN DIALOG che ha creato la conversazione.  
  
-   Quando viene inviato un messaggio in risposta a un messaggio ricevuto in precedenza da un altro servizio, utilizzare l'handle di conversazione restituito dall'istruzione RECEIVE che ha restituito il messaggio originale.  
  
 In molti casi, il codice che contiene l'istruzione SEND è separato dal codice che contiene l'istruzione BEGIN DIALOG or RECEIVE che fornisce l'handle di conversazione. In questi casi, l'handle di conversazione deve essere uno degli elementi di dati nelle informazioni sullo stato passate al codice contenente l'istruzione SEND.  
  
 I messaggi inviati a servizi in altre istanze del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] vengono archiviati in una coda di trasmissione nel database corrente fino a quando non vengono trasmessi alle code dei servizi nelle istanze remote. I messaggi inviati ai servizi nella stessa istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] vengono inseriti direttamente nelle code associate a tali servizi. Se una condizione impedisce di inserire un messaggio locale direttamente nella coda del servizio di destinazione, il messaggio può essere archiviato nella coda di trasmissione fino quando la condizione non viene risolta. Questo può accadere quando si verificano alcuni tipi di errori o quando la coda del servizio di destinazione non è attiva. Per visualizzare i messaggi nella coda di trasmissione, è possibile usare la vista di sistema **sys.transmission_queue**.  
  
 SEND è un'istruzione atomica, ovvero, se l'invio di un messaggio in più conversazioni da parte di un'istruzione SEND non riesce, ad esempio perché una conversazione è si trova in stato d'errore, non verrà archiviato alcun messaggio nella coda di trasmissione o inserito in una coda del servizio di destinazione.  
  
 Service Broker ottimizza l'archiviazione e la trasmissione di messaggi inviati in più conversazioni nella stessa istruzione SEND.  
  
 I messaggi nelle code di trasmissione per un'istanza sono trasmessi in sequenza in base a:  
  
-   Livello di priorità dell'endpoint di conversazione associato.  
  
-   All'interno del livello di priorità, la sequenza di invio nella conversazione.  
  
 I livelli di priorità specificati nelle priorità di conversazione sono applicati ai messaggi nella coda di trasmissione solo se l'opzione di database HONOR_BROKER_PRIORITY è impostata su ON. Se l'opzione HONOR_BROKER_PRIORITY è impostata su OFF, a tutti i messaggi inseriti nella coda di trasmissione per tale database viene assegnato il livello di priorità predefinito di 5. I livelli di priorità non vengono applicati a un'istruzione SEND se i messaggi vengono inseriti direttamente in una coda del servizio nella stessa istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 L'istruzione SEND blocca separatamente ogni conversazione in cui viene inviato un messaggio per garantire che il recapito sia ordinato in base alle conversazioni.  
  
 L'istruzione SEND non è valida in una funzione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 Per inviare un messaggio, l'utente corrente deve disporre dell'autorizzazione RECEIVE per la coda di ogni servizio che invia il messaggio.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene avviato un dialogo e viene inviato un messaggio XML nel dialogo. Per inviare il messaggio, l'oggetto xml viene convertito in **varbinary(max)**.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER,  
        @ExpenseReport XML ;  
  
SET @ExpenseReport = < construct message as appropriate for the application > ;  
  
BEGIN DIALOG @dialog_handle  
FROM SERVICE [//Adventure-Works.com/Expenses/ExpenseClient]  
TO SERVICE '//Adventure-Works.com/Expenses'  
ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseProcessing] ;  
  
SEND ON CONVERSATION @dialog_handle  
    MESSAGE TYPE [//Adventure-Works.com/Expenses/SubmitExpense]  
    (@ExpenseReport) ;  
```  
  
 Nell'esempio seguente vengono avviati tre dialoghi e viene inviato un messaggio XML in ciascuno di essi.  
  
```  
DECLARE @dialog_handle1 UNIQUEIDENTIFIER,  
        @dialog_handle2 UNIQUEIDENTIFIER,  
        @dialog_handle3 UNIQUEIDENTIFIER,  
        @OrderMsg XML ;  
  
SET @OrderMsg = < construct message as appropriate for the application > ;  
  
BEGIN DIALOG @dialog_handle1  
FROM SERVICE [//InitiatorDB/InitiatorService]  
TO SERVICE '//TargetDB1/TargetService’  
ON CONTRACT [//AllDBs/OrderProcessing] ;  
  
BEGIN DIALOG @dialog_handle2  
FROM SERVICE [//InitiatorDB/InitiatorService]  
TO SERVICE '//TargetDB2/TargetService’  
ON CONTRACT [//AllDBs/OrderProcessing] ;  
  
BEGIN DIALOG @dialog_handle3  
FROM SERVICE [//InitiatorDB/InitiatorService]  
TO SERVICE '//TargetDB3/TargetService’  
ON CONTRACT [//AllDBs/OrderProcessing] ;  
  
SEND ON CONVERSATION (@dialog_handle1, @dialog_handle2, @dialog_handle3)  
    MESSAGE TYPE [//AllDBs/OrderMsg]  
    (@OrderMsg) ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [END CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [RECEIVE &#40;Transact-SQL&#41;](../../t-sql/statements/receive-transact-sql.md)   
 [sys.transmission_queue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)  
  
  
