---
title: Proprietà named pipe | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- configmgr-client
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: de562f78dbf2898267a909524226387096145bee
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177170"
---
# <a name="named-pipes-properties"></a>Proprietà Named Pipes
  La pagina **Protocollo**della finestra di dialogo **Proprietà - Named Pipes** consente di visualizzare o modificare la named pipe sulla quale [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resta in attesa quando è in uso il protocollo Named Pipes.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere riavviato per abilitare o disabilitare il protocollo oppure modificare la named pipe.  
  
## <a name="options"></a>Opzioni  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**.  
  
 **Nome pipe**  
 Specifica la named pipe sulla quale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resta in attesa. Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resta in attesa su `\\.\pipe\sql\query` per l'istanza predefinita e su `\\.\pipe\MSSQL$<instancename>\sql\query` per un'istanza denominata. La lunghezza massima del campo è 2047 caratteri.  
  
## <a name="creating-an-alternate-named-pipe"></a>Creazione di una named pipe alternativa  
 Per modificare la named pipe, digitare il nome della nuova pipe nella casella **Nome pipe** e quindi arrestare e riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Poiché è noto che **sql\query** è la named pipe usata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], modificare la pipe può risultare utile per ridurre il rischio di attacco da parte di programmi dannosi.  
  
### <a name="example"></a>Esempio  
 Digitare **\\\\.\pipe\unit\app** per impostare l'attesa sulla pipe **unit\app** .  
  
 Digitare **\\\\.\pipe\acct** per impostare l'attesa sulla pipe **acct** .  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitare o disabilitare un protocollo di rete del server](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Scelta di un protocollo di rete](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Creazione di una stringa di connessione valida tramite named pipe](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
