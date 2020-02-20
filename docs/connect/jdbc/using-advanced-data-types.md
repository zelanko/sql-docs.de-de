---
title: Verwenden von erweiterten Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39461d3-48d6-4048-8300-1a886c00756d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a50bc3e4fae8fe45004374d3dd019a0f65fe544f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027010"
---
# <a name="using-advanced-data-types"></a>Verwenden von erweiterten Datentypen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] verwendet die erweiterten JDBC-Datentypen für die Konvertierung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen in ein Format, das von der Programmiersprache Java verarbeitet werden kann.  
  
## <a name="remarks"></a>Bemerkungen

Die folgende Tabelle enthält eine Liste der Standardzuordnungen zwischen den erweiterten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen sowie den JDBC- und Java-Datentypen.  
  
|SQL Server-Typen|JDBC-Typen (java.sql.Types)|Java-Typen|  
|----------------------|-----------------------------------|-------------------------|  
|varbinary(max)<br /><br /> image|LONGVARBINARY|byte[] \(default), Blob, InputStream, String|  
|text<br /><br /> varchar(max)|LONGVARCHAR|String (Standard), Clob, InputStream|  
|ntext<br /><br /> nvarchar(max)|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|String (default), Clob, NClob|  
|Xml|LONGVARCHAR<br /><br /> SQLXML|String (default), InputStream, Clob, byte[], Blob, SQLXML|  
|Udt<sup>1</sup>|VARBINARY|String (Standard), byte[], InputStream|  
|sqlvariant|SQLVARIANT|Object|  
|Geometrie<br /><br /> geography|VARBINARY|byte[]|  


<sup>1</sup> Der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt zwar das Senden und Abrufen von CLR-UDTs als binäre Daten, jedoch können CLR-Metadaten nicht bearbeitet werden.  
  
Die folgenden Abschnitte enthalten Beispiele für die Verwendung des JDBC-Treibers und der erweiterten Datentypen.  
  
## <a name="blob-and-clob-and-nclob-data-types"></a>BLOB-, CLOB- und NCLOB-Datentypen

Der JDBC-Treiber implementiert alle Methoden der java.sql.Blob-, java.sql.Clob- und java.sql.NClob-Schnittstellen.  
  
> [!NOTE]  
> CLOB-Werte können mit Datentypen von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (oder höher) mit umfangreichen Werten verwendet werden. CLOB-Typen können spezifisch mit den Datentypen **varchar(max)** und **nvarchar(max)**, BLOB-Typen mit den Datentypen **varbinary(max)** und **image** und NCLOB-Typen können mit den Datentypen **ntext** und **nvarchar(max)** verwendet werden.  

## <a name="large-value-data-types"></a>Datentypen mit umfangreichen Werten

In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] war bei der Verarbeitung von Datentypen mit umfangreichen Werten eine besondere Behandlung erforderlich. Datentypen mit umfangreichen Werten sind solche, die die maximale Zeilengröße von 8 KB überschreiten. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt einen maximalen Bezeichner für die Datentypen **varchar**, **nvarchar** und **varbinary** ein, um das Speichern von Werten in der Größenordnung von bis zu 2^31 Byte zu ermöglichen. Tabellenspalten und [!INCLUDE[tsql](../../includes/tsql-md.md)]-Variablen können den Datentyp **varchar(max)**, **nvarchar(max)** oder **varbinary(max)** angeben.  

Die Verarbeitung von Typen mit umfangreichen Werten umfasst hauptsächlich das Abrufen aus einer Datenbank sowie das Hinzufügen zu einer Datenbank. Die folgenden Abschnitte beschreiben die verschiedenen Verfahren für diese Aufgaben.  

### <a name="retrieving-large-value-types-from-a-database"></a>Abrufen von Typen mit umfangreichen Werten aus einer Datenbank

