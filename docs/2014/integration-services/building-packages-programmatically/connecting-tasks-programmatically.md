---
title: Programmgesteuertes Verbinden von Tasks | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- constraints [Integration Services]
ms.assetid: 23668e88-cef4-4009-a9cf-38e607eab7a2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d5343ecb97f631e7e9dd3dbf5e2600008dc0f8fe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62771916"
---
# <a name="connecting-tasks-programmatically"></a>Programmgesteuertes Verbinden von Tasks
  Eine Rangfolgeneinschränkung, die in dem Objektmodell durch die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>-Klasse dargestellt wird, legt die Reihenfolge, in der die <xref:Microsoft.SqlServer.Dts.Runtime.Executable>-Objekte in einem Paket ausgeführt werden, fest. Durch die Rangfolgeneinschränkung kann die Ausführung der Container und Tasks in einem Paket von dem Ergebnis der Ausführung eines vorherigen Tasks oder Containers abhängig gemacht werden. Rangfolgeneinschränkungen werden zwischen <xref:Microsoft.SqlServer.Dts.Runtime.Executable>-Objektpaaren durch Aufrufen der <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints>-Auflistung für das Containerobjekt eingerichtet. Nachdem Sie eine Einschränkung zwischen zwei ausführbaren Objekten erstellt haben, legen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A>-Eigenschaft fest, um die Kriterien für die Ausführung des zweiten ausführbaren in der Einschränkung definierten Objekts festzulegen.  
  
 Abhängig von dem Wert, den Sie, wie in der folgenden Tabelle beschrieben, für die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A>-Eigenschaft festlegen, können Sie in einer einzigen Rangfolgeneinschränkung sowohl eine Einschränkung als auch einen Ausdruck verwenden:  
  
|Wert der EvalOp-Eigenschaft|Description|  
|----------------------------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Constraint>|Gibt an, dass das Ausführungsergebnis bestimmt, ob der eingeschränkte Container oder Task ausgeführt wird. Legen Sie für die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A>-Eigenschaft von <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> den gewünschten Wert aus der <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>-Enumeration fest.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Expression>|Gibt an, dass der Wert eines Ausdrucks bestimmt, ob der eingeschränkte Container oder Task ausgeführt wird. Legen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A>-Eigenschaft von <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> fest.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionAndConstraint>|Gibt an, dass das Einschränkungsergebnis auftreten und der Ausdruck ausgewertet werden muss, damit der eingeschränkte Container oder Task ausgeführt wird. Legen Sie sowohl die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A>- als auch die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A>-Eigenschaften von <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> fest, und legen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A>-Eigenschaft als `true` fest.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionOrConstraint>|Gibt an, dass entweder das Einschränkungsergebnis auftreten oder der Ausdruck ausgewertet werden muss, damit der eingeschränkte Container oder Task ausgeführt wird. Legen Sie sowohl die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A>- als auch die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A>-Eigenschaften von <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> fest, und legen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A>-Eigenschaft als `false` fest.|  
  
 Im folgenden Codebeispiel wird das Hinzufügen von zwei Tasks zu einem Paket veranschaulicht. Zwischen ihnen wird eine <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> erstellt, die verhindert, dass der zweite Task vor Beendung des ersten Tasks ausgeführt wird.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
  
      // Add a File System task.  
      Executable eFileTask1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost1 = eFileTask1 as TaskHost;  
  
      // Add a second File System task.  
      Executable eFileTask2 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost2 = eFileTask2 as TaskHost;  
  
      // Put a precedence constraint between the tasks.  
      // Set the constraint to specify that the second File System task cannot run  
      // until the first File System task finishes.  
      PrecedenceConstraint pcFileTasks =   
        p.PrecedenceConstraints.Add((Executable)thFileHost1, (Executable)thFileHost2);  
      pcFileTasks.Value = DTSExecResult.Completion;  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task.  
    Dim eFileTask1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost1 As TaskHost = CType(eFileTask1, TaskHost)  
  
    ' Add a second File System task.  
    Dim eFileTask2 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost2 As TaskHost = CType(eFileTask2, TaskHost)  
  
    ' Put a precedence constraint between the tasks.  
    ' Set the constraint to specify that the second File System task cannot run  
    ' until the first File System task finishes.  
    Dim pcFileTasks As PrecedenceConstraint = _  
      p.PrecedenceConstraints.Add(CType(thFileHost1, Executable), CType(thFileHost2, Executable))  
    pcFileTasks.Value = DTSExecResult.Completion  
  
  End Sub  
  
End Module  
```  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Hinzufügen des Datenflusstasks](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
  
  
