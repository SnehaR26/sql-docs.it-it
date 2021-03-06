---
title: 'PDO:: SetAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 56f9ee96-e1d2-46cc-b137-38f06a251863
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66d64917b83e23739ad35e8629b028904a300060
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707689"
---
# <a name="pdosetattribute"></a>PDO::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Imposta un attributo predefinito del PDO o un attributo personalizzato del driver.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDO::setAttribute ( $attribute, $value );  
```  
  
#### <a name="parameters"></a>Parametri  
*$attribute*: attributo da impostare. Vedere la sezione Osservazioni per l'elenco degli attributi supportati.  
  
*$value*: valore (tipo misto).  
  
## <a name="return-value"></a>Valore restituito  
Restituisce true in caso di esito positivo; in caso contrario, false.  
  
## <a name="remarks"></a>Remarks  
  
|attribute|Elaborato da|Valori supportati|Descrizione|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR_CASE|PDO|PDO::CASE_LOWER<br /><br />PDO::CASE_NATURAL<br /><br />PDO::CASE_UPPER|Consente di specificare se i nomi delle colonne sono in lettere maiuscole o minuscole.<br /><br />PDO::CASE_LOWER fa sì che i nomi delle colonne siano in lettere minuscole.<br /><br />PDO::CASE_NATURAL (impostazione predefinita) consente di visualizzare i nomi delle colonne così come vengono restituiti dal database.<br /><br />PDO::CASE_UPPER fa sì che i nomi delle colonne siano in lettere maiuscole.<br /><br />Questo attributo può essere impostato usando PDO::setAttribute.|  
|PDO::ATTR_DEFAULT_FETCH_MODE|PDO|Vedere la documentazione del PDO.|Vedere la documentazione del PDO.|  
|PDO::ATTR_ERRMODE|PDO|PDO::ERRMODE_SILENT<br /><br />PDO::ERRMODE_WARNING<br /><br />PDO::ERRMODE_EXCEPTION|Specifica come il driver segnala gli errori.<br /><br />PDO::ERRMODE_SILENT (predefinito) imposta i codici di errore e le informazioni.<br /><br />PDO::ERRMODE_WARNING genera E_WARNING.<br /><br />PDO::ERRMODE_EXCEPTION causa la generazione di un'eccezione.<br /><br />Questo attributo può essere impostato usando PDO::setAttribute.|  
|PDO::ATTR_ORACLE_NULLS|PDO|Vedere la documentazione del PDO.|Consente di specificare come devono essere restituiti i valori Null.<br /><br />PDO::NULL_NATURAL non esegue alcuna conversione.<br /><br />PDO::NULL_EMPTY_STRING converte una stringa vuota in valore Null.<br /><br />PDO::NULL_TO_STRING converte il valore Null in una stringa vuota.|  
|PDO::ATTR_STATEMENT_CLASS|PDO|Vedere la documentazione del PDO.|Consente di impostare la classe di istruzione fornita dall'utente derivata da PDOStatement.<br /><br />Richiede `array(string classname, array(mixed constructor_args))`.<br /><br />Per altre informazioni, vedere la documentazione del PDO.|  
|PDO::ATTR_STRINGIFY_FETCHES|PDO|true o false|Consente di convertire i valori numerici in stringhe durante il recupero di dati.|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|1 per il limite di memoria PHP.|Imposta le dimensioni del buffer contenente il set di risultati per un cursore sul lato client.<br /><br />Il valore predefinito è 10240 KB, se non viene specificato nel file PHP. ini.<br /><br />Lo zero e i numeri negativi non sono consentiti.<br /><br />Per altre informazioni sulle query, vedere [Tipi di cursore &#40;PDO_SQLSRV Driver&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true<br /><br />false|Specifica l'esecuzione di query diretta o preparata. Per altre informazioni, vedere [Esecuzione di istruzioni diretta e preparata nel driver PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PDO::SQLSRV_ENCODING_UTF8<br /><br />PDO::SQLSRV_ENCODING_SYSTEM.|Consente di impostare la codifica del set di caratteri usato dal driver per comunicare con il server.<br /><br />PDO::SQLSRV_ENCODING_BINARY non è supportato.<br /><br />Il valore predefinito è PDO::SQLSRV_ENCODING_UTF8.|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true o false|Gestisce operazioni di recupero numerici dalle colonne con tipi numerici SQL (bit, integer, smallint, tinyint, float o real).<br /><br />Quando il flag di opzione di connessione ATTR_STRINGIFY_FETCHES è attivata, il valore restituito è una stringa, anche quando SQLSRV_ATTR_FETCHES_NUMERIC_TYPE si trova in.<br /><br />Quando il tipo PDO restituito nella colonna di binding è PDO_PARAM_INT, il valore restituito da una colonna integer è un valore int anche se SQLSRV_ATTR_FETCHES_NUMERIC_TYPE è disattivata.|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|integer|Consente di impostare il timeout in secondi della query.<br /><br />Il valore predefinito è 0, vale a dire che il driver attende i risultati per un periodo illimitato.<br /><br />I numeri negativi non sono consentiti.|  
  
Il PDO elabora alcuni attributi predefiniti e richiede al driver di elaborare gli altri. Tutti gli attributi personalizzati e le opzioni di connessione vengono elaborati dal driver. Eventuali attributi, opzioni di connessione o valori non supportati vengono segnalati in base all'impostazione di PDO::ATTR_ERRMODE.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
In questo esempio viene illustrato come impostare l'attributo PDO::ATTR_ERRMODE.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
  
   $attributes1 = array( "ERRMODE" );  
   foreach ( $attributes1 as $val ) {  
      echo "PDO::ATTR_$val: ";  
      var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
   }  
  
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
  
   $attributes1 = array( "ERRMODE" );  
   foreach ( $attributes1 as $val ) {  
      echo "PDO::ATTR_$val: ";  
      var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
   }  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
