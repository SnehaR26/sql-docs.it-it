---
title: Eseguire, rieseguire una query ed eliminare i metodi esempio (VB) | Microsoft Docs
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
- Requery method [ADO], Visual Basic example
- Clear method [ADO], Visual Basic example
- Execute method [ADO], Visual Basic example
ms.assetid: ed5e1b60-3769-4b26-a253-1d721e37941d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11fe5ef40e06772c38390096363903113a28bd46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684509"
---
# <a name="execute-requery-and-clear-methods-example-vb"></a>Eseguire, rieseguire una query ed eliminare i metodi esempio (VB)
Questo esempio viene illustrato il **Execute** metodo quando viene eseguito dallo entrambi una [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto e un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto. Usa anche il [Requery](../../../ado/reference/ado-api/requery-method.md) metodo per recuperare i dati correnti in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)e il [cancellare](../../../ado/reference/ado-api/clear-method-ado.md) metodo per cancellare il contenuto del [errori](../../../ado/reference/ado-api/errors-collection-ado.md)collection. (Il **errori** raccolta è accessibile tramite il **connessione** oggetto del [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà del [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).) Le procedure ExecuteCommand e PrintOutput sono necessari per eseguire questa procedura.  
  
```  
'BeginExecuteVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo Err_Execute  
  
    ' connection, command, and recordset variables  
    Dim Cnxn As ADODB.Connection  
    Dim cmdChange As ADODB.Command  
    Dim rstTitles As ADODB.Recordset  
    Dim Err As ADODB.Error  
    Dim strSQLChange As String  
    Dim strSQLRestore As String  
    Dim strSQLTitles  
    Dim strCnxn As String  
  
     ' Define two SQL statements to execute as command text  
    strSQLChange = "UPDATE Titles SET Type = 'self_help' WHERE Type = 'psychology'"  
    strSQLRestore = "UPDATE Titles SET Type = 'psychology' WHERE Type = 'self_help'"  
  
     ' Open connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Set Cnxn = New ADODB.Connection  
    Cnxn.Open strCnxn  
  
     ' Create command object  
    Set cmdChange = New ADODB.Command  
    Set cmdChange.ActiveConnection = Cnxn  
    cmdChange.CommandText = strSQLChange  
  
     ' Open titles table  
    Set rstTitles = New ADODB.Recordset  
    strSQLTitles = "titles"  
    rstTitles.Open strSQLTitles, Cnxn, , , adCmdTable  
  
    ' Print report of original data  
    Debug.Print _  
       "Data in Titles table before executing the query"  
    PrintOutput rstTitles  
  
    ' Call the ExecuteCommand subroutine below to execute cmdChange command  
    ExecuteCommand cmdChange, rstTitles  
  
    ' Print report of new data  
    Debug.Print _  
       "Data in Titles table after executing the query"  
    PrintOutput rstTitles  
  
    ' Use the Connection object's execute method to  
    ' execute SQL statement to restore data and trap for  
    ' errors, checking the Errors collection if necessary  
    Cnxn.Execute strSQLRestore, , adExecuteNoRecords  
  
    ' Retrieve the current data by requerying the recordset  
    rstTitles.Requery  
  
    ' Print report of restored data using sub from below  
    Debug.Print "Data after executing the query to restore the original information "  
    PrintOutput rstTitles  
  
    ' clean up  
    rstTitles.Close  
    Cnxn.Close  
    Set rstTitles = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
Err_Execute:  
    ' Notify user of any errors that result from  
    ' executing the query  
    If rstTitles.ActiveConnection.Errors.Count >= 0 Then  
       For Each Err In rstTitles.ActiveConnection.Errors  
          MsgBox "Error number: " & Err.Number & vbCr & _  
             Err.Description  
       Next Err  
    End If  
  
    ' clean up  
    If Not rstTitles Is Nothing Then  
        If rstTitles.State = adStateOpen Then rstTitles.Close  
    End If  
    Set rstTitles = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
  
Public Sub ExecuteCommand(cmdTemp As ADODB.Command, rstTemp As ADODB.Recordset)  
  
   Dim Err As Error  
  
   ' Run the specified Command object and trap for  
   ' errors, checking the Errors collection  
   On Error GoTo Err_Execute  
   cmdTemp.Execute  
   On Error GoTo 0  
  
   ' Retrieve the current data by requerying the recordset  
   rstTemp.Requery  
  
   Exit Sub  
  
Err_Execute:  
  
   ' Notify user of any errors that result from  
   ' executing the query  
   If rstTemp.ActiveConnection.Errors.Count > 0 Then  
      For Each Err In rstTemp.ActiveConnection.Errors  
         MsgBox "Error number: " & Err.Number & vbCr & _  
            Err.Description  
      Next Err  
   End If  
  
   Resume Next  
  
End Sub  
  
Public Sub PrintOutput(rstTemp As ADODB.Recordset)  
  
   ' Enumerate Recordset  
   Do While Not rstTemp.EOF  
      Debug.Print "  " & rstTemp!Title & _  
         ", " & rstTemp!Type  
      rstTemp.MoveNext  
   Loop  
  
End Sub  
'EndExecuteVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md)   
 [Eseguire il metodo (comando ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Eseguire il metodo (connessione ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Metodo Requery](../../../ado/reference/ado-api/requery-method.md)
