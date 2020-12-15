---
title: DataAdapter-, DataTable-und DataColumn-Zuordnungen
description: In diesem Artikel wird das Einrichten von DataTableMappings und ColumnMappings für eine DataAdapter-Klasse beschrieben.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: e8b2f84fbbf888fc67cdb8f945d7f0c887c14eaa
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772256"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter-, DataTable-und DataColumn-Zuordnungen

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Eine <xref:Microsoft.Data.SqlClient.SqlDataAdapter>-Klasse enthält eine Sammlung von 0 (null) oder mehr <xref:System.Data.Common.DataTableMapping>-Objekten in der zugehörigen <xref:System.Data.Common.DataAdapter.TableMappings%2A>-Eigenschaft. Eine **DataTableMapping**-Klasse stellt eine Hauptzuordnung zwischen den bei einer Abfrage einer Datenquelle zurückgegebenen Daten und einer <xref:System.Data.DataTable>-Klasse bereit. Der **DataTableMapping**-Name kann anstelle des **DataTable**-Namens an die <xref:System.Data.Common.DbDataAdapter.Fill%2A>-Methode der **DataAdapter**-Klasse übergeben werden. Im folgenden Beispiel wird eine **DataTableMapping**-Klasse mit dem Namen **AuthorsMapping** für die Tabelle **Authors** erstellt.

```csharp
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");
```

Mit einer **DataTableMapping**-Klasse können Sie in einer **DataTable**-Klasse andere Spaltennamen als in der Datenbank verwenden. Die **DataAdapter**-Klasse gleicht beim Aktualisieren der Tabelle mithilfe der Zuordnung die Spalten miteinander ab.

> [!NOTE]
> Wenn Sie beim Aufrufen der **Fill**-Methode oder der **Update**-Methode der **DataAdapter**-Klasse die **TableName**-Eigenschaft oder den **DataTableMapping**-Namen nicht angeben, sucht die **DataAdapter**-Klasse nach einer **DataTableMapping**-Klasse mit dem Namen Table. Wenn diese **DataTableMapping**-Klasse nicht vorhanden ist, lautet der Wert für die **TableName**-Eigenschaft für die **DataTable**-Klasse Table. Sie können eine Standard-**DataTableMapping**-Klasse angeben, indem Sie eine **DataTableMapping**-Klasse mit dem Namen Table erstellen.

Im folgenden Codebeispiel wird eine **DataTableMapping**-Klasse (aus dem <xref:System.Data.Common>-Namespace) erstellt und zur Standardzuordnung für die angegebene **DataAdapter**-Klasse gemacht, indem sie Table genannt wird. Das Beispiel ordnet anschließend die Spalten in der ersten Tabelle des Abfrageergebnisses (die **Customers**-Tabelle der **Northwind**-Datenbank) einer Gruppe benutzerfreundlicherer Namen in der **Northwind Customers**-Tabelle in der <xref:System.Data.DataSet>-Klasse zu. Für Spalten, die nicht zugeordnet werden, wird der Name der Spalte in der Datenquelle verwendet.

[!code-csharp[SqlDataAdapter_TableMappings#1](~/../sqlclient/doc/samples/SqlDataAdapter_TableMappings.cs#1)]

In komplexeren Situationen möchten Sie möglicherweise mit dieser **DataAdapter**-Klasse das Laden verschiedener Tabellen mit verschiedenen Zuordnungen unterstützen. Fügen Sie hierfür weitere **DataTableMapping**-Objekte hinzu.

Wenn der **Fill**-Methode eine Instanz einer **DataSet**-Klasse und ein **DataTableMapping**-Name übergeben werden, wird die Zuordnung mit diesem Namen verwendet, sofern vorhanden. Andernfalls wird eine **DataTable**-Klasse mit diesem Namen verwendet.

Im folgenden Beispiel werden eine **DataTableMapping**-Klasse mit dem Namen **Customers** und eine **DataTable**-Klasse mit dem Namen **BizTalkSchema** erstellt. Anschließend werden die von der SELECT-Anweisung zurückgegebenen Zeilen der **DataTable**-Klasse **BizTalkSchema** zugeordnet.

[!code-csharp[SqlDataAdapter_TableMappings#2](~/../sqlclient/doc/samples/SqlDataAdapter_TableMappings.cs#2)]

> [!NOTE]
> Wenn für eine Spaltenzuordnung kein Quellspaltenname bereitgestellt wird, werden automatisch Standardnamen generiert. Wenn keine Quellspalte für eine Spaltenzuordnung angegeben ist, so erhält die Spaltenzuordnung einen Standardnamen nach dem Muster **SourceColumn***N*, beginnend mit **SourceColumn1**.

> [!NOTE]
> Wenn für eine Tabellenzuordnung kein Quelltabellenname bereitgestellt wird, werden automatisch Standardnamen generiert. Wenn kein Quelltabellenname für eine Tabellenzuordnung angegeben ist, so erhält die Tabellenzuordnung einen Standardnamen nach dem Muster **SourceTable***N*, beginnend mit **SourceTable1**.

> [!NOTE]
> Es wird davon abgeraten, die Benennungskonvention **SourceColumn***N* für eine Spaltenzuordnung oder **SourceTable***N* für eine Tabellenzuordnung zu verwenden, da der von Ihnen vergebene Name möglicherweise einen Konflikt mit einem bereits vorhandenen Standard-Spaltenzuordnungsnamen in der **ColumnMappingCollection**-Klasse oder Standard-Tabellenzuordnungsnamen in der **DataTableMappingCollection**-Klasse verursacht. Wenn der angegebene Name bereits vorhanden ist, wird eine Ausnahme ausgelöst.

## <a name="handle-multiple-result-sets"></a>Umgang mit mehreren Resultsets

Wenn **SelectCommand** mehrere Tabellen zurückgibt, generiert die **Fill**-Methode automatisch Tabellennamen mit inkrementellen Werten für die Tabellen in der **DataSet**-Klasse. Der angegebene Tabellenname kommt zuerst, und die folgenden Tabellen werden nach dem Muster **TableName***N* benannt, beginnend mit **TableName1**. Mit Tabellenzuordnungen können Sie den automatisch generierten Tabellennamen einem Namen zuordnen, der für die Tabelle in der **DataSet**-Klasse angegeben werden soll. Rufen Sie beispielsweise für ein **SelectCommand**-Objekt, das die beiden Tabellen **Customers** und **Orders** zurückgibt, die **Fill**-Methode folgendermaßen auf.

```csharp
adapter.Fill(customersDataSet, "Customers");
```

In der **DataSet**-Klasse werden zwei Tabellen erstellt: **Customers** und **Customers1**. Mit Tabellenzuordnungen können Sie sicherstellen, dass die zweite Tabelle den Namen **Orders** und nicht **Customers1** erhält. Hierfür ordnen Sie der Quelltabelle von **Customers1** die **DataSet**-Tabelle **Orders** zu, wie im folgenden Beispiel zu sehen.

[!code-csharp[SqlDataAdapter_TableMappings#3](~/../sqlclient/doc/samples/SqlDataAdapter_TableMappings.cs#3)]

## <a name="see-also"></a>Weitere Informationen

- ["DataAdapters" und "DataReaders"](dataadapters-datareaders.md)
- [Abrufen und Ändern von Daten in ADO.NET](retrieving-modifying-data.md)
- [Microsoft ADO.NET für SQL Server](microsoft-ado-net-sql-server.md)
