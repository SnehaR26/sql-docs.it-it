---
title: Esempio di flusso di lavoro personalizzato (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: bfc0c557f8c645fe7dfa56850bce64b533bc9340
ms.contentlocale: it-it
ms.lasthandoff: 09/07/2017

---
# <a name="create-a-custom-workflow---example"></a>Creare un flusso di lavoro personalizzato - Esempio
  Quando in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] si crea una libreria di classi del flusso di lavoro personalizzato, viene creata una classe che implementa l'interfaccia Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender. Questa interfaccia include il metodo <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> chiamato da SQL Server MDS Workflow Integration Service all'avvio di un flusso di lavoro. Il metodo <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> contiene due parametri: *workflowType* contiene il testo immesso nella casella di testo **Tipo di flusso di lavoro** in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], mentre *dataElement* contiene i metadati e i dati dell'elemento che ha attivato la regola business del flusso di lavoro.  
  
## <a name="custom-workflow-example"></a>Esempio di flusso di lavoro personalizzato  
 Nell'esempio di codice seguente viene illustrato come implementare il metodo <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> per estrarre gli attributi Name, Code e LastChgUserName dai dati XML dell'elemento che ha attivato la regola business del flusso di lavoro e come chiamare una stored procedure per inserirli in un altro database. Per un esempio del codice XML dei dati dell'elemento e per una spiegazione dei tag in esso contenuti, vedere [Descrizione XML del flusso di lavoro personalizzato &#40;Master Data Services&#41;](../../master-data-services/develop/create-a-custom-workflow-xml-description.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un flusso di lavoro personalizzato &#40;Master Data Services&#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)  
  
  