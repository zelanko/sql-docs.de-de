---
title: Verwenden räumlicher Datentypen | Microsoft-Dokumentation
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
ms.openlocfilehash: f133fa066ef2c486cf7bb40c5b653c99e077bc46
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026946"
---
# <a name="using-spatial-datatypes"></a>Verwenden von räumlichen Datentypen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Räumliche Datentypen (Geometry und geography) werden unterstützt, wenn die Vorschauversion des JDBC-Treibers 6.5.0 gestartet wird. Räumliche Datentypen werden derzeit nicht mit gespeicherten Prozeduren, Tabellenwert Parametern (TVP), BulkCopy und Always Encrypted unterstützt. Diese Seite zeigt verschiedene Anwendungsfälle von Geometry-und geography-Datentypen mit dem JDBC-Treiber. Eine Übersicht über räumliche Datentypen finden Sie auf der Seite [Übersicht über räumliche Datentypen](https://docs.microsoft.com/sql/relational-databases/spatial/spatial-data-types-overview) .

## <a name="creating-a-geometry--geography-object"></a>Erstellen eines Geometry/geography-Objekts

Es gibt zwei Hauptmethoden zum Erstellen eines Geometry/geography-Objekts: konvertieren Sie eine Konvertierung von einem bekannten Text (WKT) oder eine bekannte Binärdatei (WKB).

### <a name="creating-from-wkt"></a>Erstellen aus WKT

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

Dadurch wird ein LineString-Geometry-Objekt mit SRID (Spatial Reference System Identifier) und ein geography-Objekt mit SRID 4326 erstellt.

### <a name="creating-from-wkb"></a>Erstellen aus WKB

```java
byte[] geomWKB = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogWKB = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomWKB);
Geography geogWKT = Geography.deserialize(geogWKB);
```

Dadurch wird ein Geometry-und geography-Objekt erstellt, das den zuvor erstellten WKT-Objekten entspricht.

## <a name="working-with-a-geometry--geography-object"></a>Arbeiten mit einem Geometry/geography-Objekt

Angenommen, der Benutzer hat eine Tabelle auf SQL Server wie unten dargestellt:

```sql
CREATE TABLE sampleTable (c1 geometry)  
```

