---
title: Provider Microsoft OLE DB per Oracle | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB provider for Oracle
- OLE DB provider for Oracle [ADO]
- Oracle provider [ADO]
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 572920ccf63f35c74e39cd02a4b32c4fd85b0550
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47698579"
---
# <a name="microsoft-ole-db-provider-for-oracle-overview"></a>Provider Microsoft OLE DB per Oracle Panoramica
> [!IMPORTANT]
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Usare invece il provider OLE DB Oracle.

 Il Provider Microsoft OLE DB per Oracle consente di ADO accedere ai database di Oracle.

## <a name="connection-string-parameters"></a>Parametri della stringa di connessione
 Per connettersi a questo provider, impostare il *Provider* argomento delle [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà:

```
MSDAORA
```

 Leggere il [Provider](../../../ado/reference/ado-api/provider-property-ado.md) proprietà restituirà anche questa stringa.

 Se una query join con un cursore dinamico o keyset viene eseguita in un database Oracle, si verifica un errore. Oracle supporta solo un cursore statico di sola lettura.

## <a name="typical-connection-string"></a>Stringa di connessione tipica
 Una stringa di connessione tipica per questo provider è:

```
"Provider=MSDAORA;Data Source=serverName;User ID=MyUserID; Password=MyPassword;"
```

 La stringa è costituita da queste parole chiave:

|Parola chiave|Description|
|-------------|-----------------|
|**Provider**|Specifica il Provider OLE DB per Oracle.|
|**Data Source**|Specifica il nome di un server.|
|**ID utente**|Specifica il nome utente.|
|**Password**|Specifica la password dell'utente.|

> [!NOTE]
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare **Trusted_Connection = yes** oppure **Integrated Security = SSPI** anziché un ID utente e password informazioni nella stringa di connessione.

## <a name="provider-specific-connection-parameters"></a>Parametri di connessione specifica del provider
 Il provider supporta vari parametri di connessione specifica del provider oltre a quelli definiti da ADO. Come con le proprietà di connessione ADO, è possibile impostare queste proprietà specifiche del provider tramite il [delle proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta di un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) o come parte del **ConnectionString**.

 Questi parametri sono descritti dettagliatamente nel [riferimento per programmatori OLE DB](http://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8). Il [indice proprietà dinamica ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) fornisce un riferimento incrociato tra questi nomi di parametro e le proprietà OLE DB corrispondenti.

|Parametro|Description|
|---------------|-----------------|
|**Handle di finestra**|Indica l'handle di finestra da usare per la richiesta di informazioni aggiuntive.|
|**Locale Identifier**|Indica un numero a 32 bit univoco (ad esempio, 1033) che specifica le preferenze relative alla lingua dell'utente. Queste preferenze indicano vengono formattati come date e ore, gli elementi vengono ordinati in ordine alfabetico, le stringhe vengono confrontate e così via.|
|**Servizi OLE DB**|Indica una maschera di bit che specifica i servizi OLE DB per abilitare o disabilitare.|
|**Richiesta**|Indica se richiedere all'utente mentre viene stabilita una connessione.|
|**Proprietà estese**|Stringa che contiene le informazioni di connessione estese specifiche del provider. Utilizzare questa proprietà solo per le informazioni di connessione specifica del provider che non possono essere descritta mediante il meccanismo di proprietà.|

## <a name="see-also"></a>Vedere anche
 [Proprietà ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [proprietà del Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
