---
title: DROP SYMMETRIC KEY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SYMMETRIC KEY
- DROP_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], removing
- deleting symmetric keys
- encryption [SQL Server], symmetric keys
- removing symmetric keys
- dropping symmetric keys
- cryptography [SQL Server], symmetric keys
- DROP SYMMETRIC KEY statement
ms.assetid: 6150bc67-08cb-402e-9c24-b04c9654b434
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b693a5d8dd45ec410b5517e564baf8ace3efb22d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-symmetric-key-transact-sql"></a>DROP SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Rimuove una chiave simmetrica dal database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP SYMMETRIC KEY symmetric_key_name [REMOVE PROVIDER KEY]  
```  
  
## <a name="arguments"></a>Argomenti  
 *symmetric_key_name*  
 Nome della chiave simmetrica da rimuovere.  
  
 REMOVE PROVIDER KEY  
 Rimuove una chiave EKM (Extensible Key Management ) da un dispositivo EKM. Per ulteriori informazioni su Extensible Key Management, vedere [Extensible Key Management &#40; EKM &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Osservazioni  
 Se la chiave è aperta nella sessione corrente, l'istruzione avrà esito negativo.  
  
 Se la chiave asimmetrica viene eseguito il mapping a una chiave di Extensible Key Management (EKM) in un dispositivo EKM e **REMOVE PROVIDER KEY** opzione non è specificata, la chiave verrà rimossa dal database ma non dal dispositivo e verrà generato un avviso.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per la chiave simmetrica.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimossa la chiave simmetrica denominata `GailSammamishKey6` dal database corrente.  
  
```  
CLOSE SYMMETRIC KEY GailSammamishKey6;  
DROP SYMMETRIC KEY GailSammamishKey6;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CLOSE SYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/close-symmetric-key-transact-sql.md)   
 [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  