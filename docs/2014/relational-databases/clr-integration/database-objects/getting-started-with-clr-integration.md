---
title: Erste Schritte mit CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration]
- namespaces [CLR integration]
- database objects [CLR integration], about CLR integration
- stored procedures [CLR integration]
- common language runtime [SQL Server], about CLR integration
- building database objects [CLR integration], about CLR integration
- common language runtime [SQL Server], stored procedures
- common language runtime [SQL Server], namespaces
- Hello World example [CLR integration]
- library [CLR integration]
ms.assetid: c73e628a-f54a-411a-bfe3-6dae519316cc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: db3a72facf1676360e7c338663facac66840a113
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089150"
---
# <a name="getting-started-with-clr-integration"></a>Erste Schritte mit der CLR-Integration
  Dieses Thema enthält eine Übersicht über die erforderlichen Namespaces und Bibliotheken zum Kompilieren von Datenbankobjekten mit dem die [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] Integration in die .NET Framework common Language Runtime (CLR). In diesem Thema wird außerdem erläutert, wie eine einfache gespeicherte CLR-Prozedur in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# geschrieben, kompiliert und ausgeführt wird.  
  
## <a name="required-namespaces"></a>Erforderliche Namespaces  
 Beginnend mit [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)]. Die CLR-Integrationsfunktionalität wird in einer Assembly mit dem Namen system.data.dll verfügbar gemacht, die Teil von .NET Framework ist. Diese Assembly befindet sich im globalen Assemblycache (GAC) sowie im .NET Framework-Verzeichnis. Ein Verweis auf diese Assembly wird in der Regel sowohl von Befehlszeilentools als auch von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio automatisch hinzugefügt und muss daher nicht manuell hinzugefügt werden.  
  
 Die system.data.dll-Assembly enthält die folgenden Namespaces, die zum Kompilieren von CLR-Datenbankobjekten erforderlich sind:  
  
 `System.Data`  
  
 `System.Data.Sql`  
  
 `Microsoft.SqlServer.Server`  
  
 `System.Data.SqlTypes`  
  
## <a name="writing-a-simple-hello-world-stored-procedure"></a>Schreiben der einfachen gespeicherten Prozedur "Hello World"  
 Kopieren Sie den folgenden Visual C#- oder [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic-Code, fügen Sie ihn in einen Texteditor ein, und speichern Sie ihn in einer Datei mit dem Namen "helloworld.cs" oder "helloworld.vb".  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
  
public class HelloWorldProc  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld(out string text)  
    {  
        SqlContext.Pipe.Send("Hello world!" + Environment.NewLine);  
        text = "Hello world!";  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.Runtime.InteropServices  
  
Public Class HelloWorldProc  
    <Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
 Dieses einfache Programm enthält eine einzelne statische Methode in einer öffentlichen Klasse. Diese Methode enthält die beiden neuen Klassen `SqlContext` und `SqlPipe` zum Erstellen von verwalteten Datenbankobjekten für die Ausgabe einer einfachen Textnachricht. Zudem weist die Methode die Zeichenfolge "Hello World!" als Wert für einen Out-Parameter. Diese Methode kann deklariert werden, wie eine gespeicherte Prozedur in [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] gespeicherte Prozedur.  
  
 Dieses Programm wird im Folgenden als Bibliothek kompiliert, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] geladen und als gespeicherte Prozedur ausgeführt.  
  
## <a name="compiling-the-hello-world-stored-procedure"></a>Kompilieren der gespeicherten Prozedur "Hello World"  
 [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] .NET Framework-neuverteilungsdateien standardmäßig. Zu diesen Dateien zählen die Dateien csc.exe und vbc.exe, die Befehlszeilencompiler für Visual C# sowie Visual Basic-Programme. Zum Kompilieren des Beispiels müssen Sie die Pfadvariable so ändern, dass sie auf das Verzeichnis mit der Datei csc.exe oder mit der Datei vbc.exe zeigt. Der Standardinstallationspfad von .NET Framework lautet wie folgt:  
  
