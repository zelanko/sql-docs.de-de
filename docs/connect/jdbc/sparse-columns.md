---
title: Sparsespalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7d4237e0-818f-4639-9093-d5ac9683fc71
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b65250d6bd0ea911ee0d043e2768ae04ce9264d4
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278692"
---
# <a name="sparse-columns"></a>Spalten mit geringer Dichte
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Spalten mit geringer Dichte sind gewöhnliche Spalten, die einen optimierten Speicher für NULL-Werte haben. Spalten mit geringer Dichte reduzieren die Speicherplatzanforderungen von NULL-Werten auf Kosten eines erhöhten Aufwands, um Werte ungleich NULL abzurufen. Verwenden Sie Sparsespalten, wenn dadurch mindestens 20 Prozent bis 40 Prozent Speicherplatz eingespart werden.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] JDBC Driver 3.0 werden bei der Herstellung einer Verbindung mit einem Server von [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] (oder höher) Sparsespalten unterstützt. Sie können [SQLServerDatabaseMetaData.getColumns](../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md), [SQLServerDatabaseMetaData.getFunctionColumns](../../connect/jdbc/reference/getfunctioncolumns-method-sqlserverdatabasemetadata.md) oder [SQLServerDatabaseMetaData.getProcedureColumns](../../connect/jdbc/reference/getprocedurecolumns-method-sqlserverdatabasemetadata.md) verwenden, um zu ermitteln, welche Spalte die Sparsespalte und welche die Spaltensatz-Spalte ist.  
  
 Spaltensätze sind berechnete Spalten, die alle Sparsespalten im nicht typisierten XML-Format zurückgeben. Verwenden Sie Spaltensätze, wenn die Tabelle eine große Anzahl an Spalten (oder mehr als 1024 Spalten) enthält und es sehr aufwändig ist, einzelne Sparsespalten zu verarbeiten. Ein Spaltensatz kann bis zu 30 000 Spalten enthalten.  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>und Beschreibung  
 Dieses Beispiel zeigt, wie Spaltensätze erkannt werden. Des Weiteren zeigt es, wie die XML-Ausgabe eines Spaltensatzes analysiert wird, um die Daten aus den Sparsespalten zu erhalten.  
  
 Die erste Codeauflistung ist die Transact-SQL, die auf diesem Server ausgeführt werden sollte.  
  
 Die zweite Codeauflistung ist der Java-Quellcode. Bevor Sie die Anwendung kompilieren, ändern Sie die Verbindungszeichenfolge an.  
  
### <a name="code"></a>Code  
  
```sql
use AdventureWorks  
CREATE TABLE ColdCalling  
(  
ID int IDENTITY(1,1) PRIMARY KEY,  
[Date] date,  
[Time] time,  
PositiveFirstName nvarchar(50) SPARSE,  
PositiveLastName nvarchar(50) SPARSE,  
SpecialPurposeColumns XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
);  
GO  
  
INSERT ColdCalling ([Date], [Time])  
VALUES ('10-13-09','07:05:24')  
GO  
  
INSERT ColdCalling ([Date], [Time], PositiveFirstName, PositiveLastName)  
VALUES ('07-20-09','05:00:24', 'AA', 'B')  
GO  
  
INSERT ColdCalling ([Date], [Time], PositiveFirstName, PositiveLastName)  
VALUES ('07-20-09','05:15:00', 'CC', 'DD')  
GO  
```  
  
### <a name="code"></a>Code  
  
```java
import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;

import org.xml.sax.InputSource;

import java.io.StringReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.Statement;

import org.w3c.dom.Document;
import org.w3c.dom.Node;
import org.w3c.dom.NodeList;

public class SparseColumns {
    public static void main(String args[]) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        ResultSet rs = null;

        try (Connection conn = DriverManager.getConnection(connectionUrl);
                Statement stmt = conn.createStatement();) {

            // Determine the column set column
            String columnSetColName = null;
            String strCmd = "SELECT name FROM sys.columns WHERE object_id=(SELECT OBJECT_ID('ColdCalling')) AND is_column_set = 1";
            rs = stmt.executeQuery(strCmd);

            if (rs.next()) {
                columnSetColName = rs.getString(1);
                System.out.println(columnSetColName + " is the set column!");
            }

            strCmd = "SELECT * FROM ColdCalling";
            rs = stmt.executeQuery(strCmd);

            // Iterate through the result set
            ResultSetMetaData rsmd = rs.getMetaData();

            DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
            DocumentBuilder db = dbf.newDocumentBuilder();
            InputSource is = new InputSource();
            while (rs.next()) {
                // Iterate through the columns
                for (int i = 1; i <= rsmd.getColumnCount(); ++i) {
                    String name = rsmd.getColumnName(i);
                    String value = rs.getString(i);

                    // If this is the column set column
                    if (name.equalsIgnoreCase(columnSetColName)) {
                        System.out.println(name);

                        // Instead of printing the raw XML, parse it
                        if (value != null) {
                            // Add artificial root node "sparse" to ensure XML is well formed
                            String xml = "<sparse>" + value + "</sparse>";

                            is.setCharacterStream(new StringReader(xml));
                            Document doc = db.parse(is);

                            // Extract the NodeList from the artificial root node that was added
                            NodeList list = doc.getChildNodes();
                            // This is the <sparse> node
                            Node root = list.item(0);
                            // These are the xml column nodes
                            NodeList sparseColumnList = root.getChildNodes();

                            // Iterate through the XML document
                            for (int n = 0; n < sparseColumnList.getLength(); ++n) {
                                Node sparseColumnNode = sparseColumnList.item(n);
                                String columnName = sparseColumnNode.getNodeName();
                                // Note that the column value is not in the sparseColumNode, it is the value of the first child of it
                                Node sparseColumnValueNode = sparseColumnNode.getFirstChild();
                                String columnValue = sparseColumnValueNode.getNodeValue();

                                System.out.println("\t" + columnName + "\t: " + columnValue);
                            }
                        }
                    }
                    else {   // Just print the name + value of non-sparse columns
                        System.out.println(name + "\t: " + value);
                    }
                }
                System.out.println();// New line between rows
            }
        }
        // Handle any errors that may have occurred.
        catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
