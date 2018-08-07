---
title: Abrufen von Resultsetdaten Datenbeispiel festlegen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1b190c36-3d38-49a2-8599-612329675851
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8fe0d97c8a8ec0f29e8a6b85542ea0627a5c6fb
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279141"
---
# <a name="retrieving-result-set-data-sample"></a>Abrufen von Resultsetdaten - Beispiel
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] veranschaulicht, wie Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenbank abgerufen und anschließend angezeigt werden.  
  
 Die Codedatei für dieses Beispiel heißt „RetrieveRS.java“ und befindet sich im folgenden Pfad:  
  
 \<*Installationsverzeichnis*> \sqljdbc_\<*Version*>\\<*Sprache*> \samples\resultsets  
  
## <a name="requirements"></a>Anforderungen  
 Wenn Sie diese Beispielanwendung ausführen möchten, müssen Sie die Datei „mssql-jdbc.jar“ in den Klassenpfad aufnehmen. Sie benötigen darüber hinaus Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] enthält die Klassenbibliotheksdateien „mssql-jdbc“ für die jeweilige Verwendung mit Ihren bevorzugten JRE-Einstellungen (Java Runtime Environment). Weitere Informationen zu der JAR-Datei auswählen, finden Sie unter [Systemanforderungen für JDBC Driver](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispielcode wird eine Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank hergestellt. Anschließend wird eine SQL-Anweisung mit dem [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt verwendet. Die SQL-Anweisung wird ausgeführt, und die zurückgegebenen Daten werden in ein [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt eingefügt.  
  
 Danach ruft der Beispielcode die benutzerdefinierte displayRow-Methode auf, um die Datenzeilen im Resultset zu durchlaufen. Mithilfe der [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)-Methode werden einige der Daten angezeigt.  
  
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class RetrieveRS {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT * FROM Production.Product;";
            ResultSet rs = stmt.executeQuery(SQL);
            displayRow("PRODUCTS", rs);
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
            System.out.println(rs.getString("ProductNumber") + " : " + rs.getString("Name"));
        }
    }
}
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Arbeiten mit Resultsets](../../connect/jdbc/working-with-result-sets.md)  
  
  
