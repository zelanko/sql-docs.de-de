---
title: SqlContext-Objekt | Microsoft-Dokumentation
description: Wenn Sie verwalteten Code in SQL Server in einer Benutzer Verbindung aufrufen, wird der Zugriff auf den Kontext des Aufrufers in einem SqlContext-Objekt abstrahiert.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: c423b4d2b6296da5ce95e62bfc51a160beb956a5
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810723"
---
# <a name="sqlcontext-object"></a>SqlContext-Objekt
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Sie rufen verwalteten Code auf dem Server auf, wenn Sie eine Prozedur oder Funktion aufrufen, eine Methode für einen benutzerdefinierten CLR (Common Language Runtime)-Typ aufrufen oder wenn Ihre Aktion einen in einer beliebigen [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Sprache definierten Trigger auslöst. Da die Ausführung dieses Codes im Rahmen einer Benutzerverbindung erforderlich ist, wird ein Zugriff auf den Kontext des aufrufenden Codes vonseiten des auf dem Server ausgeführten Code benötigt. Zusätzlich dazu sind bestimmte Datenzugriffsvorgänge unter Umständen nur gültig, wenn sie im Kontext des aufrufenden Programms ausgeführt werden. Beispielsweise ist der Zugriff auf in Triggervorgängen verwendete eingefügte und gelöschte Pseudotabellen nur im Kontext des aufrufenden Codes gültig.  
  
 Der Kontext des aufrufenden Codes wird in einem **SqlContext** -Objekt abstrahiert. Weitere Informationen zu **SqlTriggerContext** -Methoden und -Eigenschaften finden Sie in der Referenzdokumentation zur **Microsoft.SqlServer.Server.SqlTriggerContext** -Klasse im [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -SDK.  
  
 **SqlContext** stellt den Zugriff auf folgende Komponenten bereit:  
  
-   **SqlPipe**: Das **SqlPipe** -Objekt stellt die "Pipe" dar, d. h. den Kanal, durch den die Ergebnisse den Client erreichen. Weitere Informationen zum **SqlPipe** -Objekt finden Sie unter [SqlPipe-Objekt](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md).  
  
-   **SqlTriggerContext**: Das **SqlTriggerContext** -Objekt kann nur innerhalb eines CLR-Triggers abgerufen werden. Es stellt Informationen über den Vorgang bereit, durch den der Trigger ausgelöst wurde, sowie eine Übersicht der aktualisierten Spalten. Weitere Informationen zum **SqlTriggerContext** -Objekt finden Sie unter [SqlTriggerContext-Objekt](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md).  
  
-   **IsAvailable**: Die **IsAvailable** -Eigenschaft wird verwendet, um die Verfügbarkeit des Kontexts zu ermitteln.  
  
-   **WindowsIdentity**: Die **WindowsIdentity** -Eigenschaft wird verwendet, um die Windows-Identität des aufrufenden Programms abzurufen.  
  
## <a name="determining-context-availability"></a>Bestimmen der Kontextverfügbarkeit  
 Fragen Sie die **SqlContext** -Klasse ab, um zu ermitteln, ob der gerade ausgeführte Code prozessintern ausgeführt wird. Überprüfen Sie dazu die **IsAvailable** -Eigenschaft des **SqlContext** -Objekts. Die **IsAvailable** -Eigenschaft ist schreibgeschützt und gibt **True** zurück, wenn der aufrufende Code innerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird und auf andere **SqlContext** -Elemente zugegriffen werden kann. Wenn die **IsAvailable** -Eigenschaft **False**zurückgibt, lösen alle anderen **SqlContext** -Elemente eine **InvalidOperationException**-Ausnahme aus, falls sie verwendet werden. Wenn **IsAvailable****False**zurückgibt, schlagen alle Versuche, ein Verbindungsobjekt zu öffnen, bei denen "context connection=true" festgelegt ist, fehl.  
  
## <a name="retrieving-windows-identity"></a>Abrufen der Windows-Identität  
 Innerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführter CLR-Code wird immer im Kontext des Prozesskontos aufgerufen. Wenn der Code bestimmte Aktionen mit der Identität des aufrufenden Benutzers anstelle der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozessidentität ausführen soll, sollte mithilfe der **WindowsIdentity** -Eigenschaft des **SqlContext** -Objekt abstrahiert. Die **WindowsIdentity** -Eigenschaft gibt eine **WindowsIdentity** -Instanz zurück, die die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Identität des aufrufenden Benutzers darstellt, bzw. NULL, wenn der Client über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung identifiziert wurde. Nur mit der **EXTERNAL_ACCESS** -Berechtigung oder **UNSAFE** -Berechtigung markierte Assemblys können auf diese Eigenschaft zugreifen.  
  
 Nach dem Erhalt des **WindowsIdentity** -Objekts können aufrufende Benutzer einen Identitätswechsel für das Clientkonto durchführen und Aktionen mit der neuen Identität ausführen.  
  
 Die Identität des aufrufenden Benutzers ist nur über **SqlContext.WindowsIdentity** verfügbar, wenn der Client, der die Ausführung der gespeicherten Prozedur oder der Funktion initiiert hat, mithilfe der Windows-Authentifizierung eine Verbindung mit dem Server hergestellt hat. Wenn stattdessen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet wurde, ist diese Eigenschaft NULL, und der Code kann die Identität des aufrufenden Benutzers nicht feststellen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [SqlPipe-Objekt](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)   
 [SqlTriggerContext-Objekt](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)   
 [CLR-Trigger](/dotnet/framework/data/adonet/sql/clr-triggers)   
 [Von SQL Server verwendete prozessinterne spezifische Erweiterungen für ADO.NET](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
