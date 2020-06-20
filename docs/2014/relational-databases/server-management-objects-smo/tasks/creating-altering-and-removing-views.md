---
title: Erstellen, ändern und Entfernen von Sichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: stevestein
ms.author: sstein
ms.openlocfilehash: c4fd5cad7c3a2b317393561e91df130d0325965d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85037632"
---
# <a name="creating-altering-and-removing-views"></a>Erstellen, Ändern und Löschen von Sichten
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sichten durch das <xref:Microsoft.SqlServer.Management.Smo.View>-Objekt dargestellt.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.View>-Objekts definiert die Sicht. Sie entspricht der SELECT-Anweisung von [!INCLUDE[tsql](../../../includes/tsql-md.md)] zur Erstellung einer Sicht.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a>Erstellen, Ändern und Löschen einer Sicht in Visual Basic  
 In diesem Codebeispiel wird gezeigt, wie eine Sicht von zwei Tabellen mit einem inneren Join erstellt wird. Die Sicht wird im Textmodus erstellt, daher muss die <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A>-Eigenschaft festgelegt werden.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBViews1](SMO How to#SMO_VBViews1)]  -->  
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a>Erstellen, Ändern und Löschen einer Sicht in Visual C#  
 In diesem Codebeispiel wird gezeigt, wie eine Sicht von zwei Tabellen mit einem inneren Join erstellt wird. Die Sicht wird im Textmodus erstellt, daher muss die <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A>-Eigenschaft festgelegt werden.  
  
```csharp
{  
        //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a View object variable by supplying the parent database, view name and schema in the constructor.   
        View myview;   
        myview = new View(db, "Test_View", "Sales");   
        //Set the TextHeader and TextBody property to define the view.   
        myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS";   
        myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID";   
        //Create the view on the instance of SQL Server.   
        myview.Create();   
        //Remove the view.   
        myview.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-view-in-powershell"></a>Erstellen, Ändern und Löschen einer Sicht in PowerShell  
 In diesem Codebeispiel wird gezeigt, wie eine Sicht von zwei Tabellen mit einem inneren Join erstellt wird. Die Sicht wird im Textmodus erstellt, daher muss die <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A>-Eigenschaft festgelegt werden.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View -argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.
$myview.Create()  
  
# Remove the view
$myview.Drop();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
