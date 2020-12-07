---
title: Verwenden von Massenkopieren mit dem JDBC Driver
description: Mit der SQLServerBulkCopy-Klasse können Sie Datenladelösungen in Java schreiben, die gegenüber den standardmäßigen JDBC-APIs bedeutende Leistungsvorteile bieten.
ms.custom: ''
ms.date: 08/24/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 21e19635-340d-49bb-b39d-4867102fb5df
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 52f465b4cfdcb2ff771a71c1ef956af78b522358
ms.sourcegitcommit: 0c0e4ab90655dde3e34ebc08487493e621f25dda
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96442881"
---
# <a name="using-bulk-copy-with-the-jdbc-driver"></a>Verwenden von Massenkopieren mit dem JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft SQL Server enthält ein beliebtes Befehlszeilenhilfsprogramm namens `bcp` zum schnellen Massenkopieren großer Dateien in Tabellen oder Ansichten in SQL Server-Datenbanken. Die `SQLServerBulkCopy`-Klasse ermöglicht Ihnen das Schreiben von Codelösungen in Java, die eine ähnliche Funktionalität bereitstellen. Es gibt eine Reihe weiterer Verfahren, Daten in eine SQL-Server-Tabelle zu laden (beispielsweise INSERT-Anweisungen), doch bietet `SQLServerBulkCopy` ihnen gegenüber einen erheblichen Leistungsvorteil.  
  
Die `SQLServerBulkCopy`-Klasse kann nur zum Schreiben von Daten in SQL Server-Tabellen verwendet werden. Die Datenquelle ist aber nicht auf SQL Server beschränkt. Jede beliebige Datenquelle kann verwendet werden, sofern die Daten mit einer Implementierung von `ResultSet`, `RowSet` oder `ISQLServerBulkRecord` gelesen werden können.  
  
Die `SQLServerBulkCopy`-Klasse bietet folgende Möglichkeiten:  
  
- Einen einzelnen Massenkopiervorgang  
  
- Mehrere Massenkopiervorgänge  
  
- Einen Massenkopiervorgang mit einer Transaktion  
  
> [!NOTE]  
> Wenn Sie den Microsoft JDBC-Treiber 4.1 für SQL Server (der die SQLServerBulkCopy-Klasse nicht unterstützt) oder eine frühere Version verwenden, können Sie stattdessen die SQL Server Transact-SQL-Anweisung „BULK INSERT“ ausführen.  
  
## <a name="bulk-copy-example-setup"></a>Einrichten des Massenkopierbeispiels  

Die `SQLServerBulkCopy`-Klasse kann nur zum Schreiben von Daten in SQL Server-Tabellen verwendet werden. Die in diesem Artikel gezeigten Codebeispiele verwenden die SQL Server-Beispieldatenbank [AdventureWorks](../../samples/adventureworks-install-configure.md). Schreiben Sie Daten in zuvor von Ihnen erstellte Tabellen, um eine Änderung der vorhandenen Tabellen in den Codebeispielen zu vermeiden.  
  
Die Tabellen `BulkCopyDemoMatchingColumns` und `BulkCopyDemoDifferentColumns` basieren beide auf der AdventureWorks-Tabelle `Production.Products`. In Codebeispielen, die diese Tabellen verwenden, werden Daten aus der Tabelle `Production.Products` einer dieser Beispieltabellen hinzugefügt. Die Tabelle `BulkCopyDemoDifferentColumns` wird verwendet, um im Beispiel zu veranschaulichen, wie Spalten aus den Quelldaten der Zieltabelle zugeordnet werden. Für die meisten anderen Beispiele wird `BulkCopyDemoMatchingColumns` verwendet.  
  
Einige der Codebeispiele zeigen, wie eine Klasse `SQLServerBulkCopy` zum Schreiben in mehrere Tabellen verwendet werden kann. In diesen Beispielen werden die Tabellen `BulkCopyDemoOrderHeader` und `BulkCopyDemoOrderDetail` als Zieltabellen verwendet. Diese Tabellen basieren auf den Tabellen `Sales.SalesOrderHeader` und `Sales.SalesOrderDetail` in AdventureWorks.  
  
> [!NOTE]  
> Die `SQLServerBulkCopy`-Codebeispiele dienen ausschließlich der Veranschaulichung der für `SQLServerBulkCopy` verwendeten Syntax. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT …“ einfacher und schneller. SELECT“ zum Kopieren der Daten einfacher und schneller.  

### <a name="table-setup"></a>Tabelleneinrichtung  

Zum Erstellen der Tabellen, die für die ordnungsgemäße Ausführung der Codebeispiele erforderlich sind, müssen Sie die folgenden Transact-SQL-Anweisungen in einer SQL Server-Datenbank ausführen.  

```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
```

## <a name="single-bulk-copy-operations"></a>Einzelne Massenkopiervorgänge

Die einfachste Herangehensweise an einen SQL Server-Massenkopiervorgang ist das Durchführen eines einzelnen Vorgangs für eine Datenbank. Standardmäßig wird ein Massenkopiervorgang als isolierter Vorgang ausgeführt: Der Kopiervorgang erfolgt in nicht transaktionaler Weise, ohne Möglichkeit zum Rollback.  
  