Beim Abrufen eines nicht binären Datentyps mit umfangreichen Werten aus einer Datenbank, z.B. dem Datentyp **varchar(max)**, besteht eine Vorgehensweise darin, diese Daten als Zeichendatenstrom zu lesen. Im folgenden Beispiel werden Daten mit der [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse aus der Datenbank abgerufen und als Resultset zurückgegeben. Anschließend werden die Daten mit umfangreichen Werten mit der [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)-Methode der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse aus dem Resultset gelesen.  

```java
ResultSet rs = stmt.executeQuery("SELECT TOP 1 * FROM Test1");  
rs.next();  
Reader reader = rs.getCharacterStream(2);  
```

> [!NOTE]
> Dieselbe Vorgehensweise kann für die Datentypen **text**, **ntext** und **nvarchar(max)** verwendet werden.  

Beim Abrufen eines binären Datentyps mit umfangreichen Werten aus einer Datenbank, z.B. dem Datentyp **varbinary (max)**, stehen Ihnen mehrere Vorgehensweisen zur Verfügung. Die effizienteste Vorgehensweise besteht darin, die Daten als Binärdatenstrom zu lesen, wie z. B.:  

```java
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
InputStream is = rs.getBinaryStream(2);  
```

Sie können die Daten auch mit der [getBytes](../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)-Methode wie folgt als Bytearray lesen:  

```java
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
byte [] b = rs.getBytes(2);  
```

> [!NOTE]  
> Die Daten können auch als BLOB gelesen werden. Diese Vorgehensweise ist jedoch weniger effizient als die beiden oben erwähnten Methoden.  

### <a name="adding-large-value-types-to-a-database"></a>Hinzufügen von Typen mit umfangreichen Werten zu einer Datenbank

Das Hochladen von umfangreichen Daten mit dem JDBC-Treiber funktioniert problemlos, wenn die Daten in den Arbeitsspeicher passen. Wenn der Umfang der Daten größer ist als der Arbeitsspeicher, sollte Streaming verwendet werden. Die effizienteste Möglichkeit für das Hochladen von umfangreichen Daten bilden die stream-Schnittstellen.  

Es besteht auch die Möglichkeit, eine Zeichenfolge oder Bytes zu verwenden, wie z. B.:  

```java
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (c1_id, c2_vcmax) VALUES (?, ?)");  
pstmt.setInt(1, 1);  
pstmt.setString(2, htmlStr);  
pstmt.executeUpdate();  
```

> [!NOTE]  
> Diese Vorgehensweise kann auch für Werte verwendet werden, die in den Spalten **text**, **ntext** und **nvarchar(max)** gespeichert werden.  

Wenn auf dem Server eine Bildbibliothek vorhanden ist und alle binären Bilddateien in eine **varchar(max)**-Spalte geladen werden müssen, besteht die effizienteste Methode des JDBC-Treibers darin, Datenströme wie folgt direkt zu verwenden:  

```java
try (PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (Col1, Col2) VALUES(?,?)")) { 
  File inputFile = new File("CLOBFile20mb.jpg");  
  try (FileInputStream inStream = new FileInputStream(inputFile)) {
    int id = 1;  
    pstmt.setInt(1,id);  
    pstmt.setBinaryStream(2, inStream);  
    pstmt.executeUpdate();
  }
}
```

> [!NOTE]  
> Das Hochladen von umfangreichen Daten mit der CLOB- oder BLOB-Methode ist nicht effizient.  

### <a name="modifying-large-value-types-in-a-database"></a>Ändern von Typen mit umfangreichen Werten in einer Datenbank

In den meisten Fällen wird empfohlen, zum Aktualisieren oder Ändern von umfangreichen Werten in der Datenbank mit [!INCLUDE[tsql](../../includes/tsql-md.md)]-Befehlen wie `UPDATE`, `WRITE` und `SUBSTRING` Parameter über die Klassen [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) und [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) zu übergeben.  

Wenn Sie in einer umfangreichen Textdatei ein Wort ersetzen müssen, z.B. in einer archivierten HTML-Datei, können Sie ein Clob-Objekt wie folgt verwenden:  

```java
String SQL = "SELECT * FROM test1;";  
try (Statement stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE)
     ResultSet rs = stmt.executeQuery(SQL)) {
  rs.next();

  Clob clob = rs.getClob(2);  
  long pos = clob.position("dog", 1);  
  clob.setString(pos, "cat");  
  rs.updateClob(2, clob);  
  rs.updateRow();  
}
```

Darüber hinaus besteht die Möglichkeit, die gesamte Arbeit auf dem Server auszuführen und lediglich Parameter an eine vorbereitete UPDATE-Anweisung zu übergeben.  

Weitere Informationen zu Typen mit umfangreichen Werten finden Sie in der SQL Server-Onlinedokumentation unter "Verwenden von Datentypen mit umfangreichen Werten".  

## <a name="xml-data-type"></a>XML-Datentyp

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst einen **XML**-Datentyp, mit dem Sie XML-Dokumente und -Fragmente in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank speichern können. Der **XML**-Datentyp ist ein integrierter Datentyp in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und ähnelt in einigen Punkten anderen integrierten Typen wie **int** und **varchar**. Wie andere integrierte Typen können Sie den **XML**-Datentyp beim Erstellen einer Tabelle als Spaltentyp, als Variablentyp, als Parametertyp oder als Funktionsrückgabetyp bzw. in den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktionen CAST und CONVERT verwenden.  
  
Im JDBC-Treiber kann der **XML**-Datentyp als Zeichenfolgen-, Bytearray-, Stream-, CLOB-, BLOB- oder SQLXML-Objekt zugeordnet werden. Der Standard lautet Zeichenfolge. Ab JDBC Driver, Version 2.0, unterstützt der JDBC-Treiber die JDBC 4.0-API, in der die SQLXML-Schnittstelle eingeführt wurde. Die SQLXML-Schnittstelle definiert Methoden für die Interaktion mit und die Bearbeitung von XML-Daten. Der Datentyp **SQLXML** ist dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen **xml** zugeordnet. Weitere Informationen über das Lesen und Schreiben von XML-Daten in bzw. aus einer relationalen Datenbank mit dem **SQLXML**-Java-Datentyp finden Sie unter [Unterstützen von XML-Daten](../../connect/jdbc/supporting-xml-data.md).  
  
Die Implementierung des **XML**-Datentyps im JDBC-Treiber ermöglicht Folgendes:  
  
- Zugriff auf XML-Daten als normale Java UTF-16-Zeichenfolge bei den gebräuchlichsten Programmierszenarien  
  
- Eingabe von UTF-8- und anderen 8-Bit-codierten XML-Daten  
  
- Zugriff auf XML-Daten als Bytearray mit führender Bytereihenfolgemarke (Byte Order Mark, BOM) bei Codierung in UTF-16 für den Austausch mit anderen XML-Prozessoren und Datenträgerdateien  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setzt eine führende BOM für UTF-16-codierte XML-Daten voraus. Die Anwendung muss diese bereitstellen, wenn XML-Parameterwerte als Bytearrays angegeben werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt XML-Werte immer in Form von UTF-16-Zeichenfolgen ohne BOM oder eingebettete Codierungsdeklaration aus. Wenn XML-Werte als "byte[]", "BinaryStream" oder "Blob" abgerufen werden, steht vor dem Wert ein UTF-16-BOM.  
  
Weitere Informationen zum **XML**-Datentyp finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „XML-Datentyp“.  
  
## <a name="user-defined-data-type"></a>Benutzerdefinierter Datentyp  

Das SQL-Typensystem wird durch Einführung von benutzerdefinierten Typen (UDTs, User-defined Types) in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] erweitert, sodass Sie Objekte und benutzerdefinierte Datenstrukturen in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank speichern können. UDTs können mehrere Datentypen enthalten und Verhalten zeigen, das sie von den herkömmlichen Aliasdatentypen aus einem einzelnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemdatentyp unterscheidet. UDTs werden mit einer der von der Microsoft .NET Common Language Runtime (CLR) unterstützten Sprachen definiert, die überprüfbaren Code erzeugen. Dazu gehören Visual C# und Visual Basic .NET. Die Daten werden als Felder und Eigenschaften einer .NET Framework-basierten Klasse oder Struktur offen gelegt. Die Verhalten werden durch Methoden der Klasse bzw. Struktur definiert.  
  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann ein UDT als Spaltendefinition einer Tabelle, als Variable in einem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batch oder als Argument einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktion oder gespeicherten Prozedur verwendet werden.  
  
Weitere Informationen zu benutzerdefinierten Datentypen finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „Verwenden und Ändern von Instanzen von benutzerdefinierten Typen“.  
  
## <a name="sql_variant-data-type"></a>Sql_variant-Datentyp

Weitere Informationen über den Datentyp sql_variant finden Sie unter [Verwenden des sql_variant-Datentyps](../../connect/jdbc/using-sql-variant-datatype.md).  

## <a name="spatial-data-types"></a>Räumliche Datentypen

Informationen zu räumlichen Datentypen finden Sie unter [Verwenden von räumlichen Datentypen](../../connect/jdbc/use-spatial-datatypes.md).  

## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
