---
title: SqlContext-Objekt | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
caps.latest.revision: 54
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ea7cd3ca105fd599f3b157f64189210b539de4ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149906"
---
# <a name="sqlcontext-object"></a>SqlContext-Objekt
  Beim Aufrufen einer Prozedur oder Funktion, wenn Sie eine Methode in einer common Language Runtime (CLR) den benutzerdefinierten Typ aufrufen, oder wenn Ihre Aktion einen in einer der definierten Trigger auslöst, rufen Sie verwalteten Code auf dem Server die [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Sprachen. Da die Ausführung dieses Codes im Rahmen einer Benutzerverbindung erforderlich ist, wird ein Zugriff auf den Kontext des aufrufenden Codes vonseiten des auf dem Server ausgeführten Code benötigt. Zusätzlich dazu sind bestimmte Datenzugriffsvorgänge unter Umständen nur gültig, wenn sie im Kontext des aufrufenden Programms ausgeführt werden. Beispielsweise ist der Zugriff auf in Triggervorgängen verwendete eingefügte und gelöschte Pseudotabellen nur im Kontext des aufrufenden Codes gültig.  
  
 Der Kontext des aufrufenden Codes wird in einem `SqlContext`-Objekt abstrahiert. Weitere Informationen zu `SqlTriggerContext`-Methoden und -Eigenschaften finden Sie in der Referenzdokumentation zur `Microsoft.SqlServer.Server.SqlTriggerContext`-Klasse im [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-SDK.  
  
 `SqlContext` stellt den Zugriff auf folgende Komponenten bereit:  
  
-   `SqlPipe`: Das `SqlPipe`-Objekt stellt die "Pipe" dar, d. h. den Kanal, durch den die Ergebnisse den Client erreichen. Weitere Informationen zu den `SqlPipe` Objekt, finden Sie unter [SqlPipe-Objekt](sqlpipe-object.md).  
  
-   `SqlTriggerContext`: Der `SqlTriggerContext` Objekt kann nur von innerhalb einer CLR-Triggers abgerufen werden. Es stellt Informationen über den Vorgang bereit, durch den der Trigger ausgelöst wurde, sowie eine Übersicht der aktualisierten Spalten. Weitere Informationen zu den `SqlTriggerContext` Objekt, finden Sie unter [SqlTriggerContext-Objekt](sqltriggercontext-object.md).  
  
-   `IsAvailable`: Der `IsAvailable` Eigenschaft wird verwendet, um die Verfügbarkeit des Kontexts zu ermitteln.  
  
-   `WindowsIdentity`: Die `WindowsIdentity`-Eigenschaft wird verwendet, um die Windows-Identität des aufrufenden Programms abzurufen.  
  
## <a name="determining-context-availability"></a>Bestimmen der Kontextverfügbarkeit  
 Abfrage der `SqlContext` Klasse, um festzustellen, ob der gerade ausgeführte Code prozessintern ausgeführt wird. Überprüfen Sie hierzu die `IsAvailable` Eigenschaft von der `SqlContext` Objekt. Die `IsAvailable`-Eigenschaft ist schreibgeschützt und gibt `True` zurück, wenn der aufrufende Code innerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird und auf andere `SqlContext`-Elemente zugegriffen werden kann. Wenn die `IsAvailable`-Eigenschaft `False` zurückgibt, lösen alle anderen `SqlContext`-Elemente eine `InvalidOperationException`-Ausnahme aus, falls sie verwendet werden. Wenn `IsAvailable` `False` zurückgibt, schlagen alle Versuche, ein Verbindungsobjekt zu öffnen, bei denen "context connection=true" festgelegt ist, fehl.  
  
## <a name="retrieving-windows-identity"></a>Abrufen der Windows-Identität  
 CLR-codeausführung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird immer im Kontext des Prozesskontos aufgerufen. Wenn der Code bestimmte Aktionen mit der Identität des aufrufenden Benutzers anstelle von ausführen sollten die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Identitätstoken abgerufen werden sollen, über-Prozessidentität der `WindowsIdentity` Eigenschaft der `SqlContext` Objekt. Die `WindowsIdentity`-Eigenschaft gibt eine `WindowsIdentity`-Instanz zurück, die die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Identität des aufrufenden Benutzers darstellt, bzw. NULL, wenn der Client über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung identifiziert wurde. Nur mit der `EXTERNAL_ACCESS`-Berechtigung oder `UNSAFE`-Berechtigung markierte Assemblys können auf diese Eigenschaft zugreifen.  
  
 Nach dem Erhalt der `WindowsIdentity` -Objekt Aufrufer das Clientkonto imitieren und in deren Namen Aktionen ausführen können.  
  
 Die Identität des aufrufenden Benutzers ist nur über `SqlContext.WindowsIdentity` verfügbar, wenn der Client, der die Ausführung der gespeicherten Prozedur oder der Funktion initiiert hat, mithilfe der Windows-Authentifizierung eine Verbindung mit dem Server hergestellt hat. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung stattdessen verwendet wurde, diese Eigenschaft ist null, und der Code des Aufrufers annehmen kann.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Abrufen der Windows-Identität des aufrufenden Clients und der Identitätswechsel des Clients veranschaulicht.  
  
 C#  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void WindowsIDTestProc()  
{  
    WindowsIdentity clientId = null;  
    WindowsImpersonationContext impersonatedUser = null;  
  
    // Get the client ID.  
    clientId = SqlContext.WindowsIdentity;  
  
    // This outer try block is used to thwart exception filter   
    // attacks which would prevent the inner finally   
    // block from executing and resetting the impersonation.  
    try  
    {  
        try  
        {  
            impersonatedUser = clientId.Impersonate();  
            if (impersonatedUser != null)  
            {  
                // Perform some action using impersonation.  
            }  
        }  
        finally  
        {  
            // Undo impersonation.  
            if (impersonatedUser != null)  
                impersonatedUser.Undo();  
        }  
    }  
    catch  
    {  
        throw;  
    }  
}  
```  
  
 Visual Basic  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  WindowsIDTestProcVB ()  
    Dim clientId As WindowsIdentity  
    Dim impersonatedUser As WindowsImpersonationContext  
  
    ' Get the client ID.  
    clientId = SqlContext.WindowsIdentity  
  
    ' This outer try block is used to thwart exception filter   
    ' attacks which would prevent the inner finally   
    ' block from executing and resetting the impersonation.  
  
    Try  
        Try  
  
            impersonatedUser = clientId.Impersonate()  
  
            If impersonatedUser IsNot Nothing Then  
                ' Perform some action using impersonation.  
            End If  
  
        Finally  
            ' Undo impersonation.  
            If impersonatedUser IsNot Nothing Then  
                impersonatedUser.Undo()  
            End If  
        End Try  
  
    Catch e As Exception  
  
        Throw e  
  
    End Try  
End Sub  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SqlPipe-Objekt](sqlpipe-object.md)   
 [SqlTriggerContext-Objekt](sqltriggercontext-object.md)   
 [CLR-Trigger](../../database-engine/dev-guide/clr-triggers.md)   
 [Von SQL Server verwendete prozessinterne spezifische Erweiterungen für ADO.NET](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  