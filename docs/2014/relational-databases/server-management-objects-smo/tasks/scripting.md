---
title: Skripterstellung | Microsoft-Dokumentation
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
- dependencies [SMO]
- scripts [SMO]
ms.assetid: 13a35511-3987-426b-a3b7-3b2e83900dc7
caps.latest.revision: 42
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 375a8f90c4864c8f1f3db12c56db1bf0eda3b0a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37262276"
---
# <a name="scripting"></a>Skripterstellung
  Die Skripterstellung in SMO wird durch das <xref:Microsoft.SqlServer.Management.Smo.Scripter>-Objekt und dessen untergeordnete Objekte oder durch die `Script`-Methode für einzelne Objekte gesteuert. Die <xref:Microsoft.SqlServer.Management.Smo.Scripter> Objekt steuert die Ermittlung von abhängigkeitsbeziehungen für Objekte in einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Die erweiterte Skripterstellung mithilfe des <xref:Microsoft.SqlServer.Management.Smo.Scripter>-Objekts und dessen untergeordneten Objekten ist ein Prozess, der aus drei Phasen besteht:  
  
1.  Ermittlung  
  
2.  Listengenerierung  
  
3.  Skriptgenerierung  
  
 Die Ermittlungsphase verwendet das <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker>-Objekt. Bei einer URN-Liste mit Objekten gibt die <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A>-Methode des <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker>-Objekts ein <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>-Objekt für die Objekte in der URN-Liste zurück. Der boolesche Wert *fParents* Parameter wird verwendet, um auszuwählen, ob die über- oder untergeordneten Elemente des angegebenen Objekts sind, die ermittelt werden. Die Abhängigkeitsstruktur kann in dieser Phase geändert werden.  
  
 In der Listengenerierungsphase wird die Struktur übergeben und die resultierende Liste wird zurückgegeben. Diese Objektliste ist in Skriptreihenfolge und kann bearbeitet werden.  
  
 Die Listengenerierungsphase verwendet die <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A>-Methode, um <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> zurückzugeben. <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> kann in dieser Phase geändert werden.  
  
 In der dritten und abschließenden Phase wird ein Skript mit der angegebenen Liste und den Skriptoptionen generiert. Das Ergebnis wird als <xref:System.Collections.Specialized.StringCollection>-Systemobjekt zurückgegeben. In dieser Phase werden dann die abhängigen Objektnamen aus der Elementauflistung des <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>-Objekts und von Eigenschaften, wie <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> und <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A>, extrahiert.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
 Dieses Codebeispiel erfordert eine `Imports`-Anweisung für den System.Collections.Specialized-Namespace. Fügen Sie dies mit den anderen Imports-Anweisungen ein, vor jeglichen Deklarationen in der Anwendung.  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
Imports System.Collections.Specialized  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-basic"></a>Ausgeben von Abhängigkeiten für eine Datenbank in Visual Basic  
 In diesem Codebeispiel wird gezeigt, wie die Abhängigkeiten ermittelt werden und wie die Liste durchlaufen wird, um die Ergebnisse anzuzeigen.  
  
```  
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
  
Public Class A  
   Public Shared Sub Main()  
      ' database name  
      Dim dbName As [String] = "AdventureWorksLT2012"   ' database name  
  
      ' Connect to the local, default instance of SQL Server.   
      Dim srv As New Server()  
  
      ' Reference the database.    
      Dim db As Database = srv.Databases(dbName)  
  
      ' Define a Scripter object and set the required scripting options.   
      Dim scrp As New Scripter(srv)  
      scrp.Options.ScriptDrops = False  
      scrp.Options.WithDependencies = True  
      scrp.Options.Indexes = True   ' To include indexes  
      scrp.Options.DriAllConstraints = True   ' to include referential constraints in the script  
  
      ' Iterate through the tables in database and script each one. Display the script.  
      For Each tb As Table In db.Tables  
         ' check if the table is not a system table  
         If tb.IsSystemObject = False Then  
            Console.WriteLine("-- Scripting for table " + tb.Name)  
  
            ' Generating script for table tb  
            Dim sc As System.Collections.Specialized.StringCollection = scrp.Script(New Urn() {tb.Urn})  
            For Each st As String In sc  
               Console.WriteLine(st)  
            Next  
            Console.WriteLine("--")  
         End If  
      Next  
   End Sub  
End Class  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-c"></a>Ausgeben von Abhängigkeiten für eine Datenbank in Visual C#  
 In diesem Codebeispiel wird gezeigt, wie die Abhängigkeiten ermittelt werden und wie die Liste durchlaufen wird, um die Ergebnisse anzuzeigen.  
  
```  
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
  
public class A {  
   public static void Main() {   
      String dbName = "AdventureWorksLT2012"; // database name  
  
      // Connect to the local, default instance of SQL Server.   
      Server srv = new Server();  
  
      // Reference the database.    
      Database db = srv.Databases[dbName];  
  
      // Define a Scripter object and set the required scripting options.   
      Scripter scrp = new Scripter(srv);  
      scrp.Options.ScriptDrops = false;  
      scrp.Options.WithDependencies = true;  
      scrp.Options.Indexes = true;   // To include indexes  
      scrp.Options.DriAllConstraints = true;   // to include referential constraints in the script  
  
      // Iterate through the tables in database and script each one. Display the script.     
      foreach (Table tb in db.Tables) {   
         // check if the table is not a system table  
         if (tb.IsSystemObject == false) {  
            Console.WriteLine("-- Scripting for table " + tb.Name);  
  
            // Generating script for table tb  
            System.Collections.Specialized.StringCollection sc = scrp.Script(new Urn[]{tb.Urn});  
            foreach (string st in sc) {  
               Console.WriteLine(st);  
            }  
            Console.WriteLine("--");  
         }  
      }   
   }  
}  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-powershell"></a>Ausgeben von Abhängigkeiten für eine Datenbank in PowerShell  
 In diesem Codebeispiel wird gezeigt, wie die Abhängigkeiten ermittelt werden und wie die Liste durchlaufen wird, um die Ergebnisse anzuzeigen.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
# Create a Scripter object and set the required scripting options.  
$scrp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Scripter -ArgumentList (Get-Item .)  
$scrp.Options.ScriptDrops = $false  
$scrp.Options.WithDependencies = $true  
$scrp.Options.IncludeIfNotExists = $true  
  
# Set the path context to the tables in AdventureWorks2012.  
  
CD Databases\AdventureWorks2012\Tables  
  
foreach ($Item in Get-ChildItem)  
 {    
 $scrp.Script($Item)  
 }  
```  
  
  
