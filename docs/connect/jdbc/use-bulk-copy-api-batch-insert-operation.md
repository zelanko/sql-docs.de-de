---
title: Die API für Massenkopieren für Batch-Insert-Vorgang für MSSQL-JDBC-Treiber mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/27/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b205e27f24693a2dfaa6fcff2245cf45288a12b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696560"
---
# <a name="using-bulk-copy-api-for-batch-insert-operation"></a>Verwenden der Massenkopierungs-API für den Batcheinfügungsvorgang

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC-Treiber 7.0 für die API für Massenkopieren für Batch-Insert-Vorgänge für Azure Data Warehouse mithilfe von SQL Server unterstützt. Dieses Feature ermöglicht das Aktivieren der Treiber, Massenkopieren-Vorgang unter beim Ausführen von Batch insert-Vorgänge durchzuführen. Vorgang zum Einfügen der Treiber zur Verbesserung der Leistung beim Einfügen von die gleichen Daten, da der Treiber mit regulären Batch hätte erreichen möchte. Der Treiber analysiert SQL-Abfrage des Benutzers, Nutzung der API für Massenkopieren anstelle der üblichen Batch Insert-Vorgang. Im folgenden finden, dass die verschiedenen Möglichkeiten zum Aktivieren der API für das Massenkopieren für Batch-Funktion als auch die Liste der Einschränkungen einfügen. Diese Seite enthält auch einen kleinen Codebeispiel für das eine nutzungs- und auch die Leistung zu verbessern.

Dieses Feature gilt nur für "PreparedStatement" und die CallableStatement `executeBatch()`  &  `executeLargeBatch()` APIs.

## <a name="pre-requisites"></a>Voraussetzungen

Es gibt zwei Voraussetzungen für die API für Massenkopieren für batcheinfügung zu aktivieren.

* Der Server muss das Azure Data Warehouse sein.
* Die Abfrage muss eine Insert-Abfrage (die Abfrage kann die Kommentare enthalten, aber die Abfrage muss mit dem Schlüsselwort "Einfügen" für dieses Feature wirksam werden zu starten).

## <a name="enabling-bulk-copy-api-for-batch-insert"></a>Aktivieren die API für Massenkopieren für batcheinfügung

Es gibt drei Möglichkeiten, um die API für Massenkopieren für batcheinfügung zu aktivieren.

### <a name="1-enabling-with-connection-property"></a>1. Aktivieren mit der Connection-Eigenschaft

Hinzufügen von **UseBulkCopyForBatchInsert = True;** Zeichenfolge für die Verbindung kann mithilfe dieser Funktion.

```java
Connection connection = DriverManager.getConnection("jdbc:sqlserver://<server>:<port>;userName=<user>;password=<password>;database=<database>;useBulkCopyForBatchInsert=true;");
```

### <a name="2-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverconnection-object"></a>2. Aktivierung mit setUseBulkCopyForBatchInsert()-Methode der SQLServerConnection-Objekt

Aufrufen von **SQLServerConnection.setUseBulkCopyForBatchInsert(true)** können mithilfe dieser Funktion.

**SQLServerConnection.getUseBulkCopyForBatchInsert()** Ruft den aktuellen Wert für **UseBulkCopyForBatchInsert** Connection-Eigenschaft.

Der Wert für **UseBulkCopyForBatchInsert** für jede "PreparedStatement" zum Zeitpunkt der Initialisierung konstant bleibt. Alle nachfolgenden Aufrufe **SQLServerConnection.setUseBulkCopyForBatchInsert()** wirkt sich nicht im Hinblick auf den Wert, der bereits erstellten "PreparedStatement".

### <a name="3-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverdatasource-object"></a>3. Aktivierung mit setUseBulkCopyForBatchInsert()-Methode von der SQLServerDataSource-Objekt

Ähnlich wie oben, jedoch SQLServerDataSource verwenden, um ein SQLServerConnection-Objekt zu erstellen. Mit beiden Methoden werden die gleichen Ergebnisse erzielt.

## <a name="known-limitations"></a>Bekannte Einschränkungen

Es gibt derzeit diese Einschränkungen, die für dieses Feature gelten.

* INSERT-Abfragen, die nicht parametrisierten Werten enthalten (z. B. `INSERT INTO TABLE VALUES (?, 2`)), werden nicht unterstützt. Platzhalter (?) sind die einzigen unterstützten Parameter für diese Funktion.
* INSERT-Abfragen, die INSERT-SELECT-Ausdrücke enthalten (z. B. `INSERT INTO TABLE SELECT * FROM TABLE2`), werden nicht unterstützt.
* INSERT-Abfragen, die mehrere Ausdrücke enthalten (z. B. `INSERT INTO TABLE VALUES (1, 2) (3, 4)`), werden nicht unterstützt.
* Abfragen zum Einfügen, die gefolgt von der OPTION-Klausel, mit mehreren Tabellen verknüpft oder gefolgt von einer anderen Abfrage werden nicht unterstützt.
* Aufgrund von Beschränkungen der API für Massenkopieren `DATETIME`, `SMALLDATETIME`,`GEOMETRY`, und `GEOGRAPHY` -Datentypen werden für diese Funktion nicht unterstützt.

Wenn die Abfrage schlägt, da nicht fehl "SQLServer" von Netzwerkfehlern, der Treiber protokolliert der Fehlermeldung und der Fallback mit der ursprünglichen Logik für das Batch-einfügen.

## <a name="example"></a>Beispiel

Im folgenden finden Sie Beispielcode, der den Anwendungsfall für einen Batch Insert-Vorgang für Azure Data Warehouse tausend Zeilen, für beide Szenarien (reguläre Vs-API für Massenkopieren) veranschaulicht.

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

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
