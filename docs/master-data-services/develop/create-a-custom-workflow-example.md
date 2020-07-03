---
title: Beispiel für einen benutzerdefinierten Workflow
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 880cf38105bd70198a52c55feec151e163f21c28
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900990"
---
# <a name="create-a-custom-workflow---example"></a>Erstellen eines benutzerdefinierten Workflows – Beispiel

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Wenn Sie in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] eine benutzerdefinierte Klassenbibliothek für den Workflow erstellen, erstellen Sie eine Klasse, die die Schnittstelle „Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender“ implementiert. Diese Schnittstelle enthält eine Methode, [Microsoft. masterdataservices. workflowtypeextender. iworkflowtypeextender. StartWorkflow *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) , die beim Start eines Workflows von SQL Server MDS Workflow Integration Service aufgerufen wird. Die [Microsoft. masterdataservices. workflowtypeextender. iworkflowtypeextender. StartWorkflow *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) -Methode enthält zwei Parameter: Workflow Type enthält den Text, den Sie in in das Textfeld *Workflowtyp* eingegeben **Workflow type** [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] haben, und *dataelement* enthält Metadaten und Elementdaten für das Element, das die Workflow Geschäftsregel ausgelöst hat.  
  
## <a name="custom-workflow-example"></a>Beispiel für einen benutzerdefinierten Workflow  
 Im folgenden Codebeispiel wird gezeigt, wie Sie die [Microsoft. masterdataservices. workflowtypeextender. iworkflowtypeextender. StartWorkflow *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) -Methode implementieren, um die Attribute Name, Code und lastchgusername aus den XML-Daten für das Element zu extrahieren, das die Workflow Geschäftsregel ausgelöst hat Ein Beispiel für die Elementdaten-XML und eine Erläuterung der enthaltenen Tags finden Sie unter [Benutzerdefinierte Workflow-XML-Beschreibung &#40;Master Data Services&#41;](../../master-data-services/develop/create-a-custom-workflow-xml-description.md).  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines benutzerdefinierten Workflows &#40;Master Data Services&#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)  
  
  
