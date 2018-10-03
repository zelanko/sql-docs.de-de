---
title: Behandeln von SMO-Ausnahmen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3321cde44bbdecc2b7f3ad715db1e6483fa06c8c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180590"
---
# <a name="handling-smo-exceptions"></a>Behandeln von SMO-Ausnahmen
  In verwaltetem Code werden Ausnahmen ausgelöst, wenn ein Fehler auftritt. SMO-Methoden und -Eigenschaften melden keinen Erfolg oder Fehler mit dem Rückgabewert. Stattdessen können Ausnahmen von einem Ausnahmehandler abgefangen und behandelt werden.  
  
 In SMO sind verschiedene Ausnahmeklassen vorhanden. Informationen über die Ausnahme können aus den Ausnahmeeigenschaften wie der `Message`-Eigenschaft, die eine Textmeldung über die Ausnahme angibt, extrahiert werden.  
  
 Die Ausnahmebehandlungsanweisungen sind für die Programmiersprache spezifisch. In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic gibt es hierfür beispielsweise die `Catch`-Anweisung.  
  
## <a name="inner-exceptions"></a>Interne Ausnahmen  
 Ausnahmen können entweder allgemein oder spezifisch sein. Allgemeine Ausnahmen enthalten einen Satz spezifischer Ausnahmen. Mehrere `Catch` -Anweisungen können verwendet werden, erwartete Fehler zu behandeln, und lassen Sie die übrigen Fehler an den allgemeinen Ausnahmebehandlungscode. Ausnahmen treten oft in einer überlappenden Sequenz auf. Häufig wird eine SMO-Ausnahme von einer SQL-Ausnahme verursacht. Um dies zu ermitteln ist die Verwendung der `InnerException` -Eigenschaft nacheinander auf die ursprüngliche Ausnahme zu ermitteln, die die letzte Ausnahme auf oberster Ebene ausgelöst hat.  
  
> [!NOTE]  
>  Die `SQLException` Ausnahme deklariert ist, der **"System.Data.SqlClient"** Namespace.  
  
 ![Ein Diagramm, das zeigt, die Ebenen aus dem ausnahmeflussebenen](../../../database-engine/dev-guide/media/exception-flow.gif "ein Diagramm, das zeigt, die Ebenen aus dem ausnahmeflussebenen")  
  
 Die Abbildung zeigt den Verlauf der Ausnahmen durch die Anwendungsebenen.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md) oder [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md).  
  
## <a name="catching-an-exception-in-visual-basic"></a>Abfangen einer Ausnahme in Visual Basic  
 Dieses Codebeispiel zeigt, wie Sie mit der `Try…Catch…Finally` [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] Anweisung um eine SMO-Ausnahme abzufangen. Alle SMO-Ausnahmen haben den Typ SmoException und werden im SMO-Verweis aufgelistet. Die Sequenz von internen Ausnahmen wird angezeigt, um den Ursprung des Fehlers anzugeben. Weitere Informationen finden Sie unter den [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] Dokumentation zu .NET.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBExceptions1](SMO How to#SMO_VBExceptions1)]  -->  
  
## <a name="catching-an-exception-in-visual-c"></a>Abfangen einer Ausnahme in Visual C#  
 In diesem Codebeispiel wird gezeigt, wie die Visual C#-Anweisung `Try…Catch…Finally` verwendet wird, um eine SMO-Ausnahme abzufangen. Alle SMO-Ausnahmen haben den Typ SmoException und werden im SMO-Verweis aufgelistet. Die Sequenz von internen Ausnahmen wird angezeigt, um den Ursprung des Fehlers anzugeben. Weitere Informationen finden Sie in der Dokumentation zu Visual C#.  
  
```  
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
  
  
