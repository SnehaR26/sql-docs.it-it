---
title: 'SQL: mappato (SQLXML 4.0) | Documenti di Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- mapped annotation
- element mapping [SQLXML], XML Bulk Load
- attribute mapping [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:mapped
- column mapping [SQLXML]
ms.assetid: 7042741e-ce4d-4912-9c4a-d77194a028fc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 16d6d22d2bd37d6f826878a5abd0bc235c3de83a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109101"
---
# <a name="sqlmapped-sqlxml-40"></a>sql:mapped (SQLXML 4.0)
  Caricamento Bulk XML elabora il `sql:mapped` annotazione nello schema XSD come previsto, vale a dire, se lo schema di mapping specifica `sql:mapped="false"` per qualsiasi elemento o attributo, il caricamento Bulk XML non tenta di archiviare i dati associati nella colonna corrispondente.  
  
 Il caricamento bulk XML ignora gli elementi e gli attributi di cui non è stato eseguito il mapping (perché non sono descritti nello schema oppure perché vengono annotati nello schema XSD con `sql:mapped="false"`). Tutti i dati di cui non è stato eseguito il mapping vengono inseriti nella colonna di overflow, se tale colonna viene specificata tramite `sql:overflow-field`.  
  
 Si consideri, ad esempio, lo schema XSD seguente:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="1">  
<xsd:complexType>  
<xsd:sequence>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
       <xsd:attribute name="CustomerID"  type="xsd:integer" />  
       <xsd:attribute name="CompanyName" type="xsd:string" />  
       <xsd:attribute name="City"        type="xsd:string" />  
       <xsd:attribute name="HomePhone"   type="xsd:string"   
                                       sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:sequence>  
</xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 Poiché il **HomePhone** attributo specifica `sql:mapped="false"`, il caricamento Bulk XML non è associato questo attributo alla colonna corrispondente. Lo schema XSD identifica una colonna di overflow (**OverflowColumn**) in cui il caricamento di massa XML memorizza i dati non utilizzati.  
  
### <a name="to-test-a-working-sample"></a>Per testare un esempio reale  
  
1.  Creare la tabella seguente nel **tempdb** database:  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust  
              (CustomerID     int         PRIMARY KEY,  
               CompanyName    varchar(20) NOT NULL,  
               City           varchar(20) DEFAULT 'Seattle',  
               OverflowColumn nvarchar(200))  
    GO  
    ```  
  
2.  Salvare lo schema fornito in questo esempio come SampleSchema.xml.  
  
3.  Salvare i dati XML di esempio seguenti come file SampleXMLData.xml:  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai"   
                 City="NY" HomePhone="111-1111" />  
      <Customers CustomerID="1112" CompanyName="Dont Know"   
                 City="LA" HomePhone="222-2222" />  
    </ROOT>  
    ```  
  
4.  Per eseguire il caricamento bulk XML, salvare ed eseguire questo esempio di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic, Scripting Edition (VBScript) come file Sample.vbs:  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
 Di seguito viene indicato lo schema XDR equivalente:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
   <ElementType name="Customers" sql:relation="Cust"  
                             sql:overflow-field="OverflowColumn" >  
      <AttributeType name="CustomerID" />  
      <AttributeType name="CompanyName"  />  
      <AttributeType name="City"  />  
      <AttributeType name="HomePhone" />  
      <attribute type="CustomerID"  />  
      <attribute type="CompanyName"  />  
      <attribute type="City" />  
      <attribute type="HomePhone" sql:map-field="0" />  
   </ElementType>  
</Schema>  
```  
  
  
