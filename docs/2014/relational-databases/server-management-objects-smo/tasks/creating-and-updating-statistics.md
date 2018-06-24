---
title: Erstellen und Aktualisieren von Statistiken | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- statistical information [SMO]
ms.assetid: 47a0a172-a969-4deb-bca9-dd04401a0fe1
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6717d724b7edbf7185e631bca06dc6b2a9d01611
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050729"
---
# <a name="creating-and-updating-statistics"></a>Erstellen und Aktualisieren von Statistiken
  In SMO können statistische Informationen über die Verarbeitung von Abfragen in der Datenbank mithilfe des  <xref:Microsoft.SqlServer.Management.Smo.Statistic>-Objekts gesammelt werden.  
  
 Es ist möglich, zum Erstellen von Statistiken für eine Spalte mit dem <xref:Microsoft.SqlServer.Management.Smo.Statistic> und <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> Objekt. Die <xref:Microsoft.SqlServer.Management.Smo.Statistic.Update%2A>-Methode kann ausgeführt werden, um die Statistik im <xref:Microsoft.SqlServer.Management.Smo.Statistic>-Objekt zu aktualisieren. Die Ergebnisse können im Abfrageoptimierer angezeigt werden.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-and-update-statistics-in-visual-basic"></a>Erstellen und Aktualisieren von Statistiken in Visual Basic  
 Dieses Codebeispiel erstellt eine neue Tabelle für eine vorhandene Datenbank, für die die <xref:Microsoft.SqlServer.Management.Smo.Statistic> Objekt und die <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> Objekt erstellt werden.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStatistics1](SMO How to#SMO_VBStatistics1)]  -->  
  
## <a name="creating-and-update-statistics-in-visual-c"></a>Erstellen und Aktualisieren von Statistiken in Visual C#  
 Dieses Codebeispiel erstellt eine neue Tabelle für eine vorhandene Datenbank, für die die <xref:Microsoft.SqlServer.Management.Smo.Statistic> Objekt und die <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> Objekt erstellt werden.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Reference the CreditCard table.   
  
           Table tb = db.Tables["CreditCard", "Sales"];  
            //Define a Statistic object by supplying the parent table and name   
            //arguments in the constructor.   
            Statistic stat = default(Statistic);  
            stat = new Statistic(tb, "Test_Statistics");  
            //Define a StatisticColumn object variable for the CardType column   
            //and add to the Statistic object variable.   
            StatisticColumn statcol = default(StatisticColumn);  
            statcol = new StatisticColumn(stat, "CardType");  
            stat.StatisticColumns.Add(statcol);  
            //Create the statistic counter on the instance of SQL Server.   
            stat.Create();  
        }  
```  
  
## <a name="creating-and-update-statistics-in-powershell"></a>Erstellen und Aktualisieren von Statistiken in PowerShell  
 Dieses Codebeispiel erstellt eine neue Tabelle für eine vorhandene Datenbank, für die die <xref:Microsoft.SqlServer.Management.Smo.Statistic> Objekt und die <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> Objekt erstellt werden.  
  
```  
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
CD AdventureWorks2012\tables  
  
#Get a reference to the table  
$tb = get-item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -argumentlist $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -argumentlist $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index   
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -argumentlist $fti, "Name"  
  
# Add the indexed column to the index.  
$fti.IndexedColumns.Add($ftic)  
  
# Set change tracking  
$fti.ChangeTracking = [Microsoft.SqlServer.Management.SMO.ChangeTracking]::Automatic  
  
# Specify the unique index on the table that is required by the Full Text Search index.  
$fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
# Specify the catalog associated with the index.  
$fti.CatalogName = "Test_Catalog2"  
  
# Create the Full Text Search Index  
$fti.Create()  
```  
  
  