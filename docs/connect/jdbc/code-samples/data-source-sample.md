---
title: Datenquellen Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b4a933ee-f2c6-4e0d-a96d-6dd061abf759
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 61ad7ad7a2de372d4b223986d141fee76882d512
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957216"
---
# <a name="data-source-sample"></a>Beispiel für Datenquellen

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] veranschaulicht, wie unter Verwendung eines Datenquellenobjekts eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank hergestellt wird. Darüber hinaus wird gezeigt, wie Daten mithilfe einer gespeicherten Prozedur aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank abgerufen werden.

Die Codedatei für dieses Beispiel heißt „ConnectDataSource.java“ und befindet sich im folgenden Pfad:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\connections
```

## <a name="requirements"></a>Anforderungen

Wenn Sie diese Beispielanwendung ausführen möchten, müssen Sie die Datei „mssql-jdbc.jar“ in den Klassenpfad aufnehmen. Sie benötigen darüber hinaus Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] enthält die Klassenbibliotheksdateien „mssql-jdbc“ für die jeweilige Verwendung mit Ihren bevorzugten JRE-Einstellungen (Java Runtime Environment). Weitere Informationen zum Auswählen der richtigen JAR-Datei finden Sie unter [Systemanforderungen für den JDBC-Treiber](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Beispiel

Im folgenden Beispielcode werden verschiedene Verbindungseigenschaften mithilfe der Setter-Methoden des Objekts [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) festgelegt. anschließend wird die [getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)-Methode des SQLServerDataSource-Objekts aufgerufen, um ein [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt zurückzugeben.

Anschließend wird die Methode [prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) des SQLServerConnection-Objekts verwendet, um ein [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Objekt zu erstellen. Danach wird die Methode [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) aufgerufen, um die gespeicherte Prozedur auszuführen.

Abschließend wird das [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt verwendet, das von der executeQuery-Methode zurückgegeben wurde, um die von der gespeicherten Prozedur zurückgegebenen Ergebnisse zu durchlaufen.

```java
import java.sql.CallableStatement;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class ConnectDataSource {

    public static void main(String[] args) {

        // Create datasource.
        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setUser("<user>");
        ds.setPassword("<password>");
        ds.setServerName("<server>");
        ds.setPortNumber(Integer.parseInt("<port>"));
        ds.setDatabaseName("AdventureWorks");

        try (Connection con = ds.getConnection();
                CallableStatement cstmt = con.prepareCall("{call dbo.uspGetEmployeeManagers(?)}");) {
            // Execute a stored procedure that returns some data.
            cstmt.setInt(1, 50);
            ResultSet rs = cstmt.executeQuery();

            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println("EMPLOYEE: " + rs.getString("LastName") + ", " + rs.getString("FirstName"));
                System.out.println("MANAGER: " + rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));
                System.out.println();
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen

[Verbinden und Abrufen von Daten](../../../connect/jdbc/code-samples/connecting-and-retrieving-data.md)
