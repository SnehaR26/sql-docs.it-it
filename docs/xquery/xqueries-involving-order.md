---
title: Query XQuery che implicano ordine | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sequence [XQuery]
- XQuery, sequence
- ordered expressions [XQuery]
ms.assetid: 4f1266c5-93d7-402d-94ed-43f69494c04b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: df4b8f9b3c6c2a0a4e8aee3e6ff67998d3bef353
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120018"
---
# <a name="xqueries-involving-order"></a>Query XQuery che implicano l'ordinamento
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Nei database relazionali non esiste il concetto di sequenza. Ad esempio, non è possibile eseguire una richiesta per ottenere il primo cliente del database, Tuttavia, è possibile eseguire query sui documenti XML e recuperare il primo \<cliente > elemento. In questo modo si otterrà lo stesso cliente.  
  
 In questo argomento vengono illustrate le query basate sulla sequenza di visualizzazione dei nodi nel documento.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-retrieve-manufacturing-steps-at-the-second-work-center-location-for-a-product"></a>A. Recupero delle fasi di produzione di un prodotto nel secondo centro di lavorazione  
 La query seguente recupera le fasi di produzione di un modello di prodotto specifico nel secondo centro di lavorazione di una sequenza di centri coinvolti nel processo di produzione.  
  
```sql
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    <ManuStep ProdModelID = "{sql:column("Production.ProductModel.ProductModelID")}"  
                ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >  
     <Location>  
       { (//AWMI:root/AWMI:Location)[2]/@* }  
       <Steps>  
         { for $s in (//AWMI:root/AWMI:Location)[2]//AWMI:step  
           return  
              <Step>  
               { string($s) }  
              </Step>  
         }  
        </Steps>  
      </Location>  
     </ManuStep>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Le espressioni tra parentesi graffe vengono sostituite dal risultato della relativa valutazione. Per altre informazioni, vedere [costruzione di strutture XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md).  
  
-   **@\*** Recupera tutti gli attributi del secondo centro di lavorazione.  
  
-   L'iterazione di FLWOR (FOR ... RETURN) recupera tutti gli elementi figlio <`step`> del secondo centro di lavorazione.  
  
-   Il [funzione SQL: Column (XQuery)](../xquery/xquery-extension-functions-sql-column.md) include il valore relazionale nel XML che viene costruito.  
  
 Risultato:  
  
```  
<ManuStep ProdModelID="7" ProductModelName="HL Touring Frame">  
  <Location LocationID="20" SetupHours="0.15"   
              MachineHours="2"  LaborHours="1.75" LotSize="1">  
  <Steps>  
   <Step>Assemble all frame components following blueprint 1299.</Step>  
     …  
  </Steps>  
 </Location>  
