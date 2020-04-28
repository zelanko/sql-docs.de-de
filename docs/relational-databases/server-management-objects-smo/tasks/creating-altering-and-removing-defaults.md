---
title: Erstellen, Ändern und Löschen von Standardwerten
ms.custom: seo-dt-2019
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 17e7f0dd020004f0251fd470e42a591f926d7ce2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74094641"
---
# <a name="creating-altering-and-removing-defaults"></a>Erstellen, Ändern und Löschen von Standardwerten
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) wird die Standardeinschränkung durch das <xref:Microsoft.SqlServer.Management.Smo.Default>-Objekt dargestellt.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Default>-Objekts wird verwendet, um den Wert zu setzen, der eingefügt werden soll. Dies kann eine Konstante oder eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung sein, die einen konstanten Wert zurückgibt, z. B. GETDATE(). Die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A>-Eigenschaft kann über die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>-Methode nicht geändert werden. Stattdessen muss das <xref:Microsoft.SqlServer.Management.Smo.Default>-Objekt gelöscht und neu erstellt werden.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C-&#35; SMO-Projekts in Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a>Erstellen, Ändern und Löschen eines Standardwerts in Visual Basic  
 Dieses Codebeispiel zeigt, wie ein Standardwert, bei dem es sich um einen einfachen Text handelt, und ein anderer Standardwert, bei dem es sich um eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung handelt, erstellt werden. Der Standardwert muss über die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A>-Methode angehängt und über die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>-Methode getrennt werden.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a Default object variable by supplying the parent database and the default name 
'in the constructor.
Dim def As [Default]
def = New [Default](db, "Test_Default2")
'Set the TextHeader and TextBody properties that define the default.
def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"
def.TextBody = "GetDate()"
'Create the default on the instance of SQL Server.
def.Create()
'Declare a Column object variable and reference a column in the AdventureWorks2012 database.
Dim col As Column
col = db.Tables("SpecialOffer", "Sales").Columns("StartDate")
'Bind the default to the column.
def.BindToColumn("SpecialOffer", "StartDate", "Sales")
'Unbind the default from the column and remove it from the database.
def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")
def.Drop()
```
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a>Erstellen, Ändern und Löschen eines Standardwerts in Visual C#  
 Dieses Codebeispiel zeigt, wie ein Standardwert, bei dem es sich um einen einfachen Text handelt, und ein anderer Standardwert, bei dem es sich um eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung handelt, erstellt werden. Der Standardwert muss über die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A>-Methode angehängt und über die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>-Methode getrennt werden.  
  
```csharp  
{  
  
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a>Erstellen, Ändern und Löschen eines Standardwerts in PowerShell  
 Dieses Codebeispiel zeigt, wie ein Standardwert, bei dem es sich um einen einfachen Text handelt, und ein anderer Standardwert, bei dem es sich um eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung handelt, erstellt werden. Der Standardwert muss über die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A>-Methode angehängt und über die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>-Methode getrennt werden.  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
  
  
