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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f2cab3702ef41e5ea4ed01ab60c3a3b949832f84
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006360"
---
# <a name="handling-smo-exceptions"></a>Behandeln von SMO-Ausnahmen
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  In verwaltetem Code werden Ausnahmen ausgelöst, wenn ein Fehler auftritt. SMO-Methoden und -Eigenschaften melden keinen Erfolg oder Fehler mit dem Rückgabewert. Stattdessen können Ausnahmen von einem Ausnahmehandler abgefangen und behandelt werden.  
  
 In SMO sind verschiedene Ausnahmeklassen vorhanden. Informationen über die Ausnahme können aus den Ausnahmeeigenschaften wie der **Message** -Eigenschaft, die eine Textmeldung über die Ausnahme angibt, extrahiert werden.  
  
 Die Ausnahmebehandlungsanweisungen sind für die Programmiersprache spezifisch. In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic gibt es hierfür beispielsweise die **Catch** -Anweisung.  
  
## <a name="inner-exceptions"></a>Interne Ausnahmen  
 Ausnahmen können entweder allgemein oder spezifisch sein. Allgemeine Ausnahmen enthalten einen Satz spezifischer Ausnahmen. Einige **Catch** -Anweisungen können dazu verwendet werden, erwartete Fehler zu behandeln und die übrigen Fehler an den allgemeinen Ausnahmebehandlungscode weiterzugeben. Ausnahmen treten oft in einer überlappenden Sequenz auf. Häufig wird eine SMO-Ausnahme von einer SQL-Ausnahme verursacht. Um dies zu ermitteln, wird die **InnerException** -Eigenschaft nacheinander verwendet. So wird die ursprüngliche Ausnahme bestimmt, die die letzte Ausnahme auf oberster Ebene ausgelöst hat.  
  
> [!NOTE]  
>  Die **SqlException** -Ausnahme wird im Namespace " **System. Data. SqlClient** " deklariert.  
  
 ![Diagramm mit Ausnahmeflussebenen](../../../relational-databases/server-management-objects-smo/create-program/media/exception-flow.gif "Diagramm mit Ausnahmeflussebenen")  
  
 Die Abbildung zeigt den Verlauf der Ausnahmen durch die Anwendungsebenen.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C-&#35; SMO-Projekts in Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).
  
## <a name="catching-an-exception-in-visual-basic"></a>Abfangen einer Ausnahme in Visual Basic  
 In diesem Codebeispiel wird die Verwendung des **try... Catch... Schließlich** [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] Anweisung zum Abfangen einer SMO-Ausnahme. Alle SMO-Ausnahmen haben den Typ SmoException und werden im SMO-Verweis aufgelistet. Die Sequenz von internen Ausnahmen wird angezeigt, um den Ursprung des Fehlers anzugeben. Weitere Informationen finden Sie in der Dokumentation zu [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.  
  
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
 In diesem Codebeispiel wird die Verwendung des **try... Catch... **Die Visual c#-Anweisung zum Schluss fängt eine SMO-Ausnahme ab. Alle SMO-Ausnahmen haben den Typ SmoException und werden im SMO-Verweis aufgelistet. Die Sequenz von internen Ausnahmen wird angezeigt, um den Ursprung des Fehlers anzugeben. Weitere Informationen finden Sie in der Dokumentation zu Visual C#.  
  
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
  
  
