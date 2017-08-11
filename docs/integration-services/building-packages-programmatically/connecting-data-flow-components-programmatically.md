---
title: La connessione a livello di programmazione di componenti flusso di dati | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], components
- paths [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 404ecab7-7698-447b-93d6-dd256beb11ff
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 40869328965e049b5981e94655226bc0a78dc37f
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-data-flow-components-programmatically"></a>Connessione dei componenti del flusso di dati a livello di programmazione
  Dopo avere aggiunto componenti all'attività Flusso di dati, connetterli per creare un albero di esecuzione che rappresenti il flusso di dati dalle origini attraverso le trasformazioni alle destinazioni. Utilizzare oggetti <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> per connettere i componenti nel flusso di dati.  
  
## <a name="creating-a-path"></a>Creazione di un percorso  
 Chiamare il metodo di nuovo il <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.PathCollection%2A> proprietà del <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipe> interfaccia per creare un nuovo percorso e aggiungerlo alla raccolta di percorsi nell'attività flusso di dati. Questo metodo restituisce un nuovo oggetto <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> disconnesso, che verrà quindi utilizzato per connettere due componenti.  
  
 Chiamare il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100.AttachPathAndPropagateNotifications%2A> per connettere il percorso e notificare ai componenti partecipanti nel percorso che sono stati connessi. Questo metodo accetta <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> del componente a monte e <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> del componente a valle come parametri. Per impostazione predefinita, la chiamata al metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> del componente crea un singolo input per i componenti che includono input e un singolo output per i componenti che includono output. Nell'esempio seguente vengono utilizzati l'output predefinito dell'origine e l'input predefinito della destinazione.  
  
## <a name="next-step"></a>Passaggio successivo  
 Dopo aver stabilito un percorso tra due componenti, il passaggio successivo consiste nel mapping delle colonne di input nel componente a valle, descritto nell'argomento successivo, [selezione Input le colonne a livello di codice](../../integration-services/building-packages-programmatically/selecting-input-columns-programmatically.md).  
  
## <a name="sample"></a>Esempio  
 Nell'esempio di codice seguente è illustrato come stabilire un percorso tra due componenti.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Create the source component.    
      IDTSComponentMetaData100 source =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      source.ComponentClassID = "DTSAdapter.OleDbSource";  
      CManagedComponentWrapper srcDesignTime = source.Instantiate();  
      srcDesignTime.ProvideComponentProperties();  
  
      // Create the destination component.  
      IDTSComponentMetaData100 destination =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      destination.ComponentClassID = "DTSAdapter.OleDbDestination";  
      CManagedComponentWrapper destDesignTime = destination.Instantiate();  
      destDesignTime.ProvideComponentProperties();  
  
      // Create the path.  
      IDTSPath100 path = dataFlowTask.PathCollection.New();  
      path.AttachPathAndPropagateNotifications(source.OutputCollection[0],  
        destination.InputCollection[0]);  
    }  
  }  
```  
  
 }  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Create the source component.    
    Dim source As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    source.ComponentClassID = "DTSAdapter.OleDbSource"  
    Dim srcDesignTime As CManagedComponentWrapper = source.Instantiate()  
    srcDesignTime.ProvideComponentProperties()  
  
    ' Create the destination component.  
    Dim destination As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    destination.ComponentClassID = "DTSAdapter.OleDbDestination"  
    Dim destDesignTime As CManagedComponentWrapper = destination.Instantiate()  
    destDesignTime.ProvideComponentProperties()  
  
    ' Create the path.  
    Dim path As IDTSPath100 = dataFlowTask.PathCollection.New()  
    path.AttachPathAndPropagateNotifications(source.OutputCollection(0), _  
      destination.InputCollection(0))  
  
  End Sub  
  
End Module  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Selezionare le colonne di Input a livello di codice](../../integration-services/building-packages-programmatically/selecting-input-columns-programmatically.md)  
  
  