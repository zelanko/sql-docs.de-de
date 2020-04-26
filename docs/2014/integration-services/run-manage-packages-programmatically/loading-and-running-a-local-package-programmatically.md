---
title: Programmgesteuertes Laden und Ausführen eines lokalen Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Integration Services packages, running
- events [Integration Services], capturing
- packages [Integration Services], running
- loading packages programmatically
- Visual Basic [Integration Services]
- running packages [Integration Services]
- programmatically load and run packages [SSIS]
ms.assetid: 2f9fc1a8-a001-4c54-8c64-63b443725422
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 00d213bf8ca554b60edc8dc3de3f1290cd00f538
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62766892"
---
# <a name="loading-and-running-a-local-package-programmatically"></a>Programmgesteuertes Laden und Ausführen eines lokalen Pakets
  Sie können [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete mit einer der unter [Ausführen von Paketen](../packages/run-integration-services-ssis-packages.md) beschriebenen Methoden bei Bedarf oder zu vorbestimmten Zeiten ausführen. Mit nur wenigen Codezeilen können Sie ein Paket jedoch auch mit einer benutzerdefinierten Anwendung wie einer Windows Forms-Anwendung, einer Konsolenanwendung, einem Webformular oder Webdienst von ASP.NET oder einem Windows-Dienst ausführen.  
  
 In diesem Thema wird Folgendes erläutert:  
  
-   Programmgesteuertes Laden eines Pakets  
  
-   Programmgesteuertes Ausführen eines Pakets  
  
 Alle in diesem Thema erläuterten Methoden zum Laden und Ausführen von Paketen erfordern einen Verweis auf die `Microsoft.SqlServer.ManagedDTS`-Assembly. Nachdem Sie den Verweis in einem neuen Projekt hinzugefügt haben, importieren Sie den <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace mit einer `using`-Anweisung oder einer `Imports`-Anweisung.  
  
## <a name="loading-a-package-programmatically"></a>Programmgesteuertes Laden eines Pakets  
 Rufen Sie unabhängig davon, ob ein Paket lokal oder remote gespeichert ist, zum programmgesteuerten Laden des Pakets auf dem lokalen Computer eine der folgenden Methoden auf:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|Datei|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A>|  
  
> [!IMPORTANT]  
>  Die Methoden der <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse zum Arbeiten mit dem SSIS-Paketspeicher unterstützen nur ".", localhost oder den Namen des lokalen Servers. Sie können "(local)" nicht verwenden.  
  
## <a name="running-a-package-programmatically"></a>Programmgesteuertes Ausführen eines Pakets  
 Das Entwickeln einer benutzerdefinierten Anwendung in verwaltetem Code zum Ausführen eines Pakets auf dem lokalen Computer erfordert den folgenden Ansatz. Die hier zusammengefassten Schritte werden in dem folgenden Beispiel einer Konsolenanwendung veranschaulicht.  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically"></a>So führen Sie ein Paket auf dem lokalen Computer programmgesteuert aus  
  
1.  Starten Sie die Visual Studio-Entwicklungsumgebung, und erstellen Sie eine neue Anwendung in der gewünschten Entwicklungssprache. In diesem Beispiel wird eine Konsolenanwendung verwendet. Sie können ein Paket jedoch auch mit einer Windows Forms-Anwendung, einem Webformular oder Webdienst von ASP.NET oder einem Windows-Dienst ausführen.  
  
2.  Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**, und fügen Sie einen Verweis auf **Microsoft.SqlServer.ManagedDTS.dll** hinzu. Klicken Sie auf **OK**.  
  
3.  Verwenden Sie die `Imports` Visual Basic-Anweisung oder die `using` c#-Anweisung, um den **Microsoft. SqlServer. DTS. Runtime** -Namespace zu importieren.  
  
4.  Fügen Sie den folgenden Code in der Hauptroutine hinzu. Die abgeschlossene Konsolenanwendung sollte wie im folgenden Beispiel dargestellt aussehen.  
  
    > [!NOTE]  
    >  Im Beispielcode wird das Laden des Pakets aus dem Dateisystem mithilfe der <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>-Methode veranschaulicht. Sie können das Paket jedoch auch aus der MSDB-Datenbank durch Aufrufen der <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A>-Methode oder aus dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketspeicher durch Aufrufen der <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>-Methode laden.  
  
5.  Führen Sie das Projekt aus. Der Beispielcode führt das CalculatedColumns-Beispielpaket aus, das mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Beispielen installiert wird. Das Ergebnis der Paketausführung wird im Konsolenfenster angezeigt.  
  
### <a name="sample-code"></a>Beispielcode  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, Nothing)  
    pkgResults = pkg.Execute()  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, null);  
      pkgResults = pkg.Execute();  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="capturing-events-from-a-running-package"></a>Aufzeichnen von Ereignissen aus einem ausgeführten Paket  
 Wenn ein Paket wie im vorigen Beispiel dargestellt programmgesteuert ausgeführt wird, sollten auch Fehler und andere Ereignisse aufgezeichnet werden, die bei der Ausführung des Pakets auftreten. Sie können dies erreichen, indem Sie eine Klasse hinzufügen, die von der <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents>-Klasse erbt, und beim Laden des Pakets einen Verweis auf diese Klasse übergeben. Auch wenn im folgenden Beispiel nur die <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A>-Ereignisse aufgezeichnet werden, gibt es noch viele weitere Ereignisse, die mithilfe der <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents>-Klasse aufgezeichnet werden können.  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically-and-capture-package-events"></a>So führen Sie ein Paket auf dem lokalen Computer programmgesteuert aus und zeichnen Paketereignisse auf  
  
1.  Führen Sie die Schritte im vorangehenden Beispiel aus, um ein Projekt für dieses Beispiel zu erstellen.  
  
2.  Fügen Sie den folgenden Code in der Hauptroutine hinzu. Die abgeschlossene Konsolenanwendung sollte wie im folgenden Beispiel dargestellt aussehen.  
  
3.  Führen Sie das Projekt aus. Der Beispielcode führt das CalculatedColumns-Beispielpaket aus, das mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Beispielen installiert wird. Das Ergebnis der Paketausführung wird zusammen mit den aufgetretenen Fehlern im Konsolenfenster angezeigt.  
  
### <a name="sample-code"></a>Beispielcode  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    Dim eventListener As New EventListener()  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, eventListener)  
    pkgResults = pkg.Execute(Nothing, Nothing, eventListener, Nothing, Nothing)  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
  
Class EventListener  
  Inherits DefaultEvents  
  
  Public Overrides Function OnError(ByVal source As Microsoft.SqlServer.Dts.Runtime.DtsObject, _  
    ByVal errorCode As Integer, ByVal subComponent As String, ByVal description As String, _  
    ByVal helpFile As String, ByVal helpContext As Integer, _  
    ByVal idofInterfaceWithError As String) As Boolean  
  
    ' Add application-specific diagnostics here.  
    Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description)  
    Return False  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppWithEventsCS  
{  
  class MyEventListener : DefaultEvents  
  {  
    public override bool OnError(DtsObject source, int errorCode, string subComponent,   
      string description, string helpFile, int helpContext, string idofInterfaceWithError)  
    {  
      // Add application-specific diagnostics here.  
      Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description);  
      return false;  
    }  
  }  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      MyEventListener eventListener = new MyEventListener();  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, eventListener);  
      pkgResults = pkg.Execute(null, null, eventListener, null, null);  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zu den Unterschieden zwischen der lokalen und der Remote Ausführung](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [Programm gesteuertes laden und Ausführen eines Remote Pakets](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [Laden der Ausgabe eines lokalen Pakets](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
