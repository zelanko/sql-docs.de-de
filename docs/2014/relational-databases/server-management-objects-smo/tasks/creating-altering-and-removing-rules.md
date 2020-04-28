---
title: Erstellen, ändern und Löschen von Regeln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- rules [SMO]
ms.assetid: 16981459-524e-4b39-a899-4370eaf763cc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30c5c1a0593c6287cca48b4e241854b4145f4518
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "72782317"
---
# <a name="creating-altering-and-removing-rules"></a>Erstellen, Ändern und Löschen von Regeln
  In SMO werden Regeln durch das <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekt dargestellt. Die Regel wird durch die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A>-Eigenschaft definiert, wobei es sich um eine Textzeichenfolge handelt, die einen Bedingungsausdruck enthält, der Operatoren oder Prädikate wie IN, LIKE oder BETWEEN verwendet. Eine Regel kann nicht auf Spalten oder andere Datenbankobjekte verweisen. Integrierte Funktionen, die nicht auf Datenbankobjekte verweisen, dürfen in einer Regel eingeschlossen sein.  
  
 Die Definition in der <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A>-Eigenschaft muss eine Variable enthalten, die auf den eingegebenen Datenwert verweist. Ein beliebiger Name oder Symbol kann verwendet werden, um den Wert beim Erstellen der Regel darzustellen, aber das erste Zeichen \@ muss das Symbol sein.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-basic"></a>Erstellen, Ändern und Entfernen einer Regel in Visual Basic  
 Dieses Codebeispiel zeigt, wie eine Regel erstellt und an eine Spalte angefügt wird, wie Eigenschaften des <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekts geändert werden, die Regel von der Spalte getrennt und anschließend gelöscht wird.  
  
 Die `Dim`-Anweisung für das <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekt wird mit dem vollständigen Assemblypfad angegeben, um Mehrdeutigkeit in Bezug auf ein <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekt in der System.Data-Assembly zu vermeiden.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBRules1](SMO How to#SMO_VBRules1)]  -->  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-c"></a>Erstellen, Ändern und Löschen einer Regel in Visual C#  
 Dieses Codebeispiel zeigt, wie eine Regel erstellt und an eine Spalte angefügt wird, wie Eigenschaften des <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekts geändert werden, die Regel von der Spalte getrennt und anschließend gelöscht wird.  
  
 Die `Dim`-Anweisung für das <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekt wird mit dem vollständigen Assemblypfad angegeben, um Mehrdeutigkeit in Bezug auf ein <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekt in der System.Data-Assembly zu vermeiden.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
            //Note that the full namespace must be given for the Rule type to differentiate it from other Rule types.   
            Microsoft.SqlServer.Management.Smo.Rule ru;  
            ru = new Rule(db, "TestRule", "Production");  
            //Set the TextHeader and TextBody properties to define the rule.   
            ru.TextHeader = "CREATE RULE [Production].[TestRule] AS";  
            ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())";  
            //Create the rule on the instance of SQL Server.   
            ru.Create();  
            //Bind the rule to a column in the Product table by supplying the table, schema, and   
            //column as arguments in the BindToColumn method.   
            ru.BindToColumn("Product", "SellEndDate", "Production");  
            //Unbind from the column before removing the rule from the database.   
            ru.UnbindFromColumn("Product", "SellEndDate", "Production");  
            ru.Drop();  
  
        }  
```  
  
## <a name="creating-altering-and-removing-a-rule-in-powershell"></a>Erstellen, Ändern und Löschen einer Regel in PowerShell  
 Dieses Codebeispiel zeigt, wie eine Regel erstellt und an eine Spalte angefügt wird, wie Eigenschaften des <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekts geändert werden, die Regel von der Spalte getrennt und anschließend gelöscht wird.  
  
 Die `Dim`-Anweisung für das <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekt wird mit dem vollständigen Assemblypfad angegeben, um Mehrdeutigkeit in Bezug auf ein <xref:Microsoft.SqlServer.Management.Smo.Rule>-Objekt in der System.Data-Assembly zu vermeiden.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a Rule object variable by supplying the parent database, name and schema in the constructor.
$ru = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Rule -argumentlist $db, "TestRule", "Production"  
  
#Set the TextHeader and TextBody properties to define the rule.
$ru.TextHeader = "CREATE RULE [Production].[TestRule] AS"  
$ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())"  
  
#Create the rule on the instance of SQL Server.
$ru.Create()  
  
# Bind the rule to a column in the Product table by supplying the table, schema, and column as arguments in the BindToColumn method.
$ru.BindToColumn("Product", "SellEndDate", "Production")  
  
#Unbind from the column before removing the rule from the database.
$ru.UnbindFromColumn("Product", "SellEndDate", "Production")  
$ru.Drop()  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.SqlServer.Management.Smo.Rule>  
