---
title: Verwenden der Massen Kopier-API für den Batch INSERT-Vorgang für den MSSQL JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3050cdf87775a67618902dfbb88b656003020769
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027104"
---
# <a name="using-bulk-copy-api-for-batch-insert-operation"></a>Verwenden der Massenkopierungs-API für den Batcheinfügungsvorgang

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Der Microsoft JDBC-Treiber 7,0 für SQL Server unterstützt die Verwendung einer Massen Kopier-API für Batch Einfügungs Vorgänge für Azure Data Warehouse. Diese Funktion ermöglicht es Benutzern, beim Ausführen von Batch Einfügevorgängen einen Massen Kopiervorgang für den-Treiber auszuführen. Der Treiber zielt darauf ab, die Leistung zu verbessern, während die gleichen Daten wie der Treiber mit einem regulären Batch Einfügungs Vorgang eingefügt werden. Der Treiber analysiert die SQL-Abfrage des Benutzers und nutzt dabei die Massen Kopier-API anstelle des üblichen batcheinfügevorgangs. Im folgenden finden Sie verschiedene Möglichkeiten, die Massen Kopier-API für das Batch Einfügungs Feature zu aktivieren, sowie die Liste der Einschränkungen. Diese Seite enthält auch einen kleinen Beispielcode, der die Nutzung und die Leistungssteigerung veranschaulicht.

Diese Funktion gilt nur für die `executeBatch()`  &  `executeLargeBatch()` APIs PreparedStatement und CallableStatement.

## <a name="prerequisites"></a>Voraussetzungen

Zum Aktivieren der Massen Kopier-API für Batch INSERT müssen zwei Voraussetzungen erfüllt sein.

* Der Server muss ein Azure-Data Warehouse sein.
* Bei der Abfrage muss es sich um eine INSERT-Abfrage handeln (die Abfrage enthält möglicherweise Kommentare, aber die Abfrage muss mit dem INSERT-Schlüsselwort beginnen, damit dieses Feature in Kraft tritt).

## <a name="enabling-bulk-copy-api-for-batch-insert"></a>Aktivieren der Massen Kopier-API für Batch INSERT

Es gibt drei Möglichkeiten, die Massen Kopier-API für Batch INSERT zu aktivieren.

### <a name="1-enabling-with-connection-property"></a>1. Aktivieren mit der Connection-Eigenschaft

Durch das Hinzufügen von **usebulkcopyforbatchinsert = true;** zur Verbindungs Zeichenfolge wird diese Funktion aktiviert.

```java
Connection connection = DriverManager.getConnection("jdbc:sqlserver://<server>:<port>;userName=<user>;password=<password>;database=<database>;useBulkCopyForBatchInsert=true;");
```

### <a name="2-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverconnection-object"></a>2. Aktivieren mit der setusebulkcopyforbatchinsert ()-Methode aus dem SQLServerConnection-Objekt

Durch den Aufruf von **SQLServerConnection. setusebulkcopyforbatchinsert (true)** wird diese Funktion aktiviert.

**SQLServerConnection. getusebulkcopyforbatchinsert ()** Ruft den aktuellen Wert der **usebulkcopyforbatchinsert** -Verbindungs Eigenschaft ab.

Der Wert für **usebulkcopyforbatchinsert** bleibt für jede PreparedStatement-Konstante zum Zeitpunkt seiner Initialisierung konstant. Alle nachfolgenden Aufrufe von **SQLServerConnection. setusebulkcopyforbatchinsert ()** wirken sich nicht auf die bereits erstellte PreparedStatement-Anweisung hinsichtlich ihres Werts aus.

### <a name="3-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverdatasource-object"></a>3. Aktivieren mit der setusebulkcopyforbatchinsert ()-Methode aus dem SQLServerDataSource-Objekt

Ähnlich wie oben, aber die Verwendung von SQLServerDataSource zum Erstellen eines SQLServerConnection-Objekts. Mit beiden Methoden werden die gleichen Ergebnisse erzielt.

## <a name="known-limitations"></a>Bekannte Einschränkungen

Zurzeit gelten diese Einschränkungen für dieses Feature.

