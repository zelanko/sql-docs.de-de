---
title: Verwenden von Tabellenwertparametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99c1123ae138baf883d883731ba8749bae54ae85
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662392"
---
# <a name="using-table-valued-parameters"></a>Verwenden von Tabellenwertparametern

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Tabellenwertparameter bieten eine einfache Möglichkeit zum Marshallen mehrerer Datenzeilen aus einer Clientanwendung nach SQL Server, ohne dass mehrere Roundtrips oder eine spezielle serverseitige Logik für die Verarbeitung der Daten erforderlich sind. Sie können Tabellenwertparameter verwenden, um Datenzeilen in einer Clientanwendung zu kapseln und die Daten in einem einzigen parametrisierten Befehl an den Server zu senden. Die eingehenden Datenzeilen werden in einer Tabellenvariablen gespeichert, die dann verarbeitet werden können mithilfe von Transact-SQL.  
  
Spaltenwerte in Tabellenwertparametern können unter Verwendung von Transact-SQL SELECT-standardanweisungen zugegriffen werden. Tabellenwertparameter sind stark typisiert, und deren Struktur wird automatisch überprüft. Die Größe der Tabellenwertparameter wird nur vom Serverarbeitsspeicher beschränkt.  
  
> [!NOTE]  
> Unterstützung für Tabellenwertparameter ist ab Microsoft JDBC-Treiber 6.0 für SQL Server zur Verfügung.
>
> Sie können keine Daten in einem Table-valued Parameter zurückgeben. Tabellenwertparameter sind reine; Die OUTPUT-Schlüsselwort wird nicht unterstützt.  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter den folgenden Ressourcen.  
  
