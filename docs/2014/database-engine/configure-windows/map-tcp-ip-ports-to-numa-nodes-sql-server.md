---
title: Eseguire il mapping delle porte TCP/IP ai nodi NUMA (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- memory [SQL Server], NUMA
- affinity NUMA
- ports [SQL Server], working with NUMA
- CPU [SQL Server], NUMA support
- NUMA, How to map a port to a NUMA node
- NUMA affinity
- TCP/IP [SQL Server], NUMA support
- non-uniform memory access
ms.assetid: 07727642-0266-4cbc-8c55-3c367e4458ca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d8b4b63ffb3ee47ed72e0dfe3190fe4231eca5d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48184671"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a>Eseguire il mapping delle porte TCP/IP ai nodi NUMA (SQL Server)
  In questo argomento si descrive come eseguire il mapping di porte TCP/IP ai nodi NUMA (non-uniform memory access, accesso non uniforme alla memoria) tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . All'avvio, tramite il [!INCLUDE[ssDE](../../includes/ssde-md.md)] vengono scritte le informazioni sul nodo nel log degli errori.  
  
 Per determinare il numero del nodo da usare, leggere le informazioni sul nodo nel log degli errori o nella vista **sys.dm_os_schedulers** . Per impostare un indirizzo e una porta TCP/IP in uno o più nodi, aggiungere una mappa di bit per l'identificazione del nodo, ovvero una maschera di affinità, tra parentesi dopo il numero di porta. I nodi possono essere specificati in formato decimale o esadecimale. Per creare la mappa di bit, numerare in primo luogo i nodi da destra a sinistra partendo da zero, come in 76543210. Creare una rappresentazione binaria dell'elenco dei nodi, indicando 1 per i nodi che si desidera utilizzare e 0 per quelli che non si desidera utilizzare. Ad esempio, per utilizzare i nodi NUMA 0, 2 e 5, specificare 00100101.  
  
|||  
|-|-|  
|Numero del nodo NUMA|76543210|  
|Maschera per 0, 2 e 5 partendo da destra|00100101|  
  
 Convertire la rappresentazione binaria (00100101) in un valore decimale `[37]`o esadecimale `[0x25]`. Per restare in attesa su tutti i nodi, non indicare alcun identificatore di nodo.  
  
 Se viene eseguito il mapping di una porta a più nodi NUMA, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono assegnate le connessioni ai nodi seguendo uno schema round-robin senza tentare di bilanciare il carico sui nodi.  
  
> [!NOTE]  
>  Per abilitare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'ascolto su più porte TCP per ogni indirizzo IP, vedere [Configurazione del Motore di database per l'attesa su più porte TCP](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di Gestione configurazione SQL Server  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a>Per eseguire il mapping di una porta TCP/IP a un nodo NUMA  
  
1.  In Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] espandere **Configurazione di rete SQL Server**, quindi scegliere **Protocolli per** *\<nome istanza>*.  
  
2.  Nel riquadro dei dettagli fare doppio clic su **TCP/IP**.  
  
3.  Nella sezione corrispondente all'indirizzo IP da configurare della scheda **Indirizzi IP** aggiungere l'identificatore di nodo NUMA tra parentesi dopo il numero di porta nella casella **Porta TCP** . Ad esempio, per la porta TCP 1500 e i nodi 0, con 2 e 5, usare `1500[37]`, o `1500[0x25]`.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare SQL Server per l'utilizzo di Soft-NUMA &#40;SQL Server&#41;](soft-numa-sql-server.md)  
  
  
