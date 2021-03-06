---
title: La connessione tramite la crittografia SSL | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78cdeb64cbd0bc76109c7bd3db784c2262ae80ff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812189"
---
# <a name="connecting-with-ssl-encryption"></a>Connessione tramite la crittografia SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Gli esempi di questo argomento descrivono come usare le proprietà della stringa di connessione che consentono alle applicazioni di usare la crittografia SSL (Secure Sockets Layer) in un'applicazione Java. Per altre informazioni sulle nuove proprietà della stringa di connessione, ad esempio **encrypt**, **trustServerCertificate**, **trustStore**, **trustStorePassword** e **hostNameInCertificate**, vedere [Impostazione delle proprietà delle connessioni](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Se la proprietà **encrypt** è impostata su **true** e la proprietà **trustServerCertificate** è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non convalida il certificato SSL di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ciò è in genere necessario per consentire le connessioni in ambienti di test, ad esempio nel caso in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abbia solo un certificato autofirmato.  
  
 L'esempio di codice seguente illustra come impostare la proprietà **trustServerCertificate** in una stringa di connessione:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 Se la proprietà **encrypt** è impostata su **true** e la proprietà **trustServerCertificate** è impostata su **false**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] convalida il certificato SSL di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La convalida del certificato del server fa parte dell'handshake SSL e assicura che il server a cui si esegue la connessione sia quello corretto. Per la convalida del certificato del server è necessario che in fase di connessione venga fornito il materiale relativo all'attendibilità usando in modo esplicito le proprietà di connessione **trustStore** e **trustStorePassword** oppure usando in modo implicito l'archivio di scopi predefinito di JVM (Java Virtual Machine) sottostante.  
  
 La proprietà **trustStore** specifica il percorso (incluso il nome file) del file trustStore, che contiene l'elenco di certificati considerati attendibili dal client. La proprietà **trustStorePassword** specifica la password usata per verificare l'integrità dei dati del file trustStore. Per altre informazioni sull'uso di archivio di attendibilità predefinito di JVM, vedere la [configurazione del Client per la crittografia SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md).  
  
 L'esempio di codice seguente illustra come impostare le proprietà **trustStore** e **trustStorePassword** in una stringa di connessione:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 Il driver JDBC è dotato di una proprietà aggiuntiva, **hostNameInCertificate**, che specifica il nome host del server. Il valore di questa proprietà deve corrispondere alla proprietà relativa al soggetto del certificato.  
  
 L'esempio di codice seguente illustra come usare la proprietà **hostNameInCertificate** in una stringa di connessione:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  In alternativa, è possibile impostare il valore delle proprietà di connessione usando i metodi **setter** appropriati offerti dalla classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
 Se la proprietà di connessione **encrypt** è impostata su **true**, la proprietà **trustServerCertificate** è impostata su **false** e il nome del server nella stringa di connessione non corrisponde al nome del server nel certificato SSL di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], viene restituito l'errore seguente: The driver couldn't establish a secure connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using Secure Sockets Layer (SSL) encryption (Il driver non è stato in grado di stabilire una connessione protetta a SQL Server tramite crittografia SSL (Secure Sockets Layer)). Errore: "java.security.cert.CertificateException: Impossibile convalidare il nome del server in un certificato durante l'inizializzazione di SSL (Secure Sockets Layer)".  
  
## <a name="see-also"></a>Vedere anche  
 [Uso della crittografia SSL](../../connect/jdbc/using-ssl-encryption.md)   
 [Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
