---
title: Verwenden von Tabellenwert Parametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 98863afb5a47eddfd311563bd03a1c7c7120b161
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69025710"
---
# <a name="using-table-valued-parameters"></a>Verwenden von Tabellenwertparametern

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Tabellenwertparameter bieten eine einfache Möglichkeit zum Marshallen mehrerer Datenzeilen aus einer Clientanwendung nach SQL Server, ohne dass mehrere Roundtrips oder eine spezielle serverseitige Logik für die Verarbeitung der Daten erforderlich sind. Sie können Tabellenwertparameter verwenden, um Datenzeilen in einer Clientanwendung zu kapseln und die Daten in einem einzigen parametrisierten Befehl an den Server zu senden. Die eingehenden Datenzeilen werden in einer Tabellenvariablen gespeichert, die Sie dann mithilfe von Transact-SQL bearbeiten können.  
  
Auf Spaltenwerte in Tabellenwert Parametern kann mit standardmäßigen Transact-SQL-SELECT-Anweisungen zugegriffen werden. Tabellenwert Parameter sind stark typisiert, und ihre Struktur wird automatisch überprüft. Die Größe der Tabellenwert Parameter wird nur durch den Server Arbeitsspeicher beschränkt.  
  
> [!NOTE]  
> Die Unterstützung für Tabellenwert Parameter ist ab dem Microsoft JDBC-Treiber 6,0 für SQL Server verfügbar.
>
> Sie können keine Daten in einem Tabellenwert Parameter zurückgeben. Tabellenwert Parameter sind nur Eingabewerte. das OUTPUT-Schlüsselwort wird nicht unterstützt.  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie in den folgenden Ressourcen.  
  
