---
title: Aufrufen von Methoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- methods [SMO]
- calling methods
- SQL Server Management Objects, method calling
- SMO [SQL Server], method calling
ms.assetid: c88d5c5f-9ff0-4f84-b2b6-24c6b90fa15e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5c3a004d30a5edb20da77e6f93bf51a94472419b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63192160"
---
# <a name="calling-methods"></a>Aufrufen von Methoden
  -Methoden führen bestimmte Aufgaben im Zusammenhang mit dem-Objekt aus `Checkpoint` , z [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. b. das Ausgeben eines in einer Datenbank oder das Anfordern einer Aufzählungs Liste mit Anmeldungen für die-Instanz.  
  
 Methoden führen Vorgänge an Objekten aus. Methoden können Parameter enthalten, und sie verfügen häufig über einen Rückgabewert. Bei dem Rückgabewert kann es sich um einen einfachen Datentyp, ein komplexes Objekt oder eine Struktur handeln, die mehrere Elemente enthält.  
  
 Mithilfe der Ausnahmebehandlung können Sie feststellen, ob die Methode erfolgreich war. Weitere Informationen finden Sie unter [Handling SMO Exceptions](handling-smo-exceptions.md).  
  
## <a name="examples"></a>Beispiele  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="using-a-simple-smo-method-in-visual-basic"></a>Verwenden einer einfachen SMO-Methode in Visual Basic  
 In diesem Beispiel enthält die <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A>-Methode keine Parameter und hat keinen Rückgabewert.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods1](SMO How to#SMO_VBMethods1)]  -->  
  
## <a name="using-a-simple-smo-method-in-visual-c"></a>Verwenden einer einfachen SMO-Methode in Visual C#  
 In diesem Beispiel enthält die <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A>-Methode keine Parameter und hat keinen Rückgabewert.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define a Database object variable by supplying the parent server and the database name arguments in the constructor.   
Database db;   
db = new Database(srv, "Test_SMO_Database");   
//Call the Create method to create the database on the instance of SQL Server.   
db.Create();   
```  
  
 }  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-basic"></a>Verwenden einer SMO-Methode mit einem Parameter in Visual Basic  
 Das <xref:Microsoft.SqlServer.Management.Smo.Table>-Objekt verfügt über eine Methode mit dem Namen <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>. Diese Methode benötigt einen numerischen Parameter, der `FillFactor`angibt.  
  
```  
Dim srv As Server  
srv = New Server  
Dim tb As Table  
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources")  
tb.RebuildIndexes(70)  
```  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-c"></a>Verwenden einer SMO-Methode mit einem Parameter in Visual C#  
 Das <xref:Microsoft.SqlServer.Management.Smo.Table>-Objekt verfügt über eine Methode mit dem Namen <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>. Diese Methode benötigt einen numerischen Parameter, der `FillFactor`angibt.  
  
```  
{   
Server srv = default(Server);   
srv = new Server();   
Table tb = default(Table);   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
}   
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-basic"></a>Verwenden einer Enumerationsmethode in Visual Basic, die ein "DataTable"-Objekt zurückgibt  
 In diesem Abschnitt wird beschrieben, wie eine Enumerationsmethode aufgerufen wird und wie die Daten im zurückgegebenen <xref:System.Data.DataTable>-Objekt behandelt werden.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A>-Methode gibt ein <xref:System.Data.DataTable>-Objekt zurück, für das weitere Navigation erforderlich ist, auf alle verfügbaren Sortierungsinformationen zu der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zuzugreifen.  
  
```  
'Connect to the local, default instance of SQL Server.  
Dim srv As Server  
srv = New Server  
'Call the EnumCollations method and return collation information to DataTable variable.  
Dim d As DataTable  
'Select the returned data into an array of DataRow.  
d = srv.EnumCollations  
'Iterate through the rows and display collation details for the instance of SQL Server.  
Dim r As DataRow  
Dim c As DataColumn  
For Each r In d.Rows  
    Console.WriteLine("==")  
    For Each c In r.Table.Columns  
        Console.WriteLine(c.ColumnName + " = " + r(c).ToString)  
    Next  
Next  
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-c"></a>Verwenden einer Enumerationsmethode in Visual C#, die ein "DataTable"-Objekt zurückgibt  
 In diesem Abschnitt wird beschrieben, wie eine Enumerationsmethode aufgerufen wird und wie die Daten im zurückgegebenen <xref:System.Data.DataTable>-Objekt behandelt werden.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A>-Methode gibt ein <xref:System.Data.DataTable>-Systemobjekt zurück. Für das <xref:System.Data.DataTable>-Objekt ist weitere Navigation erforderlich, um auf alle verfügbaren Sortierungsinformationen zu der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zuzugreifen.  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumCollations;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=========");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="constructing-an-object-in-visual-basic"></a>Erstellen eines Objekts in Visual Basic  
 Der Konstruktor eines Objekts kann mit dem `New`-Operator aufgerufen werden. Der <xref:Microsoft.SqlServer.Management.Smo.Database>-Objektkonstruktor ist überladen, und die Version des im Beispiel verwendeten <xref:Microsoft.SqlServer.Management.Smo.Database>-Objektkonstruktors akzeptiert zwei Parameter: das übergeordnete <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt, zu dem die Datenbank gehört, und eine Zeichenfolge, die den Namen der neuen Datenbank darstellt.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods4](SMO How to#SMO_VBMethods4)]  -->  
  
## <a name="constructing-an-object-in-visual-c"></a>Erstellen eines Objekts in Visual C#  
 Der Konstruktor eines Objekts kann mit dem `New`-Operator aufgerufen werden. Der <xref:Microsoft.SqlServer.Management.Smo.Database>-Objektkonstruktor ist überladen, und die Version des im Beispiel verwendeten <xref:Microsoft.SqlServer.Management.Smo.Database>-Objektkonstruktors akzeptiert zwei Parameter: das übergeordnete <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt, zu dem die Datenbank gehört, und eine Zeichenfolge, die den Namen der neuen Datenbank darstellt.  
  
```  
{   
Server srv;   
srv = new Server();   
Table tb;   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Declare and define a Database object by supplying the parent server and the database name arguments in the constructor.   
Database d;   
d = new Database(srv, "Test_SMO_Database");   
//Create the database on the instance of SQL Server.   
d.Create();   
Console.WriteLine(d.Name);   
}  
```  
  
## <a name="copying-an-smo-object-in-visual-basic"></a>Kopieren eines SMO-Objekts in Visual Basic  
 In diesem Codebeispiel wird die <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A>-Methode zum Erstellen einer Kopie des <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekts verwendet. Das <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt stellt eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dar.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VCMethods6](SMO How to#SMO_VCMethods6)]  -->  
  
## <a name="copying-an-smo-object-in-visual-c"></a>Kopieren eines SMO-Objekts in Visual C#  
 In diesem Codebeispiel wird die <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A>-Methode zum Erstellen einer Kopie des <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekts verwendet. Das <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt stellt eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dar.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv1;   
srv1 = new Server();   
//Modify the default database and the timeout period for the connection.   
srv1.ConnectionContext.DatabaseName = "AdventureWorks2012";   
srv1.ConnectionContext.ConnectTimeout = 30;   
//Make a second connection using a copy of the ConnectionContext property and verify settings.   
Server srv2;   
srv2 = new Server(srv1.ConnectionContext.Copy);   
Console.WriteLine(srv2.ConnectionContext.ConnectTimeout.ToString);   
}  
```  
  
## <a name="monitoring-server-processes-in-visual-basic"></a>Überwachen von Serverprozessen in Visual Basic  
 Informationen zum aktuellen Statustyp der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können Sie über Enumerationsmethoden abrufen. Im Beispielcode wird die <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A>-Methode zum Ermitteln von Informationen zu den aktuellen Prozessen verwendet. Dieses Beispiel zeigt auch, wie mit den Spalten und Zeilen im zurückgegebenen <xref:System.Data.DataTable>-Objekt gearbeitet wird.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods5](SMO How to#SMO_VBMethods5)]  -->  
  
## <a name="monitoring-server-processes-in-visual-c"></a>Überwachen von Serverprozessen in Visual C#  
 Informationen zum aktuellen Statustyp der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können Sie über Enumerationsmethoden abrufen. Im Beispielcode wird die <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A>-Methode zum Ermitteln von Informationen zu den aktuellen Prozessen verwendet. Dieses Beispiel zeigt auch, wie mit den Spalten und Zeilen im zurückgegebenen <xref:System.Data.DataTable>-Objekt gearbeitet wird.  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumProcesses;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=====");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