| Ressource                                                                                                             | und Beschreibung                                                                         |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [Tabellenwertparameter (Datenbankmodul)](http://go.microsoft.com/fwlink/?LinkId=98363) in SQL Server-Onlinedokumentation | Beschreibt, wie zum Erstellen und Verwenden von Tabellenwertparametern                             |
| [Benutzerdefinierte Tabellentypen](http://go.microsoft.com/fwlink/?LinkId=98364) in SQL Server-Onlinedokumentation                  | Beschreibt benutzerdefinierte Tabellentypen, die zum Deklarieren von Tabellenwertparametern verwendet werden |
| Die [Microsoft SQL Server-Datenbank-Engine](http://go.microsoft.com/fwlink/?LinkId=120507) Abschnitt von CodePlex        | Enthält Beispiele, die veranschaulichen, wie Sie mit der SQL Server-Features und Funktionen  |
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Übergeben von mehreren Zeilen in früheren Versionen von SQLServer  

Bevor Sie Tabellenwertparameter in SQL Server 2008 eingeführt wurden, konnten die Optionen zum Übergeben mehrerer Datenzeilen an eine gespeicherte Prozedur oder einen parametrisierten SQL‑Befehl. Ein Entwickler konnte aus den folgenden Optionen zum Übergeben mehrerer Zeilen an den Server auswählen:  
  
- Verwenden Sie eine Reihe einzelner Parameter, um die Werte in mehreren Spalten und Zeilen mit Daten darzustellen. Die Menge der Daten, die mit dieser Methode übergeben werden können, wird durch die Anzahl der zulässigen Parameter beschränkt. SQL Server-Prozeduren können, höchstens über 2100 Parameter verfügen. Serverseitige Logik ist erforderlich, um diese einzelnen Werte in eine Tabellenvariable oder eine temporäre Tabelle für die Verarbeitung zu assemblieren.  
  
- Bündeln Sie mehrere Datenwerte in voneinander getrennten Zeichenfolgen oder XML-Dokumente, und übergeben Sie diese Textwerte anschließend an eine Prozedur oder Anweisung zu. Dies erfordert die Prozedur oder Anweisung, um die erforderliche Logik zum Überprüfen der Datenstrukturen und Entbündeln enthalten die Werte.  
  
- Erstellen Sie eine Reihe von einzelnen SQL-Anweisungen für datenänderungen, die mehrere Zeilen betreffen. Änderungen können an den Server gesendet wurde, einzeln oder in Gruppen zusammengefasst werden. Allerdings wird auch verwendet werden, wenn in Stapeln übermittelt, die mehrere Anweisungen enthalten, jede Anweisung separat auf dem Server ausgeführt.  
  
- Verwenden Sie das Bcp-Hilfsprogramm-Programm oder die ["sqlserverbulkcopy"](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy(v=vs.110).aspx) Objekt, das viele Zeilen mit Daten in eine Tabelle zu laden. Obwohl diese Technik sehr effizient ist, unterstützt es nicht für serverseitige Verarbeitung, es sei denn, die Daten in eine temporäre Tabelle oder Tabellenvariable geladen werden.  
  
## <a name="creating-table-valued-parameter-types"></a>Erstellen von Tabellenwertparameter-Typen  

Tabellenwertparameter basieren auf stark typisierten Tabellenstrukturen, die definiert sind, mithilfe von Transact-SQL `CREATE TYPE` Anweisungen. Sie müssen einen Tabellentyp erstellen und definieren die Struktur in SQL Server, bevor Sie Tabellenwertparameter in Ihren Clientanwendungen verwenden können. Weitere Informationen zum Erstellen von Tabellentypen finden Sie unter [benutzerdefinierte Tabellentypen](http://go.microsoft.com/fwlink/?LinkID=98364) in SQL Server-Onlinedokumentation.  

```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```

Nach der Erstellung eines Tabellentyps, können Sie die Tabellenwertparameter enthalten, die basierend auf diesem Typ deklarieren. Das folgende Transact-SQL-Fragment zeigt, wie ein Tabellenwertparameter in der Definition einer gespeicherten Prozedur deklariert wird. Beachten Sie, dass die `READONLY` -Schlüsselwort ist für das Deklarieren von-Tabellenwertparameter erforderlich.  

```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```

## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Ändern von Daten mit Tabellenwertparametern (Transact-SQL)  

Tabellenwertparameter können in setbasierten die datenänderungen verwendet werden, die mehrere Zeilen zu beeinflussen, indem Sie Ausführung einer einzelnen Anweisung. Beispielsweise können Sie wählen alle Zeilen in einem Table-valued Parameter und diese in eine Datenbanktabelle einfügen, oder Sie können eine Update-Anweisung erstellen, indem verknüpfen einen Tabellenwertparameter mit der Tabelle, die Sie aktualisieren möchten.  
  
Die folgende Transact-SQL UPDATE-Anweisung veranschaulicht, wie ein Tabellenwertparameter durch einen Join mit der Categories-Tabelle. Wenn Sie einen Tabellenwertparameter mit einem JOIN in einer FROM-Klausel verwenden, müssen Sie auch alias, wie hier gezeigt, in dem der Tabellenwertparameter ein Alias "EC" ist:  

```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```

Diese Transact-SQL-Beispiel veranschaulicht das zum Auswählen von Zeilen aus einem Tabellenwertparameter-Parameter, um einen INSERT in einem einzigen satzbasierten Vorgang auszuführen.

```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```

## <a name="limitations-of-table-valued-parameters"></a>Einschränkungen von Tabellenwertparametern

Es gibt mehrere Einschränkungen bei Tabellenwertparametern:  
  
- Sie können keine Tabellenwertparameter zu benutzerdefinierten Funktionen übergeben.  
  
- Tabellenwertparameter können nur zur Unterstützung von UNIQUE- oder PRIMARY KEY-Einschränkungen indiziert werden. SQL Server verwaltet keine Statistiken für Tabellenwertparameter.  
  
- Tabellenwertparameter sind in Transact-SQL-Code schreibgeschützt. Die Spaltenwerte in den Zeilen ein Tabellenwertparameter kann nicht aktualisiert werden und Sie können keine Zeilen einfügen oder löschen. Um die Daten, die an eine gespeicherte Prozedur übergeben wird, oder parametrisierte Anweisung Tabellenwertparameter zu ändern, müssen Sie die Daten in eine temporäre Tabelle oder in einer Tabellenvariablen einfügen.  
  
- Sie können keine ALTER TABLE-Anweisungen verwenden, zum Ändern des Entwurfs von Tabellenwertparametern.

- Sie können große Objekte in einem Table-valued Parameter streamen.  
  
## <a name="configuring-a-table-valued-parameter"></a>Konfigurieren eines Tabellenwertparameters

Microsoft JDBC-Treiber 6.0 für SQL Server ab, werden mit einer parametrisierten Anweisung oder einer parametrisierten gespeicherten Prozedur Tabellenwertparameter unterstützt werden. Tabellenwertparameter können aus einer "sqlserverdatatable" aus einem ResultSet aufgefüllt oder von einem Benutzer bereitgestellte Implementierung der ISQLServerDataRecord-Schnittstelle. Wenn Sie einen Tabellenwertparameter für eine vorbereitete Abfrage festlegen zu können, müssen Sie einen Namen angeben, der den Namen eines kompatiblen Typs, der zuvor erstellt haben, auf dem Server übereinstimmen müssen.  
  
Die folgenden zwei Codefragmente veranschaulichen einen Tabellenwertparameter mit Sqlserverpreparedstatement- und ein SQLServerCallableStatement zum Einfügen von Daten konfigurieren. SourceTVPObject kann es sich hier um eine "sqlserverdatatable", oder ein ResultSet oder ein ISQLServerDataRecord-Objekt sein. In den Beispielen wird davon ausgegangen, dass die Verbindung über eine aktive Verbindungsobjekt ist.  

```java
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =
    (SQLServerPreparedStatement) connection.prepareStatement(“INSERT INTO dbo.Categories SELECT * FROM ?”);  
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
> Finden Sie im Abschnitt **Table-Valued Parameter-API für JDBC Driver** unten für eine vollständige Liste der APIs, die zum Festlegen der Tabellenwertparameter verfügbar.  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>Ein Tabellenwert-Parameter übergeben wird, als "sqlserverdatatable"-Objekt  

Ab Microsoft JDBC-Treiber 6.0 für SQL Server, stellt die "sqlserverdatatable"-Klasse eine in-Memory-Tabelle mit relationalen Daten dar. In diesem Beispiel wird veranschaulicht, wie ein Tabellenwertparameter von in-Memory-Daten, die mithilfe der "sqlserverdatatable"-Objekts erstellt wird. Der Code zuerst erstellt ein "sqlserverdatatable"-Objekt, das Schema definiert und füllt die Tabelle mit Daten. Der Code, konfiguriert ein sqlserverpreparedstatement-Klasse, die diese Datentabelle als ein Tabellenwertparameter in SQL Server zu übergeben.  

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
> Finden Sie im Abschnitt **Table-Valued Parameter-API für JDBC Driver** unten für eine vollständige Liste der APIs, die zum Festlegen der Tabellenwertparameter verfügbar.  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>Übergeben einen Tabellenwertparameter als ein ResultSet-Objekt  

Dieses Beispiel zeigt, wie Sie Zeilen von Daten aus einem ResultSet in einen Tabellenwertparameter zu streamen. Der Code ruft zunächst Daten aus einer Quelltabelle in einer erstellt ein "sqlserverdatatable"-Objekt, das Schema definiert und füllt die Tabelle mit Daten. Der Code, konfiguriert ein sqlserverpreparedstatement-Klasse, die diese Datentabelle als ein Tabellenwertparameter in SQL Server zu übergeben.  

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
> Finden Sie im Abschnitt **Table-Valued Parameter-API für JDBC Driver** unten für eine vollständige Liste der APIs, die zum Festlegen der Tabellenwertparameter verfügbar.  

## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>Ein Tabellenwert-Parameter übergeben wird, wie ein ISQLServerDataRecord-Objekt  

Ab Microsoft JDBC-Treiber 6.0 für SQL Server eine neue Schnittstelle ISQLServerDataRecord ist für das streaming von Daten (je nachdem, wie der Benutzer für die Implementierung für sie bereitstellt) mit einem Tabellenwertparameter-Parameter. Im folgende Beispiel wird veranschaulicht, wie die ISQLServerDataRecord-Schnittstelle implementieren und ihn als einen Tabellenwert-Parameter übergeben. Aus Gründen der Einfachheit übergibt die im folgenden Beispiel wird nur eine Zeile mit hartcodierten Werten, die Tabellenwertparameter. Im Idealfall würde der Benutzer diese Schnittstelle zum Streamen von Zeilen aus beliebigen Quellen, z. B. aus einer Textdatei implementieren.  

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
> Finden Sie im Abschnitt **Table-Valued Parameter-API für JDBC Driver** unten für eine vollständige Liste der APIs, die zum Festlegen der Tabellenwertparameter verfügbar.

## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>Tabellenwertparameter API für den JDBC-Treiber

### <a name="sqlservermetadata"></a>SQLServerMetaData

Diese Klasse stellt die Metadaten für eine Spalte dar. Es wird in der ISQLServerDataRecord-Schnittstelle zum Spaltenmetadaten an den Table-valued Parameter zu übergeben. Die Methoden in dieser Klasse sind:  

| Name                                                                                                                                                                             | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Öffentliche SQLServerMetaData (Zeichenfolge ColumnName, Int SqlType, Int mit einfacher Genauigkeit, Int Skalierung, booleschen UseServerDefault, booleschen IsUniqueKey, SQLServerSortOrder SortOrder, Int SortOrdinal) | Initialisiert eine neue Instanz der SQLServerMetaData mit der angegebenen Spaltennamen, Sql-Typ, Genauigkeit, Skalierung und der Server standardmäßig. Diese Form des Konstruktors unterstützt Tabellenwertparameter, können Sie angeben, ob die Spalte in der Table-valued Parameter, die Sortierreihenfolge für die Spalte, und die Ordnungszahl der Sortierspalte eindeutig ist. <br/><br/>UseServerDefault – gibt an, ob diese Spalte den Standardserverwert verwenden soll; Standardwert ist "false".<br>IsUniqueKey – gibt an, ob die Spalte in der Tabellenwertparameter eindeutig ist; Standardwert ist "false".<br>SortOrder - gibt die Sortierreihenfolge für eine Spalte an. Standardwert ist SQLServerSortOrder.Unspecified.<br>SortOrdinal - gibt die Ordnungszahl der Sortierspalte an. SortOrdinal beginnt bei 0; Standardwert ist-1. |
| Öffentliche SQLServerMetaData (Zeichenfolge ColumnName, Int SqlType)                                                                                                                        | Initialisiert eine neue Instanz der SQLServerMetaData, die den Namen der Spalte mit der Sql-Typ.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Öffentliche SQLServerMetaData (Zeichenfolge ColumnName, Int SqlType, Genauigkeit von Int, Int-Skalierung)                                                                                              | Initialisiert eine neue Instanz der SQLServerMetaData mithilfe der Spaltenname, Sql-Datentyp, Genauigkeit und Dezimalstellen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Öffentliche SQLServerMetaData (SQLServerMetaData SqlServerMetaData)                                                                                                                    | Initialisiert einer neuen Instanz der SQLServerMetaData Vordergrund ein anderes SQLServerMetaData-Objekt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Öffentliche Zeichenfolge getColumName()                                                                                                                                                     | Ruft den Namen der Spalte ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| öffentliches Int getSqlType()                                                                                                                                                          | Ruft die Java-Sql-Typ ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| öffentliches Int getPrecision()                                                                                                                                                        | Ruft die Genauigkeit des Datentyps der Spalte übergeben.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| öffentliches Int getScale()                                                                                                                                                            | Ruft die Dezimalstellen des Typs, die an die Spalte ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Öffentliche SQLServerSortOrder getSortOrder()                                                                                                                                         | Ruft die Sortierreihenfolge ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| öffentliches Int getSortOrdinal()                                                                                                                                                      | Ruft die Ordinalzahl der Sortierung ab.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Öffentlicher boolescher isUniqueKey()                                                                                                                                                     | Gibt zurück, ob die Spalte eindeutig ist.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Öffentlicher boolescher useServerDefault()                                                                                                                                                | Gibt zurück, ob die Spalte auf wird den Standardwert für den Server verwendet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  
### <a name="sqlserversortorder"></a>SQLServerSortOrder

Eine Enumeration, die die Sortierreihenfolge definiert. Mögliche Werte sind aufsteigend, absteigend und nicht angegeben.
  
### <a name="sqlserverdatatable"></a>"Sqlserverdatatable"

Diese Klasse stellt eine Tabelle in-Memory-Daten mit Tabellenwertparametern verwendet werden. Die Methoden in dieser Klasse sind:  

| Name                                                          | und Beschreibung                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| Öffentliche SQLServerDataTable()                                   | Initialisiert eine neue Instanz der "sqlserverdatatable".    |
| Öffentliche Iterator < Eintrag\<ganze Zahl, Objekt [] >> getIterator()      | Ruft einen Iterator für die Zeilen der Datentabelle ab. |
| Öffentliche void AddColumnMetadata (Zeichenfolge ColumnName, Int SqlType) | Fügt Metadaten für die angegebene Spalte hinzu.              |
| Öffentliche void AddColumnMetadata (SQLServerDataColumn Spalte)     | Fügt Metadaten für die angegebene Spalte hinzu.              |
| Öffentliche void AddRow (Objektwerten...)                          | Fügt eine Zeile mit Daten an die Datentabelle.              |
| Öffentliche Zuordnung\<Integer, SQLServerDataColumn > getColumnMetadata() | Ruft die Spaltenmetadaten des dieser Datentabelle ab.       |
| Öffentliche void clear()                                           | Löscht diese Datentabelle.                              |

### <a name="sqlserverdatacolumn"></a>SQLServerDataColumn

Diese Klasse stellt eine Spalte mit der in-Memory-Daten-Tabelle, die durch "sqlserverdatatable" dargestellt wird. Die Methoden in dieser Klasse sind:  

| Name                                                       | und Beschreibung                                                                      |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Öffentliche SQLServerDataColumn (Zeichenfolge ColumnName, Int SqlType) | Initialisiert eine neue Instanz der SQLServerDataColumn mit dem Spaltennamen und Typ. |
| Öffentliche Zeichenfolge getColumnName()                              | Ruft den Namen der Spalte ab.                                                       |
| öffentliches Int getColumnType()                                 | Ruft den Spaltentyp ab.                                                       |

### <a name="isqlserverdatarecord"></a>ISQLServerDataRecord

Diese Klasse stellt eine Schnittstelle, die Benutzer zum Streamen von Daten auf einen Tabellenwertparameter implementieren können. Die Methoden in dieser Schnittstelle sind:  
  
| Name                                                    | und Beschreibung                                                                                             |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Öffentliche SQLServerMetaData GetColumnMetaData (Int-Spalte); | Ruft ab die Spaltenmetadaten des angegebenen Spaltenindexes.                                               |
| öffentliches Int getColumnCount();                            | Ruft die Gesamtanzahl der Spalten ab.                                                                  |
| Öffentliche getRowData() für Objekt [];                           | Ruft die Daten für die aktuelle Zeile als Array von Objekten ab.                                          |
| Öffentlicher boolescher Next()";                                  | Wechselt zur nächsten Zeile. Gibt True zurück, wenn die Verschiebung erfolgreich ist, und andernfalls eine nächste Zeile, die "false ist". |

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

Die folgenden Methoden wurden für diese Klasse zur Übergabe von Tabellenwertparameter-Unterstützung hinzugefügt.  

| Name                                                                                                    | und Beschreibung                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Öffentliche endgültige "void" SetStructured (Int ParameterIndex, Zeichenfolge TvpName "sqlserverdatatable" TvpDataTbale)    | Füllt einen Table-valued Parameter mit einer Datentabelle. ParameterIndex ist des parameterindexes und TvpDataTable ist die Tabelle das Quelldatenobjekt TvpName ist der Name des Tabellenwertparameter-Parameters.                                                                                                          |
| Öffentliche endgültige "void" SetStructured (Int ParameterIndex, Zeichenfolge TvpName ResultSet TvpResultSet)             | Füllt einen Table-valued Parameter mit einem ResultSet aus einer anderen Tabelle abgerufen. ParameterIndex ist das Angeben des Parameterindex TvpName ist der Name des Tabellenwertparameter-Parameters und TvpResultSet ist das Ergebnis Set-Quellobjekt.                                                                               |
| Öffentliche endgültige "void" SetStructured (Int ParameterIndex, Zeichenfolge TvpName ISQLServerDataRecord TvpDataRecord) | Füllt einen Table-valued Parameter mit einem ISQLServerDataRecord-Objekt. ISQLServerDataRecord wird zum Streamen von Daten verwendet, und der Benutzer entscheidet, wie Sie es verwenden. ParameterIndex ist das Angeben des Parameterindex TvpName ist der Name des Tabellenwertparameter-Parameters und TvpDataRecord ist ein ISQLServerDataRecord-Objekt. |
  
### <a name="sqlservercallablestatement"></a>SQLServerCallableStatement

Die folgenden Methoden wurden für diese Klasse zur Übergabe von Tabellenwertparameter-Unterstützung hinzugefügt.  
  
| Name                                                                                                        | und Beschreibung                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Öffentliche endgültige "void" SetStructured (ParatemeterName der Zeichenfolge, Zeichenfolge TvpName "sqlserverdatatable" TvpDataTable)    | Füllt die Table-valued Parameter, die an eine gespeicherte Prozedur mit einer Datentabelle. ParatemeterName ist der Name des Parameters, TvpName ist der Name des Tabellenwertparameter-Typs und TvpDataTable ist das Table-Objekt.                                                                                                                 |
| Öffentliche endgültige "void" SetStructured (ParatemeterName der Zeichenfolge, Zeichenfolge TvpName ResultSet TvpResultSet)             | Füllt die Table-valued Parameter an eine gespeicherte Prozedur übergeben werden, mit der ein ResultSet aus einer anderen Tabelle abgerufen. ParatemeterName ist der Name des Parameters, TvpName ist der Name des Tabellenwertparameter-Typs und TvpResultSet ist das Ergebnis Set-Quellobjekt.                                                                              |
| Öffentliche endgültige "void" SetStructured (ParatemeterName der Zeichenfolge, Zeichenfolge TvpName ISQLServerDataRecord TvpDataRecord) | Füllt die Table-valued Parameter, die an eine gespeicherte Prozedur mit einem ISQLServerDataRecord-Objekt. ISQLServerDataRecord wird zum Streamen von Daten verwendet, und der Benutzer entscheidet, wie Sie es verwenden. ParatemeterName ist der Name des Parameters, TvpName ist der Name des Tabellenwertparameter-Typs und TvpDataRecord ist ein ISQLServerDataRecord-Objekt. |

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