```  
C:\Windows\Microsoft.NET\Framework\(version)  
```  
  
 Diese Version enthält die Versionsnummer der installierten Redistributionsdatei von .NET Framework. Zum Beispiel:  
  
```  
C:\Windows\Microsoft.NET\Framework\v2.0.31113  
```  
  
 Nach dem Hinzufügen des .NET Framework-Verzeichnises zum Pfad können Sie die gespeicherte Prozedur in diesem Beispiel mit dem folgenden Befehl in eine Assembly kompilieren. Mit der `/target`-Option können Sie sie in eine Assembly kompilieren.  
  
 Für Visual C#-Quelldateien gilt:  
  
```  
csc /target:library helloworld.cs   
```  
  
 Für Visual Basic-Quelldateien gilt:  
  
```  
vbc /target:library helloworld.vb  
```  
  
 Mit diesen Befehlen wird der Visual C# - bzw. Visual Basic-Compiler unter Angabe der /target-Option aufgerufen, die festlegt, dass eine Bibliotheks-DLL erstellt werden soll.  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a>Laden und Ausführen der gespeicherten Prozedur "Hello World" in SQL Server  
 Sobald die Beispielprozedur erfolgreich kompiliert wurde, können Sie testen in [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] , und erstellen Sie eine neue Abfrage zum Herstellen einer Verbindung mit einer geeigneten Testdatenbank (z. B. der AdventureWorks-Beispieldatenbank).  
  
 Die Funktion zum Ausführen von CLR-Code (Common Language Runtime) ist in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] standardmäßig deaktiviert. Der CLR-Code kann aktiviert werden, mithilfe der **Sp_configure** gespeicherten Systemprozedur. Weitere Informationen finden Sie unter [Enabling CLR Integration](../clr-integration-enabling.md).  
  
 Sie müssen die Assembly erstellen, um auf die gespeicherte Prozedur zugreifen zu können. Für dieses Beispiel wird vorausgesetzt, dass Sie die helloworld.dll-Assembly im Verzeichnis C:\ erstellt haben. Fügen Sie die folgende [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung zur Abfrage hinzu:  
  
```  
CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE  
```  
  
 Nach dem Erstellen der Assembly können Sie mithilfe der CREATE PROCEDURE-Anweisung auf die HelloWorld-Methode zugreifen. Die gespeicherte Prozedur wird "hello" genannt:  
  
```  
  
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
 Nach dem Erstellen der Prozedur kann diese wie eine normale, in [!INCLUDE[tsql](../../../includes/tsql-md.md)] geschriebene gespeicherte Prozedur ausgeführt werden. Führen Sie den folgenden Befehl ein:  
  
```  
DECLARE @J nchar(25)  
EXEC hello @J out  
PRINT @J  
```  
  
 Daraufhin sollte im Meldungsfenster von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] folgende Ausgabe angezeigt werden.  
  
```  
Hello world!  
Hello world!  
```  
  
## <a name="removing-the-hello-world-stored-procedure-sample"></a>Entfernen des Beispiels der gespeicherten Prozedur "Hello World"  
 Wenn Sie die gespeicherte Beispielprozedur ausgeführt haben, können Sie die Prozedur und die Assembly aus der Testdatenbank entfernen.  
  
 Entfernen Sie zuerst die Prozedur. Verwenden Sie hierzu den drop procedure-Befehl.  
  
```  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
 Nach dem Löschen der Prozedur können Sie die Assembly entfernen, die den Beispielcode enthält.  
  
```  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-gespeicherte Prozeduren](../../../database-engine/dev-guide/clr-stored-procedures.md)   
 [SQL Server In-Process-spezifische Erweiterungen für ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)   
 [Debuggen von CLR-Datenbankobjekten](../debugging-clr-database-objects.md)   
 [Sicherheit der CLR-Integration](../security/clr-integration-security.md)  
  
  
