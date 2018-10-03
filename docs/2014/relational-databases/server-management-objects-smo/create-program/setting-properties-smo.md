---
title: Festlegen von Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SMO [SQL Server], properties
- SQL Server Management Objects, properties
- properties [SMO]
ms.assetid: 342569ba-d2f7-44d2-8f3f-ae9c701c7f0f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ceffa7d590ad7861b07700ac13ab795a309bff39
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080990"
---
# <a name="setting-properties"></a>Festlegen von Eigenschaften
  Eigenschaften sind Werte, die aussagekräftige Informationen über das Objekt speichern. Z. B. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Konfigurationsoptionen werden dargestellt, durch die <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> Eigenschaften des Objekts. Auf Eigenschaften kann mit der Eigenschaftsauflistung entweder direkt oder indirekt zugegriffen werden. Für den direkten Zugriff auf Eigenschaften wird die folgende Syntax verwendet:  
  
 `objInstance.PropertyName`  
  
 Ein Eigenschaftswert kann geändert oder abgerufen werden. Dies hängt davon ab, ob die Eigenschaft Lese-/Schreibzugriff hat oder schreibgeschützt ist. Bevor ein Objekt erstellt wird, müssen bestimmte Eigenschaften festgelegt werden. Weitere Informationen finden Sie in der SMO-Referenz für das entsprechende Objekt.  
  
> [!NOTE]  
>  Auflistungen von untergeordneten Objekten werden als Eigenschaft eines Objekts angezeigt. Z. B. die `Tables` Sammlung ist eine Eigenschaft einer `Server` Objekt. Weitere Informationen finden Sie unter [verwenden Auflistungen](using-collections.md).  
  
 Die Eigenschaften eines Objekts sind Mitglieder einer Eigenschaftsauflistung. Mithilfe der Eigenschaftsauflistung kann jede Eigenschaft eines Objekts durchlaufen werden.  
  
 Mitunter ist eine Eigenschaft aus den folgenden Gründen nicht verfügbar:  
  
-   Die Serverversion unterstützt die Eigenschaft nicht, z. B. wenn Sie versuchen auf eine Eigenschaft, die eine neue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Funktion darstellt, in einer älteren Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zuzugreifen.  
  
-   Der Server bietet keine Daten für die Eigenschaft, z. B. Wenn Sie versuchen, eine Eigenschaft zuzugreifen, die darstellt eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Komponente, die nicht installiert ist.  
  
 Sie können diese Situationen bewältigen, indem Sie die <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException>- und die <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException> SMO-Ausnahmen abfangen.  
  
## <a name="setting-default-initialization-fields"></a>Festlegen von Standardinitialisierungsfeldern  
 Beim Abrufen von Objekten führt SMO eine Optimierung aus. Die Optimierung minimiert die Anzahl von Eigenschaften, die durch automatisches Skalieren zwischen den folgenden Status geladen werden:  
  
1.  Teilweise geladen. Wenn auf ein Objekt erstmalig verwiesen wird, steht ein Minimum an Eigenschaften zur Verfügung (z. B. Name und Schema).  
  
2.  Vollständig geladen. Wenn auf eine Eigenschaft verwiesen wird, werden die übrigen Eigenschaften, die schnell geladen werden können, initialisiert und zur Verfügung gestellt.  
  
3.  Eigenschaften, die viel Arbeitsspeicher in Anspruch nehmen. Die übrigen nicht verfügbaren Eigenschaften nehmen viel Arbeitsspeicher und haben eine <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> -Eigenschaftswert True (z. B. <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>). Diese Eigenschaften werden nur geladen, wenn auf sie ausdrücklich verwiesen wird.  
  
 Wenn Ihre Anwendung zusätzliche Eigenschaften zu den im teilweise geladenen Status verfügbaren Eigenschaften abruft, übermittelt sie eine Abfrage zum Abrufen dieser zusätzlichen Eigenschaften und wechselt in den vollständig geladenen Status. Dies kann unnötigen Datenverkehr zwischen dem Client und dem Server verursachen. Weitere Optimierung kann erreicht werden, durch den Aufruf der <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> Methode. Die <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A>-Methode ermöglicht die Angabe der Eigenschaften, die beim Initialisieren des Objekts geladen werden.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A>-Methode legt das Verhalten zum Laden von Eigenschaften für die restliche Anwendung oder bis zum Zurücksetzen der Anwendung fest. Sie können das ursprüngliche Verhalten speichern, mithilfe der <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> Methode, und es nach Bedarf wiederherstellen.  
  
