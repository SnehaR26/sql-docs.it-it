---
title: Tabelle insieme (ADOX) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Catalog::Tables
- Tables
helpviewer_keywords:
- Tables collection [ADOX]
ms.assetid: 38d750e7-f3fb-426e-b4b4-55eea4f1a654
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1489bb1716cb29116e385158e6f05dcc3d028431
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="tables-collection-adox"></a>Raccolta di tabelle (ADOX)
Contiene tutti [tabella](../../../ado/reference/adox-api/table-object-adox.md) gli oggetti di un catalogo.  
  
## <a name="remarks"></a>Osservazioni  
 Il [Append](../../../ado/reference/adox-api/append-method-adox-tables.md) metodo per un **tabelle** insieme è univoco in ADOX. È possibile effettuare le operazioni seguenti:  
  
-   Aggiungere una nuova tabella alla raccolta con il **Append** metodo.  
  
 Le proprietà e i metodi rimanenti sono standard per le raccolte di ADO. È possibile effettuare le operazioni seguenti:  
  
-   Accedere a una tabella nella raccolta con il [elemento](../../../ado/reference/ado-api/item-property-ado.md) proprietà.  
  
-   Restituire il numero di tabelle contenute nella raccolta con il [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà.  
  
-   Rimuovere una tabella dalla raccolta con il [eliminare](../../../ado/reference/adox-api/delete-method-adox-collections.md) metodo.  
  
-   Aggiornare gli oggetti nella raccolta in modo da riflettere lo schema del database corrente con il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo.  
  
 Alcuni provider può restituire altri oggetti dello schema, ad esempio una vista, nel **tabelle** insieme. Di conseguenza, alcuni insiemi ADOX possono contenere più riferimenti allo stesso oggetto. Se si elimina l'oggetto da una raccolta, la modifica non saranno visibile in un altro insieme che fa riferimento all'oggetto eliminato finché il **aggiornamento** metodo viene chiamato per la raccolta. Con il Provider OLE DB per Microsoft Jet, ad esempio, vengono restituite le visualizzazioni con la **tabelle** insieme. Se si rimuove una vista, è necessario aggiornare il **tabelle** raccolta prima che la raccolta verrà applicata la modifica.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà di raccolta di tabelle, metodi ed eventi](../../../ado/reference/adox-api/tables-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà ActiveConnection catalogo (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Le colonne e tabelle aggiungere metodi, esempio di proprietà Name (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connessione Close (metodo), esempio di proprietà di tipo tabella (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Chiavi Aggiungi metodo, tipo di chiave, RelatedColumn, RelatedTable e UpdateRule proprietà esempio (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Oggetto del catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Oggetto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)