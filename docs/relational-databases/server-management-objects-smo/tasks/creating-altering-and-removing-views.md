---
description: Erstellen, Ändern und Löschen von Sichten
title: Erstellen, Ändern und Löschen von Sichten
ms.custom: seo-dt-2019
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b4c942adfbe2b9edf450d332450bf8a8a958a80e
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475541"
---
# <a name="creating-altering-and-removing-views"></a>Erstellen, Ändern und Löschen von Sichten
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sichten durch das <xref:Microsoft.SqlServer.Management.Smo.View>-Objekt dargestellt.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.View>-Objekts definiert die Sicht. Sie entspricht der SELECT-Anweisung von [!INCLUDE[tsql](../../../includes/tsql-md.md)] zur Erstellung einer Sicht.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C-&#35; SMO-Projekts in Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a>Erstellen, Ändern und Löschen einer Sicht in Visual Basic  
 In diesem Codebeispiel wird gezeigt, wie eine Sicht von zwei Tabellen mit einem inneren Join erstellt wird. Die Sicht wird im Textmodus erstellt, daher muss die <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A>-Eigenschaft festgelegt werden.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a View object variable by supplying the parent database, view name and schema in the constructor.
Dim myview As View
myview = New View(db, "Test_View", "Sales")
'Set the TextHeader and TextBody property to define the view.
myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"
myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"
'Create the view on the instance of SQL Server.
myview.Create()
'Remove the view.
myview.Drop()
```
  
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
$db = get-item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.   
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View `  
-argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.   
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.   
$myview.Create()  
  
# Remove the view.   
$myview.Drop();  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
  
  