</ManuStep>    
```  
  
 La query precedente recupera unicamente i nodi di testo. Se si desidera che l'intera <`step`> elemento restituito al contrario, rimuovere il **String ()** funzione della query:  
  
### <a name="b-find-all-the-material-and-tools-used-at-the-second-work-center-location-in-the-manufacturing-of-a-product"></a>B. Ricerca di tutti i materiali e gli strumenti utilizzati nel secondo centro di lavorazione per la produzione di un prodotto  
 La query seguente recupera gli strumenti e i materiali utilizzati per un modello di prodotto specifico nel secondo centro di lavorazione della sequenza di centri coinvolta nel processo di produzione.  
  
```sql
SELECT Instructions.query('  
    declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   <Location>  
      { (//AWMI:root/AWMI:Location)[1]/@* }  
       <Tools>  
         { for $s in (//AWMI:root/AWMI:Location)[1]//AWMI:step//AWMI:tool  
           return  
              <Tool>  
                { string($s) }  
              </Tool>  
          }  
        </Tools>  
        <Materials>  
            { for $s in (//AWMI:root/AWMI:Location)[1]//AWMI:step//AWMI:material  
              return  
                 <Material>  
                    { string($s) }  
                 </Material>  
             }  
         </Materials>  
  </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   La query crea l'elemento <Loca`tion`> e recupera i valori dei relativi attributi dal database.  
  
-   La query utilizza due iterazioni di FLWOR (for...return), una per recuperare gli strumenti e l'altra per recuperare i materiali utilizzati.  
  
 Risultato:  
  
```xml
<Location LocationID="10" SetupHours=".5"   
          MachineHours="3" LaborHours="2.5" LotSize="100">  
  <Tools>  
    <Tool>T-85A framing tool</Tool>  
    <Tool>Trim Jig TJ-26</Tool>  
    <Tool>router with a carbide tip 15</Tool>  
    <Tool>Forming Tool FT-15</Tool>  
  </Tools>  
  <Materials>  
    <Material>aluminum sheet MS-2341</Material>  
  </Materials>  
</Location>  
```  
  
### <a name="c-retrieve-the-first-two-product-feature-descriptions-from-the-product-catalog"></a>C. Recupero delle descrizioni delle prime due caratteristiche di un prodotto dal catalogo dei prodotti  
 La query seguente recupera le descrizioni delle prime due caratteristiche di un modello di prodotto specifico dall'elemento <`Features`> nel catalogo dei modelli del prodotto.  
  
```sql
SELECT CatalogDescription.query('  
     declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <ProductModel ProductModelID= "{ data( (/p1:ProductDescription/@ProductModelID)[1] ) }"  
                   ProductModelName = "{ data( (/p1:ProductDescription/@ProductModelName)[1] ) }" >  
       {  
         for $F in /p1:ProductDescription/p1:Features  
         return   
           $F/*[position() <= 2]   
       }  
     </ProductModel>  
      ') as x  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Dalla query precedente si noti quanto segue:  
  
 La query costruisce il codice XML che include l'elemento <`ProductModel`> per cui sono presenti gli attributi ProductModelID e ProductModelName.  
  
-   La query utilizza un ciclo FOR ... RETURN per recuperare le descrizioni delle caratteristiche del modello del prodotto. Il **Position** funzione viene utilizzata per recuperare le prime due caratteristiche.  
  
 Risultato:  
  
```xml
<ProductModel ProductModelID="19" ProductModelName="Mountain 100">  
 <p1:Warranty   
  xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
  <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
  <p1:Description>parts and labor</p1:Description>  
 </p1:Warranty>  
 <p2:Maintenance   
  xmlns:p2="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
  <p2:NoOfYears>10</p2:NoOfYears>  
  <p2:Description>maintenance contact available through your dealer   
            or any AdventureWorks retail store.  
  </p2:Description>  
 </p2:Maintenance>  
</ProductModel>   
```  
  
### <a name="d-find-the-first-two-tools-used-at-the-first-work-center-location-in-the-manufacturing-process-of-the-product"></a>D. Ricerca dei primi due strumenti utilizzati nel primo centro di lavorazione coinvolto nel processo di produzione del prodotto  
 La query seguente restituisce i primi due strumenti utilizzati per un modello di prodotto nel primo centro di lavorazione della sequenza di centri coinvolti nel processo di produzione. La query viene eseguita sulle istruzioni di produzione archiviati nel **istruzioni** della colonna della **Production. ProductModel** tabella.  
  
```sql
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   for $Inst in (//AWMI:root/AWMI:Location)[1]  
   return   
     <Location>  
       { $Inst/@* }  
       <Tools>  
         { for $s in ($Inst//AWMI:step//AWMI:tool)[position() <= 2]  
           return  
             <Tool>  
               { string($s) }  
             </Tool>  
         }  
       </Tools>  
     </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Risultato:  
  
```xml
<Location LocationID="10" SetupHours=".5"   
            MachineHours="3" LaborHours="2.5" LotSize="100">  
  <Tools>  
    <Tool>T-85A framing tool</Tool>  
    <Tool>Trim Jig TJ-26</Tool>  
  </Tools>  
</Location>   
```  
  
### <a name="e-find-the-last-two-manufacturing-steps-at-the-first-work-center-location-in-the-manufacturing-of-a-specific-product"></a>E. Ricerca delle ultime due fasi di produzione nel primo centro di lavorazione coinvolto nella produzione di un prodotto specifico  
 La query Usa la **Last** funzione per recuperare le ultime due fasi di produzione.  
  
```sql
SELECT Instructions.query('   
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  <LastTwoManuSteps>  
   <Last-1Step>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[(last()-1)]/text() }  
   </Last-1Step>  
   <LastStep>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[last()]/text() }  
   </LastStep>  
  </LastTwoManuSteps>') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Risultato:  
  
```xml
<LastTwoManuSteps>  
   <Last-1Step>When finished, inspect the forms for defects per   
               Inspection Specification .</Last-1Step>  
   <LastStep>Remove the frames from the tool and place them in the   
             Completed or Rejected bin as appropriate.</LastStep>  
</LastTwoManuSteps>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Dati XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Costruzione di strutture XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)  
  
  
