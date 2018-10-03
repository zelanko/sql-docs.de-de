---
title: Zwischenspeichern von Resultsetdaten Datenbeispiel festlegen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 13a95ebb-996c-4713-a1bd-5834fe22a334
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ed4174dcd164163307259100e752d277f9b200c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47823978"
---
# <a name="caching-result-set-data-sample"></a>Zwischenspeichern von Resultsetdaten - Beispiel

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] veranschaulicht, wie umfangreiche Daten aus einer Datenbank abgerufen werden und mithilfe der [setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)-Methode des [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts die Anzahl der Datenzeilen gesteuert wird, die im Client zwischengespeichert werden.  
  
> [!NOTE]  
> Die Einschränkung der im Client zwischengespeicherten Zeilen ist nicht mit der Einschränkung der Gesamtanzahl von Zeilen identisch, die ein Resultset enthalten kann. Verwenden Sie zum Steuern der Gesamtanzahl der in einem Resultset enthaltenen Zeilen die Methode [setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) des Objekts [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), das von den Objekten [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) und [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) geerbt wird.  
  
Zum Einschränken der Anzahl von Zeilen, die im Client zwischengespeichert werden, müssen Sie zunächst einen serverseitigen Cursor verwenden, wenn Sie eines der Statement-Objekte erstellen. Geben Sie hierzu den spezifischen Cursortyp an, der bei der Erstellung des Statement-Objekts verwendet werden soll. Der JDBC-Treiber enthält beispielsweise den Cursortyp TYPE_SS_SERVER_CURSOR_FORWARD_ONLY (ein schneller schreibgeschützter serverseitiger Vorwärtscursor für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbanken).  
  
> [!NOTE]  
> Alternativ zum SQL Server-spezifischen Cursortyp kann die selectMethod-Verbindungszeichenfolgeneigenschaft verwendet werden, indem deren Wert auf "cursor" festgelegt wird. Weitere Informationen zu den vom JDBC-Treiber unterstützten Cursortypen finden Sie unter [Grundlegendes zu Cursortypen](../../../connect/jdbc/understanding-cursor-types.md).  
  
Nachdem die Abfrage im Statement-Objekt ausgeführt und die Daten als Resultset an den Client zurückgegeben wurden, können Sie die setFetchSize-Methode aufrufen und den aus der Datenbank abgerufenen Umfang der Daten steuern. Wenn eine Tabelle beispielsweise 100 Datenzeilen enthält und die Abrufgröße auf 10 festgelegt wird, werden im Client jeweils nur immer 10 Datenzeilen zwischengespeichert. Obwohl dadurch die Verarbeitungsgeschwindigkeit der Daten sinkt, ist auf dem Client weniger Speicher erforderlich, was insbesondere dann von Nutzen sein kann, wenn umfangreiche Daten verarbeitet werden müssen.  
  
Die Codedatei für dieses Beispiel heißt „CacheResultSet.java“ und befindet sich im folgenden Pfad:  

```bash  
\<installation directory>\sqljdbc_<version>\<language>\samples\resultsets  
```

## <a name="requirements"></a>Anforderungen  

Wenn Sie diese Beispielanwendung ausführen möchten, müssen Sie die Datei „mssql-jdbc.jar“ in den Klassenpfad aufnehmen. Sie benötigen darüber hinaus Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
> Der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] enthält die Klassenbibliotheksdateien „mssql-jdbc“ für die jeweilige Verwendung mit Ihren bevorzugten JRE-Einstellungen (Java Runtime Environment). Weitere Informationen zu der JAR-Datei auswählen, finden Sie unter [Systemanforderungen für JDBC Driver](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  

## <a name="example"></a>Beispiel  

Im folgenden Beispielcode wird eine Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank hergestellt. Anschließend wird eine SQL-Anweisung mit dem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt verwendet und der serverseitige Cursortyp angegeben. Die SQL-Anweisung wird ausgeführt, und die zurückgegebenen Daten werden in ein SQLServerResultSet-Objekt eingefügt.  
  
Danach wird die benutzerdefinierte timerTest-Methode aufgerufen, wobei die zu verwendende Abrufgröße und das Resultset als Argumente übergeben werden. Die timerTest-Methode legt dann die Abrufgröße des Resultsets mithilfe der setFetchSize-Methode sowie die Startzeit des Tests fest. Anschließend wird das Resultset mit einer `While`-Schleife durchlaufen. Unmittelbar nachdem die `While`-Schleife verlassen wurde, wird die Beendigungszeit des Tests festgelegt. Anschließend wird das Testergebnis einschließlich Abrufgröße, der Anzahl verarbeiteter Zeilen und der Zeit für die Testausführung angezeigt.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.ArrayList;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

public class CacheResultSet {

    @SuppressWarnings("serial")
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(SQLServerResultSet.TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, SQLServerResultSet.CONCUR_READ_ONLY);) {

            String SQL = "SELECT * FROM Sales.SalesOrderDetail;";

            for (int n : new ArrayList<Integer>() {
                {
                    add(1);
                    add(10);
                    add(100);
                    add(1000);
                    add(0);
                }
            }) {
                // Perform a fetch for every nth row in the result set.
                try (ResultSet rs = stmt.executeQuery(SQL)) {
                    timerTest(n, rs);
                }
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void timerTest(int fetchSize,
            ResultSet rs) throws SQLException {

        // Declare the variables for tracking the row count and elapsed time.
        int rowCount = 0;
        long startTime = 0;
        long stopTime = 0;
        long runTime = 0;

        // Set the fetch size then iterate through the result set to
        // cache the data locally.
        rs.setFetchSize(fetchSize);
        startTime = System.currentTimeMillis();
        while (rs.next()) {
            rowCount++;
        }
        stopTime = System.currentTimeMillis();
        runTime = stopTime - startTime;

        // Display the results of the timer test.
        System.out.println("FETCH SIZE: " + rs.getFetchSize());
        System.out.println("ROWS PROCESSED: " + rowCount);
        System.out.println("TIME TO EXECUTE: " + runTime);
        System.out.println();
    }
}
```

## <a name="see-also"></a>Weitere Informationen finden Sie unter  

[Arbeiten mit Resultsets](../../../connect/jdbc/code-samples/working-with-result-sets.md)  
