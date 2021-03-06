---
title: Utilizzo dell'isolamento dello Snapshot | Documenti di Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], snapshot isolation
- SQLNCLI, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, snapshot isolation
- SQL Server Native Client ODBC driver, snapshot isolation
- SQL Server Native Client, snapshot isolation
- SQLGetInfo function
- concurrency [SQL Server Native Client]
- SQLSetConnectAttr function
ms.assetid: 39e87eb1-677e-45dd-bc61-83a4025a7756
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 49037855283373fb501888b71e7f2d1a72f7a06a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843639"
---
# <a name="working-with-snapshot-isolation"></a>Utilizzo dell'isolamento dello snapshot
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] è stato introdotto un nuovo livello di isolamento dello "snapshot" destinato a migliorare la concorrenza delle applicazioni per l'elaborazione delle transazioni online (OLTP). Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la concorrenza è basata esclusivamente sul blocco. Questa caratteristica può causare problemi di blocco e deadlock per alcune applicazioni. L'isolamento dello snapshot dipende dai miglioramenti apportati al controllo delle versioni delle righe e ha lo scopo di migliorare le prestazioni evitando scenari di blocco in lettura/scrittura.  
  
 Le transazioni avviate con l'isolamento dello snapshot leggono uno snapshot del database che risale all'avvio della transazione. Uno dei possibili risultati è che, se aperti nel contesto di una transazione snapshot, i cursori server keyset statici e dinamici si comporteranno come cursori statici aperti in transazioni serializzabili. Tuttavia, quando i cursori vengono aperti con il livello di isolamento dello snapshot, non vengono acquisiti blocchi. In questo modo viene ridotto il numero di blocchi nel server.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Provider OLE DB di SQL Server Native Client  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client presenta miglioramenti che sfruttano l'isolamento dello snapshot introdotto in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Tra questi miglioramenti figurano le modifiche ai set di proprietà DBPROPSET_DATASOURCEINFO e DBPROPSET_SESSION.  
  
### <a name="dbpropsetdatasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 Il set di proprietà DBPROPSET_DATASOURCEINFO è stato modificato per indicare che il livello di isolamento dello snapshot è supportato dall'aggiunta del valore DBPROPVAL_TI_SNAPSHOT utilizzato nella proprietà DBPROP_SUPPORTEDTXNISOLEVELS. Questo nuovo valore indica che il livello di isolamento dello snapshot è supportato indipendentemente dall'abilitazione del controllo delle versioni nel database. Di seguito viene presentato un elenco dei valori DBPROP_SUPPORTEDTXNISOLEVELS:  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|Tipo: VT_I4<br /><br /> L/S: Sola lettura<br /><br /> Descrizione: maschera di bit che specifica i livelli di isolamento delle transazioni supportati. Combinazione di zero o più dei valori seguenti:<br /><br /> DBPROPVAL_TI_CHAOS<br /><br /> DBPROPVAL_TI_READUNCOMMITTED<br /><br /> DBPROPVAL_TI_BROWSE<br /><br /> DBPROPVAL_TI_CURSORSTABILITY<br /><br /> DBPROPVAL_TI_READCOMMITTED<br /><br /> DBPROPVAL_TI_REPEATABLEREAD<br /><br /> DBPROPVAL_TI_SERIALIZABLE<br /><br /> DBPROPVAL_TI_ISOLATED<br /><br /> DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropsetsession"></a>DBPROPSET_SESSION  
 Il set di proprietà DBPROPSET_SESSION è stato modificato per indicare che il livello di isolamento dello snapshot è supportato dall'aggiunta del valore DBPROPVAL_TI_SNAPSHOT utilizzato nella proprietà DBPROP_SESS_AUTOCOMMITISOLEVELS. Questo nuovo valore indica che il livello di isolamento dello snapshot è supportato indipendentemente dall'abilitazione del controllo delle versioni nel database. Di seguito viene presentato un elenco dei valori DBPROP_SESS_AUTOCOMMITISOLEVELS:  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Tipo: VT_I4<br /><br /> L/S: Sola lettura<br /><br /> Descrizione: specifica una maschera di bit che indica il livello di isolamento delle transazioni durante la modalità di autocommit. I valori che è possibile impostare in questa maschera di bit sono uguali a quelli che è possibile impostare per DBPROP_SUPPORTEDTXNISOLEVELS.|  
  
> [!NOTE]  
>  Si verifica l'errore DB_S_ERRORSOCCURRED o DB_E_ERRORSOCCURRED se DBPROPVAL_TI_SNAPSHOT viene impostato quando si utilizzano versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Per informazioni su come l'isolamento dello snapshot è supportato nelle transazioni, vedere [che supportano le transazioni locali](../../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Driver ODBC di SQL Server Native Client  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client fornisce supporto per l'isolamento dello snapshot tuttavia apportati miglioramenti per la [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) e [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md) funzioni.  
  
### <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Il **SQLSetConnectAttr** funzione supporta ora l'uso dell'attributo SQL_COPT_SS_TXN_ISOLATION. Impostando SQL_COPT_SS_TXN_ISOLATION su SQL_TXN_SS_SNAPSHOT si indica che la transazione si verificherà con il livello di isolamento dello snapshot.  
  
### <a name="sqlgetinfo"></a>SQLGetInfo  
 Il [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md) funzione supporta ora il valore SQL_TXN_SS_SNAPSHOT aggiunto al tipo di informazioni SQL_TXN_ISOLATION_OPTION.  
  
 Per informazioni su come l'isolamento dello snapshot è supportato nelle transazioni, vedere [livello di isolamento delle transazioni di cursore](../../../relational-databases/native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Proprietà e comportamenti dei set di righe](../../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