> [!NOTE]  
> Wenn Sie für den Massenkopiervorgang beim Auftreten eines Fehlers einen teilweisen oder vollständigen Rollback ausführen müssen, können Sie entweder eine von `SQLServerBulkCopy` verwaltete Transaktion verwenden oder den Massenkopiervorgang innerhalb einer vorhandenen Transaktion ausführen.  
> Weitere Informationen finden Sie unter [Transaktionen und Massenkopiervorgänge](#transaction-and-bulk-copy-operations).  
  
 Dies sind die allgemeinen Schritte zum Durchführen eines Massenkopiervorgangs:  
  
1. Herstellen einer Verbindung mit dem Quellserver und Abrufen der zu kopierenden Daten. Die Daten können auch aus einer anderen Quelle stammen, solange sie aus einem `ResultSet`-Objekt oder einer `ISQLServerBulkRecord`-Implementierung abgerufen werden können.  
  
2. Stellen Sie eine Verbindung mit dem Zielserver her (sofern die Verbindung nicht von `SQLServerBulkCopy` hergestellt werden soll).  
  
3. Erstellen Sie ein `SQLServerBulkCopy`-Objekt, und nehmen Sie über `setBulkCopyOptions` die erforderlichen Einstellungen vor.  
  
4. Rufen Sie die `setDestinationTableName`-Methode auf, um die Zieltabelle für den Masseneinfügungsvorgang anzugeben.  
  
5. Rufen Sie eine der `writeToServer`-Methoden auf.  
  
6. Optional können Sie Eigenschaften über `setBulkCopyOptions` aktualisieren und `writeToServer` bei Bedarf wieder aufrufen.  
  
7. Rufen Sie `close` auf, oder umschließen Sie die Massenkopiervorgänge durch eine try-with-resources-Anweisung.  
  
> [!CAUTION]  
> Wir empfehlen die Verwendung gleicher Datentypen für Quell- und Zielspalten. Wenn die Datentypen nicht übereinstimmen, versucht `SQLServerBulkCopy` jeden Quellwert in den Zieldatentyp zu konvertieren. Konvertierungen wirken sich negativ auf die Leistung aus und können außerdem zu unerwarteten Fehlern führen. Beispielsweise kann ein Datentyp „double“ in den meisten Fällen in den Datentyp „decimal“ konvertiert werden, aber nicht immer.  
  
### <a name="example"></a>Beispiel

Die folgende Anwendung zeigt das Laden von Daten mithilfe der Klasse `SQLServerBulkCopy`. In diesem Beispiel werden in der SQL Server-Datenbank AdventureWorks unter Verwendung von `ResultSet` Daten aus der Tabelle Production.Product in eine ähnliche Tabelle derselben Datenbank kopiert.  
  
> [!IMPORTANT]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](#table-setup) beschrieben erstellt haben. Der angegebene Code dient nur zur Demonstration der Syntax für die Verwendung von `SQLServerBulkCopy`. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT …“ einfacher und schneller. SELECT“ zum Kopieren der Daten einfacher und schneller.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;

public class BulkCopySingle {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection)) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // In real world applications you would
            // not use SQLServerBulkCopy to move data from one table to the other
            // in the same database. This is for demonstration purposes only.

            // Set up the bulk copy object.
            // Note that the column positions in the source
            // table match the column positions in
            // the destination table so there is no need to
            // map columns.
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            bulkCopy.writeToServer(rsSourceData);

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="performing-a-bulk-copy-operation-using-transact-sql"></a>Ausführen eines Massenkopiervorgangs mithilfe von Transact-SQL

Das folgende Beispiel zeigt die Verwendung der Methode `executeUpdate` zum Ausführen der Anweisung BULK INSERT.  
  
> [!NOTE]  
> Der Dateipfad für die Datenquelle ist relativ zum Server. Der Serverprozess muss Zugriff auf diesen Pfad besitzen, damit der Massenkopiervorgang erfolgreich ausgeführt werden kann.  

```java
try (Connection con = DriverManager.getConnection(connectionUrl);
        Statement stmt = con.createStatement()) {
    // Perform the BULK INSERT
    stmt.executeUpdate(
            "BULK INSERT Northwind.dbo.[Order Details] " + "FROM 'f:\\mydata\\data.tbl' " + "WITH ( FORMATFILE='f:\\mydata\\data.fmt' )");
}
```  

## <a name="multiple-bulk-copy-operations"></a>Mehrere Massenkopiervorgänge  

Mithilfe einer einzelnen Instanz einer `SQLServerBulkCopy`-Klasse können Sie mehrere Massenkopiervorgänge ausführen. Wenn sich die Parameter für den Vorgang zwischen den Ausführungen ändern (z. B. der Name der Zieltabelle), müssen Sie sie wie im folgenden Beispiel gezeigt vor allen nachfolgenden Aufrufen einer der `writeToServer`-Methoden ändern. Sofern sie nicht explizit geändert werden, bleiben alle Eigenschaftswerte die gleichen wie beim letzten Massenkopiervorgang für eine bestimmte Instanz.  

> [!NOTE]  
> Das Ausführen mehrerer Massenkopiervorgänge mithilfe der gleichen Instanz von `SQLServerBulkCopy` ist normalerweise effizienter als die Verwendung einer separaten Instanz für jeden Vorgang.  
  
Wenn Sie mehrere Massenkopiervorgänge mithilfe des gleichen `SQLServerBulkCopy`-Objekts ausführen, bestehen normalerweise keine Einschränkungen hinsichtlich der Gleichheit oder Verschiedenheit der Quell- und Zielinformationen für die einzelnen Vorgänge. Sie müssen jedoch sicherstellen, dass die Informationen zur Spaltenzuordnung bei jedem Schreibvorgang auf dem Server ordnungsgemäß festgelegt sind.  
  
