---
title: 'Passaggio 2: Richiamare il programma di Server (esercitazione su RDS) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], invoking server program
ms.assetid: 5e74c2da-65ee-4de4-8b41-6eac45c3632e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0a2e7b62276234dcf11067395ff2512a8e93af96
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800509"
---
# <a name="step-2-invoke-the-server-program-rds-tutorial"></a>Passaggio 2: Richiamare il programma del server (esercitazione su RDS)
Quando si richiama un metodo sul client *proxy*, il programma effettivo sul server esegue il metodo. In questo passaggio, si sarà esegue una query sul server.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più incluse nel sistema operativo Windows (vedere Windows 8 e [indicazioni sulla compatibilità di Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). I componenti client di servizi desktop remoto verranno rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che usano servizi desktop remoto devono eseguire la migrazione a [di WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 **La parte** se non è stato usato [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) in questa esercitazione, il modo più semplice per eseguire questo passaggio, è possibile usare il [Servizi Desktop remoto. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto. Il **Servizi Desktop remoto. DataControl** combina il passaggio precedente per la creazione di un proxy, che in questo passaggio, eseguire la query.  
  
 Impostare il **Servizi Desktop remoto. DataControl** oggetti [Server](../../../ado/reference/rds-api/server-property-rds.md) proprietà per identificare in cui il programma del server deve essere creata un'istanza; il [Connect](../../../ado/reference/rds-api/connect-property-rds.md) proprietà per specificare la stringa di connessione per accedere all'origine dati; e il [SQL](../../../ado/reference/rds-api/sql-property.md) proprietà per specificare il testo del comando query. Quindi rilasciare il [Refresh](../../../ado/reference/rds-api/refresh-method-rds.md) metodo causano il programma di server per connettersi all'origine dati, recupero di righe specificate dalla query e restituire una **Recordset** oggetto al client.  
  
 Questa esercitazione non usa il **Servizi Desktop remoto. DataControl**, ma ciò è come se fosse ha sempre fatto:  
  
```  
Sub RDSTutorial2A()  
   Dim DC as New RDS.DataControl  
   DC.Server = "http://yourServer"  
   DC.Connect = "DSN=Pubs"  
   DC.SQL = "SELECT * FROM Authors"  
   DC.Refresh  
...  
```  
  
 Né esercitazione richiama Servizi Desktop remoto con gli oggetti ADO, ma è come se fosse ha sempre fatto:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _  
        "Remote Server=http://yourServer;Remote Provider=SQLOLEDB;"  
```  
  
 **La parte B** il metodo generale di esecuzione di questo passaggio consiste nel richiamare il **RDSServer** oggetto [Query](../../../ado/reference/rds-api/query-method-rds.md) (metodo). Tale metodo accetta una stringa di connessione, che viene usato per connettersi a un'origine dati, e un testo del comando, che consente di specificare le righe da restituire dall'origine dati.  
  
 Questa esercitazione Usa la **DataFactory** oggetto **Query** metodo:  
  
```  
Sub RDSTutorial2B()  
   Dim DS as New RDS.DataSpace  
   Dim DF  
   Dim RS as ADODB.Recordset  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Passaggio 3: Server otterrà un Recordset (esercitazione su RDS)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)   
 [Esercitazione su RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
