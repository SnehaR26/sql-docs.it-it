---
title: 'IRowsetFastLoad:: Commit (OLE DB) | Documenti di Microsoft'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IRowsetFastLoad::Commit (OLE DB)
apitype: COM
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a54accbcebcc24a08b16a71e1b63fa8a5a6e66e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713699"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Contrassegna la fine di un batch di righe inserite e scrive le righe nella tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per esempi, vedere [Bulk copia i dati usando IRowsetFastLoad &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) e [inviare dati BLOB a SQL SERVER utilizzando IROWSETFASTLOAD e ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT Commit(  
      BOOL fDone);  
```  
  
## <a name="arguments"></a>Argomenti  
 *fDone*[in]  
 Se impostato su FALSE, il set di righe resta valido e può essere utilizzato dal consumer per l'inserimento di altre righe. Se impostato su TRUE, il set di righe non è più valido e il consumer non può inserire altre righe.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito e tutti i dati inseriti sono stati scritti nella tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 E_FAIL  
 Si è verificato un errore specifico del provider. Recuperare informazioni relative al testo dell'errore specifico dal provider.  
  
 E_UNEXPECTED  
 Il metodo è stato chiamato su un set di righe della copia bulk precedentemente invalidato dal metodo **IRowsetFastLoad::Commit**.  
  
## <a name="remarks"></a>Note  
 Oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di righe copia bulk del provider OLE DB Native Client si comporta come un set di righe di modalità di aggiornamento ritardato. Quando l'utente inserisce dati di riga nel set di righe, le righe inserite vengono gestite analogamente agli inserimenti in sospeso di un set di righe che supporta **IRowsetUpdate**.  
  
 Il consumer deve chiamare il metodo **Commit** sul set di righe della copia bulk per scrivere le righe inserite nella tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esattamente come quando si usa il metodo **IRowsetUpdate::Update** per inviare le righe in sospeso a un'istanza di SQL Server.  
  
 Se il consumer rilascia il riferimento al set di righe della copia bulk senza chiamare il metodo **Commit**, tutte le righe inserite e non scritte in precedenza andranno perse.  
  
 Il consumer può raggruppare le righe inserite chiamando il metodo **Commit** con l'argomento *fDone* impostato su FALSE. Quando *fDone* è impostato su TRUE, il set di righe non è più valido. Un set di righe della copia bulk non valido supporta solo l'interfaccia **ISupportErrorInfo** e il metodo **IRowsetFastLoad::Release**.  
  
## <a name="see-also"></a>Vedere anche  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
