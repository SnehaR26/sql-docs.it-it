---
title: Utilizzo di set di risultati | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c3144eb103a1197d36ddc165d15bf16f828ebd9f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610152"
---
# <a name="working-with-result-sets"></a>Utilizzo dei set di risultati

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Quando si usano i dati contenuti in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un metodo di manipolazione dei dati consiste nell'uso di un set di risultati. [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] supporta l'uso dei set di risultati tramite l'oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md). Usando l'oggetto SQLServerResultSet, è possibile recuperare i dati restituiti da un'istruzione SQL o da una stored procedure, aggiornare i dati secondo le necessità e quindi inviare nuovamente i dati al database.  
  
L'oggetto SQLServerResultSet offre anche metodi per la navigazione nelle righe di dati, per il recupero o l'impostazione dei dati in esso contenuti, per la creazione di vari livelli di sensibilità alle modifiche nel database sottostante.  
  
> [!NOTE]  
> Per altre informazioni sulla gestione dei set di risultati, inclusa la sensibilità alle modifiche, vedere [gestione dei set di risultati con il Driver JDBC](../../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
Negli argomenti della sezione vengono descritti vari modi di usare un set di risultati per manipolare i dati contenuti in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
| Argomento                                                                                           | Descrizione                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Esempio di recupero dei dati del set di risultati](../../../connect/jdbc/code-samples/retrieving-result-set-data-sample.md) | Descrive come usare un set di risultati per recuperare i dati da un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e visualizzarli.                                                         |
| [Esempio di modifica dei dati dei set di risultati](../../../connect/jdbc/code-samples/modifying-result-set-data-sample.md)   | Descrive come usare un set di risultati per inserire, recuperare e modificare i dati in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].                                                      |
| [Esempio di memorizzazione nella cache dei dati dei set di risultati](../../../connect/jdbc/code-samples/caching-result-set-data-sample.md)       | Descrive come usare il set di risultati per recuperare grandi quantità di dati da un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e per controllare come vengono memorizzati i dati nel client. |
  
## <a name="see-also"></a>Vedere anche  

[Applicazioni di esempio del driver JDBC](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
  
