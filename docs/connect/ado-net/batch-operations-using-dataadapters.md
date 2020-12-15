---
title: Batchvorgänge mit DataAdapters
description: In diesem Artikel wird beschrieben, wie Sie die Anwendungsleistung verbessern, indem Sie die Anzahl von Roundtrips zu SQL Server beim Anwenden von Updates aus der DataSet-Klasse reduzieren.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 1b720dff0678c68396fe7d8cf1f60f3ade70dd9d
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772267"
---
# <a name="batch-operations-using-dataadapters"></a>Batchvorgänge mit DataAdapters

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Durch Batch-Unterstützung in ADO.NET kann ein <xref:System.Data.Common.DataAdapter> die Operationen INSERT, UPDATE und DELETE aus einem <xref:System.Data.DataSet> oder einer <xref:System.Data.DataTable> an einen Server zusammenfassen, anstatt nur jeweils eine Operation senden zu können. Durch das Reduzieren der Anzahl von Roundtrips zum Server kann im Allgemeinen die Leistung beträchtlich gesteigert werden. Batchupdates werden für den Microsoft SqlClient-Datenanbieter für SQL Server (<xref:Microsoft.Data.SqlClient>) unterstützt.

Beim Aktualisieren einer Datenbank mit Änderungen aus einem <xref:System.Data.DataSet> wurde die Datenbank in früheren Versionen von ADO.NET mit der `Update`-Methode eines `DataAdapter` zeilenweise aktualisiert. Dabei wurden die Zeilen in der angegebenen <xref:System.Data.DataTable> durchlaufen, wobei jede <xref:System.Data.DataRow> auf Änderungen geprüft wurde. Wenn die Zeile geändert worden war, wurde, abhängig vom Wert der `UpdateCommand`-Eigenschaft für die Zeile, der entsprechende `InsertCommand`, `DeleteCommand` oder <xref:System.Data.DataRow.RowState%2A> aufgerufen. Für jede Zeilenaktualisierung war ein Netzwerkroundtrip zur Datenbank erforderlich.

Im Microsoft SqlClient-Datenanbieter für SQL Server stellt die <xref:Microsoft.Data.SqlClient.SqlDataAdapter>-Klasse eine <xref:Microsoft.Data.SqlClient.SqlDataAdapter.UpdateBatchSize%2A>-Eigenschaft bereit. Wenn die `UpdateBatchSize`-Eigenschaft auf einen positiven ganzzahligen Wert festgelegt wird, werden Updates der Datenbank als Batches mit der angegebenen Größe gesendet. Wenn z. B. für `UpdateBatchSize` der Wert 10 festgelegt wird, bedeutet dies, dass jeweils 10 Anweisungen in einer Gruppe zusammengefasst und zusammen als Batch gesendet werden. Wird dagegen für `UpdateBatchSize` 0 festgelegt, verwendet der <xref:Microsoft.Data.SqlClient.SqlDataAdapter> die größtmöglichen Batches, die der Server unterstützt. Bei einem Wert von 1 werden Batchupdates deaktiviert, weil die Zeilen einzeln nacheinander gesendet werden.

> [!NOTE]
> Die Ausführung eines extrem großen Batches könnte die Leistung verringern. Daher sollten Sie die Einstellung für eine optimale Batchgröße vor der Implementierung Ihrer Anwendung austesten.

## <a name="use-the-updatebatchsize-property"></a>Verwenden der UpdateBatchSize-Eigenschaft

Wenn Batchupdates aktiviert sind, sollte der <xref:System.Data.IDbCommand.UpdatedRowSource%2A>-Eigenschaftswert von `UpdateCommand`, `InsertCommand` und `DeleteCommand` des DataAdapter auf <xref:System.Data.UpdateRowSource.None> oder <xref:System.Data.UpdateRowSource.OutputParameters> festgelegt werden. Beim Update eines Batches sind der <xref:System.Data.IDbCommand.UpdatedRowSource%2A>-Wert und der <xref:System.Data.UpdateRowSource.FirstReturnedRecord>-Wert der <xref:System.Data.UpdateRowSource.Both>-Eigenschaft des Befehls ungültig.
  
