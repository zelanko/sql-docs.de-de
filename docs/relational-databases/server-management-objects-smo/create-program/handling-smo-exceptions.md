---
title: Behandeln von SMO-Ausnahmen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b533291a9cc7a04efe0f3f2de0b39bc3fc544f83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098279"
---
# <a name="handling-smo-exceptions"></a>Behandeln von SMO-Ausnahmen
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In verwaltetem Code werden Ausnahmen ausgelöst, wenn ein Fehler auftritt. SMO-Methoden und -Eigenschaften melden keinen Erfolg oder Fehler mit dem Rückgabewert. Stattdessen können Ausnahmen von einem Ausnahmehandler abgefangen und behandelt werden.  
  
 In SMO sind verschiedene Ausnahmeklassen vorhanden. Informationen über die Ausnahme können aus den Ausnahmeeigenschaften wie der **Message** -Eigenschaft, die eine Textmeldung über die Ausnahme angibt, extrahiert werden.  
  
 Die Ausnahmebehandlungsanweisungen sind für die Programmiersprache spezifisch. In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic gibt es hierfür beispielsweise die **Catch** -Anweisung.  
  
## <a name="inner-exceptions"></a>Interne Ausnahmen  
 Ausnahmen können entweder allgemein oder spezifisch sein. Allgemeine Ausnahmen enthalten einen Satz spezifischer Ausnahmen. Einige **Catch** -Anweisungen können dazu verwendet werden, erwartete Fehler zu behandeln und die übrigen Fehler an den allgemeinen Ausnahmebehandlungscode weiterzugeben. Ausnahmen treten oft in einer überlappenden Sequenz auf. Häufig wird eine SMO-Ausnahme von einer SQL-Ausnahme verursacht. Um dies zu ermitteln, wird die **InnerException** -Eigenschaft nacheinander verwendet. So wird die ursprüngliche Ausnahme bestimmt, die die letzte Ausnahme auf oberster Ebene ausgelöst hat.  
  
> [!NOTE]  
>  Die **SQLException** Ausnahme deklariert ist, der **"System.Data.SqlClient"** Namespace.  
  
 ![Ein Diagramm, das zeigt, die Ebenen aus dem ausnahmeflussebenen](../../../relational-databases/server-management-objects-smo/create-program/media/exception-flow.gif "ein Diagramm, das zeigt, die Ebenen aus dem ausnahmeflussebenen")  
  
 Die Abbildung zeigt den Verlauf der Ausnahmen durch die Anwendungsebenen.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).
  
## <a name="catching-an-exception-in-visual-basic"></a>Abfangen einer Ausnahme in Visual Basic  
 Dieses Codebeispiel zeigt, wie Sie mit der **testen... Catch... Zum Schluss** [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] Anweisung um eine SMO-Ausnahme abzufangen. Alle SMO-Ausnahmen haben den Typ SmoException und werden im SMO-Verweis aufgelistet. Die Sequenz von internen Ausnahmen wird angezeigt, um den Ursprung des Fehlers anzugeben. Weitere Informationen finden Sie in der Dokumentation zu [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.  
  
```VBNET
'This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace is included.
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.
'Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.
Dim op As [Operator]
op = New [Operator](srv.JobServer, "Test_Operator")
op.Create()
'Start exception handling.
Try
    'Create the operator again to cause an SMO exception.
    Dim opx As OperatorCategory
    opx = New OperatorCategory(srv.JobServer, "Test_Operator")
    opx.Create()
    'Catch the SMO exception
Catch smoex As SmoException
    Console.WriteLine("This is an SMO Exception")
    'Display the SMO exception message.
    Console.WriteLine(smoex.Message)
    'Display the sequence of non-SMO exceptions that caused the SMO exception.
    Dim ex As Exception
    ex = smoex.InnerException
    Do While ex.InnerException IsNot (Nothing)
        Console.WriteLine(ex.InnerException.Message)
        ex = ex.InnerException
    Loop
    'Catch other non-SMO exceptions.
Catch ex As Exception
    Console.WriteLine("This is not an SMO exception.")
End Try
``` 
  
## <a name="catching-an-exception-in-visual-c"></a>Abfangen einer Ausnahme in Visual C#  
 Dieses Codebeispiel zeigt, wie Sie mit der **testen... Catch... Zum Schluss** Visual C# Anweisung um eine SMO-Ausnahme abzufangen. Alle SMO-Ausnahmen haben den Typ SmoException und werden im SMO-Verweis aufgelistet. Die Sequenz von internen Ausnahmen wird angezeigt, um den Ursprung des Fehlers anzugeben. Weitere Informationen finden Sie in der Dokumentation zu Visual C#.  
  
```csharp  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
