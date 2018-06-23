---
title: Behandeln von SMO-Ausnahmen | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 329cc87a9a82545708f71202f15de4eb219463e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149029"
---
# <a name="handling-smo-exceptions"></a>Behandeln von SMO-Ausnahmen
  In verwaltetem Code werden Ausnahmen ausgelöst, wenn ein Fehler auftritt. SMO-Methoden und -Eigenschaften melden keinen Erfolg oder Fehler mit dem Rückgabewert. Stattdessen können Ausnahmen von einem Ausnahmehandler abgefangen und behandelt werden.  
  
 In SMO sind verschiedene Ausnahmeklassen vorhanden. Informationen über die Ausnahme können aus den Ausnahmeeigenschaften wie der `Message`-Eigenschaft, die eine Textmeldung über die Ausnahme angibt, extrahiert werden.  
  
 Die Ausnahmebehandlungsanweisungen sind für die Programmiersprache spezifisch. In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic gibt es hierfür beispielsweise die `Catch`-Anweisung.  
  
## <a name="inner-exceptions"></a>Interne Ausnahmen  
 Ausnahmen können entweder allgemein oder spezifisch sein. Allgemeine Ausnahmen enthalten einen Satz spezifischer Ausnahmen. Mehrere `Catch` erwartete Fehler zu behandeln, und lassen die übrigen Fehler an den allgemeinen Ausnahmebehandlungscode können Anweisungen verwendet werden. Ausnahmen treten oft in einer überlappenden Sequenz auf. Häufig wird eine SMO-Ausnahme von einer SQL-Ausnahme verursacht. Die Möglichkeit, dies zu ermitteln ist die Verwendung der `InnerException` -Eigenschaft nacheinander auf die ursprüngliche Ausnahme zu bestimmen, die die letzte Ausnahme auf oberster Ebene verursacht hat.  
  
> [!NOTE]  
>  Die `SQLException` Ausnahme wird deklariert, der **System.Data.SqlClient** Namespace.  
  
 ![Ein Diagramm, das zeigt, die Ebenen aus dem ausnahmeflussebenen](../../../database-engine/dev-guide/media/exception-flow.gif "ein Diagramm, das zeigt, die Ebenen aus dem ausnahmeflussebenen")  
  
 Die Abbildung zeigt den Verlauf der Ausnahmen durch die Anwendungsebenen.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md).  
  
## <a name="catching-an-exception-in-visual-basic"></a>Abfangen einer Ausnahme in Visual Basic  
 Dieses Codebeispiel zeigt, wie Sie die `Try…Catch…Finally` [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] Anweisung um eine SMO-Ausnahme abzufangen. Alle SMO-Ausnahmen haben den Typ SmoException und werden im SMO-Verweis aufgelistet. Die Sequenz von internen Ausnahmen wird angezeigt, um den Ursprung des Fehlers anzugeben. Weitere Informationen finden Sie unter der [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET-Dokumentation.  
  
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
  
  