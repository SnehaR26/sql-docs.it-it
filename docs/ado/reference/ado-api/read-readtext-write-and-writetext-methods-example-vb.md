---
title: Read, ReadText, Write e WriteText metodi esempio (VB) | Microsoft Docs
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
- ReadText method [ADO], Visual Basic example
- Write method [ADO], Visual Basic example
- Read method [ADO], Visual Basic example
- WriteText method [ADO], Visual Basic example
ms.assetid: 699b73f7-04f9-4d46-94b2-6cb12be6de56
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7cf21d0f932708b23978bb36db5c800358a6fa90
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731001"
---
# <a name="read-readtext-write-and-writetext-methods-example-vb"></a>Read, ReadText, Write e WriteText metodi esempio (VB)
In questo esempio viene illustrato come leggere il contenuto di una casella di testo in un testo entrambe [Stream](../../../ado/reference/ado-api/stream-object-ado.md) e un file binario **Stream**. Includono altre proprietà e metodi illustrati [posizione](../../../ado/reference/ado-api/position-property-ado.md), [Size](../../../ado/reference/ado-api/size-property-ado-parameter.md), [Charset](../../../ado/reference/ado-api/charset-property-ado.md), e [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
```  
'BeginReadVB  
Private Sub cmdRead_Click()  
    On Error GoTo ErrorHandler  
  
    'Declare variables  
    Dim objStream As Stream  
    Dim varA As Variant  
    Dim bytA() As Byte  
    Dim i As Integer  
    Dim strBytes As String  
  
    'Instantiate and Open Stream  
    Set objStream = New Stream  
    objStream.Open  
  
    'Write the text content of a textbox to the stream  
    If Text1.Text = "" Then  
        Err.Raise 1, , "The text field is blank."  
    End If  
    objStream.WriteText Text1.Text  
  
    'Display the text contents and size of the stream  
    objStream.Position = 0  
    Debug.Print "Default text:"  
    Debug.Print objStream.ReadText  
    Debug.Print objStream.Size  
  
    'Switch character set and display  
    objStream.Position = 0  
    objStream.Charset = "Windows-1252"  
    Debug.Print "New Charset text:"  
    Debug.Print objStream.ReadText  
    Debug.Print objStream.Size  
  
    'Switch to a binary stream and display  
    objStream.Position = 0  
    objStream.Type = adTypeBinary  
    Debug.Print "Binary:"  
    Debug.Print objStream.Read  
    Debug.Print objStream.Size  
  
    'Load an array of bytes with the text box text  
    ReDim bytA(Len(Text1.Text))  
    For i = 1 To Len(Text1.Text)  
        bytA(i - 1) = CByte(Asc(Mid(Text1.Text, i, 1)))  
    Next  
  
    'Write the buffer to the binary stream and display  
    objStream.Position = 0  
    objStream.Write bytA()  
    objStream.SetEOS  
    objStream.Position = 0  
    Debug.Print "Binary after Write:"  
    Debug.Print objStream.Read  
    Debug.Print objStream.Size  
  
    'Switch back to a text stream and display  
    Debug.Print "Translated back:"  
    objStream.Position = 0  
    objStream.Type = adTypeText  
    Debug.Print objStream.ReadText  
    Debug.Print objStream.Size  
  
    ' clean up  
    objStream.Close  
    Set objStream = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not objStream Is Nothing Then  
        If objStream.State = adStateOpen Then objStream.Close  
    End If  
    Set objStream = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndReadVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Charset (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)   
 [Proprietà Position (ADO)](../../../ado/reference/ado-api/position-property-ado.md)   
 [Metodo Read](../../../ado/reference/ado-api/read-method.md)   
 [Metodo ReadText](../../../ado/reference/ado-api/readtext-method.md)   
 [Metodo SetEOS](../../../ado/reference/ado-api/seteos-method.md)   
 [Proprietà Size (Stream ADO)](../../../ado/reference/ado-api/size-property-ado-stream.md)   
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Write (metodo)](../../../ado/reference/ado-api/write-method.md)   
 [Metodo WriteText](../../../ado/reference/ado-api/writetext-method.md)
