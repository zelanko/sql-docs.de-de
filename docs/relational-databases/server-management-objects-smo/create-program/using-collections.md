---
title: Verwenden von Sammlungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c3f4c31da84c2ca07b948faeba4aed7b93ad011
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148697"
---
# <a name="using-collections"></a>Verwenden von Auflistungen
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Eine Auflistung ist eine Liste von Objekten, die aus der gleichen Objektklasse gebildet wurden und über dasselbe übergeordnete Objekt verfügen. Das Auflistungsobjekt enthält immer den Namen des Objekttyps mit dem Suffix „Collection“. Um beispielsweise auf die Spalten einer gegebenen Tabelle zuzugreifen, verwenden Sie den <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection>-Objekttyp. Er enthält alle <xref:Microsoft.SqlServer.Management.Smo.Column>-Objekte, die zum gleichen <xref:Microsoft.SqlServer.Management.Smo.Table>-Objekt gehören.  
  
 Mit der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] **For...Each** -Anweisung oder der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] **foreach** -Anweisung können die einzelnen Elemente der Auflistung durchlaufen werden.  
  
## <a name="examples"></a>Beispiele  
Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a>Verweisen auf ein Objekt mithilfe einer Auflistung in Visual Basic  
 Dieses Codebeispiel zeigt, wie eine Spalteneigenschaft mithilfe der Eigenschaften <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> und <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> festgelegt wird. Diese Eigenschaften repräsentieren Auflistungen, mit denen ein bestimmtes Objekt identifiziert werden kann, wenn sie mit einem Parameter verwendet werden, der den Namen des Objekts angibt. Der Name und das Schema sind für die <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> Auflistungsobjekteigenschaft erforderlich.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Modify a property using the Databases, Tables, and Columns collections to reference a column.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Nullable = True
'Call the Alter method to make the change on the instance of SQL Server.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Alter()
```
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a>Verweisen auf ein Objekt mithilfe einer Auflistung in Visual C#  
 Dieses Codebeispiel zeigt, wie eine Spalteneigenschaft mithilfe der Eigenschaften <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> und <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> festgelegt wird. Diese Eigenschaften repräsentieren Auflistungen, mit denen ein bestimmtes Objekt identifiziert werden kann, wenn sie mit einem Parameter verwendet werden, der den Namen des Objekts angibt. Der Name und das Schema sind für die <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> Auflistungsobjekteigenschaft erforderlich.  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Modify a property using the Databases, Tables, and Columns collections to reference a column.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Nullable = true;   
//Call the Alter method to make the change on the instance of SQL Server.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Alter();   
}  
```  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-basic"></a>Durchlaufen der Elemente einer Auflistung in Visual Basic  
 In diesem Codebeispiel wird die <xref:Microsoft.AnalysisServices.Server.Databases%2A>-Auflistungseigenschaft durchlaufen, und anschließend werden alle Datenbankverbindungen mit der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] angezeigt.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
Dim count As Integer
Dim total As Integer
'Iterate through the databases and call the GetActiveDBConnectionCount method.
Dim db As Database
For Each db In srv.Databases
    count = srv.GetActiveDBConnectionCount(db.Name)
    total = total + count
    'Display the number of connections for each database.
    Console.WriteLine(count & " connections on " & db.Name)
Next
'Display the total number of connections on the instance of SQL Server.
Console.WriteLine("Total connections =" & total)
```
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a>Durchlaufen der Elemente einer Auflistung in Visual C#  
 In diesem Codebeispiel wird die <xref:Microsoft.AnalysisServices.Server.Databases%2A>-Auflistungseigenschaft durchlaufen, und anschließend werden alle Datenbankverbindungen mit der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] angezeigt.  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
int count = 0;   
int total = 0;   
//Iterate through the databases and call the GetActiveDBConnectionCount method.   
Database db = default(Database);   
foreach ( db in srv.Databases) {   
  count = srv.GetActiveDBConnectionCount(db.Name);   
  total = total + count;   
  //Display the number of connections for each database.   
  Console.WriteLine(count + " connections on " + db.Name);   
}   
//Display the total number of connections on the instance of SQL Server.   
Console.WriteLine("Total connections =" + total);   
}   
```  
  
  
