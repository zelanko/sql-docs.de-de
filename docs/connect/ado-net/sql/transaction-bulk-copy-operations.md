---
title: Transaktionen und Massenkopiervorgänge
description: Beschreibt, wie ein Massen Kopiervorgang innerhalb einer Transaktion ausgeführt wird, einschließlich des Commits oder Rollbacks der Transaktion.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: c2e855407edd6b2af51ae5710cd6601e9aa25654
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451917"
---
# <a name="transaction-and-bulk-copy-operations"></a>Transaktionen und Massenkopiervorgänge

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Massenkopiervorgänge können als isolierte Vorgänge oder im Rahmen einer aus mehreren Schritten bestehenden Transaktion ausgeführt werden. Diese zweite Option ermöglicht Ihnen das Ausführen mehrerer Massenkopiervorgänge innerhalb der gleichen Transaktion sowie die Durchführung weiterer Datenbankvorgänge (wie etwa Einfüge-, Aktualisierungs- und Löschvorgänge), während die Möglichkeit zum Commit oder Rollback der gesamten Transaktion erhalten bleibt.  
  
Standardmäßig wird ein Massenkopiervorgang als isolierter Vorgang ausgeführt. Der Massenkopiervorgang erfolgt nicht transaktional, ohne Möglichkeit zum Rollback. Wenn Sie beim Auftreten eines Fehlers einen Rollback für den gesamten Massenkopiervorgang oder einen Teil davon ausführen müssen, können Sie eine von <xref:Microsoft.Data.SqlClient.SqlBulkCopy> verwaltete Transaktion verwenden, den Massenkopiervorgang in einer bestehenden Transaktion durchführen oder den Massenkopiervorgang in **System.Transactions**<xref:System.Transactions.Transaction> auflisten.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Ausführen eines nicht transaktionalen Massenkopiervorgangs  
Die folgende Konsolenanwendung zeigt, was geschieht, wenn bei einem nicht transaktionalen Massenkopiervorgang nach teilweiser Ausführung ein Fehler auftritt.  
  
Im Beispiel enthalten Quell- und Zieltabelle jeweils eine `Identity`-Spalte namens **ProductID**. Der Code bereitet zunächst die Zieltabelle vor, indem er alle Zeilen löscht und dann eine einzelne Zeile einfügt, deren **ProductID** bekanntermaßen in der Quelltabelle vorhanden ist. Standardmäßig wird für die Spalte `Identity` in der Zieltabelle für jede hinzugefügte Zeile ein neuer Wert generiert. In diesem Beispiel wird beim Öffnen der Verbindung eine Option festgelegt, die den Massenladevorgang zwingt, stattdessen die `Identity`-Werte aus der Quelltabelle zu verwenden.  
  
Der Massenkopiervorgang wird mit dem Wert „10“ für die Eigenschaft <xref:Microsoft.Data.SqlClient.SqlBulkCopy.BatchSize%2A> ausgeführt. Wenn der Vorgang auf die ungültige Zeile trifft, wird eine Ausnahme ausgelöst. In diesem ersten Beispiel ist der Massenkopiervorgang nicht transaktional. Für alle bis zum Auftreten des Fehlers kopierten Batches wird ein Commit ausgeführt; für den Batch, der den doppelten Schlüssel enthält, wird ein Rollback ausgeführt, und der Massenkopiervorgang wird vor dem Verarbeiten weiterer Batches angehalten.  
  
> [!NOTE]
>  Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Massenkopierbeispiel-Einrichtung](bulk-copy-example-setup.md) beschrieben erstellt haben. Der angegebene Code dient nur zur Demonstration der Syntax für die Verwendung von **SqlBulkCopy**. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung `INSERT … SELECT` zum Kopieren der Daten einfacher und schneller.  
  