## <a name="examples"></a>Beispiele  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="getting-and-setting-a-property-in-visual-basic"></a>Abrufen und Festlegen einer Eigenschaft in Visual Basic  
 Dieses Codebeispiel zeigt, wie Sie Abrufen der <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Information> Objekt und zum Festlegen der <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> Eigenschaft, um die `ExecuteSql` Mitglied der <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> Enumerationstyp.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties1](SMO How to#SMO_VBProperties1)]  -->  
  
## <a name="getting-and-setting-a-property-in-visual-c"></a>Abrufen und Festlegen einer Eigenschaft in Visual C#  
 Dieses Codebeispiel zeigt, wie Sie Abrufen der <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Information> Objekt und zum Festlegen der <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> Eigenschaft, um die `ExecuteSql` Mitglied der <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> Enumerationstyp.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Get a property.   
Console.WriteLine(srv.Information.Version);   
//Set a property.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-basic"></a>Festlegen von verschiedenen Eigenschaften vor dem Erstellen eines Objekts in Visual Basic  
 Dieses Codebeispiel zeigt, wie Sie direkt festlegen der <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Table> Objekt und das Erstellen und Hinzufügen von Spalten vor der Erstellung der <xref:Microsoft.SqlServer.Management.Smo.Table> Objekt.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties2](SMO How to#SMO_VBProperties2)]  -->  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-c"></a>Festlegen von verschiedenen Eigenschaften vor dem Erstellen eines Objekts in Visual C#  
 Dieses Codebeispiel zeigt, wie Sie direkt festlegen der <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Table> Objekt und das Erstellen und Hinzufügen von Spalten vor der Erstellung der <xref:Microsoft.SqlServer.Management.Smo.Table> Objekt.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Create a new table in the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
Table tb;   
//Specify the parent database, table schema, and the table name in the constructor.   
tb = new Table(db, "Test_Table", "HumanResources");   
//Add columns because the table requires columns before it can be created.   
Column c1;   
//Specify the parent table, the column name, and data type in the constructor.   
c1 = new Column(tb, "ID", DataType.Int);   
tb.Columns.Add(c1);   
c1.Nullable = false;   
c1.Identity = true;   
c1.IdentityIncrement = 1;   
c1.IdentitySeed = 0;   
Column c2;   
c2 = new Column(tb, "Name", DataType.NVarChar(100));   
c2.Nullable = false;   
tb.Columns.Add(c2);   
tb.AnsiNullsStatus = true;   
//Create the table on the instance of SQL Server.   
tb.Create();   
}  
```  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-basic"></a>Durchlaufen aller Eigenschaften eines Objekts in Visual Basic  
 Dieses Codebeispiel durchläuft die `Properties` Auflistung von der <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> -Objekt und zeigt sie auf die [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Ausgabefenster.  
  
 Im Beispiel die <xref:Microsoft.SqlServer.Management.Smo.Property> Objekt wurde in eckige Klammern gesetzt wurde, da es auch eine [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] Schlüsselwort.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties3](SMO How to#SMO_VBProperties3)]  -->  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-c"></a>Durchlaufen aller Eigenschaften eines Objekts in Visual C#  
 Dieses Codebeispiel durchläuft die `Properties` Auflistung von der <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> -Objekt und zeigt sie auf die [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Ausgabefenster.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Set properties on the uspGetEmployeedManagers stored procedure on the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
StoredProcedure sp;   
sp = db.StoredProcedures("uspGetEmployeeManagers");   
sp.AnsiNullsStatus = false;   
sp.QuotedIdentifierStatus = false;   
//Iterate through the properties of the stored procedure and display.   
  Property p;   
  foreach ( p in sp.Properties) {   
    Console.WriteLine(p.Name + p.Value);   
  }   
}  
```  
  
## <a name="setting-default-initialization-fields-in-visual-basic"></a>Festlegen von Standardinitialisierungsfeldern in Visual Basic  
 In diesem Codebeispiel wird gezeigt, wie die Anzahl der in einem SMO-Programm initialisierten Objekteigenschaften minimiert wird. Sie gehören müssen die `using System.Collections.Specialized`; Anweisung zum Verwenden der <xref:System.Collections.Specialized.StringCollection> Objekt.  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] kann verwendet werden, um die mit dieser Optimierung an die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendeten Zahlenanweisungen zu vergleichen.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaultInitFields1](SMO How to#SMO_VBDefaultInitFields1)]  -->  
  
## <a name="setting-default-initialization-fields-in-visual-c"></a>Festlegen von Standardinitialisierungsfeldern in Visual C#  
 In diesem Codebeispiel wird gezeigt, wie die Anzahl der in einem SMO-Programm initialisierten Objekteigenschaften minimiert wird. Sie gehören müssen die `using System.Collections.Specialized`; Anweisung zum Verwenden der <xref:System.Collections.Specialized.StringCollection> Objekt.  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] kann verwendet werden, um die mit dieser Optimierung an die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendeten Zahlenanweisungen zu vergleichen.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Assign the Table object type to a System.Type object variable.   
Table tb;   
Type typ;   
tb = new Table();   
typ = tb.GetType;   
//Assign the current default initialization fields for the Table object type to a   
//StringCollection object variable.   
StringCollection sc;   
sc = srv.GetDefaultInitFields(typ);   
//Set the default initialization fields for the Table object type to the CreateDate property.   
srv.SetDefaultInitFields(typ, "CreateDate");   
//Retrieve the Schema, Name, and CreateDate properties for every table in AdventureWorks2012.   
   //Note that the improvement in performance can be viewed in SQL Server Profiler.   
foreach ( tb in db.Tables) {   
   Console.WriteLine(tb.Schema + "." + tb.Name + " " + tb.CreateDate);   
}   
//Set the default initialization fields for the Table object type back to the original settings.   
srv.SetDefaultInitFields(typ, sc);   
}  
```  
  
  
