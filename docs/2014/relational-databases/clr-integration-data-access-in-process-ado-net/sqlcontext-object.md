---
title: SqlContext-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 223111874ca34ba4df4968c550e6cc47edf2b390
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920046"
---
# <a name="sqlcontext-object"></a>SqlContext-Objekt
  Sie rufen verwalteten Code auf dem Server auf, wenn Sie eine Prozedur oder Funktion aufrufen, eine Methode für einen benutzerdefinierten CLR (Common Language Runtime)-Typ aufrufen oder wenn Ihre Aktion einen in einer beliebigen [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Sprache definierten Trigger auslöst. Da die Ausführung dieses Codes im Rahmen einer Benutzerverbindung erforderlich ist, wird ein Zugriff auf den Kontext des aufrufenden Codes vonseiten des auf dem Server ausgeführten Code benötigt. Zusätzlich dazu sind bestimmte Datenzugriffsvorgänge unter Umständen nur gültig, wenn sie im Kontext des aufrufenden Programms ausgeführt werden. Beispielsweise ist der Zugriff auf in Triggervorgängen verwendete eingefügte und gelöschte Pseudotabellen nur im Kontext des aufrufenden Codes gültig.  
  
 Der Kontext des aufrufenden Codes wird in einem `SqlContext`-Objekt abstrahiert. Weitere Informationen zu `SqlTriggerContext`-Methoden und -Eigenschaften finden Sie in der Referenzdokumentation zur `Microsoft.SqlServer.Server.SqlTriggerContext`-Klasse im [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-SDK.  
  
 `SqlContext` stellt den Zugriff auf folgende Komponenten bereit:  
  
-   `SqlPipe`: Die `SqlPipe` -Objekt stellt die "Pipe" dar, über die Ergebnisse an den Client erreichen. Weitere Informationen zu den `SqlPipe` Objekt, finden Sie unter [SqlPipe-Objekt](sqlpipe-object.md).  
  
-   `SqlTriggerContext`: Die `SqlTriggerContext` Objekt kann nur von innerhalb eines CLR-Triggers abgerufen werden. Es stellt Informationen über den Vorgang bereit, durch den der Trigger ausgelöst wurde, sowie eine Übersicht der aktualisierten Spalten. Weitere Informationen zu den `SqlTriggerContext` Objekt, finden Sie unter [SqlTriggerContext-Objekt](sqltriggercontext-object.md).  
  
-   `IsAvailable`: Die `IsAvailable` Eigenschaft wird verwendet, um die Verfügbarkeit des Kontexts zu ermitteln.  
  
-   `WindowsIdentity`: Die `WindowsIdentity` Eigenschaft wird verwendet, um die Windows-Identität des Aufrufers abrufen.  
  
## <a name="determining-context-availability"></a>Bestimmen der Kontextverfügbarkeit  
 Fragen Sie die `SqlContext`-Klasse ab, um zu ermitteln, ob der gerade ausgeführte Code prozessintern ausgeführt wird. Überprüfen Sie dazu die `IsAvailable`-Eigenschaft des `SqlContext`-Objekts. Die `IsAvailable`-Eigenschaft ist schreibgeschützt und gibt `True` zurück, wenn der aufrufende Code innerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird und auf andere `SqlContext`-Elemente zugegriffen werden kann. Wenn die `IsAvailable`-Eigenschaft `False` zurückgibt, lösen alle anderen `SqlContext`-Elemente eine `InvalidOperationException`-Ausnahme aus, falls sie verwendet werden. Wenn `IsAvailable` `False` zurückgibt, schlagen alle Versuche, ein Verbindungsobjekt zu öffnen, bei denen "context connection=true" festgelegt ist, fehl.  
  
## <a name="retrieving-windows-identity"></a>Abrufen der Windows-Identität  
 Innerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführter CLR-Code wird immer im Kontext des Prozesskontos aufgerufen. Wenn der Code bestimmte Aktionen mit der Identität des aufrufenden Benutzers anstelle der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozessidentität ausführen soll, sollte mithilfe der `WindowsIdentity`-Eigenschaft des `SqlContext`-Objekts ein Identitätstoken abgerufen werden. Die `WindowsIdentity`-Eigenschaft gibt eine `WindowsIdentity`-Instanz zurück, die die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Identität des aufrufenden Benutzers darstellt, bzw. NULL, wenn der Client über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung identifiziert wurde. Nur mit der `EXTERNAL_ACCESS`-Berechtigung oder `UNSAFE`-Berechtigung markierte Assemblys können auf diese Eigenschaft zugreifen.  
  
 Nach dem Erhalt des `WindowsIdentity`-Objekts können aufrufende Benutzer einen Identitätswechsel für das Clientkonto durchführen und Aktionen mit der neuen Identität ausführen.  
  
 Die Identität des aufrufenden Benutzers ist nur über `SqlContext.WindowsIdentity` verfügbar, wenn der Client, der die Ausführung der gespeicherten Prozedur oder der Funktion initiiert hat, mithilfe der Windows-Authentifizierung eine Verbindung mit dem Server hergestellt hat. Wenn stattdessen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet wurde, ist diese Eigenschaft NULL, und der Code kann die Identität des aufrufenden Benutzers nicht feststellen.  
  
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
  
  