In der folgenden Prozedur wird die Verwendung der `UpdateBatchSize`-Eigenschaft veranschaulicht. Die Prozedur akzeptiert zwei Argumente: ein <xref:System.Data.DataSet>-Objekt mit Spalten für die Felder **ProductCategoryID** und **Name** in der **Production.ProductCategory**-Tabelle und eine ganze Zahl, die die Batchgröße (die Anzahl der Zeilen im Batch) darstellt. Der Code erstellt ein neues <xref:Microsoft.Data.SqlClient.SqlDataAdapter>-Objekt und legt dessen Eigenschaften <xref:Microsoft.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:Microsoft.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> und <xref:Microsoft.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> fest. Der Code geht davon aus, dass das <xref:System.Data.DataSet>-Objekt geänderte Zeilen aufweist. Er legt einen Wert für die `UpdateBatchSize`-Eigenschaft fest und führt das Update aus.

[!code-csharp[SqlDataAdapter_Batch#1](~/../sqlclient/doc/samples/SqlDataAdapter_Batch.cs#1)]

## <a name="handle-batch-update-related-events-and-errors"></a>Umgang mit Ereignissen und Fehlern im Zusammenhang mit Batchupdates

Die **DataAdapter**-Klasse verfügt über zwei updaterelevante Ereignisse: **RowUpdating** und **RowUpdated**. Weitere Informationen finden Sie unter [Umgang mit DataAdapter-Ereignissen](handle-dataadapter-events.md).

### <a name="event-behavior-changes-with-batch-updates"></a>Behavior Changes in Bezug auf Ereignisse bei Batchupdates

Bei aktivierter Batchverarbeitung werden mehrere Zeilen in einer einzigen Datenbankoperation aktualisiert. Deshalb findet pro Batch nur ein `RowUpdated`-Ereignis statt, wohingegen das `RowUpdating`-Ereignis für jede verarbeitete Zeile auftritt. Bei deaktivierter Batchverarbeitung werden die beiden Ereignisse mit Einzelverschachtelung ausgelöst, wobei für jede Zeile zunächst ein `RowUpdating`-Ereignis und dann ein `RowUpdated`-Ereignis ausgelöst wird. Diese Abfolge der Auslösung von `RowUpdating`-Ereignissen und `RowUpdated`-Ereignissen setzt sich so lange fort, bis alle Zeilen verarbeitet wurden.

### <a name="access-updated-rows"></a>Zugreifen auf aktualisierte Zeilen

Bei deaktivierter Batchverarbeitung kann auf die zu aktualisierende Zeile mit der <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A>-Eigenschaft der <xref:System.Data.Common.RowUpdatedEventArgs>-Klasse zugegriffen werden.

Bei aktivierter Batchverarbeitung wird für mehrere Zeilen ein einziges `RowUpdated`-Ereignis generiert. Daher ist der Wert der `Row`-Eigenschaft  in jeder Zeile NULL. Es werden weiterhin `RowUpdating`-Ereignisse für jede Zeile generiert. Mit der <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>-Methode der <xref:System.Data.Common.RowUpdatedEventArgs>-Klasse können Sie auf die verarbeiteten Zeilen zugreifen, indem Sie Verweise auf die Zeilen in ein Array kopieren. Wenn keine Zeilen verarbeitet werden, löst `CopyToRows` eine <xref:System.ArgumentNullException> aus. Verwenden Sie die <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A>-Eigenschaft, um vor dem Aufruf der <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>-Methode die Anzahl der verarbeiteten Zeilen zurückzugeben.

### <a name="handle-data-errors"></a>Behandlung von Datenfehlern

Eine Batchausführung hat dieselben Auswirkungen wie die Ausführung einzelner Anweisungen. Anweisungen werden in der Reihenfolge ausgeführt, in der sie dem Batch hinzugefügt wurden. Fehler werden im Batchmodus in derselben Weise behandelt wie bei deaktiviertem Batchmodus. Jede Zeile wird einzeln verarbeitet. Nur Zeilen, die erfolgreich in der Datenbank verarbeitet wurden, werden in der entsprechenden <xref:System.Data.DataRow> innerhalb der <xref:System.Data.DataTable> aktualisiert.

> [!NOTE]
> Der Microsoft SqlClient-Datenanbieter für SQL Server und der Back-End-Datenbankserver bestimmen, welche SQL-Konstrukte für die Batchausführung unterstützt werden. Wenn eine nicht unterstützte Anweisung ausgeführt werden soll, wird möglicherweise eine Ausnahme ausgelöst.

## <a name="see-also"></a>Weitere Informationen

- ["DataAdapters" und "DataReaders"](dataadapters-datareaders.md)
- [Aktualisieren von Datenquellen mit DataAdapters](update-data-sources-with-dataadapters.md)
- [Verarbeiten von DataAdapter-Ereignissen](handle-dataadapter-events.md)
- [Microsoft ADO.NET für SQL Server](microsoft-ado-net-sql-server.md)
