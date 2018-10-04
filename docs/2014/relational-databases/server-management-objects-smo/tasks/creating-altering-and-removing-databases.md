---
title: Erstellen, ändern und Entfernen von Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- databases [SMO]
- databases [SMO], creating
- databases [SMO], modifying
- databases [SMO], deleting
ms.assetid: fcfb3ec2-7556-4f72-971a-501295892cb0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f56738b576fcbe6dc46a41a8151f3fd87f7d17a3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48204230"
---
# <a name="creating-altering-and-removing-databases"></a>Erstellen, Ändern und Löschen von Datenbanken
  In SMO wird eine Datenbank durch das <xref:Microsoft.SqlServer.Management.Smo.Database>-Objekt dargestellt.  
  
 Um diese zu ändern oder zu löschen, ist es nicht erforderlich, ein <xref:Microsoft.SqlServer.Management.Smo.Database>-Objekt zu erstellen. Auf die Datenbank kann mit einer Sammlung verwiesen werden.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-database-in-visual-basic"></a>Erstellen, Ändern und Löschen einer Datenbank in Visual Basic  
 In diesem Codebeispiel wird eine neue Datenbank erstellt. Dateien und Dateigruppen werden für die Datenbank automatisch erstellt.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDatabase1](SMO How to#SMO_VBDatabase1)]  -->  
  
## <a name="creating-altering-and-removing-a-database-in-visual-c"></a>Erstellen, Ändern und Löschen einer Datenbank in Visual C#  
 In diesem Codebeispiel wird eine neue Datenbank erstellt. Dateien und Dateigruppen werden für die Datenbank automatisch erstellt.  
  
```  
{  
                //Connect to the local, default instance of SQL Server.   
                Server srv;  
                srv = new Server();  
                //Define a Database object variable by supplying the server and the database name arguments in the constructor.   
                Database db;  
                db = new Database(srv, "Test_SMO_Database");  
                //Create the database on the instance of SQL Server.   
                db.Create();  
                //Reference the database and display the date when it was created.   
                db = srv.Databases["Test_SMO_Database"];  
                Console.WriteLine(db.CreateDate);  
                //Remove the database.   
                db.Drop();  
            }  
```  
  
## <a name="creating-altering-and-removing-a-database-in-powershell"></a>Erstellen, Ändern und Löschen einer Datenbank in PowerShell  
 In diesem Codebeispiel wird eine neue Datenbank erstellt. Dateien und Dateigruppen werden für die Datenbank automatisch erstellt.  
  
```  
#Get a server object which corresponds to the default instance  
cd \sql\localhost\  
$srv = get-item default  
  
#Create a new database  
$db = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Database -argumentlist $srv, "Test_SMO_Database"  
$db.Create()  
  
#Reference the database and display the date when it was created.   
$db = $srv.Databases["Test_SMO_Database"]  
$db.CreateDate  
  
#Drop the database  
$db.Drop()  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.SqlServer.Management.Smo.Database>  
  
  
