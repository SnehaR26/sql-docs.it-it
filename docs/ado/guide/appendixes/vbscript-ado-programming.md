---
title: Programmazione ADO VBScript | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, VBScript
- VBScript [ADO]
ms.assetid: 6aaaf6d0-1376-4473-bea6-b81f2645a9ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8fe2eb1d6d5c83a85fed628b02869cbf7b29eee4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679999"
---
# <a name="vbscript-ado-programming"></a>Programmazione ADO VBScript
## <a name="creating-an-ado-project"></a>Creazione di un progetto di ADO  
 Microsoft Visual Basic, Scripting Edition non supporta le librerie dei tipi, quindi non è necessario fare riferimento ADO nel progetto. Di conseguenza, è supportata alcuna funzionalità associata come il completamento della riga di comando. Inoltre, per impostazione predefinita, le costanti enumerate ADO non sono definite in VBScript.  
  
 ADO fornisce, tuttavia, che è con due simboli di includere i file che contiene le definizioni seguenti da usare con VBScript:  
  
-   Per la creazione di script sul lato server utilizzare Adovbs. Inc, che viene installato nella cartella c:\Program Files\Common Files\System\ado\ per impostazione predefinita.  
  
-   Per l'uso degli script lato client Adcvbs. Inc, che viene installato nella cartella c:\Program Files\Common Files\System\msdac\ per impostazione predefinita.  
  
 È possibile copiare e incollare le definizioni di costanti da questi file nelle pagine ASP oppure, se si sta eseguendo lo scripting lato server, copiare i file Adovbs. inc in una cartella sul sito Web e farvi riferimento dalla pagina ASP simile al seguente:  
  
```  
<!--#include File="adovbs.inc"-->  
```  
  
## <a name="creating-ado-objects-in-vbscript"></a>Creazione di oggetti ADO VBScript  
 Non è possibile usare la **Dim** istruzione per assegnare gli oggetti a un tipo specifico in VBScript. VBScript, inoltre, non supporta il **New** sintassi utilizzata con la **Dim** istruzione in Visual Basic, Applications Edition. È invece necessario usare il **CreateObject** chiamata di funzione:  
  
```  
Dim Rs1  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
```  
  
## <a name="vbscript-examples"></a>Esempi di VBScript  
 Il codice seguente è un esempio generico del VBScript programmazione lato server in un file di pagina ASP (Active Server):  
  
```  
<%  @LANGUAGE="VBSCRIPT" %>  
<%  Option Explicit %>  
<!--#include File="adovbs.inc"-->  
<HTML>  
    <BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
  
    <!-- Your ASP Code goes here -->  
<%  
Dim Source  
Dim Connect  
Dim Rs1  
  
Source = "SELECT * FROM Authors"  
Connect = "Provider=sqloledb;Data Source=srv;" & _  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
Rs1.Open Source, Connect, adOpenForwardOnly  
Response.Write("Success!")  
%>  
    </BODY>  
</HTML>  
```  
  
 Esempi più specifici di VBScript sono inclusi nella documentazione di ADO. Per altre informazioni, vedere [esempi di codice ADO in Microsoft Visual Basic Scripting Edition](../../../ado/reference/ado-api/ado-code-examples-vbscript.md).  
  
## <a name="differences-between-vbscript-and-visual-basic"></a>Differenze tra VBScript e Visual Basic  
 Uso di ADO con VBScript è simile all'uso di ADO con Visual Basic in molti modi, tra cui utilizzo di sintassi. Tuttavia, esistono alcune differenze significative:  
  
-   Solo il tipo di dati Variant, che può contenere diversi tipi di dati supportato da VBScript. È possibile archiviare i dati che necessari in un tipo di dati Variant e i dati funzionerà in modo appropriato a causa di un cast eseguite da VBScript. Riconosce il tipo richiesto da ADO e la conversione del valore della variante di conseguenza.  
  
-   Non è possibile usare **in errore goto \<label >** all'interno di VBScript.  
  
-   Alcune delle funzioni predefinite di Visual Basic è supportato, ad esempio da VBScript **Msgbox**, **data**, e **IsNumeric**. Tuttavia, in quanto VBScript è un subset di Visual Basic, non tutte le funzioni predefinite sono supportate. Ad esempio, VBScript non supporta il **formato** funzione e alle funzioni dei / o file.
