---
title: Modificare l'Account di amministratore di sistema (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 593e71b63cb4fc6e63c1c087e62f24c37c399e8e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069939"
---
# <a name="change-the-system-administrator-account-master-data-services"></a>Modificare l'account amministratore di sistema (Master Data Services)
  È possibile modificare l'account utente che è designato come il [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] amministratore di sistema.  
  
> [!WARNING]  
>  Al termine di questa procedura, l'account utente dell'amministratore di sistema precedente viene eliminato.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario aggiungere il nome utente del nuovo amministratore all'elenco degli utenti di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Per altre informazioni, vedere [aggiungere un utente &#40;Master Data Services&#41;](add-a-user-master-data-services.md).  
  
-   È necessario disporre dell'autorizzazione per visualizzare mdm.tblUser ed eseguire la stored procedure mdm.udpSecurityMemberProcessRebuildModel nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Per altre informazioni, vedere [Sicurezza di oggetti di database &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-change-the-administrator-account"></a>Per modificare l'account amministratore  
  
1.  Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] e connettersi all'istanza [!INCLUDE[ssDE](../includes/ssde-md.md)] per il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  In MDM. tbluser individuare l'utente che sarà il nuovo amministratore e copiare il valore di `SID` colonna.  
  
3.  Creare una nuova query.  
  
4.  Digitare il testo seguente, sostituendo *DOMINIO\nome_utente.* con il nome utente dell'amministratore e *SID* con il valore copiato nel passaggio 2.  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  Consente di eseguire la query.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli amministratori di &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
