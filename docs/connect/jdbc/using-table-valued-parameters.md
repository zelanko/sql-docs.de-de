---
title: Verwenden von Tabellenwertparametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 66d9c24a31002f0c991fbf1dfdd7210adbf53172
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74249712"
---
# <a name="using-table-valued-parameters"></a>Verwenden von Tabellenwertparametern

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Tabellenwertparameter bieten eine einfache Möglichkeit zum Marshallen mehrerer Datenzeilen aus einer Clientanwendung nach SQL Server, ohne dass mehrere Roundtrips oder eine spezielle serverseitige Logik für die Verarbeitung der Daten erforderlich sind. Sie können Tabellenwertparameter verwenden, um Datenzeilen in einer Clientanwendung zu kapseln und die Daten in einem einzigen parametrisierten Befehl an den Server zu senden. Die eingehenden Datenzeilen werden in einer Tabellenvariablen gespeichert, die Sie dann mithilfe von Transact-SQL bearbeiten können.  
  
Für den Zugriff auf Spaltenwerte in Tabellenwertparametern können Standard-SELECT-Anweisungen in Transact-SQL verwendet werden. Tabellenwertparameter sind stark typisiert, und ihre Struktur wird automatisch validiert. Die Größe von Tabellenwertparametern ist lediglich durch den Arbeitsspeicher des Servers beschränkt.  
  
> [!NOTE]  
> Unterstützung für Tabellenwertparameter ist ab Microsoft JDBC-Treiber 6.0 für SQL Server verfügbar.
>
> In Tabellenwertparametern können keine Daten zurückgegeben werden. Tabellenwertparameter sind reine Eingabeparameter. Das Schlüsselwort OUTPUT wird nicht unterstützt.  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie in den folgenden Ressourcen.  
  
