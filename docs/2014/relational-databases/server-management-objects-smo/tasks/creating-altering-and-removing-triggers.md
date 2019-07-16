---
title: Erstellen, ändern und Entfernen von Triggern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b4f6cf3b1e988d12a39096d46275058d080a23c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68211897"
---
# <a name="creating-altering-and-removing-triggers"></a>Erstellen, Ändern und Löschen von Trigger
  In SMO werden Trigger durch das <xref:Microsoft.SqlServer.Management.Smo.Trigger>-Objekt dargestellt. Die [!INCLUDE[tsql](../../../includes/tsql-md.md)] Code, der ausgeführt wird, wenn der Trigger, die ausgelöst wird, festgelegt ist, indem Sie die <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> Eigenschaft des Trigger-Objekts. Der Typ des Triggers wird über andere Eigenschaften des <xref:Microsoft.SqlServer.Management.Smo.Trigger>-Objekts gesetzt, beispielsweise durch die <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A>-Eigenschaft. Hierbei handelt es sich um eine boolesche Eigenschaft, die angibt, ob der Trigger durch ein `UPDATE` von Datensätzen auf der übergeordneten Tabelle ausgelöst wird.  
  
 Das <xref:Microsoft.SqlServer.Management.Smo.Trigger>-Objekt stellt herkömmlicherweise Datenbearbeitungssprachentrigger (DML) dar. In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höheren Versionen werden auch DDL (Data Definition Language)-Trigger unterstützt. DDL-Trigger werden durch das <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger>-Objekt und das <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger>-Objekt dargestellt.  
  
## <a name="example"></a>Beispiel  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a>Erstellen, Ändern und Löschen eines Triggers in Visual Basic  
 Dieses Codebeispiel zeigt, wie ein UPDATE-Trigger für eine vorhandene Tabelle mit dem Namen `Sales`in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] -Datenbank erstellt und eingefügt wird. Der Trigger sendet eine Erinnerungsmitteilung, wenn die Tabelle aktualisiert oder ein neuer Datensatz eingefügt wird.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTriggers1](SMO How to#SMO_VBTriggers1)]  -->  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a>Erstellen, Ändern und Löschen eines Triggers in Visual C#  
 Dieses Codebeispiel zeigt, wie ein UPDATE-Trigger für eine vorhandene Tabelle mit dem Namen `Sales`in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] -Datenbank erstellt und eingefügt wird. Der Trigger sendet eine Erinnerungsmitteilung, wenn die Tabelle aktualisiert oder ein neuer Datensatz eingefügt wird.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a>Erstellen, Ändern und Löschen eines Triggers in PowerShell  
 Dieses Codebeispiel zeigt, wie ein UPDATE-Trigger für eine vorhandene Tabelle mit dem Namen `Sales`in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] -Datenbank erstellt und eingefügt wird. Der Trigger sendet eine Erinnerungsmitteilung, wenn die Tabelle aktualisiert oder ein neuer Datensatz eingefügt wird.  
  
```  
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = get-item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger `  
-argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.   
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.   
$tr.Create()  
  
#Remove the trigger.   
$tr.Drop()  
```  
  
  
