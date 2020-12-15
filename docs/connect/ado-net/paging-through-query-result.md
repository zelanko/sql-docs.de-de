---
title: Paging durch ein Abfrageergebnis
description: Enthält ein Beispiel für das Anzeigen der Ergebnisse einer Abfrage als Datenseiten.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 2de305e1069964f2d1a67b7f201578c7448d3e09
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772216"
---
# <a name="paging-through-a-query-result"></a>Paging durch ein Abfrageergebnis

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Beim Paging durch ein Abfrageergebnis werden die Ergebnisse einer Abfrage in kleineren Untergruppen von Daten oder Seiten zurückgegeben. Dies ist eine allgemein übliche Vorgehensweise, um einem Benutzer Ergebnisse in kleinen Blöcken anzuzeigen, die sich leicht verwalten lassen.

Die <xref:Microsoft.Data.SqlClient.SqlDataAdapter>-Klasse stellt eine Funktion bereit, mit der durch Überladungen der <xref:System.Data.Common.DbDataAdapter.Fill%2A>-Methode nur eine Seite mit Daten zurückgegeben wird. Dies ist jedoch möglicherweise nicht die beste Methode zum Einteilen umfangreicher Abfrageergebnisse in Seiten. Dies liegt daran, dass weiterhin die Ressourcen zum Zurückgeben der gesamten Abfrage verwendet werden, auch wenn die **DataAdapter**-Klasse das Ziel <xref:System.Data.DataTable> oder <xref:System.Data.DataSet> nur mit den angeforderten Datensätzen füllt.

Geben Sie zusätzliche Kriterien für Ihre Abfrage ein, um eine Seite mit Daten von einer Datenquelle ohne die Ressourcen zurückzugeben, die zum Zurückgeben der gesamten Abfrage erforderlich sind, sodass nur die erforderlichen Zeilen zurückgegeben werden.

Wenn Sie die <xref:System.Data.Common.DbDataAdapter.Fill%2A>-Methode zum Zurückgeben einer Seite mit Daten verwenden möchten, legen Sie für den ersten Datensatz auf der Datenseite einen **startRecord**-Parameter fest und für die Anzahl von Datensätzen auf der Datenseite einen **maxRecords**-Parameter.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird gezeigt, wie mit der <xref:System.Data.Common.DbDataAdapter.Fill%2A>-Methode die erste Seite mit fünf Datensätzen eines Abfrageergebnisses zurückgegeben wird.

[!code-csharp[SqlDataAdapter_Paging#1](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#1)]

Im vorherigen Beispiel wird die **DataSet**-Klasse nur mit fünf Datensätzen gefüllt, aber die gesamte **Orders**-Tabelle zurückgegeben. Verwenden Sie die Klauseln `TOP` und `WHERE` in Ihrer SQL-Anweisung wie im folgenden Codebeispiel gezeigt, um die **DataSet**-Klasse mit diesen fünf Datensätzen zu füllen, aber nur fünf Datensätze zurückzugeben.

[!code-csharp[SqlDataAdapter_Paging#2](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#2)]

> [!NOTE]
> Wenn Sie die Abfrageergebnisse auf diese Weise in Seiten einteilen, müssen Sie den eindeutigen Bezeichner, mit dem die Zeilen sortiert werden, beibehalten, um die eindeutige ID an den Befehl zu übergeben, um die nächste Seite mit Datensätzen zurückzugeben, wie im folgenden Codebeispiel gezeigt.

[!code-csharp[SqlDataAdapter_Paging#4](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#4)]

Wenn Sie die nächste Seite mit Datensätzen durch Überladen der **Fill**-Methode mit den Parametern **startRecord** und **maxRecords** zurückgeben möchten, müssen Sie den aktuellen Datensatzindex um die Seitengröße erhöhen und die Tabelle füllen.

> [!NOTE]
> Denken Sie daran, dass der Datenbankserver alle Abfrageergebnisse zurückgibt, auch wenn nur eine Seite mit Datensätzen zur **DataSet**-Klasse hinzugefügt wird.

Im folgenden Codebeispiel wird der Inhalt der Tabellenzeilen gelöscht, bevor sie mit der nächsten Seite mit Daten gefüllt werden. Möglicherweise soll eine bestimmte Anzahl zurückgegebener Zeilen in einem lokalen Cache beibehalten werden, um die Anzahl der Schleifen zum Datenbankserver zu reduzieren.

[!code-csharp[SqlDataAdapter_Paging#3](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#3)]

Geben Sie restriktive Kriterien für die SQL-Anweisung SELECT an, um die nächste Seite mit Datensätzen zurückzugeben, ohne dass der Datenbankserver die gesamte Abfrage zurückgeben muss. Da im vorhergehenden Beispiel der zuletzt zurückgegebene Datensatz beibehalten wurde, können Sie ihn in der WHERE-Klausel verwenden, um – wie im folgenden Codebeispiel gezeigt – einen Ausgangspunkt für die Abfrage anzugeben.

[!code-csharp[SqlDataAdapter_Paging#5](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#5)]

## <a name="see-also"></a>Weitere Informationen

- ["DataAdapters" und "DataReaders"](dataadapters-datareaders.md)
- [Microsoft ADO.NET für SQL Server](microsoft-ado-net-sql-server.md)
