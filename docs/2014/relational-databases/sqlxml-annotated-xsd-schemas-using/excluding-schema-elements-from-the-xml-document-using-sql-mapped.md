---
title: 'Esclusione di elementi dello Schema dal documento XML risultante tramite sql: mapped (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 96afa13033fee6a2767fc1ad3f6b6761c4a8247f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222313"
---
# <a name="excluding-schema-elements-from-the-resulting-xml-document-using-sqlmapped-sqlxml-40"></a>Esclusione di elementi dello schema dal documento XML risultante tramite sql:mapped (SQLXML 4.0)
  A causa del mapping predefinito, viene eseguito il mapping di ogni elemento e attributo nello schema XSD a una vista/tabella e a una colonna di database. Se si desidera creare un elemento nello schema XSD di cui non venga eseguito il mapping a qualsiasi tabella (vista) o colonna di database e che non venga visualizzato in XML, è possibile specificare l'annotazione `sql:mapped`.  
  
 L'annotazione `sql:mapped` risulta particolarmente utile se lo schema non può essere modificato o se viene utilizzato per la convalida XML da altre origini pur contenendo dati non archiviati nel database. La differenza tra l'annotazione `sql:mapped` e `sql:is-constant` consiste nel fatto che gli elementi e gli attributi di cui non è stato eseguito il mapping non vengono visualizzati nel documento XML.  
  
 L'annotazione `sql:mapped` accetta un valore booleano (0=false, 1=true). I valori possibili sono 0, 1, true e false.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per altre informazioni, vedere [requisiti per l'esecuzione di esempi di SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. Specifica dell'annotazione sql:mapped  
 Si supponga di disporre di uno schema XSD di un'altra origine. Questo schema XSD è costituito da un  **\<Person. Contact >** elemento con **ContactID**, **FirstName**, **LastName**, e **HomeAddress** attributi.  
  
 Nel mapping dello schema XSD alla tabella Person. Contact nel database AdventureWorks, `sql:mapped` viene specificata per il **HomeAddress** attributo perché la tabella Employees non archivia gli indirizzi personali dei dipendenti. Di conseguenza, questo attributo non viene mappato al database e non viene restituito nel documento XML risultante quando viene specificata una query XPath sullo schema di mapping.  
  
 Per il resto dello schema viene eseguito il mapping predefinito. Il  **\<Person. Contact >** elemento viene mappato alla tabella Person. Contact e tutti gli attributi vengono mappati alle colonne con lo stesso nome della tabella Person. Contact.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome sql-mapped.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome sql-mappedT.xml nella stessa directory in cui è stato salvato il file sql-mapped.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (MySchema.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per altre informazioni, vedere [utilizzo di ADO per eseguire query SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Set di risultati:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 Si noti che gli attributi ContactID, FirstName e LastName sono presenti, mentre HomeAdress è assente, in quanto lo schema di mapping specifica il valore 0 per l'attributo `sql:mapped`.  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping predefinito degli attributi ed elementi XSD a tabelle e colonne &#40;SQLXML 4.0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
