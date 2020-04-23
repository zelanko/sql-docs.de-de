---
title: API für das Massenkopieren für Batcheinfügevorgänge in JDBC
description: Der Microsoft JDBC-Treiber für SQL Server unterstützt die Verwendung der API für das Massenkopieren für Batcheinfügevorgänge in Azure Data Warehouse.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 497b68b2b1f19d5d67ca3e790f06844592205d70
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633990"
---
# <a name="using-bulk-copy-api-for-batch-insert-operation"></a>Verwenden der Massenkopierungs-API für den Batcheinfügungsvorgang

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Der Microsoft JDBC-Treiber 7.0 für SQL Server unterstützt die Verwendung der API für das Massenkopieren für Batcheinfügevorgänge in Azure Data Warehouse. Mit diesem Feature können Benutzer dem Treiber bei der Ausführung von Batcheinfügevorgängen das Massenkopieren im Hintergrund ermöglichen. Der Treiber strebt beim Einfügen derselben Daten eine bessere Leistung an, als der Treiber bei einem regulären Batcheinfügevorgang erzielen könnte. Der Treiber analysiert die SQL-Abfrage des Benutzers und nutzt anstelle des üblichen Batcheinfügevorgangs die API zum Massenkopieren. Nachfolgend werden die verschiedenen Möglichkeiten zum Aktivieren der API für das Massenkopieren für Batcheinfügevorgänge sowie die geltenden Einschränkungen aufgeführt. Diese Seite enthält außerdem ein kleines Codebeispiel, das eine Verwendung und die Leistungssteigerung veranschaulicht.

Dieses Feature ist nur auf die `executeBatch()` & `executeLargeBatch()`-APIs von PreparedStatement und CallableStatement anwendbar.

## <a name="prerequisites"></a>Voraussetzungen

Für die Aktivierung der API zum Massenkopieren für Batcheinfügevorgänge gelten zwei Voraussetzungen.

* Der Server muss eine Azure Data Warehouse-Instanz sein.
* Die Abfrage muss eine Einfügeabfrage sein (die Abfrage darf Kommentare enthalten, aber muss mit dem INSERT-Schlüsselwort beginnen, damit dieses Feature wirksam ist).

## <a name="enabling-bulk-copy-api-for-batch-insert"></a>Aktivieren der API für das Massenkopieren für Batcheinfügevorgänge

Es gibt drei Möglichkeiten, die API für das Massenkopieren für Batcheinfügevorgänge zu aktivieren.

### <a name="1-enabling-with-connection-property"></a>1. Aktivierung mit der Verbindungseigenschaft

Durch das Hinzufügen von **useBulkCopyForBatchInsert=true;** zur Verbindungszeichenfolge wird dieses Feature aktiviert.

```java
Connection connection = DriverManager.getConnection("jdbc:sqlserver://<server>:<port>;userName=<user>;password=<password>;database=<database>;useBulkCopyForBatchInsert=true;");
```

### <a name="2-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverconnection-object"></a>2. Aktivierung mit der setUseBulkCopyForBatchInsert()-Methode aus dem SQLServerConnection-Objekt

Durch den Aufruf von **SQLServerConnection.setUseBulkCopyForBatchInsert(true)** wird dieses Feature aktiviert.

**SQLServerConnection.getUseBulkCopyForBatchInsert()** ruft den aktuellen Wert für die Verbindungseigenschaft **useBulkCopyForBatchInsert** ab.

Der Wert für **useBulkCopyForBatchInsert** bleibt für jede PreparedStatement zum Zeitpunkt der Initialisierung konstant. Alle nachfolgenden Aufrufe von **SQLServerConnection.setUseBulkCopyForBatchInsert()** haben keine Auswirkung auf den Wert der bereits erstellten PreparedStatement.

### <a name="3-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverdatasource-object"></a>3. Aktivierung mit der setUseBulkCopyForBatchInsert()-Methode aus dem SQLServerDataSource-Objekt

Ähnlich wie oben, aber es wird SQLServerDataSource verwendet, um ein SQLServerConnection-Objekt zu erstellen. Mit beiden Methoden werden die gleichen Ergebnisse erzielt.

## <a name="known-limitations"></a>Bekannte Einschränkungen

Für dieses Feature gelten aktuell die folgenden Einschränkungen.

* Einfügeabfragen, die nicht parametrisierte Werte (z. B. `INSERT INTO TABLE VALUES (?, 2`) enthalten, werden nicht unterstützt. Platzhalter (?) sind die einzigen unterstützten Parameter für diese Funktion.
* Einfügeabfragen, die INSERT-SELECT-Ausdrücke (z. B. `INSERT INTO TABLE SELECT * FROM TABLE2`) enthalten, werden nicht unterstützt.
* Einfügeabfragen, die mehrere VALUE-Ausdrücke (z. B. `INSERT INTO TABLE VALUES (1, 2) (3, 4)`) enthalten, werden nicht unterstützt.
* Einfügeabfragen, auf die eine OPTION-Klausel in Kombination mit mehreren Tabellen oder eine andere Abfrage folgt, werden nicht unterstützt.
* Aufgrund der Einschränkungen für die API für das Massenkopieren werden die Datentypen `MONEY`, `SMALLMONEY`, `DATE`, `DATETIME`, `DATETIMEOFFSET`, `SMALLDATETIME`, `TIME`, `GEOMETRY` und `GEOGRAPHY` für dieses Feature aktuell nicht unterstützt.

Wenn die Abfrage aufgrund eines nicht SQL Server-bezogenen Fehlers nicht ausgeführt werden kann, protokolliert der Treiber die Fehlermeldung und verwendet die ursprüngliche Logik für Batcheinfügevorgänge.

## <a name="example"></a>Beispiel

Das nachfolgende Codebeispiel veranschaulicht einen Anwendungsfall für einen Batcheinfügevorgang in einem Azure Data Warehouse mit tausend Zeilen für beide Szenarien (regulär im Vergleich zur API für das Massenkopieren).

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

## <a name="see-also"></a>Weitere Informationen

[Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](improving-performance-and-reliability-with-the-jdbc-driver.md)