| Ressource                                                                                                             | und Beschreibung                                                                         |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [Tabellenwert Parameter (Datenbank-Engine)](https://go.microsoft.com/fwlink/?LinkId=98363) in SQL Server-Onlinedokumentation | Beschreibt das Erstellen und Verwenden von Tabellenwert Parametern.                             |
| [Benutzerdefinierte Tabellentypen](https://go.microsoft.com/fwlink/?LinkId=98364) in SQL Server-Onlinedokumentation                  | Beschreibt benutzerdefinierte Tabellentypen, die zum Deklarieren von Tabellenwert Parametern verwendet werden. |
| Der Abschnitt " [Microsoft SQL Server Datenbank-Engine](https://go.microsoft.com/fwlink/?LinkId=120507) " von CodePlex        | Enthält Beispiele, die veranschaulichen, wie SQL Server Features und Funktionen verwendet werden.  |
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Übergeben mehrerer Zeilen in früheren Versionen von SQL Server  

Vor der Einführung von Tabellenwert Parametern in SQL Server 2008 waren die Optionen zum Übergeben mehrerer Daten Zeilen an eine gespeicherte Prozedur oder einen parametrisierten SQL-Befehl eingeschränkt. Ein Entwickler kann aus den folgenden Optionen auswählen, um mehrere Zeilen an den Server zu übergeben:  
  
- Verwenden Sie eine Reihe einzelner Parameter, um die Werte in mehreren Spalten und Zeilen der Daten darzustellen. Die Menge der Daten, die mit dieser Methode übermittelt werden kann, ist durch die zulässige Anzahl von Parametern beschränkt. SQL Server Prozeduren können höchstens 2100 Parameter aufweisen. Server seitige Logik ist erforderlich, um diese einzelnen Werte für die Verarbeitung in einer Tabellen Variablen oder einer temporären Tabelle zusammenzufassen.  
  
- Bündeln Sie mehrere Datenwerte in durch Trennzeichen getrennte Zeichen folgen oder XML-Dokumente, und übergeben Sie diese Text Werte dann an eine Prozedur oder Anweisung. Hierfür ist es erforderlich, dass die Prozedur oder die Anweisung die erforderliche Logik zum Überprüfen der Datenstrukturen und zur Entflechtung der Werte einschließt.  
  
- Erstellen Sie eine Reihe von einzelnen SQL-Anweisungen für Datenänderungen, die sich auf mehrere Zeilen auswirken. Änderungen können einzeln an den Server übermittelt oder in Gruppen zusammengefasst werden. Auch wenn Sie in Batches übermittelt werden, die mehrere-Anweisungen enthalten, wird jede-Anweisung separat auf dem Server ausgeführt.  
  
- Verwenden Sie das Hilfsprogramm bcp oder das [sqlserverbulkcopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy(v=vs.110).aspx) -Objekt, um viele Daten Zeilen in eine Tabelle zu laden. Obwohl dieses Verfahren sehr effizient ist, wird die serverseitige Verarbeitung nur dann unterstützt, wenn die Daten in eine temporäre Tabelle oder Tabellen Variable geladen werden.  
  
## <a name="creating-table-valued-parameter-types"></a>Erstellen von Tabellenwert Parameter-Typen  

Tabellenwert Parameter basieren auf stark typisierten Tabellenstrukturen, die mithilfe von Transact-SQL `CREATE TYPE` -Anweisungen definiert werden. Sie müssen einen Tabellentyp erstellen und die Struktur in SQL Server definieren, bevor Sie Tabellenwert Parameter in Ihren Client Anwendungen verwenden können. Weitere Informationen zum Erstellen von Tabellentypen finden Sie unter [Benutzerdefinierte Tabellentypen](https://go.microsoft.com/fwlink/?LinkID=98364) in SQL Server-Onlinedokumentation.  

```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```

Nachdem Sie einen Tabellentyp erstellt haben, können Sie Tabellenwert Parameter basierend auf diesem Typ deklarieren. Das folgende Transact-SQL-Fragment veranschaulicht, wie ein Tabellenwert Parameter in der Definition einer gespeicherten Prozedur deklariert wird. Beachten Sie, `READONLY` dass das-Schlüsselwort zum Deklarieren eines Tabellenwert Parameters erforderlich ist.  

```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```

## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Ändern von Daten mit Tabellenwert Parametern (Transact-SQL)  

Tabellenwert Parameter können in Satz basierten Datenänderungen verwendet werden, die sich auf mehrere Zeilen auswirken, indem eine einzige Anweisung ausgeführt wird. Beispielsweise können Sie alle Zeilen in einem Tabellenwert Parameter auswählen und in eine Datenbanktabelle einfügen, oder Sie können eine Update-Anweisung erstellen, indem Sie einen Tabellenwert Parameter mit der Tabelle verbinden, die Sie aktualisieren möchten.  
  
Die folgende Transact-SQL-Update-Anweisung veranschaulicht, wie Sie einen Tabellenwert Parameter verwenden, indem Sie ihn mit der Categories-Tabelle verbinden. Wenn Sie einen Tabellenwert Parameter mit einem Join in einer from-Klausel verwenden, müssen Sie diesen ebenfalls als Alias angeben, wie hier gezeigt, wobei der Tabellenwert Parameter als "EC" Alias verwendet wird:  

```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```

Dieses Transact-SQL-Beispiel veranschaulicht, wie Zeilen aus einem Tabellenwert Parameter ausgewählt werden, um einen INSERT-Vorgang in einem einzelnen Satz basierten Vorgang auszuführen.

```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```

## <a name="limitations-of-table-valued-parameters"></a>Einschränkungen von Tabellenwert Parametern

Es gibt mehrere Einschränkungen für Tabellenwert Parameter:  
  
- Tabellenwert Parameter können nicht an benutzerdefinierte Funktionen übergeben werden.  
  
- Tabellenwert Parameter können nur indiziert werden, um Unique-oder PRIMARY KEY-Einschränkungen zu unterstützen. SQL Server verwaltet keine Statistiken für Tabellenwertparameter.  
  
- Tabellenwert Parameter sind im Transact-SQL-Code schreibgeschützt. Sie können die Spaltenwerte in den Zeilen eines Tabellenwert Parameters nicht aktualisieren, und Sie können keine Zeilen einfügen oder löschen. Um die Daten zu ändern, die an eine gespeicherte Prozedur oder eine parametrisierte Anweisung in einem Tabellenwert Parameter übergeben werden, müssen Sie die Daten in eine temporäre Tabelle oder in eine Tabellen Variable einfügen.  
  
- ALTER TABLE-Anweisungen können nicht zum Ändern des Entwurfs von Tabellenwert Parametern verwendet werden.

- Sie können große Objekte in einem Tabellenwert Parameter streamen.  
  
## <a name="configuring-a-table-valued-parameter"></a>Konfigurieren eines Tabellenwertparameters

Beginnend mit dem Microsoft JDBC-Treiber 6,0 für SQL Server werden Tabellenwert Parameter mit einer parametrisierten-Anweisung oder einer parametrisierten gespeicherten Prozedur unterstützt. Tabellenwert Parameter können aus einer sqlserverdattable, einem Resultset oder einer vom Benutzer bereitgestellten Implementierung der isqlserverdatarecord-Schnittstelle ausgefüllt werden. Wenn Sie einen Tabellenwert Parameter für eine vorbereitete Abfrage festlegen, müssen Sie einen Typnamen angeben, der dem Namen eines kompatiblen Typs entsprechen muss, der zuvor auf dem Server erstellt wurde.  
  
Die folgenden beiden Code Fragmente veranschaulichen, wie Sie einen Tabellenwert Parameter mit SQLServerPreparedStatement und mit einem SQLServerCallableStatement zum Einfügen von Daten konfigurieren. Sourcetvpobject kann ein sqlserverdattable-oder ein Resultset-oder ein isqlserverdatarecord-Objekt sein. In den Beispielen wird angenommen, dass die Verbindung ein aktives Verbindungs Objekt ist.  

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
> Eine umfassende Liste der APIs, die zum Festlegen des Tabellenwert Parameters verfügbar sind, finden Sie unten im Abschnitt **Tabellenwert Parameter-API für den JDBC-Treiber** .  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>Übergeben eines Tabellenwert Parameters als sqlserverdattial-Objekt  

Beginnend mit dem Microsoft JDBC-Treiber 6,0 für SQL Server stellt die sqlserverdatabel-Klasse eine in-Memory-Tabelle mit relationalen Daten dar. In diesem Beispiel wird veranschaulicht, wie ein Tabellenwert Parameter aus in-Memory-Daten mithilfe des sqlserverdattable-Objekts erstellt wird. Der Code erstellt zunächst ein sqlserverdattable-Objekt, definiert das zugehörige Schema und füllt die Tabelle mit Daten auf. Der Code konfiguriert dann eine SQLServerPreparedStatement, die diese Datentabelle als Tabellenwert Parameter an SQL Server übergibt.  

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
> Eine umfassende Liste der APIs, die zum Festlegen des Tabellenwert Parameters verfügbar sind, finden Sie unten im Abschnitt **Tabellenwert Parameter-API für den JDBC-Treiber** .  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>Übergeben eines Tabellenwert Parameters als Resultset-Objekt  

In diesem Beispiel wird veranschaulicht, wie Daten Zeilen aus einem Resultset in einen Tabellenwert Parameter gestreamt werden. Der Code ruft zunächst Daten aus einer Quell Tabelle in einem-Objekt ab, erstellt ein sqlserverdattable-Objekt, definiert das zugehörige Schema und füllt die Tabelle mit Daten auf. Der Code konfiguriert dann eine SQLServerPreparedStatement, die diese Datentabelle als Tabellenwert Parameter an SQL Server übergibt.  

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
> Eine umfassende Liste der APIs, die zum Festlegen des Tabellenwert Parameters verfügbar sind, finden Sie unten im Abschnitt **Tabellenwert Parameter-API für den JDBC-Treiber** .  

## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>Übergeben eines Tabellenwert Parameters als isqlserverdatarecord-Objekt  

Ab dem Microsoft JDBC-Treiber 6,0 für SQL Server ist eine neue Schnittstelle isqlserverdatarecord zum Streamen von Daten (abhängig davon, wie der Benutzer die Implementierung bereitstellt) mithilfe eines Tabellenwert Parameters verfügbar. Im folgenden Beispiel wird veranschaulicht, wie die isqlserverdatarecord-Schnittstelle implementiert wird und wie Sie als Tabellenwert Parameter übergeben wird. Der Einfachheit halber übergibt das folgende Beispiel nur eine Zeile mit hart codierten Werten an den Tabellenwert Parameter. Im Idealfall würde der Benutzer diese Schnittstelle implementieren, um Zeilen aus beliebigen Quellen zu streamen, z. b. aus Textdateien.  

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
> Eine umfassende Liste der APIs, die zum Festlegen des Tabellenwert Parameters verfügbar sind, finden Sie unten im Abschnitt **Tabellenwert Parameter-API für den JDBC-Treiber** .

## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>Tabellenwert Parameter-API für den JDBC-Treiber

### <a name="sqlservermetadata"></a>SQLServerMetaData

Diese Klasse stellt Metadaten für eine Spalte dar. Sie wird in der isqlserverdatarecord-Schnittstelle verwendet, um Spalten Metadaten an den Tabellenwert Parameter zu übergeben. Die Methoden in dieser Klasse lauten:  

| Name                                                                                                                                                                             | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Public sqlservermetadata (String ColumnName, int SQLType, int Precision, int Scale, booleschen \eserverdefault, booleschen IsUniqueKey, sqlserversortorder SortOrder, int sortordin.) | Initialisiert eine neue Instanz von sqlservermetadata mit den Angaben für den Spaltennamen, den SQL-Typ, die Genauigkeit, die Skala und den Server Standardwert. Diese Form des Konstruktors unterstützt Tabellenwert Parameter, indem es Ihnen ermöglicht, anzugeben, ob die Spalte im Tabellenwert Parameter eindeutig ist, die Sortierreihenfolge für die Spalte und die Ordnungszahl der Sortier Spalte. <br/><br/>"Windows Server default": gibt an, ob für diese Spalte der Standard Server Wert verwendet werden soll. Der Standardwert ist false.<br>IsUniqueKey: gibt an, ob die Spalte im Tabellenwert Parameter eindeutig ist. Der Standardwert ist false.<br>sortor: gibt die Sortierreihenfolge für eine Spalte an. Der Standardwert ist sqlserversortor der. nicht angegeben.<br>sortoriale-gibt die Ordnungszahl der Sortier Spalte an. sortorion beginnt bei 0. Der Standardwert ist-1. |
| Public sqlservermetadata (String ColumnName, int sqlType)                                                                                                                        | Initialisiert eine neue Instanz von sqlservermetadata unter Verwendung des Spaltennamens und des SQL-Typs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Public sqlservermetadata (String ColumnName, int SQLType, int length)                                                                                                                        | Initialisiert eine neue Instanz von sqlservermetadata unter Verwendung des Spaltennamens, des SQL-Typs und der Länge (für Zeichen folgen Daten). Die Länge wird verwendet, um große Zeichen folgen aus Zeichen folgen mit einer Länge von weniger als 4000 Zeichen zu unterscheiden. Eingeführt in Version 7,2 des JDBC-Treibers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Public sqlservermetadata (String ColumnName, int SQLType, int Precision, int Scale)                                                                                              | Initialisiert eine neue Instanz von sqlservermetadata unter Verwendung des Spaltennamens, des SQL-Typs, der Genauigkeit und der Skala.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Public sqlservermetadata (sqlservermetadata sqlservermetadata)                                                                                                                    | Initialisiert eine neue Instanz von sqlservermetadata aus einem anderen sqlservermetadata-Objekt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| public String getColumName()                                                                                                                                                     | Ruft den Spaltennamen ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| public int getSqlType()                                                                                                                                                          | Ruft den Java-SQL-Typ ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| public int getPrecision ()                                                                                                                                                        | Ruft die Genauigkeit des an die Spalte über gebenden Typs ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| öffentliches int getScale ()                                                                                                                                                            | Ruft die Skala des an die Spalte über gebenden Typs ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public SQLServerSortOrder getSortOrder()                                                                                                                                         | Ruft die Sortierreihenfolge ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| public int getsortor ()                                                                                                                                                      | Ruft die Sortier Ordinalzahl ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public boolean isUniqueKey()                                                                                                                                                     | Gibt zurück, ob die Spalte eindeutig ist.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public boolean useServerDefault()                                                                                                                                                | Gibt zurück, ob die Spalte den Standard Server Wert verwendet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  
### <a name="sqlserversortorder"></a>SQLServerSortOrder

Eine-Aufzählung, die die Sortierreihenfolge definiert. Mögliche Werte sind aufsteigend, absteigend und nicht angegeben.
  
### <a name="sqlserverdatatable"></a>SQLServerDataTable

Diese Klasse stellt eine in-Memory-Datentabelle dar, die mit Tabellenwert Parametern verwendet werden soll. Die Methoden in dieser Klasse lauten:  

| Name                                                          | und Beschreibung                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| Public sqlserverdatabel ()                                   | Initialisiert eine neue Instanz von sqlserverdatabel.    |
| public Iterator<Entry\<Integer, Object[]>> getIterator()      | Ruft einen Iterator für die Zeilen der Datentabelle ab. |
| public void addColumnMetadata(String columnName, int sqlType) | Fügt Metadaten für die angegebene Spalte hinzu.              |
| öffentliches void addcolumnmetadata (sqlserverdatacolenn-Spalte)     | Fügt Metadaten für die angegebene Spalte hinzu.              |
| öffentliches void AddRow (Objekt... Werte                          | Fügt der Datentabelle eine Daten Zeile hinzu.              |
| öffentliche Karten\<Ganzzahl, sqlserverdatacolumschlag > getcolumnmetadata () | Ruft Spalten Metadaten dieser Datentabelle ab.       |
| public void clear()                                           | Löscht diese Datentabelle.                              |

### <a name="sqlserverdatacolumn"></a>SQLServerDataColumn

Diese Klasse stellt eine Spalte der in-Memory-Datentabelle dar, die von sqlserverdatabel dargestellt wird. Die Methoden in dieser Klasse lauten:  

| Name                                                       | und Beschreibung                                                                      |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Public sqlserverdatacolumschlag (String ColumnName, int sqlType) | Initialisiert eine neue Instanz von sqlserverdatacolenn mit dem Spaltennamen und dem Typ. |
| public String getColumnName()                              | Ruft den Spaltennamen ab.                                                       |
| public int GetColumnType ()                                 | Ruft den Spaltentyp ab.                                                       |

### <a name="isqlserverdatarecord"></a>ISQLServerDataRecord

Diese Klasse stellt eine Schnittstelle dar, die Benutzer implementieren können, um Daten in einen Tabellenwert Parameter zu streamen. Die Methoden in dieser Schnittstelle lauten wie folgt:  
  
| Name                                                    | und Beschreibung                                                                                             |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Public sqlservermetadata getcolumnmetadata (int-Spalte); | Ruft die Spalten Metadaten des angegebenen Spalten Indexes ab.                                               |
| public int getColumnCount();                            | Ruft die Gesamtanzahl der Spalten ab.                                                                  |
| public Object[] getRowData();                           | Ruft die Daten für die aktuelle Zeile als Array von Objekten ab.                                          |
| public boolean next();                                  | Wechselt zur nächsten Zeile. Gibt "true" zurück, wenn die Verschiebung erfolgreich war und eine nächste Zeile vorhanden ist, andernfalls "false". |

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

Die folgenden Methoden wurden dieser Klasse hinzugefügt, um das Übergeben von Tabellenwert Parametern zu unterstützen.  

| Name                                                                                                    | und Beschreibung                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public final void setStructured(int parameterIndex, String tvpName, SQLServerDataTable tvpDataTable)    | Füllt einen Tabellenwert Parameter mit einer Datentabelle auf. Parameterindex ist der Parameter Index, tvpname ist der Name des Tabellenwert Parameters, und tvpdattable ist das Quelldaten Tabellenobjekt.                                                                                                          |
| public final void setstrukturierte (int parameterIndex, String tvpname, Resultset tvpresultset)             | Füllt einen Tabellenwert Parameter mit einem Resultset auf, das aus einer anderen Tabelle abgerufen wurde. Parameterindex ist der Parameter Index, tvpname ist der Name des Tabellenwert Parameters, und tvpresultset ist das Quellresultset-Objekt.                                                                               |
| public final void setStructured(int parameterIndex, String tvpName, ISQLServerDataRecord tvpDataRecord) | Füllt einen Tabellenwert Parameter mit einem isqlserverdatarecord-Objekt auf. Isqlserverdatarecord wird zum Streamen von Daten verwendet, und der Benutzer entscheidet, wie er verwendet werden soll. Parameterindex ist der Parameter Index, tvpname ist der Name des Tabellenwert Parameters, und tvpdatarecord ist ein isqlserverdatarecord-Objekt. |
  
### <a name="sqlservercallablestatement"></a>SQLServerCallableStatement

Die folgenden Methoden wurden dieser Klasse hinzugefügt, um das Übergeben von Tabellenwert Parametern zu unterstützen.  
  
| Name                                                                                                        | und Beschreibung                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| öffentliches Finale void setstrukturiert (Zeichenfolge Parameter Name, String tvpname, sqlserverdatabel tvpdatabel)    | Füllt einen Tabellenwert Parameter auf, der mit einer Datentabelle an eine gespeicherte Prozedur übergeben wird. "Parameter Name" ist der Name des Parameters, "tvpname" ist der Name des Typs "TVP", und "tvpdattable" ist das Datentabellen Objekt.                                                                                                                 |
| öffentliches Finale void setstrukturierte (String Elementname, String tvpname, Resultset tvpresultset)             | Füllt einen Tabellenwert Parameter auf, der an eine gespeicherte Prozedur übergeben wird, wobei ein Resultset aus einer anderen Tabelle abgerufen wird. Parameter Name ist der Name des Parameters, tvpname ist der Name des Typs TVP, und tvpresultset ist das Quellresultset-Objekt.                                                                              |
| öffentliches Finale void setstrukturierte (String Elementname, String tvpname, isqlserverdatarecord tvpdatarecord) | Füllt einen Tabellenwert Parameter auf, der mit einem isqlserverdatarecord-Objekt an eine gespeicherte Prozedur übergeben wird. Isqlserverdatarecord wird zum Streamen von Daten verwendet, und der Benutzer entscheidet, wie er verwendet werden soll. Parameter Name ist der Name des Parameters, tvpname ist der Name des Typs TVP, und tvpdatarecord ist ein isqlserverdatarecord-Objekt. |

## <a name="see-also"></a>Siehe auch

[Übersicht über den JDBC-Treiber](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
