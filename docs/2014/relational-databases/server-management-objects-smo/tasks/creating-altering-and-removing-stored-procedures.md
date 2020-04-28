---
title: Erstellen, ändern und Löschen gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 58890cc7b9e34a3e8ff9262af1f6b1a67b47841e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "72782358"
---
# <a name="creating-altering-and-removing-stored-procedures"></a>Erstellen, Ändern und Löschen von gespeicherten Prozeduren
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) werden gespeicherte Prozeduren durch das <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>-Objekt dargestellt.  
  
 Die Erstellung eines <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>-Objekts in SMO erfordert, dass die Einstellung der <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A>-Eigenschaft auf das [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Skript gesetzt wird, das die gespeicherte Prozedur definiert. Für Parameter ist \@ das Präfix erforderlich, und Sie müssen <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> einzeln mithilfe von-Objekten <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> erstellt und der <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> -Auflistung des-Objekts hinzugefügt werden.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a>Erstellen, Ändern und Entfernen einer gespeicherten Prozedur in Visual Basic  
 Dieses Codebeispiel zeigt, wie eine gespeicherte Prozedur für die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] -Datenbank erstellt wird. Im Beispiel wird der Nachname eines Mitarbeiters zurückgegeben, wenn die Mitarbeiter-ID-Nummer angegeben wird. Die gespeicherte Prozedur erfordert einen Eingabeparameter zur Angabe der Mitarbeiter-ID-Nummer und einen Ausgabeparameter für die Rückgabe des Nachnamens des Mitarbeiters.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a>Erstellen, Ändern und Löschen einer gespeicherten Prozedur in Visual C#  
 Dieses Codebeispiel zeigt, wie eine gespeicherte Prozedur für die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] -Datenbank erstellt wird. Im Beispiel wird der Nachname eines Mitarbeiters zurückgegeben, wenn die Mitarbeiter-ID-Nummer angegeben wird (`BusinessEntityID`). Die gespeicherte Prozedur erfordert einen Eingabeparameter zur Angabe der Mitarbeiter-ID-Nummer und einen Ausgabeparameter für die Rückgabe des Nachnamens des Mitarbeiters.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a>Erstellen, Ändern und Löschen einer gespeicherten Prozedur in PowerShell  
 Dieses Codebeispiel zeigt, wie eine gespeicherte Prozedur für die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] -Datenbank erstellt wird. Im Beispiel wird der Nachname eines Mitarbeiters zurückgegeben, wenn die Mitarbeiter-ID-Nummer angegeben wird (`BusinessEntityID`). Die gespeicherte Prozedur erfordert einen Eingabeparameter zur Angabe der Mitarbeiter-ID-Nummer und einen Ausgabeparameter für die Rückgabe des Nachnamens des Mitarbeiters.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.
$sp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure -argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.
$sp.Drop()  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