[!code-csharp[DataWorks SqlBulkCopyOpeions_Default#1](~/../sqlclient/doc/samples/SqlBulkCopyOptions_Default.cs#1)]
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Ausführen eines dedizierten Massenkopiervorgangs in einer Transaktion  
Standardmäßig stellt ein Massenkopiervorgang seine eigene Transaktion dar. Wenn Sie einen dedizierten Massen Kopiervorgang ausführen möchten, erstellen Sie eine neue Instanz von <xref:Microsoft.Data.SqlClient.SqlBulkCopy> mit einer Verbindungs Zeichenfolge, oder verwenden Sie ein vorhandenes <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekt ohne aktive Transaktion. In jedem Szenario erstellt der Massenkopiervorgang die Transaktion, für die er dann einen Commit oder einen Rollback ausführt.  
  
Sie können explizit die Option <xref:Microsoft.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> im Klassenkonstruktor <xref:Microsoft.Data.SqlClient.SqlBulkCopy> angeben, um explizit die Ausführung eines Massenkopiervorgangs innerhalb einer eigenen Transaktion zu veranlassen, was dazu führt, dass jeder Batch des Massenkopiervorgangs in einer eigenen Transaktion ausgeführt wird.  
  
> [!NOTE]
>  Da verschiedene Batches in verschiedenen Transaktionen ausgeführt werden, wird für alle Zeilen im aktuellen Batch beim Auftreten eines Fehlers ein Rollback ausgeführt, die Zeilen aus vorhergehenden Batches verbleiben jedoch in der Datenbank.  
  
Die folgende Konsolenanwendung ähnelt dem vorhergehenden Beispiel, mit einer Ausnahme: In diesem Beispiel verwaltet der Massenkopiervorgang seine eigenen Transaktionen. Für alle bis zum Auftreten des Fehlers kopierten Batches wird ein Commit ausgeführt; für den Batch, der den doppelten Schlüssel enthält, wird ein Rollback ausgeführt, und der Massenkopiervorgang wird vor dem Verarbeiten weiterer Batches angehalten.  
  
> [!IMPORTANT]
>  Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Massenkopierbeispiel-Einrichtung](bulk-copy-example-setup.md) beschrieben erstellt haben. Der angegebene Code dient nur zur Demonstration der Syntax für die Verwendung von **SqlBulkCopy**. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung `INSERT … SELECT` zum Kopieren der Daten einfacher und schneller.  
  
[!code-csharp[DataWorks SqlBulkCopyOptions_UseInternalTransaction#1](~/../sqlclient/doc/samples/SqlBulkCopyOptions_UseInternalTransaction.cs#1)]
  
## <a name="using-existing-transactions"></a>Verwenden vorhandener Transaktionen  
Sie können ein vorhandenes <xref:Microsoft.Data.SqlClient.SqlTransaction>-Objekt als Parameter in einem <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Konstruktor angeben. In dieser Situation wird der Massenkopiervorgang in einer vorhandenen Transaktion ausgeführt, und es tritt keine Änderung am Transaktionsstatus ein (d. h. für sie wird weder ein Commit noch ein Abbruch ausgeführt). Dies macht es möglich, dass Anwendungen den Massenkopiervorgang zusammen mit anderen Datenbankvorgängen in einer Transaktion einschließen. Wenn Sie jedoch kein <xref:Microsoft.Data.SqlClient.SqlTransaction> Objekt angeben und einen NULL-Verweis übergeben und die Verbindung über eine aktive Transaktion verfügt, wird eine Ausnahme ausgelöst.  
  
Wenn Sie einen Rollback für den gesamten Massen Kopiervorgang ausführen müssen, weil ein Fehler auftritt, oder wenn der Massen Kopiervorgang als Teil eines größeren Prozesses ausgeführt werden soll, für den ein Rollback ausgeführt werden kann, können Sie ein <xref:Microsoft.Data.SqlClient.SqlTransaction> Objekt für den <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Konstruktor bereitstellen.  
  
Die folgende Konsolenanwendung ähnelt dem ersten (nicht transaktionalen) Beispiel, mit einer Ausnahme: in diesem Beispiel ist der Massenkopiervorgang in einer größeren, externen Transaktion enthalten. Wenn der Fehler aufgrund des Primärschlüsselverstoßes auftritt, wird ein Rollback der gesamten Transaktion ausgeführt, und der Zieltabelle werden keine Zeilen hinzugefügt.  
  
> [!IMPORTANT]
>  Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Massenkopierbeispiel-Einrichtung](bulk-copy-example-setup.md) beschrieben erstellt haben. Der angegebene Code dient nur zur Demonstration der Syntax für die Verwendung von **SqlBulkCopy**. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung `INSERT … SELECT` zum Kopieren der Daten einfacher und schneller.  
  
[!code-csharp[DataWorks SqlBulkCopy_ExternalTransaction#1](~/../sqlclient/doc/samples/SqlBulkCopy_ExternalTransaction.cs#1)]
  
## <a name="next-steps"></a>Nächste Schritte
- [Massenkopiervorgänge in SQL Server](bulk-copy-operations-sql-server.md)
