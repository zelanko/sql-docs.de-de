---
title: Ändern von Resultsetdaten Datenbeispiel festlegen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b5ae54dc-2a79-4664-bb21-cacdb7d745e1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e46eec18eca6123839034fec1fb5b3e5aadbcd0f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624038"
---
# <a name="modifying-result-set-data-sample"></a>Ändern von Resultsetdaten - Beispiel

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] veranschaulicht, wie ein aktualisierbarer Datensatz aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank abgerufen wird. Anschließend wird mit den Methoden der [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse eine Datenzeile in das Datenset eingefügt, geändert und schließlich wieder gelöscht.

Die Codedatei für dieses Beispiel heißt „UpdateResultSet.java“ und befindet sich im folgenden Pfad:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\resultsets
```

## <a name="requirements"></a>Anforderungen

Wenn Sie diese Beispielanwendung ausführen möchten, müssen Sie die Datei „mssql-jdbc.jar“ in den Klassenpfad aufnehmen. Sie benötigen darüber hinaus Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] enthält die Klassenbibliotheksdateien „mssql-jdbc“ für die jeweilige Verwendung mit Ihren bevorzugten JRE-Einstellungen (Java Runtime Environment). Weitere Informationen zu der JAR-Datei auswählen, finden Sie unter [Systemanforderungen für JDBC Driver](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Beispiel

Im folgenden Beispielcode wird eine Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank hergestellt. Anschließend wird eine SQL-Anweisung mit dem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt verwendet. Die SQL-Anweisung wird ausgeführt, und die zurückgegebenen Daten werden in ein aktualisierbares SQLServerResultSet-Objekt eingefügt.

Danach wird der Resultsetcursor mithilfe der [moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md)-Methode zur neuen Zeile bewegt. Mit mehreren [updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)-Methoden werden anschließend Daten in die Zeile eingefügt. Daraufhin wird die [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md)-Methode aufgerufen, um die neue Datenzeile in der Datenbank zu speichern.

Nachdem die neue Datenzeile eingefügt wurde, wird die zuvor eingefügte Zeile mithilfe einer SQL-Anweisung abgerufen. Anschließend wird die Datenzeile mit einer Kombination der Methoden „updateString“ und [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) aktualisiert und erneut in der Datenbank gespeichert.

Schließlich wird die zuvor aktualisierte Datenzeile abgerufen und mit der [deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md)-Methode aus der Datenbank gelöscht.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class UpdateResultSet {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);) {

            // Create and execute an SQL statement, retrieving an updateable result set.
            String SQL = "SELECT * FROM HumanResources.Department;";
            ResultSet rs = stmt.executeQuery(SQL);

            // Insert a row of data.
            rs.moveToInsertRow();
            rs.updateString("Name", "Accounting");
            rs.updateString("GroupName", "Executive General and Administration");
            rs.updateString("ModifiedDate", "08/01/2006");
            rs.insertRow();

            // Retrieve the inserted row of data and display it.
            SQL = "SELECT * FROM HumanResources.Department WHERE Name = 'Accounting';";
            rs = stmt.executeQuery(SQL);
            displayRow("ADDED ROW", rs);

            // Update the row of data.
            rs.first();
            rs.updateString("GroupName", "Finance");
            rs.updateRow();

            // Retrieve the updated row of data and display it.
            rs = stmt.executeQuery(SQL);
            displayRow("UPDATED ROW", rs);

            // Delete the row of data.
            rs.first();
            rs.deleteRow();
            System.out.println("ROW DELETED");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        while (rs.next()) {
            System.out.println(rs.getString("Name") + " : " + rs.getString("GroupName"));
            System.out.println();
        }
    }
}

```

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Arbeiten mit Resultsets](../../../connect/jdbc/code-samples/working-with-result-sets.md)