> [!IMPORTANT]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](#table-setup) beschrieben erstellt haben. Der angegebene Code dient nur zur Demonstration der Syntax für die Verwendung von `SQLServerBulkCopy`. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT …“ einfacher und schneller. SELECT“ zum Kopieren der Daten einfacher und schneller.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyMultiple {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationHeaderTable = "dbo.BulkCopyDemoOrderHeader";
        String destinationDetailTable = "dbo.BulkCopyDemoOrderDetail";
        int countHeaderBefore, countDetailBefore, countHeaderAfter, countDetailAfter;
        ResultSet rsHeader, rsDetail;

        try (Connection sourceConnection1 = DriverManager.getConnection(connectionUrl);
                Connection sourceConnection2 = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection1.createStatement();
                PreparedStatement preparedStmt1 = sourceConnection1.prepareStatement(
                        "SELECT [SalesOrderID], [OrderDate], [AccountNumber] FROM [Sales].[SalesOrderHeader] WHERE [AccountNumber] = ?;");
                PreparedStatement preparedStmt2 = sourceConnection2.prepareStatement(
                        "SELECT [Sales].[SalesOrderDetail].[SalesOrderID], [SalesOrderDetailID], [OrderQty], [ProductID], [UnitPrice] FROM "
                                + "[Sales].[SalesOrderDetail] INNER JOIN [Sales].[SalesOrderHeader] ON "
                                + "[Sales].[SalesOrderDetail].[SalesOrderID] = [Sales].[SalesOrderHeader].[SalesOrderID] WHERE [AccountNumber] = ?;");
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(connectionUrl);) {

            // Empty the destination tables.
            stmt.executeUpdate("DELETE FROM " + destinationHeaderTable);
            stmt.executeUpdate("DELETE FROM " + destinationDetailTable);

            // Perform an initial count on the destination
            // table with matching columns.
            countHeaderBefore = getRowCount(stmt, destinationHeaderTable);

            // Perform an initial count on the destination
            // table with different column positions.
            countDetailBefore = getRowCount(stmt, destinationDetailTable);

            // Get data from the source table as a ResultSet.
            // The Sales.SalesOrderHeader and Sales.SalesOrderDetail
            // tables are quite large and could easily cause a timeout
            // if all data from the tables is added to the destination.
            // To keep the example simple and quick, a parameter is
            // used to select only orders for a particular account
            // as the source for the bulk insert.
            preparedStmt1.setString(1, "10-4020-000034");
            rsHeader = preparedStmt1.executeQuery();

            // Get the Detail data in a separate connection.
            preparedStmt2.setString(1, "10-4020-000034");
            rsDetail = preparedStmt2.executeQuery();

            // Create the SQLServerBulkCopySQLServerBulkCopy object.
            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setBulkCopyTimeout(100);
            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationHeaderTable);

            // Guarantee that columns are mapped correctly by
            // defining the column mappings for the order.
            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");
            bulkCopy.addColumnMapping("OrderDate", "OrderDate");
            bulkCopy.addColumnMapping("AccountNumber", "AccountNumber");

            // Write rsHeader to the destination.
            bulkCopy.writeToServer(rsHeader);

            // Set up the order details destination.
            bulkCopy.setDestinationTableName(destinationDetailTable);

            // Clear the existing column mappings
            bulkCopy.clearColumnMappings();

            // Add order detail column mappings.
            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");
            bulkCopy.addColumnMapping("SalesOrderDetailID", "SalesOrderDetailID");
            bulkCopy.addColumnMapping("OrderQty", "OrderQty");
            bulkCopy.addColumnMapping("ProductID", "ProductID");
            bulkCopy.addColumnMapping("UnitPrice", "UnitPrice");

            // Write rsDetail to the destination.
            bulkCopy.writeToServer(rsDetail);

            // Perform a final count on the destination
            // tables to see how many rows were added.
            countHeaderAfter = getRowCount(stmt, destinationHeaderTable);
            countDetailAfter = getRowCount(stmt, destinationDetailTable);

            System.out.println((countHeaderAfter - countHeaderBefore) + " rows were added to the Header table.");
            System.out.println((countDetailAfter - countDetailBefore) + " rows were added to the Detail table.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

## <a name="transaction-and-bulk-copy-operations"></a>Transaktionen und Massenkopiervorgänge

 Massenkopiervorgänge können als isolierte Vorgänge oder im Rahmen einer aus mehreren Schritten bestehenden Transaktion ausgeführt werden. Diese zweite Option ermöglicht Ihnen das Ausführen mehrerer Massenkopiervorgänge innerhalb der gleichen Transaktion sowie die Durchführung weiterer Datenbankvorgänge (wie etwa Einfüge-, Aktualisierungs- und Löschvorgänge), während die Möglichkeit zum Commit oder Rollback der gesamten Transaktion erhalten bleibt.  
  
 Standardmäßig wird ein Massenkopiervorgang als isolierter Vorgang ausgeführt. Der Massenkopiervorgang erfolgt nicht transaktional, ohne Möglichkeit zum Rollback. Wenn Sie für den Massenkopiervorgang beim Auftreten eines Fehlers einen teilweisen oder vollständigen Rollback ausführen müssen, können Sie eine von `SQLServerBulkCopy` verwaltete Transaktion verwenden oder den Massenkopiervorgang innerhalb einer vorhandenen Transaktion ausführen.  

## <a name="extended-bulk-copy-for-azure-data-warehouse"></a>Erweitertes Massenkopieren für Azure Data Warehouse

Mit der Treiberversion v8.4.1 wird die neue Verbindungseigenschaft `sendTemporalDataTypesAsStringForBulkCopy` hinzugefügt. Diese boolesche Eigenschaft ist standardmäßig auf `true` festgelegt.

Wenn diese Verbindungseigenschaft auf `false` festgelegt ist, werden die Datentypen **DATE**, **DATETIME**, **DATIMETIME2**, **DATETIMEOFFSET**, **SMALLDATETIME** und **TIME** in Form ihrer jeweiligen Datentypen und nicht als Zeichenfolgen gesendet.

Das Senden der temporalen Datentypen in Form ihrer jeweiligen Datentypen ermöglicht dem Benutzer das Senden von Daten an diese Spalten für Azure Synapse Analytics. Das war zuvor nicht möglich, weil der Treiber die Daten in Zeichenfolgen konvertiert hat. Das Senden von Zeichenfolgendaten an temporale Spalten funktioniert bei SQL Server, weil SQL Server eine implizite Konvertierung durchführt. Dies ist bei Azure Synapse Analytics nicht der Fall.

Zusätzlich gilt: Selbst wenn diese Verbindungszeichenfolge nicht auf „false“ festgelegt wird, werden ab **v8.4.1** die Datentypen **MONEY** und **SMALLMONEY** als **MONEY** / **SMALLMONEY** anstatt als **DECIMAL** gesendet. Dadurch können diese Datentypen ebenfalls in einem Massenvorgang nach Azure Synapse Analytics kopiert werden.

### <a name="extended-bulk-copy-for-azure-data-warehouse-limitations"></a>Einschränkungen beim erweiterten Massenkopieren für Azure Data Warehouse

Derzeit gibt es zwei Einschränkungen:

1. Wenn diese Verbindungseigenschaft auf `false` festgelegt ist, akzeptiert der Treiber für jeden temporalen Datentyp nur das Standardformat des Zeichenfolgenliterals. Beispiel:

    `DATE: YYYY-MM-DD`

    `DATETIME: YYYY-MM-DD hh:mm:ss[.nnn]`

    `DATETIME2: YYYY-MM-DD hh:mm:ss[.nnnnnnn]`

    `DATETIMEOFFSET: YYYY-MM-DD hh:mm:ss[.nnnnnnn] [{+/-}hh:mm]`

    `SMALLDATETIME:YYYY-MM-DD hh:mm:ss`

    `TIME: hh:mm:ss[.nnnnnnn]`

2. Wenn diese Verbindungseigenschaft auf `false` festgelegt ist, muss bei dem für das Massenkopieren angegebenen Spaltentyp das [hier enthaltene](../../connect/jdbc/using-basic-data-types.md) Diagramm für Datentypzuordnungen berücksichtigt werden. Beispielsweise konnten Benutzer zuvor `java.sql.Types.TIMESTAMP` für das Massenkopieren von Daten in eine `DATE`-Spalte angeben. Wenn diese Funktion aktiviert ist, müssen sie jedoch `java.sql.Types.DATE` angeben, um denselben Vorgang auszuführen.
  
### <a name="performing-a-non-transacted-bulk-copy-operation"></a>Ausführen eines nicht transaktionalen Massenkopiervorgangs

Die folgende Anwendung zeigt, was geschieht, wenn bei einem nicht transaktionalen Massenkopiervorgang nach teilweiser Ausführung ein Fehler auftritt.  
  
In dem Beispiel enthalten die Quell- und Zieltabelle jeweils eine Identitätsspalte mit Namen `ProductID`. Der Code bereitet zunächst die Zieltabelle vor, indem er alle Zeilen löscht und dann eine einzelne Zeile einfügt, deren `ProductID` bekanntermaßen in der Quelltabelle vorhanden ist. Standardmäßig wird für die Spalte „Identity“ in der Zieltabelle für jede hinzugefügte Zeile ein neuer Wert generiert. In diesem Beispiel wird beim Öffnen der Verbindung eine Option festgelegt, die den Massenladevorgang zwingt, stattdessen die Identity-Werte aus der Quelltabelle zu verwenden.  
  
Der Massenkopiervorgang wird mit dem Wert „10“ für die Eigenschaft `BatchSize` ausgeführt. Wenn der Vorgang auf die ungültige Zeile trifft, wird eine Ausnahme ausgelöst. In diesem ersten Beispiel ist der Massenkopiervorgang nicht transaktional. Für alle bis zum Auftreten des Fehlers kopierten Batches wird ein Commit ausgeführt; für den Batch, der den doppelten Schlüssel enthält, wird ein Rollback ausgeführt, und der Massenkopiervorgang wird vor dem Verarbeiten weiterer Batches angehalten.  
  
> [!NOTE]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](#table-setup) beschrieben erstellt haben. Der angegebene Code dient nur zur Demonstration der Syntax für die Verwendung von `SQLServerBulkCopy`. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT …“ einfacher und schneller. SELECT“ zum Kopieren der Daten einfacher und schneller.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyNonTransacted {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(connectionUrl)) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Add a single row that will result in duplicate key
            // when all rows from source are bulk copied.
            // Note that this technique will only be successful in
            // illustrating the point if a row with ProductID = 446
            // exists in the AdventureWorks Production.Products table.
            // If you have made changes to the data in this table, change
            // the SQL statement in the code to add a ProductID that
            // does exist in your version of the Production.Products
            // table. Choose any ProductID in the middle of the table
            // (not first or last row) to best illustrate the result.
            stmt.executeUpdate("SET IDENTITY_INSERT " + destinationTable + " ON;" + "INSERT INTO " + destinationTable
                    + "([ProductID], [Name] ,[ProductNumber]) VALUES(446, 'Lock Nut 23','LN-3416'); SET IDENTITY_INSERT " + destinationTable
                    + " OFF");

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // Set up the bulk copy object using the KeepIdentity option and BatchSize = 10.
            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setKeepIdentity(true);
            copyOptions.setBatchSize(10);

            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            // This should fail with a duplicate key error
            // after some of the batches have been copied.
            try {
                bulkCopy.writeToServer(rsSourceData);
            }
            catch (SQLException e) {
                e.printStackTrace();
            }

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Ausführen eines dedizierten Massenkopiervorgangs in einer Transaktion

Standardmäßig werden bei einem Massenkopiervorgang keine Transaktionen selbst erstellt. Wenn Sie einen dedizierten Massenkopiervorgang ausführen möchten, erstellen Sie eine neue Instanz von `SQLServerBulkCopy` mit einer Verbindungszeichenfolge. In diesem Szenario wird jeder Batch des Massenkopiervorgangs implizit von der Datenbank committet. Sie können die `UseInternalTransaction`-Option in `SQLServerBulkCopyOptions` auf `true` festlegen, damit vom Massenkopiervorgang Transaktionen erstellt werden und nach jedem Batch des Massenkopiervorgangs ein Commit ausgeführt wird.
  
```java
SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
copyOptions.setKeepIdentity(true);
copyOptions.setBatchSize(10);
copyOptions.setUseInternalTransaction(true);
```

### <a name="using-existing-transactions"></a>Verwenden vorhandener Transaktionen

Sie können ein `Connection`-Objekt, für das Transaktionen aktiviert sind, als Parameter in einem `SQLServerBulkCopy`-Konstruktor übergeben. In dieser Situation wird der Massenkopiervorgang in einer vorhandenen Transaktion ausgeführt, und der Transaktionsstatus wird nicht verändert (d. h. kein Commit oder Abbruch). Dies macht es möglich, dass Anwendungen den Massenkopiervorgang zusammen mit anderen Datenbankvorgängen in einer Transaktion einschließen. Wenn Sie einen Rollback des gesamten Massenkopiervorgangs durchführen müssen, weil ein Fehler auftritt, oder wenn die Massenkopie im Rahmen eines größeren Prozesses ausgeführt werden soll, für den ein Rollback durchgeführt werden kann, können Sie den Rollback für das `Connection`-Objekt zu jedem beliebigen Zeitpunkt nach dem Massenkopiervorgang ausführen.  
  
Die folgende Anwendung ähnelt `BulkCopyNonTransacted` mit der Ausnahme, dass in diesem Beispiel der Massenkopiervorgang in einer größeren, externen Transaktion enthalten ist. Wenn der Fehler aufgrund des Primärschlüsselverstoßes auftritt, wird ein Rollback der gesamten Transaktion ausgeführt, und der Zieltabelle werden keine Zeilen hinzugefügt.

> [!NOTE]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](#table-setup) beschrieben erstellt haben. Der angegebene Code dient nur zur Demonstration der Syntax für die Verwendung von `SQLServerBulkCopy`. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT …“ einfacher und schneller. SELECT“ zum Kopieren der Daten einfacher und schneller.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyExistingTransactions {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;
        SQLServerBulkCopyOptions copyOptions;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection);) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Add a single row that will result in duplicate key
            // when all rows from source are bulk copied.
            // Note that this technique will only be successful in
            // illustrating the point if a row with ProductID = 446
            // exists in the AdventureWorks Production.Products table.
            // If you have made changes to the data in this table, change
            // the SQL statement in the code to add a ProductID that
            // does exist in your version of the Production.Products
            // table. Choose any ProductID in the middle of the table
            // (not first or last row) to best illustrate the result.
            stmt.executeUpdate("SET IDENTITY_INSERT " + destinationTable + " ON;" + "INSERT INTO " + destinationTable
                    + "([ProductID], [Name] ,[ProductNumber]) VALUES(446, 'Lock Nut 23','LN-3416'); SET IDENTITY_INSERT " + destinationTable
                    + " OFF");

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // Set up the bulk copy object inside the transaction.
            destinationConnection.setAutoCommit(false);

            copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setKeepIdentity(true);
            copyOptions.setBatchSize(10);

            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            // This should fail with a duplicate key error.
            try {
                bulkCopy.writeToServer(rsSourceData);
                destinationConnection.commit();
            }
            catch (SQLException e) {
                e.printStackTrace();
                destinationConnection.rollback();
            }

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        catch (Exception e) {
            // Handle any errors that may have occurred.
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="bulk-copy-from-a-csv-file"></a>Massenkopieren aus einer CSV-Datei  

 Die folgende Anwendung zeigt das Laden von Daten mithilfe der Klasse `SQLServerBulkCopy`. In diesem Beispiel wird eine CSV-Datei verwendet, um aus der Tabelle „Production.Product“ in der SQL Server AdventureWorks-Datenbank exportierte Daten in eine ähnliche Tabelle in der gleichen Datenbank zu kopieren.  
  
> [!IMPORTANT]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](#table-setup) beschrieben erstellt haben, um es abzurufen.  
  
1. Öffnen Sie **SQL Server Management Studio**, und stellen Sie eine Verbindung mit dem SQL Server-Computer mit der AdventureWorks-Datenbank her.  
  
2. Erweitern Sie die Datenbanken, klicken Sie mit der rechten Maustaste auf die AdventureWorks-Datenbank, und wählen Sie **Aufgaben** und **Daten exportieren** aus.  
  
3. Wählen Sie als Datenquelle die **Datenquelle** aus, die Ihnen die Verbindung mit Ihrem SQL Server ermöglicht (z. B. SQL Server Native Client 11.0), überprüfen Sie die Konfiguration, und kicken Sie anschließend auf **Weiter**.  
  
4. Wählen Sie als Ziel das **Flatfileziel** aus, und geben Sie einen **Dateinamen** mit einem Zielspeicherort wie etwa `C:\Test\TestBulkCSVExample.csv` ein. Überprüfen Sie, ob das **Format** „Mit Trennzeichen“, der **Textqualifizierer** „Ohne“ ist, und aktivieren Sie **Spaltennamen in der ersten Datenzeile**. Wählen Sie anschließend **Weiter** aus.  
  
5. Wählen Sie **Abfrage zum Abgeben der zu übertragenden Daten schreiben** und anschließend **Weiter** aus.  Geben Sie die **SQL-Anweisung** `SELECT ProductID, Name, ProductNumber FROM Production.Product` ein, und klicken Sie auf **Weiter**.  
  
6. Überprüfen Sie die Konfiguration: Sie können für das Zeilentrennzeichen weiterhin `{CR}{LF}` und für das Spaltentrennzeichen weiterhin das Komma `{,}` verwenden.  Klicken Sie auf **Zuordnungen bearbeiten**, und überprüfen Sie, ob der **Datentyp** für die einzelnen Spalten richtig ist (z. B. Integer für `ProductID` und Unicode-Zeichenfolge für die anderen).  
  
7. Überspringen Sie die weiteren Optionen bis zu **Fertig stellen**, und führen Sie den Exportvorgang aus.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCSVFileRecord;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;

public class BulkCopyCSV {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;

        // Get data from the source file by loading it into a class that implements ISQLServerBulkRecord.
        // Here we are using the SQLServerBulkCSVFileRecord implementation to import the example CSV file.
        try (Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = destinationConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection);
                SQLServerBulkCSVFileRecord fileRecord = new SQLServerBulkCSVFileRecord("C:\\Test\\TestBulkCSVExample.csv", true);) {

            // Set the metadata for each column to be copied.
            fileRecord.addColumnMetadata(1, null, java.sql.Types.INTEGER, 0, 0);
            fileRecord.addColumnMetadata(2, null, java.sql.Types.NVARCHAR, 50, 0);
            fileRecord.addColumnMetadata(3, null, java.sql.Types.NVARCHAR, 25, 0);

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Set up the bulk copy object.
            // Note that the column positions in the source
            // data reader match the column positions in
            // the destination table so there is no need to
            // map columns.
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            bulkCopy.writeToServer(fileRecord);

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```  

### <a name="bulk-copy-with-delimiters-as-data-in-csv-file"></a>Massenkopieren mit Trennzeichen als Daten in einer CSV-Datei

Mit der Treiberversion 8.4.1 wird die neue `SQLServerBulkCSVFileRecord.setEscapeColumnDelimitersCSV(boolean)`-API eingeführt. Wenn diese auf „true“ festgelegt ist, gelten die folgenden Regeln:

- Jedes Feld kann in doppelte Anführungszeichen eingeschlossen sein oder nicht.
- Wenn Felder nicht in doppelte Anführungszeichen eingeschlossen sind, werden doppelte Anführungszeichen möglicherweise nicht innerhalb der Felder angezeigt.
- Felder, die doppelte Anführungszeichen und Trennzeichen enthalten, müssen in doppelte Anführungszeichen eingeschlossen werden.
- Wenn Felder mithilfe doppelter Anführungszeichen eingeschlossen werden, muss ein doppeltes Anführungszeichen innerhalb eines Felds mit einem Escapezeichen versehen werden, das einem weiteren vorangestellten doppelten Anführungszeichen entspricht.

### <a name="bulk-copy-with-always-encrypted-columns"></a>Massenkopieren mit Always Encrypted-Spalten  

Ab dem Microsoft JDBC-Treiber 6.0 für SQL Server wird das Massenkopieren mit Always Encrypted-Spalten unterstützt.  
  
Je nach Massenkopieroptionen und je nach Verschlüsselungstyp der Quell- und Zieltabellen kann der JDBC-Treiber die Daten transparent entschlüsseln und verschlüsseln, oder die verschlüsselten Daten werden unverändert gesendet. Im Falle eines Massenkopiervorgangs von Daten aus einer verschlüsselten Spalte in eine nicht verschlüsselte Spalte entschlüsselt der Treiber die Daten beispielsweise transparent, bevor sie an SQL Server gesendet werden. Ähnlich verhält es sich für Massenkopiervorgänge von Daten aus einer nicht verschlüsselten Spalte (oder einer CSV-Datei) in eine verschlüsselte Spalte: Hier verschlüsselt der Treiber die Daten transparent, bevor sie an SQL Server gesendet werden. Wenn sowohl die Quelle als auch das Ziel verschlüsselt sind, sendet der Treiber je nach `allowEncryptedValueModifications`-Massenkopieroption die Daten entweder unverändert, oder er entschlüsselt die Daten und verschlüsselt sie dann wieder, bevor sie an SQL Server gesendet werden.  
  
Weitere Informationen finden Sie weiter unten unter der Massenkopieroption `allowEncryptedValueModifications` und unter [Verwenden von Always Encrypted mit dem JDBC-Treiber](using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
> Einschränkung für den Microsoft JDBC-Treiber 6.0 für SQL Server beim Massenkopieren von Daten aus einer CSV-Datei in verschlüsselte Spalten:  
>
> Nur das Transact-SQL-Standardzeichenfolgenliteralformat wird für Datums- und Uhrzeittypen unterstützt.  
>
> Die Datentypen „DATETIME“ und „SMALLDATETIME“ werden nicht unterstützt.  
  
## <a name="bulk-copy-api-for-jdbc-driver"></a>Massenkopieren-API für JDBC Driver  
  
### <a name="sqlserverbulkcopy"></a>SQLServerBulkCopy

Damit können Sie effizient eine SQL Server-Tabelle mit Massendaten aus einer anderen Quelle laden.  
  
Microsoft SQL Server enthält ein beliebtes Befehlszeilen-Hilfsprogramm namens bcp zum Verschieben von Daten aus einer Tabelle in eine andere, das auf einem einzelnen Server oder serverübergreifend ausgeführt werden kann. Die Klasse `SQLServerBulkCopy` ermöglicht Ihnen das Erstellen von Codelösungen in Java, die eine ähnliche Funktionalität bieten. Es gibt eine Reihe weiterer Verfahren, Daten in eine SQL Server-Tabelle zu laden (beispielsweise INSERT-Anweisungen), aber `SQLServerBulkCopy` bietet im Vergleich einen erheblichen Leistungsvorteil.  
  
Die `SQLServerBulkCopy`-Klasse kann nur zum Schreiben von Daten in SQL Server-Tabellen verwendet werden. Die Datenquelle ist aber nicht auf SQL Server beschränkt. Jede beliebige Datenquelle kann verwendet werden, sofern die Daten mit einer Instanz von `ResultSet` oder einer `ISQLServerBulkRecord`-Implementierung gelesen werden können.  
  
| Konstruktor | BESCHREIBUNG |
| ----------- | ----------- |
| `SQLServerBulkCopy(Connection connection)` | Hiermit wird eine neue Instanz der `SQLServerBulkCopy`-Klasse mithilfe der angegebenen geöffneten Instanz von `SQLServerConnection` initialisiert. Wenn für die `Connection` Transaktionen aktiviert sind, werden die Kopiervorgänge innerhalb der betreffenden Transaktion ausgeführt. |
| `SQLServerBulkCopy(String connectionURL)` | Hiermit wird eine neue Instanz von `SQLServerConnection` auf Grundlage der angegebenen `connectionURL` initialisiert und geöffnet. Im Konstruktor wird die `SQLServerConnection` verwendet, um eine neue Instanz der `SQLServerBulkCopy`-Klasse zu initialisieren. |
  
| Eigenschaft | BESCHREIBUNG |
| -------- | ----------- |
| `String DestinationTableName` | Name der Zieltabelle auf dem Server.<br /><br /> Wenn der `DestinationTableName` nicht festgelegt wurde, wenn `writeToServer` aufgerufen wird, wird eine `SQLServerException` ausgelöst.<br /><br /> `DestinationTableName` ist ein aus drei Teilen bestehender Name (`<database>.<owningschema>.<name>`). Sie können den Tabellennamen mit seiner Datenbank und dem besitzenden Schema qualifizieren, wenn Sie das wünschen. Wenn im Tabellennamen jedoch ein Unterstrich ("_") oder ein anderes Sonderzeichen vorkommt, müssen Sie den Namen in eckige Klammern einschließen. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md). |
| `ColumnMappings` | Spaltenzuordnungen definieren die Beziehungen zwischen Spalten in der Datenquelle und Spalten im Ziel.<br /><br /> Wenn keine Zuordnungen definiert sind, werden die Spalten implizit auf der Grundlage ihrer Ordinalposition zugeordnet. Damit dies funktioniert, müssen Quell- und Zielschema übereinstimmen. Ist dies nicht der Fall, wird eine Ausnahme ausgelöst.<br /><br /> Wenn die Zuordnung nicht leer ist, muss nicht jede in der Datenquelle vorhandene Spalte angegeben werden. Nicht zugeordnete Spalten werden ignoriert.<br /><br /> Sie können auf Quell- und Zielspalten über den Namen oder die Ordnungszahl verweisen. |
  
| Methode | Beschreibung |
| ------ | ----------- |
| `void addColumnMapping(int sourceColumn, int destinationColumn)` | Fügt eine neue Spaltenzuordnung hinzu, und verwendet für die Angabe von Quell- und Zielspalten Ordnungszahlen. |
| `void addColumnMapping (int sourceColumn, String destinationColumn)` | Fügt eine neue Spaltenzuordnung hinzu und verwendet für die Quellspalte eine Ordnungszahl und für die Zielspalte den Spaltennamen. |
| `void addColumnMapping (String sourceColumn, int destinationColumn)` | Fügt eine neue Spaltenzuordnung hinzu und verwendet einen Spaltennamen zum Beschreiben der Quellspalte und eine Ordnungszahl zum Angeben der Zielspalte. |
| `void addColumnMapping (String sourceColumn, String destinationColumn)` | Fügt eine neue Spaltenzuordnung hinzu, und verwendet für die Angabe von Quell- und Zielspalten Spaltennamen. |
| `void clearColumnMappings()` | Löscht den Inhalt der Spaltenzuordnungen. |
| `void close()` | Hiermit wird die `SQLServerBulkCopy`-Instanz geschlossen. |
| `SQLServerBulkCopyOptions getBulkCopyOptions()` | Hiermit werden die aktuellen `SQLServerBulkCopyOptions` abgerufen. |
| `String getDestinationTableName()` | Ruft den Namen der aktuellen Zieltabelle ab. |
| `void setBulkCopyOptions(SQLServerBulkCopyOptions copyOptions)` | Hiermit wird das Verhalten der `SQLServerBulkCopy`-Instanz gemäß den angegebenen Optionen aktualisiert. |
| `void setDestinationTableName(String tableName)` | Legt den Namen der Zieltabelle fest. |
| `void writeToServer(ResultSet sourceData)` | Hiermit werden alle Zeilen in der angegebenen `ResultSet` in eine Zieltabelle kopiert, die durch die `DestinationTableName`-Eigenschaft des `SQLServerBulkCopy`-Objekts festgelegt wird. |
| `void writeToServer(RowSet sourceData)` | Hiermit werden alle Zeilen in der angegebenen `RowSet` in eine Zieltabelle kopiert, die durch die `DestinationTableName`-Eigenschaft des `SQLServerBulkCopy`-Objekts festgelegt wird. |
| `void writeToServer(ISQLServerBulkRecord sourceData)` | Hiermit werden alle Zeilen in der angegebenen `ISQLServerBulkRecord`-Implementierung in eine Zieltabelle kopiert, die durch die `DestinationTableName`-Eigenschaft des `SQLServerBulkCopy`-Objekts festgelegt wird. |
  
### <a name="sqlserverbulkcopyoptions"></a>SQLServerBulkCopyOptions  

 Dies ist eine Sammlung von Einstellungen, die steuern, wie sich die `writeToServer`-Methoden in einer Instanz von `SQLServerBulkCopy` verhalten.  
  
| Konstruktor | BESCHREIBUNG |
| ----------- | ----------- |
| `SQLServerBulkCopyOptions()` | Hiermit wird eine neue Instanz der `SQLServerBulkCopyOptions`-Klasse mit Standardwerten für alle Einstellungen initialisiert. |
  
 Für die folgenden Optionen sind Getter und Setter vorhanden:  
  
| Option | BESCHREIBUNG | Standard |
| ------ | ----------- | ------- |
| `boolean CheckConstraints` | Überprüft Bedingungen während der Einfügung von Daten. | False – es werden keine Bedingungen überprüft. |
| `boolean FireTriggers` | Bei dieser Option wird der Server veranlasst, die Einfügetrigger für die in die Datenbank eingefügten Zeilen auszulösen. | False – es werden keine Trigger ausgelöst |
| `boolean KeepIdentity` | Die Identitätswerte der Quelltabelle werden beibehalten. | False – die Identitätswerte werden vom Ziel zugewiesen |
| `boolean KeepNulls` | NULL-Werte in der Zieltabelle werden beibehalten, unabhängig von der Einstellung für Standardwerte. | False – NULL-Werte werden, falls anwendbar, durch Standardwerte ersetzt. |
| `boolean TableLock` | Für die Dauer des Massenimportvorgangs wird eine Sperre für Massenaktualisierung aktiviert. | False – es werden Sperren auf Zeilenebene verwendet. |
| `boolean UseInternalTransaction` | Wenn `true` festgelegt ist, wird jeder Batch des Massenkopiervorgangs innerhalb einer Transaktion verarbeitet. Wenn `SQLServerBulkCopy` eine vorhandene Verbindung verwendet (wie vom Konstruktor angegeben), tritt eine `SQLServerException` auf.  Wenn `SQLServerBulkCopy` eine dedizierte Verbindung hergestellt hat, wird eine Transaktion erstellt und für jeden Batch committet. | False – keine Transaktion |
| `int BatchSize` | Anzahl der Zeilen in jedem Batch. Am Ende jedes Batches werden die im Batch enthaltenen Zeilen an den Server gesendet.<br /><br /> Ein Batch ist abgeschlossen, wenn die `BatchSize`-Zeilen verarbeitet wurden oder keine weiteren Zeilen mehr zum Senden an die Zieldatenquelle vorhanden sind.  Wenn die `SQLServerBulkCopy`-Instanz mit der auf `false` festgelegten Option `UseInternalTransaction` deklariert wurde, werden Zeilen jeweils an die `BatchSize`-Serverzeilen gesendet, aber es wird keine transaktionsbezogene Aktion durchgeführt. Wenn `UseInternalTransaction` auf `true` festgelegt ist, wird jeder Batch von Zeilen innerhalb einer expliziten Transaktion ausgeführt. | 0 gibt an, dass jeder `writeToServer`-Vorgang ein einzelner Batch ist. |
| `int BulkCopyTimeout` | Anzahl der Sekunden für den Abschluss des Vorgangs, bevor ein Timeout eintritt. Der Wert „0“ bedeutet, dass keine Einschränkung vorliegt, und der Massenkopiervorgang wartet unbegrenzt. | 60 Sekunden. |
| `boolean allowEncryptedValueModifications` | Diese Option ist ab dem Microsoft JDBC-Treiber 6.0 für SQL Server verfügbar.<br /><br /> Wenn diese Option auf `true` festgelegt ist, kann der Benutzer durch `allowEncryptedValueModifications` Massenkopiervorgänge für verschlüsselte Daten zwischen Tabellen oder Datenbanken durchführen, ohne dabei die Daten zu verschlüsseln. Normalerweise würde eine Anwendung Daten aus verschlüsselten Spalten aus einer Tabelle auswählen, ohne die Daten zu entschlüsseln. Die App würde eine Verbindung zur Datenbank herstellen, und das Spaltenverschlüsselungseinstellungsschlüsselwort wäre auf „deaktiviert“ festgelegt. Dann würde die Anwendung diese Option zum Masseneinfügen der Daten verwenden, die noch verschlüsselt wären. Weitere Informationen finden Sie unter [Verwenden von Always Encrypted mit dem ODBC-Treiber](using-always-encrypted-with-the-jdbc-driver.md).<br /><br /> Seien Sie vorsichtig, wenn Sie `allowEncryptedValueModifications` auf `true` festlegen, da dies möglicherweise zu einer Beschädigung der Datenbank führen kann, weil der Treiber nicht überprüft, ob die Daten tatsächlich verschlüsselt oder mit demselben Verschlüsselungstyp, Algorithmus und Schlüssel wie die Zielspalte ordnungsgemäß verschlüsselt wurden. |
  
 Getter und Setter:  
  
| Methoden | BESCHREIBUNG |
| ------- | ----------- |
| `boolean isCheckConstraints()` | Gibt an, ob Einschränkungen überprüft werden müssen, während die Daten eingefügt werden. |
| `void setCheckConstraints(boolean checkConstraints)` | Legt fest, ob Einschränkungen überprüft werden müssen, während die Daten eingefügt werden. |
| `boolean isFireTriggers()` | Gibt an, ob der Server die Einfügetrigger für die in die Datenbank eingefügten Zeilen auslösen sollte. |
| `void setFireTriggers(boolean fireTriggers)` | Legt fest, ob der Server die Einfügetrigger für die in die Datenbank eingefügten Zeilen auslösen sollte. |
| `boolean isKeepIdentity()` | Gibt an, ob Quellenidentitätswerte beibehalten werden sollen. |
| `void setKeepIdentity(boolean keepIdentity)` | Legt fest, ob Quellenidentitätswerte beibehalten werden sollen. |
| `boolean isKeepNulls()` | Gibt an, ob NULL-Werte in der Zieltabelle unabhängig von den Einstellungen für Standardwerte beibehalten werden sollen, oder ob sie durch die Standardwerte (wo möglich) ersetzt werden sollten. |
| `void setKeepNulls(boolean keepNulls)` | Legt fest, ob NULL-Werte in der Zieltabelle unabhängig von den Einstellungen für Standardwerte beibehalten werden sollen, oder ob sie durch die Standardwerte (wo möglich) ersetzt werden sollten. |
| `boolean isTableLock()` | Hiermit wird angegeben, ob für die Dauer des Massenkopiervorgangs für `SQLServerBulkCopy` eine Sperre für Massenaktualisierung gelten soll. |
| `void setTableLock(boolean tableLock)` | Hiermit wird festgelegt, ob für die Dauer des Massenkopiervorgangs für `SQLServerBulkCopy` eine Sperre für Massenaktualisierung gelten soll. |
| `boolean isUseInternalTransaction()` | Gibt an, ob jeder Batch des Massenkopiervorgangs innerhalb einer Transaktion verarbeitet wird. |
| `void setUseInternalTranscation(boolean useInternalTransaction)` | Legt fest, ob jeder Batch des Massenkopiervorgangs innerhalb einer Transaktion verarbeitet wird. |
| `int getBatchSize()` | Ruft die Anzahl der Zeilen in jedem Batch ab. Am Ende jedes Batches werden die im Batch enthaltenen Zeilen an den Server gesendet. |
| `void setBatchSize(int batchSize)` | Legt die Anzahl der Zeilen in jedem Batch fest. Am Ende jedes Batches werden die im Batch enthaltenen Zeilen an den Server gesendet. |
| `int getBulkCopyTimeout()` | Ruft die Anzahl der Sekunden für den Abschluss des Vorgangs ab, bevor ein Timeout eintritt. |
| `void  setBulkCopyTimeout(int timeout)` | Legt die Anzahl der Sekunden für den Abschluss des Vorgangs fest, bevor ein Timeout eintritt. |
| `boolean isAllowEncryptedValueModifications()` | Hiermit wird angegeben, ob die `allowEncryptedValueModifications`-Einstellung aktiviert oder deaktiviert ist. |
| `void setAllowEncryptedValueModifications(boolean allowEncryptedValueModifications)` | Hiermit wird die Einstellung `allowEncryptedValueModifications` konfiguriert, die für das Massenkopieren mit Always Encrypted-Spalten verwendet wird. |
  
### <a name="isqlserverbulkrecord"></a>ISQLServerBulkRecord  

 Die Schnittstelle `ISQLServerBulkRecord` kann verwendet werden, um Klassen zu erstellen, die Daten aus jeder beliebigen Quelle (wie etwa einer Datei) einlesen. Sie ermöglicht einer `SQLServerBulkCopy`-Instanz das Massenladen einer SQL Server-Tabelle mit diesen Daten.  
  
| Schnittstellenmethoden | BESCHREIBUNG |
| ----------------- | ----------- |
| `set<Integer> getColumnOrdinals()` | Ruft die Ordnungszahlen für jede der in diesem Datensatz enthaltenen Spalten ab. |
| `String getColumnName(int column)` | Ruft den Namen der angegebenen Spalte ab. |
| `int getColumnType(int column)` | Ruft den JDBC-Datentyp der angegebenen Spalte ab. |
| `int getPrecision(int column)`  | Ruft die Genauigkeit für die angegebene Spalte ab. |
| `object[] getRowData()` | Ruft die Daten für die aktuelle Zeile als Array von Objekten ab.<br /><br /> Jedes Objekt muss mit dem Java-Sprachtyp übereinstimmen, der zur Darstellung des angegebenen JDBC-Datentyps für die angegebene Spalte verwendet wird.  Weitere Informationen und die passenden Zuordnungen finden Sie unter [Grundlegendes zu den Datentypen des JDBC-Treibers](understanding-the-jdbc-driver-data-types.md). |
| `int getScale(int column)` | Ruft die Dezimalstellen für die angegebene Spalte ab. |
| `boolean isAutoIncrement(int column)` | Zeigt an, ob es sich bei der Spalte um eine Identitätsspalte handelt. |
| `boolean next()` | Springt zur nächsten Datenzeile. |
  
### <a name="sqlserverbulkcsvfilerecord"></a>SQLServerBulkCSVFileRecord  

Dies ist eine einfache Implementierung der `ISQLServerBulkRecord`-Schnittstelle, die zum Einlesen der einfachen Java-Datentypen aus einer Datei mit Trennzeichen verwendet werden kann, in der jede Zeile eine Datenzeile darstellt.  
  
Hinweise zur Implementierung und Einschränkungen:  
  
1. Die maximal in jeder vorhandenen Zeile zulässige Datenmenge ist durch den verfügbaren Arbeitsspeicher begrenzt, da die Daten zeilenweise gelesen werden.  
  
2. Das Streaming von großen Datentypen wie `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `sqlxml` und `ntext` wird nicht unterstützt.  
  
3. Das für die CSV-Datei verwendete Trennzeichen darf an keiner Stelle innerhalb der Daten auftreten und muss ordnungsgemäß escaped werden, wenn es in den regulären Java-Ausdrücken zu den eingeschränkten Zeichen gehört.  
  
4. In der CSV-Dateiimplementierung werden doppelte Anführungszeichen als Teil der Daten behandelt. Beispielsweise würde die Zeile `hello,"world","hello,world"` als aus vier Spalten mit den Werten `hello`, `"world"`, `"hello` und `world"` bestehende Einheit behandelt werden, wenn als Trennzeichen ein Komma verwendet wird.  
  
5. Zeilenvorschubzeichen werden als Zeilenendzeichen verwendet und dürfen an keiner Stelle in den Daten auftreten.  
  
| Konstruktor | BESCHREIBUNG |
| ----------- | ----------- |
| `SQLServerBulkCSVFileRecord(String fileToParse, String encoding, String delimiter, boolean firstLineIsColumnNames)` | Hiermit wird eine neue Instanz der `SQLServerBulkCSVFileRecord`-Klasse initialisiert, die jede Zeile in der zu analysierenden Datei `fileToParse` mit dem angegebenen Trennzeichen und der angegebenen Codierung analysiert. Wenn `firstLineIsColumnNames` auf „True“ festgelegt ist, wird der Inhalt der ersten Zeile der Datei als Spaltennamen analysiert.  Wenn die Codierung NULL ist, wird die Standardcodierung verwendet. |
| `SQLServerBulkCSVFileRecord(String fileToParse, String encoding, boolean firstLineIsColumnNames)` | Hiermit wird eine neue Instanz der `SQLServerBulkCSVFileRecord`-Klasse initialisiert, die jede Zeile in der zu analysierenden Datei `fileToParse` mit einem Komma als Trennzeichen und der angegebenen Codierung analysiert. Wenn `firstLineIsColumnNames` auf „True“ festgelegt ist, wird der Inhalt der ersten Zeile der Datei als Spaltennamen analysiert.  Wenn die Codierung NULL ist, wird die Standardcodierung verwendet. |
| `SQLServerBulkCSVFileRecord(String fileToParse, boolean firstLineIsColumnNames` | Hiermit wird eine neue Instanz der `SQLServerBulkCSVFileRecord`-Klasse initialisiert, die jede Zeile in der zu analysierenden Datei `fileToParse` mit einem Komma als Trennzeichen und der Standardcodierung analysiert. Wenn `firstLineIsColumnNames` auf „True“ festgelegt ist, wird der Inhalt der ersten Zeile der Datei als Spaltennamen analysiert. |
  
| Methode | BESCHREIBUNG |
| ------ | ----------- |
| `void addColumnMetadata(int positionInFile, String columnName, int jdbcType, int precision, int scale)` | Fügt Metadaten für die angegebene Spalte in der Datei hinzu. |
| `void close()` | Gibt alle dem Dateileser zugeordneten Ressourcen frei. |
| `void setTimestampWithTimezoneFormat(DateTimeFormatter dateTimeFormatter)` | Hiermit wird das Format für die Analyse von Zeitstempeldaten aus der Datei auf `java.sql.Types.TIMESTAMP_WITH_TIMEZONE` festgelegt. |
| `void setTimestampWithTimezoneFormat(String dateTimeFormat)` | Hiermit wird das Format für die Analyse von Zeitdaten aus der Datei auf `java.sql.Types.TIME_WITH_TIMEZONE` festgelegt. |
| `void setTimeWithTimezoneFormat(DateTimeFormatter dateTimeFormatter)` | Hiermit wird das Format für die Analyse von Zeitdaten aus der Datei auf `java.sql.Types.TIME_WITH_TIMEZONE` festgelegt. |
| `void setTimeWithTimezoneFormat(String timeFormat)` | Hiermit wird das Format für die Analyse von Zeitdaten aus der Datei auf `java.sql.Types.TIME_WITH_TIMEZONE` festgelegt. |
  
## <a name="see-also"></a>Weitere Informationen  

[Übersicht über den JDBC-Treiber](overview-of-the-jdbc-driver.md)  
