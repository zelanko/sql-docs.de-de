---
title: Beispiel für Standarddatentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 43a19765231aeea5f28ead28b74130befb10bb1a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922620"
---
# <a name="basic-data-types-sample"></a>Standarddatentypen – Beispiel

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] veranschaulicht, wie Werte von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standarddatentypen mithilfe von Getter-Methoden für Resultsets abgerufen und wie diese Werte mithilfe von Updatemethoden für Resultsets aktualisiert werden.  
  
Die Codedatei für dieses Beispiel heißt „BasicDataTypes.java“ und befindet sich im folgenden Pfad:  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes  
```

## <a name="requirements"></a>Requirements (Anforderungen)  

Wenn Sie diese Beispielanwendung ausführen möchten, müssen Sie die Datei „mssql-jdbc.jar“ in den Klassenpfad aufnehmen. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
> Der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] enthält die Klassenbibliotheksdateien „mssql-jdbc“ für die jeweilige Verwendung mit Ihren bevorzugten JRE-Einstellungen (Java Runtime Environment). Weitere Informationen zum Auswählen der richtigen JAR-Datei finden Sie unter [Systemanforderungen für den JDBC-Treiber](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Beispiel

Im folgenden Beispielcode wird eine Verbindung mit der Datenbank hergestellt. Anschließend wird eine einzelne Datenzeile aus der DataTypesTable-Testtabelle abgerufen. Danach wird die benutzerdefinierte displayRow-Methode aufgerufen, um alle im Resultset enthaltenen Daten mithilfe der verschiedenen get\<Type>-Methoden der [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse anzuzeigen.  
  
Anschließend werden die im Resultset enthaltenen Daten mithilfe der verschiedenen update\<Type>-Methoden der SQLServerResultSet-Klasse aktualisiert. Daraufhin wird die [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)-Methode aufgerufen, um die Daten in der Datenbank zu speichern.  
  
Schließlich werden die im Resultset enthaltenen Daten aktualisiert, und die benutzerdefinierte displayRow-Methode wird erneut aufgerufen, um die Daten anzuzeigen.  

```java
import java.sql.Connection;
import java.sql.Date;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.Time;
import java.sql.Timestamp;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

import microsoft.sql.DateTimeOffset;

public class BasicDataTypes {
    private static final String tableName = "DataTypesTable";

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);) {

            dropAndCreateTable(stmt);
            insertOriginalData(con);

            String SQL = "SELECT * FROM " + tableName;
            ResultSet rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("ORIGINAL DATA", rs);

            // Update the data in the result set.
            rs.updateString(2, "B");
            rs.updateString(3, "Some updated text.");
            rs.updateBoolean(4, true);
            rs.updateDouble(5, 77.89);
            rs.updateDouble(6, 1000.01);
            long timeInMillis = System.currentTimeMillis();
            Timestamp ts = new Timestamp(timeInMillis);
            rs.updateTimestamp(7, ts);
            rs.updateDate(8, new Date(timeInMillis));
            rs.updateTime(9, new Time(timeInMillis));
            rs.updateTimestamp(10, ts);

            // -480 indicates GMT - 8:00 hrs
            ((SQLServerResultSet) rs).updateDateTimeOffset(11, DateTimeOffset.valueOf(ts, -480));

            rs.updateRow();

            // Get the updated data from the database and display it.
            rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("UPDATED DATA", rs);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        System.out.println(rs.getInt(1) + " , " +                 // SQL integer type.
                rs.getString(2) + " , " +                         // SQL char type.
                rs.getString(3) + " , " +                         // SQL varchar type.
                rs.getBoolean(4) + " , " +                        // SQL bit type.
                rs.getDouble(5) + " , " +                         // SQL decimal type.
                rs.getDouble(6) + " , " +                         // SQL money type.
                rs.getTimestamp(7) + " , " +                      // SQL datetime type.
                rs.getDate(8) + " , " +                           // SQL date type.
                rs.getTime(9) + " , " +                           // SQL time type.
                rs.getTimestamp(10) + " , " +                     // SQL datetime2 type.
                ((SQLServerResultSet) rs).getDateTimeOffset(11)); // SQL datetimeoffset type.
        System.out.println();
    }

    private static void dropAndCreateTable(Statement stmt) throws SQLException {
        stmt.executeUpdate("if object_id('" + tableName + "','U') is not null" + " drop table " + tableName);

        String sql = "create table " + tableName + " (" + "c1 int, " + "c2 char(20), " + "c3 varchar(20), " + "c4 bit, "
                + "c5 decimal(10,5), " + "c6 money, " + "c7 datetime, " + "c8 date, " + "c9 time(7), "
                + "c10 datetime2(7), " + "c11 datetimeoffset(7), " + ");";

        stmt.execute(sql);
    }

    private static void insertOriginalData(Connection con) throws SQLException {
        String sql = "insert into " + tableName + " values( " + "?,?,?,?,?,?,?,?,?,?,?" + ")";
        try (PreparedStatement pstmt = con.prepareStatement(sql)) {
            pstmt.setObject(1, 100);
            pstmt.setObject(2, "original text");
            pstmt.setObject(3, "original text");
            pstmt.setObject(4, false);
            pstmt.setObject(5, 12.34);
            pstmt.setObject(6, 56.78);
            pstmt.setObject(7, new java.util.Date(1453500034839L));
            pstmt.setObject(8, new java.util.Date(1453500034839L));
            pstmt.setObject(9, new java.util.Date(1453500034839L));
            pstmt.setObject(10, new java.util.Date(1453500034839L));
            pstmt.setObject(11, new java.util.Date(1453500034839L));
            pstmt.execute();
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen  

[Arbeiten mit Datentypen &#40;JDBC&#41;](../../../connect/jdbc/code-samples/working-with-data-types-jdbc.md)  
  