| Resource                                                                                                             | Beschreibung                                                                         |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [Tabellenwertparameter (Datenbankmodul)](https://go.microsoft.com/fwlink/?LinkId=98363) in der SQL Server-Onlinedokumentation | Beschreibt, wie Sie Tabellenwertparameter erstellen und verwenden.                             |
| [Benutzerdefinierte Tabellentypen](https://go.microsoft.com/fwlink/?LinkId=98364) in der SQL Server-Onlinedokumentation.                  | Beschreibt die benutzerdefinierten Tabellentypen, die zum Deklarieren von Tabellenwertparametern verwendet werden. |
| Der Abschnitt [Microsoft SQL Server-Datenbank-Engine](https://go.microsoft.com/fwlink/?LinkId=120507) von CodePlex.        | Enthält Beispiele, in denen die Verwendung von SQL Server-Features und -Funktionalität veranschaulicht wird.  |
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Übergeben mehrerer Zeilen in früheren Versionen von SQL Server  

Vor der Einführung von Tabellenwertparametern in SQL Server 2008 bestanden nur eingeschränkte Möglichkeiten zum Übergeben mehrerer Datenzeilen an eine gespeicherte Prozedur oder einen parametrisierten SQL-Befehl. Entwickler hatten folgende Möglichkeiten, um mehrere Zeilen an den Server zu übergeben:  
  
- Verwenden von mehreren Einzelparametern zur Darstellung der Werte in mehreren Datenspalten und -zeilen. Die Menge der Daten, die mit dieser Methode übergeben werden können, ist aufgrund der maximal zulässigen Anzahl von Parametern beschränkt. SQL Server-Prozeduren können höchstens über 2100 Parameter verfügen. Um diese Einzelwerte zur Verarbeitung in einer Tabellenvariable oder einer temporären Tabelle zusammenzusetzen, ist serverseitige Logik erforderlich.  
  
- Bündeln mehrerer Datenwerte in Zeichenfolgen mit Trennzeichen oder XML-Dokumenten und Übergeben dieser Textwerte an eine Prozedur oder Anweisung. Bei dieser Vorgehensweise muss die Prozedur oder Anweisung die erforderliche Logik zum Überprüfen der Datenstrukturen und Entbündeln der Werte enthalten.  
  
- Erstellen einer Reihe von SQL-Einzelanweisungen für Datenänderungen, die sich auf mehrere Zeilen auswirken. Änderungen können einzeln an den Server übermittelt oder in Gruppen zusammengefasst werden. Auch wenn sie in Batches übermittelt werden, die mehrere Anweisungen enthalten, wird jede Anweisung einzeln auf dem Server ausgeführt.  
  
- Verwenden des bcp-Hilfsprogramms oder von [SQLServerBulkCopy](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md), um eine Vielzahl von Datenzeilen in eine Tabelle zu laden. Wenngleich dieses Verfahren sehr effizient ist, wird die serverseitige Verarbeitung nur dann unterstützt, wenn die Daten in eine temporäre Tabelle oder Tabellenvariable geladen werden.
  
## <a name="creating-table-valued-parameter-types"></a>Erstellen von Tabellenwertparameter-Typen  

Tabellenwertparameter basieren auf stark typisierten Tabellenstrukturen, die mit `CREATE TYPE`-Anweisungen in Transact-SQL definiert werden. Sie müssen einen Tabellentyp erstellen und die Struktur in SQL Server definieren, bevor Sie Tabellenwertparameter in Ihren Clientanwendungen verwenden können. Weitere Informationen über das Erstellen von Tabellentypen finden Sie unter [Benutzerdefinierte Tabellentypen](https://go.microsoft.com/fwlink/?LinkID=98364) in der SQL Server-Onlinedokumentation.  

```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```

Nachdem Sie einen Tabellentyp erstellt haben, können Sie Tabellenwertparameter basierend auf diesem Typ deklarieren. Das folgende Transact-SQL-Fragment veranschaulicht, wie ein Tabellenwertparameter in der Definition einer gespeicherten Prozedur deklariert wird. Beachten Sie, dass das Schlüsselwort `READONLY` erforderlich ist, um einen Tabellenwertparameter zu deklarieren.  

```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```

## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Ändern von Daten mit Tabellenwertparametern (Transact-SQL)  

Um Tabellenwertparameter bei Datenänderungen zu verwenden, die auf Sätzen basieren und sich auf mehrere Zeilen auswirken, kann eine einzelne Anweisung ausgeführt werden. Beispielsweise können Sie alle Zeilen in einem Tabellenwertparameter auswählen und in eine Datenbanktabelle einfügen, oder Sie können eine update-Anweisung erstellen, indem Sie einen Tabellenwertparameter mit der Tabelle verbinden, die Sie aktualisieren möchten.  
  
Mit der folgenden UPDATE-Anweisung in Transact-SQL wird veranschaulicht, wie ein Tabellenwertparameter durch einen Join mit der Categories-Tabelle verwendet wird. Wenn Sie einen Tabellenwertparameter mit einem JOIN in einer FROM-Klausel verwenden, müssen Sie auch einen Alias angeben, wie in diesem Beispiel gezeigt (der Alias des Tabellenwertparameters lautet „ec“):  

```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```

Dieses Transact-SQL-Beispiel veranschaulicht, wie Zeilen aus einem Tabellenwertparameter ausgewählt werden, um einen INSERT-Vorgang in einem einzelnen mengenbasierten Vorgang auszuführen.

```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```

## <a name="limitations-of-table-valued-parameters"></a>Einschränkungen bei Tabellenwertparametern

Für Tabellenwertparameter gelten verschiedene Einschränkungen:  
  
- Tabellenwertparameter können nicht an benutzerdefinierte Funktionen übergeben werden.  
  
- Tabellenwertparameter können nur für die Unterstützung der UNIQUE- oder PRIMARY KEY-Einschränkungen indiziert werden. SQL Server verwaltet keine Statistiken für Tabellenwertparameter.  
  
- Tabellenwertparameter sind in Transact-SQL-Code schreibgeschützt. Sie können die Spaltenwerte in den Zeilen eines Tabellenwertparameters nicht aktualisieren, und Sie können keine Zeilen einfügen oder löschen. Um die Daten zu ändern, die an eine gespeicherte Prozedur oder eine parametrisierte Anweisung in einem Tabellenwertparameter übergeben werden, müssen Sie die Daten in eine temporäre Tabelle oder in eine Tabellenvariable einfügen.  
  
- Der Aufbau von Tabellenwertparametern kann nicht mithilfe von ALTER TABLE-Anweisungen geändert werden.

- Sie können große Objekte in einen Tabellenwertparameter streamen.  
  
## <a name="configuring-a-table-valued-parameter"></a>Konfigurieren eines Tabellenwertparameters

Ab Version 6.0 des Microsoft-JDBC-Treibers für SQL Server werden Tabellenwertparameter mit parametrisierten Anweisungen oder parametrisierten gespeicherten Prozeduren unterstützt. Tabellenwertparameter können aus einer SQLServerDataTable, einem ResultSet oder einer vom Benutzer bereitgestellten Implementierung der ISQLServerDataRecord-Schnittstelle aufgefüllt werden. Beim Einrichten eines Tabellenwertparameters für eine vorbereitete Abfrage müssen Sie einen Typnamen angeben, der dem Namen eines vergleichbaren, zuvor auf dem Server erstellten Typs entsprechen muss.  
  
Die beiden folgenden Codefragmente veranschaulichen, wie Sie einen Tabellenwertparameter mit einer SQLServerPreparedStatement und einer SQLServerCallableStatement konfigurieren, um Daten einzufügen. Hier kann sourceTVPObject kann ein SQLServerDataTable-, ein ResultSet oder ein ISQLServerDataRecord-Objekt sein. Bei diesem Beispielen wird davon ausgegangen, dass die Verbindung ein aktives Connection-Objekt ist.  

```java
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =
    (SQLServerPreparedStatement) connection.prepareStatement("INSERT INTO dbo.Categories SELECT * FROM ?");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);  
pStmt.execute();  
```

```java
// Using table-valued parameter with a SQLServerCallableStatement.  
SQLServerCallableStatement pStmt =
    (SQLServerCallableStatement) connection.prepareCall("exec usp_InsertCategories ?");
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);;  
pStmt.execute();  
```

> [!NOTE]  
> Eine vollständige Liste der zum Festlegen des Tabellenwertparameters verfügbaren APIs finden Sie im Abschnitt **Tabellenwertparameter-API für den JDBC-Treiber** weiter unten.  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>Übergeben eines Tabellenwertparameters als SQLServerDataTable-Objekt  

Ab Version 6.0 des Microsoft-JDBC-Treibers für SQL Server repräsentiert die SQLServerDataTable-Klasse eine In-Memory-Tabelle mit relationalen Daten. Dieses Beispiel zeigt, wie Sie mithilfe des SQLServerDataTable-Objekts einen Tabellenwertparameter aus In-Memory-Daten konstruieren. Der Code erstellt zunächst ein SQLServerDataTable-Objekt, definiert das zugehörige Schema und füllt die Tabelle mit Daten auf. Dann konfiguriert der Code eine SQLServerPreparedStatement, die diese Daten als Tabellenwertparameter an SQL Server übergibt.  

```java
/* Assumes connection is an active Connection object. */

// Create an in-memory data table.  
SQLServerDataTable sourceDataTable = new SQLServerDataTable();
  
// Define metadata for the data table.  
sourceDataTable.addColumnMetadata("CategoryID" ,java.sql.Types.INTEGER);
sourceDataTable.addColumnMetadata("CategoryName" ,java.sql.Types.NVARCHAR);
  
// Populate the data table.  
sourceDataTable.addRow(1, "CategoryNameValue1");
sourceDataTable.addRow(2, "CategoryNameValue2");
  
// Pass the data table as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
            "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceDataTable);  
pStmt.execute();  
```

> [!NOTE]  
> Eine vollständige Liste der zum Festlegen des Tabellenwertparameters verfügbaren APIs finden Sie im Abschnitt **Tabellenwertparameter-API für den JDBC-Treiber** weiter unten.  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>Übergeben eines Tabellenwertparameters als ResultSet-Objekt  

Dieses Beispiel zeigt, wie Sie Datenzeilen aus einem ResultSet an einen Tabellenwertparameter streamen. Der Code ruft zunächst Daten aus einer Quelltabelle in ein SQLServerDataTable-Objekt ab, definiert das zugehörige Schema und füllt die Tabelle mit Daten auf. Dann konfiguriert der Code eine SQLServerPreparedStatement, die diese Daten als Tabellenwertparameter an SQL Server übergibt.  

```java
/* Assumes connection is an active Connection object. */

// Create the source ResultSet object. Here SourceCategories is a table defined with the same schema as Categories table.
ResultSet sourceResultSet = connection.createStatement().executeQuery("SELECT * FROM SourceCategories");  

// Pass the source result set as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceResultSet);  
pStmt.execute();  
```

> [!NOTE]  
> Eine vollständige Liste der zum Festlegen des Tabellenwertparameters verfügbaren APIs finden Sie im Abschnitt **Tabellenwertparameter-API für den JDBC-Treiber** weiter unten.  

## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>Übergeben eines Tabellenwertparameters als ISQLServerDataRecord-Objekt  

Ab Version 6.0 des Microsoft-JDBC-Treibers für SQL Server ist ein neues ISQLServerDataRecord-Schnittstellenobjekt verfügbar, um Daten mithilfe eines Tabellenwertparameters zu streamen (je nachdem, wie der Benutzer die Implementierung dafür bereitstellt). Das folgende Beispiel zeigt, wie Sie die ISQLServerDataRecord-Schnittstelle implementieren und als Tabellenwertparameter übergeben. Zur Vereinfachung übergibt das folgende Beispiel nur eine Zeile mit hartcodierten Werten an den Tabellenwertparameter. Idealerweise sollte der Benutzer diese Schnittstelle implementieren, um Zeilen aus einer beliebigen Quelle zu streamen, z. B. aus Textdateien.  

```java
class MyRecords implements ISQLServerDataRecord  
{  
    int currentRow = 0;  
    Object[] row = new Object[2];  
  
    MyRecords(){  
        // Constructor. This implementation has just one row.
        row[0] = new Integer(1);  
        row[1] = "categoryName1";  
    }  
  
    public int getColumnCount(){  
        // Return the total number of columns, for this example it is 2.  
        return 2;  
    }  
  
    public SQLServerMetaData getColumnMetaData(int columnIndex) {  
        // Return the column metadata.  
        if (1 == columnIndex)  
            return new SQLServerMetaData("CategoryID", java.sql.Types.INTEGER);  
        else  
            return new SQLServerMetaData("CategoryName", java.sql.Types.NVARCHAR);  
    }  
  
    public Object[] getRowData(){  
        // Return the columns in the current row as an array of objects. This implementation has just one row.  
        return row;
    }  
  
    public boolean next(){  
        // Move to the next row. This implementation has just one row, after processing the first row, return false.  
        currentRow++;  
        if (1 == currentRow)  
            return true;  
        else  
            return false;  
    }
}

// Following code demonstrates how to pass MyRecords object as a table-valued parameter.  
MyRecords sourceRecords = new MyRecords();  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceRecords);  
pStmt.execute();  
```

> [!NOTE]  
> Eine vollständige Liste der zum Festlegen des Tabellenwertparameters verfügbaren APIs finden Sie im Abschnitt **Tabellenwertparameter-API für den JDBC-Treiber** weiter unten.

## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>Tabellenwertparameter-API für den JDBC-Treiber

### <a name="sqlservermetadata"></a>SQLServerMetaData

Diese Klasse repräsentiert Metadaten für eine Spalte. Sie wird in der ISQLServerDataRecord-Schnittstelle verwendet, um Spaltenmetadaten an den Tabellenwertparameter zu übergeben. Diese Klasse enthält folgende Methoden:  

| Name                                                                                                                                                                             | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData(String columnName, int sqlType, int precision, int scale, boolean useServerDefault, boolean isUniqueKey, SQLServerSortOrder sortOrder, int sortOrdinal) | Initialisiert eine neue Instanz von SQLServerMetaData mit dem angegebenen Werten für Spaltenname, SQL-Typ, Genauigkeit, Dezimalstellen und Serverstandardwert. Diese Form des Konstruktors unterstützt Tabellenwertparameter: Sie können angeben, ob die Spalte im Tabellenwertparameter eindeutig ist, und Sie können die Sortierreihenfolge für die Spalte sowie die Ordnungszahl der Sortierspalte festlegen. <br/><br/>useServerDefault - – gibt an, ob diese Spalte den Serverstandardwert verwenden soll. Der Standardwert lautet „false“.<br>isUniqueKey – gibt an, ob die Spalte im Tabellenwertparameter eindeutig ist. Der Standardwert lautet „false“.<br>sortOrder  – gibt die Sortierreihenfolge für eine Spalte an. Der Standardwert lautet „SQLServerSortOrder.Unspecified“.<br>sortOrdinal – gibt die Ordnungszahl der Sortierspalte an. Die Werte für sortOrdinal beginnen bei 0, der Standardwert lautet „-1“. |
| public SQLServerMetaData( String columnName, int sqlType)                                                                                                                        | Initialisiert unter Verwendung des Spaltennamens und des SQL-Typs eine neue Instanz von SQLServerMetaData.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| public SQLServerMetaData( String columnName, int sqlType, int length)                                                                                                                        | Initialisiert unter Verwendung des Spaltennamens, des SQL-Typs und der Länge (bei Zeichenfolgendaten) eine neue Instanz von SQLServerMetaData. Der Wert für „length“ wird verwendet, um umfangreiche Zeichenfolgen von Zeichenfolgen zu unterscheiden, die kürzer als 4000 Zeichen sind. Wurde in Version 7.2 des JDBC-Treibers eingeführt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public SQLServerMetaData( String columnName, int sqlType, int precision, int scale)                                                                                              | Initialisiert unter Verwendung von Spaltennamen, SQL-Typ, Genauigkeit und Dezimalstellen eine neue Instanz von SQLServerMetaData.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Public SQLServerMetaData(SQLServerMetaData sqlServerMetaData)                                                                                                                    | Initialisiert eine neue Instanz von SQLServerMetaData aus einem anderen SQLServerMetaData-Objekt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| public String getColumName()                                                                                                                                                     | Ruft den Spaltennamen ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| public int getSqlType()                                                                                                                                                          | Ruft den Java-SQL-Typ ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| public int getPrecision()                                                                                                                                                        | Ruft die Genauigkeit des an die Spalte übergebenen Typs ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| public int getScale()                                                                                                                                                            | Ruft die Dezimalstellen des an die Spalte übergebenen Typs ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public SQLServerSortOrder getSortOrder()                                                                                                                                         | Ruft die Sortierreihenfolge ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| public int getSortOrdinal()                                                                                                                                                      | Ruft die Ordnungszahl der Sortierspalte ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public boolean isUniqueKey()                                                                                                                                                     | Gibt Informationen darüber zurück, ob die Spalte eindeutig ist.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public boolean useServerDefault()                                                                                                                                                | Gibt Informationen darüber zurück, ob die Spalte den Standardwert für den Server verwendet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  
### <a name="sqlserversortorder"></a>SQLServerSortOrder

Eine Enumeration, die die Sortierreihenfolge definiert. Mögliche Werte: „Ascending“, „Descending“ und „Unspecified“.
  
### <a name="sqlserverdatatable"></a>SQLServerDataTable

Diese Klasse repräsentiert eine In-Memory-Datentabelle, die mit Tabellenwertparametern verwendet werden soll. Diese Klasse enthält folgende Methoden:  

| Name                                                          | Beschreibung                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| Public SQLServerDataTable()                                   | Initialisiert eine neue Instanz von SQLServerDataTable.    |
| public Iterator<Entry\<Integer, Object[]>> getIterator()      | Ruft einen Iterator für die Zeilen der Datentabelle ab. |
| public void addColumnMetadata(String columnName, int sqlType) | Fügt Metadaten für die angegebene Spalte hinzu.              |
| public void addColumnMetadata(SQLServerDataColumn column)     | Fügt Metadaten für die angegebene Spalte hinzu.              |
| public void addRow(Object... values)                          | Fügt der Datentabelle eine Datenzeile hinzu.              |
| public Map\<Integer, SQLServerDataColumn> getColumnMetadata() | Ruft Spaltenmetadaten dieser Datentabelle ab.       |
| public void clear()                                           | Leert diese Datentabelle.                              |

### <a name="sqlserverdatacolumn"></a>SQLServerDataColumn

Diese Klasse repräsentiert eine Spalte der In-Memory-Datentabelle, die durch SQLServerDataTable dargestellt wird. Diese Klasse enthält folgende Methoden:  

| Name                                                       | Beschreibung                                                                      |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------- |
| public SQLServerDataColumn(String columnName, int sqlType) | Initialisiert unter Verwendung des Spaltennamens und des SQL-Typs eine neue Instanz von SQLServerDataColumn. |
| public String getColumnName()                              | Ruft den Spaltennamen ab.                                                       |
| public int getColumnType()                                 | Ruft den Spaltentyp ab.                                                       |

### <a name="isqlserverdatarecord"></a>ISQLServerDataRecord

Diese Klasse repräsentiert eine Schnittstelle, die Benutzer zum Streamen von Daten in einen Tabellenwertparameter implementieren können. Diese Schnittstelle enthält folgende Methoden:  
  
| Name                                                    | Beschreibung                                                                                             |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData getColumnMetaData(int column); | Ruft die Spaltenmetadaten des angegebenen Spaltenindex ab.                                               |
| public int getColumnCount();                            | Ruft die Gesamtanzahl von Spalten ab.                                                                  |
| public Object[] getRowData();                           | Ruft die Daten für die aktuelle Zeile als Array von Objekten ab.                                          |
| public boolean next();                                  | Wechselt zur nächsten Zeile. Gibt „true“ zurück, wenn der Wechsel erfolgreich und eine nächste Zeile vorhanden ist. Andernfalls wird „false“ zurückgegeben. |

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

Die folgenden Methoden wurden dieser Klasse hinzugefügt, um die Übergabe von Tabellenwertparametern zu unterstützen.  

| Name                                                                                                    | Beschreibung                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public final void setStructured(int parameterIndex, String tvpName, SQLServerDataTable tvpDataTable)    | Füllt einen Tabellenwertparameter mit einer Datentabelle auf. parameterIndex ist der Parameterindex, tvpName ist der Name des Tabellenwertparameters, und tvpDataTable ist das Quelldatentabellenobjekt.                                                                                                          |
| public final void setStructured(int parameterIndex, String tvpName, ResultSet tvpResultSet)             | Füllt einen Tabellenwertparameter mit einem aus einer anderen Tabelle abgerufenen ResultSet auf. parameterIndex ist der Parameterindex, tvpName ist der Name des Tabellenwertparameters, und tvpResultSet ist das Quellresultsetobjekt.                                                                               |
| public final void setStructured(int parameterIndex, String tvpName, ISQLServerDataRecord tvpDataRecord) | Füllt einen Tabellenwertparameter mit einem ISQLServerDataRecord-Objekt auf. ISQLServerDataRecord wird zum Streamen von Daten verwendet, und der Benutzer entscheidet, wie die Verwendung erfolgt. parameterIndex ist der Parameterindex, tvpName ist der Name des Tabellenwertparameters, und tvpDataRecord ist ein ISQLServerDataRecord-Objekt. |
  
### <a name="sqlservercallablestatement"></a>SQLServerCallableStatement

Die folgenden Methoden wurden dieser Klasse hinzugefügt, um die Übergabe von Tabellenwertparametern zu unterstützen.  
  
| Name                                                                                                        | Beschreibung                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public final void setStructured(String parameterName, String tvpName, SQLServerDataTable tvpDataTable)    | Füllt einen an eine gespeicherte Prozedur übergebenen Tabellenwertparameter mit einer Datentabelle auf. parameterName ist der Name des Parameters, tvpName ist der Name des Tabellenwertparametertyps, und tvpDataTable ist das Datentabellenobjekt.                                                                                                                 |
| public final void setStructured(String parameterName, String tvpName, ResultSet tvpResultSet)             | Füllt einen an eine gespeicherte Prozedur übergebenen Tabellenwertparameter mit einem aus einer anderen Tabelle abgerufenen ResultSet auf. parameterName ist der Name des Parameters, tvpName ist der Name des Tabellenwertparametertyps, und tvpResultSet ist das Quellresultsetobjekt.                                                                              |
| public final void setStructured(String parameterName, String tvpName, ISQLServerDataRecord tvpDataRecord) | Füllt einen an eine gespeicherte Prozedur übergebenen Tabellenwertparameter mit einem ISQLServerDataRecord-Objekt auf. ISQLServerDataRecord wird zum Streamen von Daten verwendet, und der Benutzer entscheidet, wie die Verwendung erfolgt. parameterName ist der Name des Parameters, tvpName ist der Name des Tabellenwertparametertyps, und tvpDataRecord ist ein ISQLServerDataRecord-Objekt. |

## <a name="see-also"></a>Weitere Informationen

[Übersicht über den JDBC-Treiber](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
