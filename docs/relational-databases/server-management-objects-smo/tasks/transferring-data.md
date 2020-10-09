---
description: Übertragen von Daten
title: Übertragen von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- data transfers [SMO]
- transferring data
ms.assetid: eea255c3-8251-40f0-973b-fe4ef6cb5261
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: de139744d0c14668d0d7e67ada36be1142721762
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91869232"
---
# <a name="transferring-data"></a>Übertragen von Daten
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Die <xref:Microsoft.SqlServer.Management.Smo.Transfer>-Klasse ist eine Hilfsprogrammklasse, die Tools zur Übertragung von Objekten und Daten bereitstellt.  
  
 Objekte im Datenbankschema werden übertragen, indem auf dem Zielserver ein generiertes Skript ausgeführt wird. <xref:Microsoft.SqlServer.Management.Smo.Table>-Daten werden mit einem dynamisch erstellten DTS-Paket übertragen.  
  
 Das- <xref:Microsoft.SqlServer.Management.Smo.Transfer> Objekt verwendet die [SqlBulkCopy](/dotnet/api/system.data.sqlclient.sqlbulkcopy) -API, um Daten zu übertragen. Zudem befinden sich die für die Durchführung von Datenübertragungen verwendeten Methoden und Eigenschaften im <xref:Microsoft.SqlServer.Management.Smo.Transfer>-Objekt statt im <xref:Microsoft.SqlServer.Management.Smo.Database>-Objekt. Das Verschieben von Funktionalität aus den Instanzenklassen in die Hilfsprogrammklassen entspricht einem weniger umfangreichen Objektmodell, da der Code für spezifische Aufgaben nur dann geladen wird, wenn er benötigt wird.  
  
 Das <xref:Microsoft.SqlServer.Management.Smo.Transfer>-Objekt unterstützt keine Datenübertragungen in eine Zieldatenbank, deren <xref:Microsoft.SqlServer.Management.Smo.Database.CompatibilityLevel%2A> geringer als die Version der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz ist.  
  
## <a name="example"></a>Beispiel  
Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C-&#35; SMO-Projekts in Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-basic"></a>Übertragen von Schema und Daten aus einer Datenbank in eine andere in Visual Basic  
 Dieses Codebeispiel stellt die Übertragung von Schema und Daten mithilfe des <xref:Microsoft.SqlServer.Management.Smo.Transfer>-Objekts von einer Datenbank in eine andere dar.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Create a new database that is to be destination database.
Dim dbCopy As Database
dbCopy = New Database(srv, "AdventureWorks2012Copy")
dbCopy.Create()
'Define a Transfer object and set the required options and properties.
Dim xfr As Transfer
xfr = New Transfer(db)
xfr.CopyAllTables = True
xfr.Options.WithDependencies = True
xfr.Options.ContinueScriptingOnError = True
xfr.DestinationDatabase = "AdventureWorks2012Copy"
xfr.DestinationServer = srv.Name
xfr.DestinationLoginSecure = True
xfr.CopySchema = True
'Script the transfer. Alternatively perform immediate data transfer with TransferData method.
xfr.ScriptTransfer()
```
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-c"></a>Übertragen von Schema und Daten aus einer Datenbank in eine andere in Visual C#  
 Dieses Codebeispiel stellt die Übertragung von Schema und Daten mithilfe des <xref:Microsoft.SqlServer.Management.Smo.Transfer>-Objekts von einer Datenbank in eine andere dar.  
  
```csharp  
{  
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Create a new database that is to be destination database.   
            Database dbCopy;  
            dbCopy = new Database(srv, "AdventureWorks2012Copy");  
            dbCopy.Create();  
            //Define a Transfer object and set the required options and properties.   
            Transfer xfr;  
            xfr = new Transfer(db);  
            xfr.CopyAllTables = true;  
            xfr.Options.WithDependencies = true;  
            xfr.Options.ContinueScriptingOnError = true;  
            xfr.DestinationDatabase = "AdventureWorks2012Copy";  
            xfr.DestinationServer = srv.Name;  
            xfr.DestinationLoginSecure = true;  
            xfr.CopySchema = true;  
            //Script the transfer. Alternatively perform immediate data transfer   
            // with TransferData method.   
            xfr.ScriptTransfer();  
        }   
```  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-powershell"></a>Übertragen von Schema und Daten aus einer Datenbank in eine andere in PowerShell  
 Dieses Codebeispiel stellt die Übertragung von Schema und Daten mithilfe des <xref:Microsoft.SqlServer.Management.Smo.Transfer>-Objekts von einer Datenbank in eine andere dar.  
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Reference the AdventureWorks2012 database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a database to hold the copy of AdventureWorks  
$dbCopy = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Database -argumentlist $srv, "AdventureWorksCopy"  
$dbCopy.Create()  
  
#Define a Transfer object and set the required options and properties.  
$xfr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Transfer -argumentlist $db  
  
#Set this objects properties  
$xfr.CopyAllTables = $true  
$xfr.Options.WithDependencies = $true  
$xfr.Options.ContinueScriptingOnError = $true  
$xfr.DestinationDatabase = "AdventureWorksCopy"  
$xfr.DestinationServer = $srv.Name  
$xfr.DestinationLoginSecure = $true  
$xfr.CopySchema = $true  
"Scripting Data Transfer"  
#Script the transfer. Alternatively perform immediate data transfer with TransferData method.  
$xfr.ScriptTransfer()  
```  
  
