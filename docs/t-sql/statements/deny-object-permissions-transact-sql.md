---
title: DENY oggetto autorizzazioni (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- DENY statement, objects
- table permissions [SQL Server]
ms.assetid: 0b8d3ddc-38c0-4241-b7bb-ee654a5081aa
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2655a796d6d097cb635576313664ea6bfa7162db
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="deny-object-permissions-transact-sql"></a>DENY - autorizzazioni per oggetti (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Nega le autorizzazioni per un membro della classe OBJECT delle entità a protezione diretta. I membri della classe OBJECT sono costituiti da tabelle, viste, funzioni con valori di tabella, stored procedure, stored procedure estese, funzioni scalari, funzioni di aggregazione, code di servizio e sinonimi.  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DENY <permission> [ ,...n ] ON   
    [ OBJECT :: ][ schema_name ]. object_name [ ( column [ ,...n ] ) ]  
        TO <database_principal> [ ,...n ]   
    [ CASCADE ]  
        [ AS <database_principal> ]  
  
<permission> ::=  
    ALL [ PRIVILEGES ] | permission [ ( column [ ,...n ] ) ]  
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login  
```  
  
## <a name="arguments"></a>Argomenti  
 *autorizzazione*  
 Specifica un'autorizzazione che può essere negata per un oggetto contenuto nello schema. Per un elenco delle autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 ALL  
 L'opzione ALL non nega tutte le autorizzazioni possibili. L'impostazione di ALL equivale a negare tutte le autorizzazioni ANSI-92 applicabili all'oggetto specificato. Il significato di ALL è variabile, come indicato di seguito:  
  
 - Autorizzazioni per funzioni scalari: EXECUTE, REFERENCES.  
 - Autorizzazioni per funzioni con valori di tabella: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
 - Autorizzazioni per stored procedure: EXECUTE.  
 - Autorizzazioni per tabelle: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
 - Autorizzazioni per viste: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
  
PRIVILEGES  
 Opzione inclusa per compatibilità con ANSI-92. Non modifica il funzionamento di ALL.  
  
*colonna*  
 Specifica il nome di una colonna in una tabella, vista o funzione con valori di tabella per la quale viene negata l'autorizzazione. Le parentesi **()** sono necessari. Per una colonna si possono negare solo le autorizzazioni SELECT, REFERENCES e UPDATE. *colonna* può essere specificato nella clausola delle autorizzazioni o dopo il nome dell'entità a protezione diretta.  
  
> [!CAUTION]  
>  Un'istruzione DENY a livello di tabella non ha la precedenza rispetto a un'istruzione GRANT a livello di colonna. Questa incoerenza nella gerarchia delle autorizzazioni è stata mantenuta per compatibilità con le versioni precedenti.  
  
 ON [oggetto **::** ] [ *schema_name* ] **.** *object_name*  
 Specifica l'oggetto per cui viene negata l'autorizzazione. L'utilizzo di OBJECT è facoltativo se *schema_name* specificato. Se si utilizza Object, il qualificatore di ambito (**::**) è obbligatorio. Se *schema_name* viene omesso, viene utilizzato lo schema predefinito. Se *schema_name* è specificato, il qualificatore di ambito dello schema (**.**) è obbligatorio.  
  
 PER \<database_principal >  
 Specifica l'entità a cui viene negata l'autorizzazione.  
  
 CASCADE  
 Indica che l'autorizzazione negata viene negata anche ad altre entità alle quali è stata concessa da questa entità.  
  
 AS \<database_principal >  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di negare l'autorizzazione.  
  
 *Database_user*  
 Specifica un utente di database.  
  
 *Database_role*  
 Specifica un ruolo del database.  
  
 *Application_role*  
 Specifica un ruolo applicazione.  
  
 *Database_user_mapped_to_Windows_User*  
 Specifica un utente del database sul quale viene eseguito il mapping a un utente di Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
 Specifica un utente del database sul quale viene eseguito il mapping a un gruppo di Windows.  
  
 *Database_user_mapped_to_certificate*  
 Specifica un utente del database sul quale viene eseguito il mapping a un certificato.  
  
 *Database_user_mapped_to_asymmetric_key*  
 Specifica un utente del database sul quale viene eseguito il mapping a una chiave asimmetrica.  
  
 *Database_user_with_no_login*  
 Specifica un utente del database per cui non esiste un'entità corrispondente a livello del server.  
  
## <a name="remarks"></a>Osservazioni  
 Le informazioni sugli oggetti sono visibili in varie viste del catalogo. Per ulteriori informazioni, vedere [oggetto viste del catalogo &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md).  
  
 Un oggetto è un'entità a protezione diretta a livello di schema contenuta nello schema padre nella gerarchia delle autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile negare per un oggetto, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione per l'oggetto|Autorizzazione dell'oggetto in cui è inclusa|Autorizzazione dello schema in cui è inclusa|  
|-----------------------|----------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|DELETE|CONTROL|DELETE|  
|Eseguire|CONTROL|Eseguire|  
|INSERT|CONTROL|INSERT|  
|RECEIVE|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|RECEIVE|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|VIEW CHANGE TRACKING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per l'oggetto.  
  
 Se si utilizza la clausola AS, l'entità specificata deve essere proprietaria dell'oggetto per cui vengono negate le autorizzazioni.  
  
## <a name="examples"></a>Esempi  
L'esempio seguente usa il database AdventureWorks.
  
### <a name="a-denying-select-permission-on-a-table"></a>A. Negazione dell'autorizzazione SELECT per una tabella  
 Nell'esempio seguente viene negata il `SELECT` autorizzazione all'utente `RosaQdM` nella tabella `Person.Address`.  
  
```  
DENY SELECT ON OBJECT::Person.Address TO RosaQdM;  
GO  
```  
  
### <a name="b-denying-execute-permission-on-a-stored-procedure"></a>B. Negazione dell'autorizzazione EXECUTE per una stored procedure  
 Nell'esempio seguente viene negata l'autorizzazione `EXECUTE` per la stored procedure `HumanResources.uspUpdateEmployeeHireInfo` a un ruolo applicazione denominato `Recruiting11`.  
  
```  
DENY EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO   
```  
  
### <a name="c-denying-references-permission-on-a-view-with-cascade"></a>C. Negazione dell'autorizzazione REFERENCES per una vista con CASCADE  
 Nell'esempio seguente viene negata l'autorizzazione `REFERENCES` per la colonna `BusinessEntityID` nella vista `HumanResources.vEmployee` all'utente `Wanida` con `CASCADE`.  
  
```  
DENY REFERENCES (BusinessEntityID) ON OBJECT::HumanResources.vEmployee   
    TO Wanida CASCADE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [GRANT - autorizzazioni per oggetti &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [REVOCARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)   
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)  
  
  
