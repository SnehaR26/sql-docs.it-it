---
title: Protezione di applicazioni del Driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8033e1690fcaa01ca73ce1a7d0d9972ac2d3ba9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="securing-jdbc-driver-applications"></a>Protezione delle applicazioni del driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per migliorare la sicurezza di un [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] applicazione prevede più di evitare problemi di codifica comuni. Un'applicazione che accede ai dati presenta numerosi punti di errore potenziali che un pirata informatico può sfruttare recuperare, modificare o distruggere dati sensibili. È importante comprendere tutti gli aspetti della sicurezza, dal processo di classificazione dei rischi durante la fase di progettazione dell'applicazione all'eventuale distribuzione fino all'importanza di una continua manutenzione.  
  
 Negli argomenti di questa sezione vengono descritti alcuni problemi di sicurezza comuni, inclusi quelli relativi a stringhe di connessione, convalida dell'input utente e sicurezza generale delle applicazioni.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Protezione delle stringhe di connessione](../../connect/jdbc/securing-connection-strings.md)|Vengono descritte le tecniche per la protezione delle informazioni utilizzate per la connessione a un'origine dati.|  
|[Convalida dell'Input utente](../../connect/jdbc/validating-user-input.md)|Vengono descritte le tecniche per la convalida dell'input utente.|  
|[Sicurezza delle applicazioni](../../connect/jdbc/application-security.md)|Viene descritto come utilizzare le autorizzazioni relative ai criteri Java per proteggere un'applicazione del driver JDBC.|  
|[Utilizzo della crittografia SSL](../../connect/jdbc/using-ssl-encryption.md)|Viene descritto come stabilire un canale di comunicazione protetta con un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizza Secure Sockets Layer (SSL).|  
|[Modalità FIPS](../../connect/jdbc/fips-mode.md)|Viene descritto come utilizzare il driver JDBC in modalità ricorrente FIPS.| 
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del Driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  