---
title: Editor attività Invia messaggi (pagina messaggio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3f8c4992477fa5bdbf533f3a1933c4092f1d162c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089500"
---
# <a name="send-mail-task-editor-mail-page"></a>Editor attività Invia messaggi (pagina Messaggio)
  Usare la pagina **Messaggio** della finestra di dialogo **Editor attività Invia messaggi** per specificare i destinatari, il tipo di messaggio e la priorità relativi a un messaggio. È inoltre possibile allegare file al messaggio. Il testo del messaggio può essere una stringa specificata, una connessione a un file che contiene il testo o il nome di una variabile che contiene il testo.  
  
 Per ulteriori informazioni su questa attività, vedere [Send Mail Task](control-flow/send-mail-task.md).  
  
## <a name="options"></a>Opzioni  
 **SMTPConnection**  
 Selezionare una gestione connessione SMTP nell'elenco oppure fare clic su **\<Nuova connessione>** per creare una nuova gestione connessione.  
  
> [!IMPORTANT]  
>  La gestione connessione SMTP supporta solo l'autenticazione anonima e l'autenticazione di Windows. Non supporta l'autenticazione di base.  
  
 **Argomenti correlati:** [Gestione connessione SMTP](connection-manager/smtp-connection-manager.md)  
  
 **From**  
 Consente di specificare l'indirizzo di posta elettronica del mittente.  
  
 **Per**  
 Consente di specificare gli indirizzi di posta elettronica dei destinatari, separati da punti e virgola.  
  
 **Cc**  
 Consente di specificare gli indirizzi di posta elettronica, separati da punti e virgola, di altri destinatari che riceveranno copie del messaggio.  
  
 **Bcc**  
 Consente di specificare gli indirizzi di posta elettronica, separati da punti e virgola, di destinatari in copia nascosta che riceveranno copie del messaggio.  
  
 **Oggetto**  
 Consente di specificare l'oggetto del messaggio di posta elettronica.  
  
 **MessageSourceType**  
 Consente di selezionare il tipo di origine del messaggio. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|**Input diretto**|Consente di impostare l'origine sul testo del messaggio. Selezionando questo valore, verrà visualizzata l'opzione dinamica **MessageSource**.|  
|**Connessione file**|Consente di impostare l'origine sul file contenente il testo del messaggio. Selezionando questo valore, verrà visualizzata l'opzione dinamica **MessageSource**.|  
|**Variabile**|Consente di impostare l'origine su una variabile contenente il testo del messaggio. Selezionando questo valore, verrà visualizzata l'opzione dinamica **MessageSource**.|  
  
 **Priorità**  
 Consente di impostare il livello di priorità del messaggio.  
  
 **Allegati**  
 Consente di specificare i nomi file degli allegati del messaggio di posta elettronica, separati dal carattere di barra verticale (|).  
  
> [!NOTE]  
>  Le righe A, Cc e Ccn sono limitate a 256 caratteri, in conformità con gli standard Internet.  
  
## <a name="messagesourcetype-dynamic-options"></a>Opzioni dinamiche MessageSourceType  
  
### <a name="messagesourcetype--direct-input"></a>MessageSourceType = Input diretto  
 **MessageSource**  
 Digitare il testo del messaggio oppure fare clic sul pulsante Sfoglia (…), quindi digitare il messaggio nella finestra di dialogo **Origine messaggio** .  
  
### <a name="messagesourcetype--file-connection"></a>MessageSourceType = Connessione file  
 **MessageSource**  
 Selezionare una gestione connessione file nell'elenco o fare clic su \<**Nuova connessione**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="messagesourcetype--variable"></a>MessageSourceType = Variabile  
 **MessageSource**  
 Selezionare una variabile nell'elenco oppure fare clic su \<**Nuova variabile**> per crearne una nuova.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Aggiungi variabile](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Invia messaggi &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Pagina Espressioni](expressions/expressions-page.md)  
  
  
