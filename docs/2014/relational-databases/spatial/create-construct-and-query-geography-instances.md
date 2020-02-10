---
title: Erstellen, Aufbauen und Abfragen von geography-Instanzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server]
- geodetic data type [SQL Server]
- geography data type [SQL Server], about geography data type
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 5dde7575a3f657b89d29fefa0da52002bcd6af28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014297"
---
# <a name="create-construct-and-query-geography-instances"></a>Erstellen, Aufbauen und Abfragen von geography-Instanzen
  Der räumliche `geography`-Datentyp stellt Daten in einem Erdkugel-Koordinatensystem dar. Dieser Datentyp wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]als .NET CLR-Datentyp (Common Language Runtime) implementiert. Der Datentyp [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` speichert elliptische Daten (Globusmodell), wie z. B. GPS-Koordinaten in Längen- und Breitengraden.  
  
 Der `geography`-Typ ist vordefiniert und in jeder Datenbank verfügbar. Sie können Tabellenspalten des `geography`-Typs in der gleichen Weise erstellen und `geography`-Daten in der gleichen Weise verwenden wie andere vom System bereitgestellte Typen.  
  
##  <a name="creating"></a>Erstellen oder Erstellen einer neuen geography-Instanz  
  
###  <a name="existing"></a>Erstellen einer neuen geography-Instanz aus einer vorhandenen Instanz  
 Der `geography`-Datentyp stellt viele integrierte Methoden zur Verfügung, mit denen neue `geography`-Instanzen auf der Grundlage vorhandener Instanzen erstellt werden können.  
  
 **So erstellen Sie einen Puffer um eine Geografie**  
 [STBuffer &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 **So erstellen Sie einen Puffer um eine Geografie mit einer Toleranz**  
 [BufferWithTolerance &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 **So erstellen Sie eine geography-Instanz aus der Schnittmenge von zwei geography-Instanzen**  
 [Stschnitt &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **So erstellen Sie eine geography-Instanz aus der Vereinigung von zwei geography-Instanzen**  
 [Der Datentyp der STUnion-&#40;geography&#41;](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 **So erstellen Sie eine Geografie aus den Punkten, an denen sich eine Geografie nicht überschneidet**  
 [STDifference &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="wkt"></a>Erstellen einer geography-Instanz anhand einer bekannten Text Eingabe  
 Der `geography`-Datentyp bietet mehrere integrierte Methoden zur Erstellung einer Geografie anhand der WKT-Darstellung des Open Geospatial Consortium (OGC). Der WKT-Standard ist eine Textzeichenfolge, die den Austausch von Geografiedaten in Textform ermöglicht.  
  
 **So erstellen Sie einen beliebigen geography-Instanztyp anhand einer WKT-Eingabe**  
 [STGeomFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [&#40;geography-Datentyp analysieren&#41;](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 **So erstellen Sie eine geography-Point-Instanz anhand einer WKT-Eingabe**  
 [STPointFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 **So erstellen Sie eine Multipoint-geography-Instanz anhand einer WKT-Eingabe**  
 [STMPointFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 **So erstellen Sie eine LineString-geography-Instanz anhand einer WKT-Eingabe**  
 STLineFromText (geography-Datentyp)  
  
 **So erstellen Sie eine MultiLineString-geography-Instanz anhand einer WKT-Eingabe**  
 [STMLineFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 **So erstellen Sie eine Polygon-geography-Instanz anhand einer WKT-Eingabe**  
 [STPolyFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 **So erstellen Sie eine MultiPolygon-geography-Instanz anhand einer WKT-Eingabe**  
 [STMPolyFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 **So erstellen Sie eine GeometryCollection-geography-Instanz anhand einer WKT-Eingabe**  
 [STGeomCollFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="wkb"></a>Erstellen einer geography-Instanz aus einer bekannten binären Eingabe  
 WKB ist ein vom OGC spezifiziertes Binärformat, das den Austausch von `Geography`-Daten zwischen einer Clientanwendung und einer SQL-Datenbank ermöglicht. Die folgenden Funktionen akzeptieren die WKB-Eingabe zum Zweck der Erstellung von geography-Instanzen:  
  
 **So erstellen Sie einen beliebigen geography-Instanztyp anhand einer WKB-Eingabe**  
 [STGeomFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 **So erstellen Sie eine geography-Point-Instanz anhand einer WKB-Eingabe**  
 [STPointFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 **So erstellen Sie eine Multipoint-geography-Instanz anhand einer WKB-Eingabe**  
 [STMPointFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 **So erstellen Sie eine LineString-geography-Instanz anhand einer WKB-Eingabe**  
 [STLineFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 **So erstellen Sie eine MultiLineString-geography-Instanz anhand einer WKB-Eingabe**  
 [STMLineFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 **So erstellen Sie eine Polygon-geography-Instanz anhand einer WKB-Eingabe**  
 [STPolyFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 **So erstellen Sie eine MultiPolygon-geography-Instanz anhand einer WKB-Eingabe**  
 [STMPolyFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 **So erstellen Sie eine GeometryCollection-geography-Instanz anhand einer WKB-Eingabe**  
 [STGeomCollFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type) STGeomCollFromWKB (geography-Datentyp)  
  
###  <a name="gml"></a>Erstellen einer geography-Instanz anhand einer GML-Text Eingabe  
 Der `geography` -Datentyp stellt eine Methode bereit, `geography` die eine-Instanz aus GML generiert, einer `geography` XML-Darstellung einer-Instanz. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt eine Teilmenge von GML.  
  
 Weitere Informationen über Geography Markup Language finden Sie in der OGC-Spezifikation: [OGC Specifications, Geography Markup Language.](https://go.microsoft.com/fwlink/?LinkId=93629)  
  
 **So erstellen Sie einen beliebigen geography-Instanztyp anhand einer GML-Eingabe**  
 [GeomFromGml &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning"></a>Zurückgeben von wohl bekanntem Text und bekannter Binärdaten aus einer geography-Instanz  
 Anhand der folgenden Methoden können Sie entweder das WKT- oder das WKB-Format einer `geography` zurückgeben:  
  
 **So geben Sie die WKT-Darstellung einer geography-Instanz zurück**  
 [Der Datentyp "STAsText &#40;geography"&#41;](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [&#40;geography-Datentyp ""&#41;](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 **So geben Sie die WKT-Darstellung einer geography-Instanz einschließlich der Z-und M-Werte zurück**  
 [AsTextZM &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 **So geben Sie die WKB-Darstellung einer geography-Instanz zurück**  
 [STAsBinary-&#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 **So geben Sie eine GML-Darstellung einer geography-Instanz zurück**  
 [Datentyp der AsGml-&#40;geography&#41;](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="query"></a>Abfragen von Eigenschaften und Verhalten von geography-Instanzen  
 Alle `geography` -Instanzen verfügen über eine Reihe von Eigenschaften, die über von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellte Methoden abgerufen werden können. In den folgenden Themen werden die Eigenschaften und Verhalten von geography-Typen und die Methoden zum Abrufen der einzelnen Eigenschaften und Verhalten beschrieben.  
  
###  <a name="valid"></a>Gültigkeit, Instanztyp und GeometryCollection-Informationen  
 Nachdem eine `geography`-Instanz erstellt wurde, können Sie anhand der folgenden Methoden den Instanztyp zurückgeben. Wenn es sich um eine `GeometryCollection`-Instanz handelt, können Sie eine bestimmte `geography`-Instanz zurückgeben.  
  
 **So geben Sie den Instanztyp einer Geografie zurück**  
 [STGeometryType &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 **So bestimmen Sie, ob eine Geografie einen gegebenen Instanztyp hat**  
 [Instanceof &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 **So bestimmen Sie, ob eine geography-Instanz für Ihren Instanztyp wohl geformt ist**  
 [STNumGeometries &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 **So geben Sie eine bestimmte Geografie in einer GeometryCollection-Instanz zurück**  
 [STGeometryN &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type) STGeometryN (geography-Datentyp)  
  
###  <a name="number"></a>Anzahl von Punkten  
 Alle nicht leeren `geography` Instanzen bestehen aus *Punkten*. Diese Punkte stellen den Längengrad und den Breitengrad der Erde dar, auf die die `geography`-Instanzen gezeichnet werden. Der Datentyp `geography` stellt zahlreiche integrierte Methoden bereit zum Abfragen der Punkte einer Instanz.  
  
 **So geben Sie die Anzahl von Punkten zurück, aus denen eine Instanz besteht**  
 [STNumPoints &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 **So geben Sie einen bestimmten Punkt in einer Instanz zurück**  
 [STPointN &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 **So geben Sie den Startpunkt einer Instanz zurück**  
 [STStartPoint &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 **So geben Sie den Endpunkt einer Instanz zurück**  
 [STEndpoint &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a>Maß  
 Eine nicht leere `geography`-Instanz kann null-, ein- oder zweidimensional sein. NULL dimensionale `geography` Instanzen, wie z. `Point` b `MultiPoint`. und, haben keine Länge bzw. keinen Bereich. Eindimensionale Objekte (z. B. `LineString, CircularString`, `CompoundCurve` und `MultiLineString`) weisen eine Länge auf. Zweidimensionale Instanzen (z. B. `Polygon, CurvePolygon` und `MultiPolygon`) weisen eine Fläche und eine Länge auf. Für leere Instanzen wird als Dimension -1 ausgegeben, und für eine `GeometryCollection`-Auflistung wird die maximale Dimension der darin enthaltenen Elemente zurückgegeben.  
  
 **So geben Sie die Dimension einer Instanz zurück**  
 [STDimension &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 **So geben Sie die Länge einer Instanz zurück**  
 [STLength &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 **So geben Sie den Bereich einer Instanz zurück**  
 [Datentyp der STArea-&#40;geography&#41;](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a>Leer  
 Eine *leere* `geography` -Instanz besitzt keine Punkte. Die Länge von leeren `LineString, CircularString`-, `CompoundCurve`- und `MultiLineString`-Instanzen ist 0 (null). Die Fläche von leeren `Polygon, CurvePolygon`- und `MultiPolygon`-Instanzen ist 0 (null).  
  
 **So bestimmen Sie, ob eine Instanz leer ist**  
 [Stitmpty &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a>Sperrung  
 Eine *geschlossene* `geography` -Instanz ist eine Abbildung, deren Start-und Endpunkte identisch sind. Alle `Polygon`-Instanzen gelten als geschlossen. Alle `Point`-Instanzen gelten als nicht geschlossen.  
  
 Ein Ring ist eine einfache, geschlossene `LineString`-Instanz.  
  
 **So bestimmen Sie, ob eine Instanz geschlossen ist**  
 [STIsClosed &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 **So geben Sie die Anzahl von Ringen in einer Polygon-Instanz zurück**  
 [NumRings &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 **So geben Sie einen angegebenen Ring einer geography-Instanz zurück**  
 [Der Datentyp "RingN &#40;geography"&#41;](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="srid"></a>SRID (Spatial Reference ID)  
 Der SRID (Spatial Reference ID) ist ein Bezeichner, der das ellipsenförmige Koordinatensystem angibt, in dem die `geography`-Instanz dargestellt wird. Zwei `geography`-Instanzen mit unterschiedlichen SRIDs können nicht verglichen werden.  
  
 **So können Sie die SRID einer Instanz festlegen oder zurückgeben**  
 [STSrid &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 Diese Eigenschaft kann geändert werden.  
  
##  <a name="rel"></a>Bestimmen von Beziehungen zwischen geography-Instanzen  
 Der `geography`-Datentyp stellt viele integrierte Methoden zur Verfügung, mit denen die Beziehungen zwischen zwei `geography`-Instanzen bestimmt werden können.  
  
 **So bestimmen Sie, ob zwei Instanzen die gleiche Punkt Menge umfassen**  
 [STEquals &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 **So bestimmen Sie, ob zwei Instanzen disjunkt sind**  
 [STDisjoint &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 **So bestimmen Sie, ob sich zwei Instanzen überschneiden**  
 [STIntersects &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 **So bestimmen Sie die Punkte oder Punkte, an denen sich zwei Instanzen überschneiden**  
 [Stschnitt &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **So bestimmen Sie die kürzeste Entfernung zwischen Punkten in zwei geography-Instanzen**  
 [STDistance &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 **So bestimmen Sie den Unterschied zwischen zwei geography-Instanzen in Punkten**  
 [STDifference &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 **So leiten Sie die symmetrische Differenz oder eindeutigen Punkte einer geography-Instanz ab, die mit einer anderen Instanz verglichen wird**  
 [STSymDifference &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="supportedsrid"></a>geography-Instanzen müssen unterstützte SRID verwenden  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt SRIDs auf der Grundlage der EPSG-Standards. Wenn Berechnungen mit geografischen räumlichen Daten ausgeführt werden oder Methoden mit geografischen räumlichen Daten verwendet werden, müssen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützte SRIDs für `geography`-Instanzen verwendet werden. Die SRID muss mit einer der SRIDs übereinstimmen, die in der **sys.spatial_reference_systems** -Katalogsicht angezeigt werden. Wie bereits erwähnt, hängen die Ergebnisse von Berechnungen mit räumlichen Daten unter Verwendung des `geography`-Datentyps von der Ellipsenform ab, die zur Erstellung der Daten verwendet wurde, da jeder Ellipsenform ein bestimmter SRID zugeordnet wird.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird beim Einsatz von Methoden für `geography`-Instanzen standardmäßig der SRID 4326 verwendet, der dem räumlichen Referenzsystem WGS 84 zugeordnet ist. Wenn Sie Daten aus einem anderen räumlichen Referenzsystem als WGS 84 (bzw. SRID 4326) verwenden, müssen Sie die SRID dieser geografischen räumlichen Daten bestimmen.  
  
##  <a name="examples"></a>Beispiele  
 Die folgenden Beispiele zeigen, wie Geografiedaten hinzugefügt und abgefragt werden.  
  
-   Im ersten Beispiel wird eine Tabelle mit einer Identitätsspalte und der `geography` -Spalte `GeogCol1`erstellt. Eine dritte Spalte rendert die `geography` -Spalte als Darstellung im Open Geospatial Consortium (OGC) WKT-Format und verwendet die `STAsText()` -Methode. Dann werden zwei Zeilen eingefügt: Eine Zeile enthält eine `LineString` -Instanz des Typs `geography`und die andere eine `Polygon` -Instanz.  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   Im zweiten Beispiel werden mithilfe der `STIntersection()` -Methode die Punkte zurückgegeben, an denen die beiden zuvor eingegebenen `geography` -Instanzen sich schneiden.  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Räumliche Daten &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
