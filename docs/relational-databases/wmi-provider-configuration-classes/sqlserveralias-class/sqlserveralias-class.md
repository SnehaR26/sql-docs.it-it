---
title: Classe SqlServerAlias | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- SqlServerAlias Class
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 75ca27fc8c035a2b62cc70bbf740dd746f341d45
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603529"
---
# <a name="sqlserveralias-class"></a>Classe SqlServerAlias
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  La [classe SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) rappresenta un alias di connessione al server.  
  
 È necessario un alias di connessione al server quando si verificano le seguenti condizioni:  
  
-   Il client si connette a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su un trasporto di rete diverso da quello predefinito.  
  
-   L'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a cui è connesso il client è in attesa su una named pipe alternativa.  
  
 **Nota:** La [classe SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) eredita il metodo **Put** dalla classe Provider. Tuttavia, non viene restituito alcun risultato come indicato dal metodo **Provider::Put** . Per ulteriori informazioni, vedere la documentazione di WMI.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli client](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