Ein Beispielskript zum Einfügen eines Geometrie Werts wäre:

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) connection.prepareStatement("insert into sampleTable values (?)");
pstmt.setGeometry(1, geomWKT);  
pstmt.execute();
```

Dasselbe gilt für das Geography-Pendant mit einer geography-Spalte und der **setgeography ()** -Methode.

So lesen Sie eine Geometry/geography-Spalte:

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

Dasselbe gilt für das Geography-Pendant mit einer geography-Spalte und der **getgeography ()** -Methode.

## <a name="newly-introduced-apis"></a>Neu eingeführte APIs

Dabei handelt es sich um die neuen öffentlichen APIs, die mit dieser Addition eingeführt wurden, in den Klassen **SQLServerPreparedStatement**, **SQLServerResultSet**, **Geometry**und **geography**.

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|Methode|und Beschreibung|
|:------|:----------|
|void setgeometry (int n, Geometry x)| Legt den angegebenen Parameter auf das angegebene Microsoft. SQL. Geometry-Klassenobjekt fest.
|void setGeography(int n, Geography x)| Legt den angegebenen Parameter auf das angegebene Microsoft. SQL. geography-Klassenobjekt fest.

### <a name="sqlserverresultset"></a>SQLServerResultSet

|Methode|und Beschreibung|
|:------|:----------|
|Geometrie GetGeometry (int colunindex)| Gibt den Wert der angegebenen Spalte in der aktuellen Zeile dieses Resultset-Objekts als com. Microsoft. SqlServer. JDBC. Geometry-Objekt in der Programmiersprache Java zurück.
|Geometrie GetGeometry (String ColumnName)| Gibt den Wert der angegebenen Spalte in der aktuellen Zeile dieses Resultset-Objekts als com. Microsoft. SqlServer. JDBC. Geometry-Objekt in der Programmiersprache Java zurück.
|Geography getgeography (int colunindex)| Gibt den Wert der angegebenen Spalte in der aktuellen Zeile dieses Resultset-Objekts als com. Microsoft. SqlServer. JDBC. geography-Objekt in der Programmiersprache Java zurück.
|Geography getgeography (String ColumnName)| Gibt den Wert der angegebenen Spalte in der aktuellen Zeile dieses Resultset-Objekts als com. Microsoft. SqlServer. JDBC. geography-Objekt in der Programmiersprache Java zurück.

### <a name="geometry"></a>Geometry

|Methode|und Beschreibung|
|:------|:----------|
|Geometry STGeomFromText (String WKT, int SRID)| Konstruktor für eine Geometry-Instanz aus einer WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium), die um alle von der Instanz getragenen Z- und M-Werte (Höhe/Measure) erweitert wurde.
|Geometry STGeomFromWKB(byte[] wkb)| Konstruktor für eine Geometry-Instanz aus einer Darstellung des Typs „Open Geospatial-Konsortium (OGC) Well-Known Binary (WKB)“.
|Deserialisieren von Geometrien (Byte [] WKB)| Konstruktor für eine geometry-Instanz aus einem internen SQL Server-Format für räumliche Daten.
|Geometry-Analyse (Zeichenfolge WKT)| Konstruktor für eine Geometry-Instanz aus einer WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium). Der räumliche Verweis Bezeichner wird standardmäßig auf 0 (null).
|Geometry-Punkt (Double x, Double y, int SRID)| Konstruktor für eine geometry-Instanz, die eine Point-Instanz aus den X-und Y-Werten und einem räumlichen Verweis Bezeichner darstellt.
|Zeichenfolge STAsText ()| Gibt die WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium) einer Geometry-Instanz zurück. Dieser Text enthält keine Z (Höhe)- oder M (Measure)-Werte, die von der Instanz getragen werden.
|byte[] STAsBinary()| Gibt die WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium) einer Geometry-Instanz zurück. Dieser Wert enthält keine Z- oder M-Werte, die von der Instanz getragen werden.
|byte[] serialize()| Gibt die Bytes zurück, die ein internes SQL Server-Format vom Geometry-Typ darstellen.
|Boolescher HasM ()| Gibt zurück, wenn das Objekt einen M (Measure)-Wert enthält.
|Boolescher Hasz ()| Gibt zurück, wenn das Objekt einen Z-Wert (Höhe) enthält.
|Double GetX ()| Gibt den X-Koordinaten Wert zurück.
|Double Gety ()| Gibt den Y-Koordinaten Wert zurück.
|Double getm ()| Gibt den M (Measure)-Wert des-Objekts zurück.
|Double Getz ()| Gibt den Z-Wert (Höhe) des-Objekts zurück.
|int getSrid()| Gibt den SRID-Wert (Spatial Reference Identifier) zurück.
|boolean isNull()| Gibt zurück, wenn das Geometry-Objekt NULL ist.
|int STNumPoints()| Gibt die Anzahl der Punkte im Geometry-Objekt zurück.
|String STGeometryType ()| Gibt den durch eine geometry-Instanz dargestellten Open Geospatial Consortium (OGC)-Typnamen zurück.
|Zeichenfolge AsTextZM ()| Gibt die WKT-Darstellung (Well-Known Text) des Geometry-Objekts zurück.
|String-Zeichenfolge ()| Gibt die Zeichenfolgendarstellung des Geometry-Objekts zurück.

### <a name="geography"></a>Geography

|Methode|und Beschreibung|
|:------|:----------|
|Geography STGeomFromText (String WKT, int SRID)| Konstruktor für eine Geography-Instanz aus einer WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium), die um alle von der Instanz getragenen Z- und M-Werte (Höhe/Measure) erweitert wurde.
|Geography STGeomFromWKB(byte[] wkb)| Konstruktor für eine Geography-Instanz aus einer Darstellung des Typs „Open Geospatial-Konsortium (OGC) Well-Known Binary (WKB)“.
|Geography-Deserialisierung (Byte [] WKB)| Konstruktor für eine geography-Instanz aus einem internen SQL Server-Format für räumliche Daten.
|Geography-Analyse (Zeichenfolge WKT)| Konstruktor für eine Geography-Instanz aus WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium). Der räumliche Verweis Bezeichner wird standardmäßig auf 0 (null).
|Geography Point (Double Lon, Double lat, int SRID)| Konstruktor für eine Geography-Instanz, die mit Ihren Längen- und Breitengraden sowie mit einem Spatial Reference Identifier eine Point-Instanz darstellt.
|Zeichenfolge STAsText ()| Gibt die WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium) einer Geography-Instanz zurück. Dieser Text enthält keine Z (Höhe)- oder M (Measure)-Werte, die von der Instanz getragen werden.
|byte[] STAsBinary())| Gibt die WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium) einer Geography-Instanz zurück. Dieser Wert enthält keine Z- oder M-Werte, die von der Instanz getragen werden.
|byte[] serialize()| Gibt die Bytes zurück, die ein internes SQL Server-Format vom Geography-Typ darstellen.
|Boolescher HasM ()| Gibt zurück, wenn das Objekt einen M (Measure)-Wert enthält.
|Boolescher Hasz ()| Gibt zurück, wenn das Objekt einen Z-Wert (Höhe) enthält.
|Double getlatitude ()| Gibt den Breitengrad Wert zurück.
|Double getLongitude()| Gibt den Längen Wert zurück.
|Double getm ()| Gibt den M (Measure)-Wert des-Objekts zurück.
|Double Getz ()| Gibt den Z-Wert (Höhe) des-Objekts zurück.
|int getSrid()| Gibt den SRID-Wert (Spatial Reference Identifier) zurück.
|boolean isNull()| Gibt zurück, wenn das Geography-Objekt NULL ist.
|int STNumPoints()| Gibt die Anzahl der Punkte im geography-Objekt zurück.
|String stgeographytype ()| Gibt den durch eine geography-Instanz dargestellten Open Geospatial Consortium (OGC)-Typnamen zurück.
|Zeichenfolge AsTextZM ()| Gibt die WKT-Darstellung (Well-Known Text) des geography-Objekts zurück.
|String-Zeichenfolge ()| Gibt die Zeichenfolgendarstellung des Geography-Objekts zurück.

## <a name="limitations-of-spatial-datatypes"></a>Einschränkungen räumlicher Datentypen

1. Die räumlichen untergeordneten Datatypes **circularstring**, **compoundcurve**, **CurvePolygon**und **fullglobe** werden nur ab SQL Server 2012 und höher unterstützt.

2. Always Encrypted kann nicht mit räumlichen Datentypen verwendet werden.

3. Gespeicherte Prozeduren, TVP und BulkCopy-Vorgänge werden derzeit nicht mit räumlichen Datentypen unterstützt.

## <a name="see-also"></a>Siehe auch

[Beispiel für räumliche Datentypen (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)
