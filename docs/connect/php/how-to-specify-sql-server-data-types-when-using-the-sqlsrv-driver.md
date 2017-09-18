---
title: 'Procedura: specificare i tipi di dati SQL Server quando si utilizza il Driver SQLSRV | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data types
- streaming data
ms.assetid: 1fcf73cb-5634-4d89-948f-9326f1dbd030
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f73404e08956a0b8335d3a54cc35df030d687b3e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver"></a>Procedura: Specificare i tipi di dati di SQL Server con il driver SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento viene illustrato come usare il driver SQLSRV per specificare il tipo di dati di SQL Server per i dati inviati al server. Le informazioni di questo argomento non si applicano al driver PDO_SQLSRV.  
  
Per specificare il tipo di dati di SQL Server, è necessario usare la matrice facoltativa *$params* per la preparazione o l'esecuzione di una query che inserisce o aggiorna i dati. Per informazioni dettagliate sulla struttura e la sintassi della matrice *$params* , vedere [sqlsrv_query](../../connect/php/sqlsrv-query.md) o [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md).  
  
Di seguito sono elencati i passaggi principali per la specifica del tipo di dati di SQL Server durante l'invio di dati al server:  
  
> [!NOTE]  
> Se non viene specificato alcun tipo di dati di SQL Server, verranno usati i tipi predefiniti. Per altre informazioni sui tipi di dati di SQL Server predefiniti, vedere [Default SQL Server Data Types](../../connect/php/default-sql-server-data-types.md).  
  
1.  Definire una query Transact-SQL che inserisce o aggiorna i dati. Usare i punti interrogativi (?) come segnaposto per i valori dei parametri nella query.  
  
2.  Inizializzare o aggiornare le variabili PHP che corrispondono ai segnaposto della query Transact-SQL.  
  
3.  Costruire la matrice *$params* da usare durante la preparazione o l'esecuzione della query. Si noti che ogni elemento della matrice *$params* deve essere una matrice quando si specifica il tipo di dati di SQL Server.  
  
4.  Specificare il tipo di dati di SQL Server desiderato, utilizzando i **SQLSRV_SQLTYPE\* ** costante come quarto parametro in ciascuna matrice secondaria del *$params* matrice. Per un elenco completo del **SQLSRV_SQLTYPE\* ** costanti, vedere la sezione SqlType di [costanti &#40; Driver Microsoft per PHP per SQL Server &#41; ](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md). Ad esempio, nel codice seguente, *$changeDate*, *$rate*e *$payFrequency* sono specificati rispettivamente come tipi di SQL Server **datetime**, **money**e **tinyint** nella matrice *$params* . Poiché non è specificato alcun tipo di SQL Server per *$employeeId* che viene inizializzato su un numero intero, viene usato il tipo di SQL Server predefinito **integer** .  
  
    ```  
    $employeeId = 5;  
    $changeDate = "2005-06-07";  
    $rate = 30;  
    $payFrequency = 2;  
    $params = array(  
                array($employeeId, null),  
                array($changeDate, null, null, SQLSRV_SQLTYPE_DATETIME),  
                array($rate, null, null, SQLSRV_SQLTYPE_MONEY),  
                array($payFrequency, null, null, SQLSRV_SQLTYPE_TINYINT)  
              );  
    ```  
  
## <a name="example"></a>Esempio  
L'esempio seguente inserisce i dati nella tabella *HumanResources.EmployeePayHistory* del database AdventureWorks. I tipi di SQL Server sono specificati per i parametri *$changeDate*, *$rate*e *$payFrequency* . Il tipo di SQL Server predefinito viene usato per il parametro *$employeeId* . Per verificarne il corretto inserimento, i dati vengono recuperati e visualizzati.  
  
Nell'esempio si presuppone che SQL Server e il database [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) siano installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nella console.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Define the query. */  
$tsql1 = "INSERT INTO HumanResources.EmployeePayHistory (EmployeeID,  
                                                        RateChangeDate,  
                                                        Rate,  
                                                        PayFrequency)  
           VALUES (?, ?, ?, ?)";  
  
/* Construct the parameter array. */  
$employeeId = 5;  
$changeDate = "2005-06-07";  
$rate = 30;  
$payFrequency = 2;  
$params1 = array(  
               array($employeeId, null),  
               array($changeDate, null, null, SQLSRV_SQLTYPE_DATETIME),  
               array($rate, null, null, SQLSRV_SQLTYPE_MONEY),  
               array($payFrequency, null, null, SQLSRV_SQLTYPE_TINYINT)  
           );  
  
/* Execute the INSERT query. */  
$stmt1 = sqlsrv_query($conn, $tsql1, $params1);  
if( $stmt1 === false )  
{  
     echo "Error in execution of INSERT.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve the newly inserted data. */  
/* Define the query. */  
$tsql2 = "SELECT EmployeeID, RateChangeDate, Rate, PayFrequency  
          FROM HumanResources.EmployeePayHistory  
          WHERE EmployeeID = ? AND RateChangeDate = ?";  
  
/* Construct the parameter array. */  
$params2 = array($employeeId, $changeDate);  
  
/*Execute the SELECT query. */  
$stmt2 = sqlsrv_query($conn, $tsql2, $params2);  
if( $stmt2 === false )  
{  
     echo "Error in execution of SELECT.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the results. */  
$row = sqlsrv_fetch_array( $stmt2 );  
if( $row === false )  
{  
     echo "Error in fetching data.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
echo "EmployeeID: ".$row['EmployeeID']."\n";  
echo "Change Date: ".date_format($row['RateChangeDate'], "Y-m-d")."\n";  
echo "Rate: ".$row['Rate']."\n";  
echo "PayFrequency: ".$row['PayFrequency']."\n";  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt($stmt1);  
sqlsrv_free_stmt($stmt2);  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Recupero di dati](../../connect/php/retrieving-data.md)  
[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
[Procedura: Specificare i tipi di dati PHP](../../connect/php/how-to-specify-php-data-types.md)  
[Converting Data Types](../../connect/php/converting-data-types.md)  
[Procedura: Invio e recupero di dati UTF-8 con il supporto incorporato di UTF-8](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)  
  
