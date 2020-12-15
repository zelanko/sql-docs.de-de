---
title: Hinzufügen von vorhandenen Einschränkungen zu einem DataSet
description: In diesem Artikel wird beschrieben, wie Sie einer DataSet-Klasse vorhandene Einschränkungen hinzufügen.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 9471f62c36604cb01ea78f558ac3bfbcb7f4bc01
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772273"
---
# <a name="add-existing-constraints-to-a-dataset"></a>Hinzufügen von vorhandenen Einschränkungen zu einem DataSet

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Die <xref:System.Data.Common.DbDataAdapter.Fill%2A>-Methode der <xref:Microsoft.Data.SqlClient.SqlDataAdapter>-Klasse füllt eine <xref:System.Data.DataSet>-Klasse nur mit Tabellenspalten und -zeilen aus einer Datenquelle. Einschränkungen werden zwar häufig durch die Datenquelle festgelegt, die **Fill**-Methode fügt diese Schemainformationen jedoch nicht standardmäßig der **DataSet**-Klasse hinzu.

Wenn Sie Informationen zu vorhandenen Primärschlüsseleinschränkungen aus einer Datenquelle in eine **DataSet**-Klasse übernehmen möchten, können Sie vor dem Aufrufen der **Fill**-Methode entweder die <xref:System.Data.Common.DbDataAdapter.FillSchema%2A>-Methode der **DataAdapter**-Klasse aufrufen oder die <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A>-Eigenschaft der **DataAdapter**-Klasse auf **AddWithKey** festlegen. Dadurch wird sichergestellt, dass die Primärschlüsseleinschränkungen in der **DataSet**-Klasse denen in der Datenquelle entsprechen.

> [!NOTE]
> Informationen zu Fremdschlüsseleinschränkungen sind nicht enthalten und müssen explizit erstellt werden.

Wenn Sie einer **DataSet**-Klasse vor dem Füllen mit Daten Schemainformationen hinzufügen, wird sichergestellt, dass Primärschlüsseleinschränkungen in den <xref:System.Data.DataTable>-Objekten in der **DataSet**-Klasse enthalten sind. Folglich werden die Primärschlüsselspalteninformationen bei weiteren Aufrufen zum Füllen der **DataSet**-Klasse zum Abgleich neuer Zeilen aus der Datenquelle mit den aktuellen Zeilen in allen **DataTable**-Klassen verwendet, und die aktuellen Daten in den Tabellen werden mit Daten aus der Datenquelle überschrieben. Ohne die Schemainformationen werden die neuen Zeilen aus der Datenquelle an die **DataSet**-Klasse angefügt, was zu doppelten Zeilen führt.

> [!NOTE]
> Wenn in einer Datenquelle eine Spalte mit automatischer Inkrementierung ermittelt wird, erstellt die <xref:System.Data.Common.DbDataAdapter.FillSchema%2A>-Methode oder die <xref:System.Data.Common.DbDataAdapter.Fill%2A>-Methode mit dem Wert **AddWithKey** für die <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A>-Eigenschaft eine **DataColumn**-Klasse, deren **AutoIncrement**-Eigenschaft auf `true` festgelegt ist. Die Werte für **AutoIncrementStep** und **AutoIncrementSeed** müssen Sie jedoch selbst festlegen.

> [!NOTE]
> Wenn Sie die **FillSchema**-Methode verwenden oder die **MissingSchemaAction**-Eigenschaft auf **AddWithKey** festlegen, sind zum Ermitteln von Informationen zur Primärschlüsselspalte zusätzliche Verarbeitungsschritte in der Datenquelle erforderlich. Diese zusätzlichen Verarbeitungsschritte können zu einem Leistungsabfall führen. Wenn Sie die Primärschlüsselinformationen zur Entwurfszeit kennen, empfiehlt es sich, zum Erzielen einer optimalen Leistung die Primärschlüsselspalte(n) explizit in der richtigen Reihenfolge anzugeben.

Im folgenden Codebeispiel wird gezeigt, wie Sie einer **DataSet**-Klasse mit <xref:System.Data.Common.DbDataAdapter.FillSchema%2A> Schemainformationen hinzufügen:

[!code-csharp[SqlDataAdapter_FillDataSet#1](~/../sqlclient/doc/samples/SqlDataAdapter_FillDataSet.cs#1)]

Im folgenden Codebeispiel wird gezeigt, wie Sie einer **DataSet**-Klasse mit der <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A>-Eigenschaft und der <xref:System.Data.Common.DbDataAdapter.Fill%2A>-Methode Schemainformationen hinzufügen:

[!code-csharp[SqlDataAdapter_FillDataSet#2](~/../sqlclient/doc/samples/SqlDataAdapter_FillDataSet.cs#2)]

## <a name="handling-multiple-result-sets"></a>Umgang mit mehreren Resultsets

Wenn die **DataAdapter**-Klasse feststellt, dass mehrere Resultsets von der <xref:Microsoft.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>-Eigenschaft zurückgegeben werden, erstellt sie mehrere Tabellen in der **DataSet**-Klasse. Diesen Tabellen werden Standardnamen nach dem Muster **Table***N* zugewiesen, beginnend bei 0, allerdings mit **Table** statt Table0. Wenn ein Tabellenname als Argument an die <xref:System.Data.Common.DbDataAdapter.FillSchema%2A>-Methode übergeben wird, erhalten die Tabellen Namen nach dem Muster **TableName***N*, beginnend bei 0, allerdings mit **TableName** statt TableName0.

## <a name="see-also"></a>Weitere Informationen

- ["DataAdapters" und "DataReaders"](dataadapters-datareaders.md)
- [Abrufen und Ändern von Daten in ADO.NET](retrieving-modifying-data.md)
- [Microsoft ADO.NET für SQL Server](microsoft-ado-net-sql-server.md)