* INSERT-Abfragen, die nicht parametrisierte Werte (z `INSERT INTO TABLE VALUES (?, 2`. b.) enthalten, werden nicht unterstützt. Platzhalter (?) sind die einzigen unterstützten Parameter für diese Funktion.
* INSERT-Abfragen, die INSERT-SELECT-Ausdrücke (z `INSERT INTO TABLE SELECT * FROM TABLE2`. b.) enthalten, werden nicht unterstützt.
* INSERT-Abfragen, die mehrere Wert Ausdrücke (z `INSERT INTO TABLE VALUES (1, 2) (3, 4)`. b.) enthalten, werden nicht unterstützt.
* INSERT-Abfragen, auf die die Option-Klausel folgt, die mit mehreren Tabellen verknüpft ist, oder auf die eine andere Abfrage folgt, werden nicht unterstützt.
* Aufgrund `MONEY`der Einschränkungen der Massen Kopier-API werden die Datentypen `DATETIME` `GEOMETRY` `TIME` `DATE`, `DATETIMEOFFSET` `SMALLMONEY` `SMALLDATETIME`,,,,, `GEOGRAPHY` , und derzeit nicht unterstützt. befinden.

Wenn die Abfrage aufgrund von nicht "SQL Server"-bezogenen Fehlern fehlschlägt, protokolliert der Treiber die Fehlermeldung und führt einen Fall Back auf die ursprüngliche Logik für die Batch Einfügung aus.

## <a name="example"></a>Beispiel

Im folgenden finden Sie einen Beispielcode, der den Anwendungsfall für einen Batch Einfügungs Vorgang für Azure DW mit tausend Zeilen für beide Szenarios (reguläre vs-Massen Kopier-API) veranschaulicht.

```java
    public static void main(String[] args) throws Exception
    {
        String tableName = "batchTest";
        String tableNameBulkCopyAPI = "batchTestBulk";

        String azureDWconnectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(azureDWconnectionUrl); // connects to an Azure Data Warehouse.
                Statement stmt = con.createStatement();
                PreparedStatement pstmt = con.prepareStatement("insert into " + tableName + " values (?, ?)");) {

            String dropSql = "if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[" + tableName + "]') and OBJECTPROPERTY(id, N'IsUserTable') = 1) DROP TABLE [" + tableName + "]";
            stmt.execute(dropSql);

            String createSql = "create table " + tableName + " (c1 int, c2 varchar(20))";
            stmt.execute(createSql);

            System.out.println("Starting batch operation using regular batch insert operation.");
            long start = System.currentTimeMillis();
            for (int i = 0; i < 1000; i++) {
                pstmt.setInt(1, i);
                pstmt.setString(2, "test" + i);
                pstmt.addBatch();
            }
            pstmt.executeBatch();

            long end = System.currentTimeMillis();

            System.out.println("Finished. Time taken : " + (end - start) + " milliseconds.");
        }

        try (Connection con = DriverManager.getConnection(azureDWconnectionUrl + ";useBulkCopyForBatchInsert=true"); // connects to an Azure Data Warehouse, with useBulkCopyForBatchInsert connection property set to true.
                Statement stmt = con.createStatement();
                PreparedStatement pstmt = con.prepareStatement("insert into " + tableNameBulkCopyAPI + " values (?, ?)");) {

            String dropSql = "if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[" + tableNameBulkCopyAPI + "]') and OBJECTPROPERTY(id, N'IsUserTable') = 1) DROP TABLE [" + tableNameBulkCopyAPI + "]";
            stmt.execute(dropSql);

            String createSql = "create table " + tableNameBulkCopyAPI + " (c1 int, c2 varchar(20))";
            stmt.execute(createSql);

            System.out.println("Starting batch operation using Bulk Copy API.");
            long start = System.currentTimeMillis();
            for (int i = 0; i < 1000; i++) {
                pstmt.setInt(1, i);
                pstmt.setString(2, "test" + i);
                pstmt.addBatch();
            }
            pstmt.executeBatch();

            long end = System.currentTimeMillis();

            System.out.println("Finished. Time taken : " + (end - start) + " milliseconds.");
        }
    }
```

Ergebnis:

```bash
Starting batch operation using regular batch insert operation.
Finished. Time taken : 104132 milliseconds.
Starting batch operation using Bulk Copy API.
Finished. Time taken : 1058 milliseconds.
```

## <a name="see-also"></a>Siehe auch

[Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
