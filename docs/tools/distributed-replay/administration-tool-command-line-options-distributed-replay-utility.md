---
title: Opzioni della riga di comando dello strumento di amministrazione (utilità Riesecuzione distribuita) | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e7dc5cdb9e6ccc575a029c0f4ac931107af05ae7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686782"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>Opzioni della riga di comando dello strumento di amministrazione (Distributed Replay Utility)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Lo strumento di amministrazione Riesecuzione distribuita di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , **DReplay.exe**, è uno strumento da riga di comando per comunicare con il controller di Riesecuzione distribuita. Usare lo strumento di amministrazione per avviare, monitorare e annullare operazioni nel controller.  
  
 ![Icona di collegamento all'argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento all'argomento")Per altre informazioni sulle convenzioni relative alla sintassi dello strumento di amministrazione, vedere [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-m controller] -i input_trace_file  
    -d controller_working_dir [-c config_file] [-f status_interval]  
  
  dreplay replay [-m controller] -d controller_working_dir [-o]  
    [-s target_server] -w clients [-c config_file]  
    [-f status_interval]  
  
  dreplay status [-m controller] [-f status_interval]  
  
  dreplay cancel [-m controller] [-q]   
```  
  
## <a name="remarks"></a>Remarks  
 Con **DReplay.exe**è possibile eseguire le seguenti opzioni della riga di comando:  
  
 **preprocess**  
 Avvia la fase di pre-elaborazione. Il controller prepara i dati di traccia di input, acquisiti dall'ambiente di produzione, per la riproduzione sul server di destinazione.  
  
 **replay**  
 Avvia la fase di riproduzione dell'evento. Il controller recapita i dati di riproduzione ai client specificati, avvia la riproduzione distribuita e sincronizza i client. Ogni client selezionato può eventualmente registrare l'attività di riproduzione e salvare in locale i file di traccia dei risultati.  
  
 **status**  
 Viene eseguita una query sul controller e viene visualizzato lo stato corrente.  
  
 **cancel**  
 Viene annullata l'operazione corrente eseguita nel controller.  
  
 Per informazioni dettagliate sulla sintassi, inclusi gli argomenti dei comandi e gli esempi, vedere gli argomenti seguenti:  
  
-   [Opzione preprocess &#40;strumento di amministrazione Distributed Replay&#41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)  
  
-   [Opzione replay &#40;strumento di amministrazione Distributed Replay&#41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)  
  
-   [Opzione status &#40;strumento di amministrazione Distributed Replay&#41;](../../tools/distributed-replay/status-option-distributed-replay-administration-tool.md)  
  
-   [Opzione cancel &#40;strumento di amministrazione Distributed Replay&#41;](../../tools/distributed-replay/cancel-option-distributed-replay-administration-tool.md)  
  
 Le chiamate RPC vengono riprodotte come RPC e non come eventi di linguaggio.  
  
## <a name="permissions"></a>Permissions  
 È necessario eseguire lo strumento di amministrazione come utente interattivo, scegliendo tra utente locale e account utente di dominio. Per utilizzare un account utente locale, lo strumento di amministrazione e il controller devono essere eseguiti nello stesso computer.  
  
 Per altre informazioni, vedere [Sicurezza di Riesecuzione distribuita](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
