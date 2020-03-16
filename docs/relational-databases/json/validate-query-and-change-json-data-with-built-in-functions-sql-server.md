---
title: Überprüfen, Abfragen und Ändern von JSON-Daten mit integrierten Funktionen
ms.date: 07/17/2017
ms.prod: sql
ms.reviewer: genemi
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- JSON, built-in functions
- functions (JSON)
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
author: jovanpop-msft
ms.author: jovanpop
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8ddc5fb198a62374fc43ebacb5fa7423ac9fadd5
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79287894"
---
# <a name="validate-query-and-change-json-data-with-built-in-functions-sql-server"></a>Überprüfen, Abfragen und Ändern von JSON-Daten mit integrierten Funktionen (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Die integrierte Unterstützung für JSON umfasst die integrierten Funktionen, die in diesem Thema kurz beschrieben werden.  
  
-   [ISJSON](#ISJSON) testet, ob eine Zeichenfolge gültiges JSON enthält.  
  
-   [JSON_VALUE](#VALUE) extrahiert einen skalaren Wert aus einer JSON-Zeichenfolge.  
  
-   [JSON_QUERY](#QUERY) extrahiert ein Objekt oder ein Array aus einer JSON-Zeichenfolge.  
  
-   [JSON_MODIFY](#MODIFY) aktualisiert den Wert einer Eigenschaft in einer JSON-Zeichenfolge und gibt die aktualisierte JSON-Zeichenfolge zurück.  
 
## <a name="json-text-for-the-examples-on-this-page"></a>JSON-Text für die Beispiele auf dieser Seite

In den Beispielen auf dieser Seite wird der JSON-Text verwendet, der dem im folgenden Beispiel gezeigten Inhalt ähnelt:

```json
{
  "id": "WakefieldFamily",
  "parents": [
      { "familyName": "Wakefield", "givenName": "Robin" },
      { "familyName": "Miller", "givenName": "Ben" }
  ],
  "children": [
      {
        "familyName": "Merriam",
        "givenName": "Jesse",
        "gender": "female",
        "grade": 1,
        "pets": [
            { "givenName": "Goofy" },
            { "givenName": "Shadow" }
        ]
      },
      { 
        "familyName": "Miller",
         "givenName": "Lisa",
         "gender": "female",
         "grade": 8 }
  ],
  "address": { "state": "NY", "county": "Manhattan", "city": "NY" },
  "creationDate": 1431620462,
  "isRegistered": false
}
```

Dieses JSON-Dokument, das geschachtelte komplexe Elemente enthält, wird in der folgenden Beispieltabelle gespeichert:

```sql
CREATE TABLE Families (
   id int identity constraint PK_JSON_ID primary key,
   doc nvarchar(max)
)
``` 

##  <a name="ISJSON"></a> Überprüfen von JSON-Text mithilfe der ISJSON-Funktion  
 Die **ISJSON**-Funktion testet, ob eine Zeichenfolge gültiges JSON enthält.  
  
Im folgenden Beispiel werden die Spalten zurückgegeben, in denen die JSON-Spalte einen gültigen JSON-Text enthält. Beachten Sie, dass Sie ohne explizite JSON-Beschränkung jeden beliebigen Text in der Spalte NVARCHAR eingeben können:  
  
```sql  
SELECT *
FROM Families
WHERE ISJSON(doc) > 0 
```  

Weitere Informationen finden Sie unter [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md).  
  
##  <a name="VALUE"></a> Extrahieren eines Wertes aus JSON-Text mithilfe der JSON_VALUE-Funktion  
Die **JSON_VALUE** -Funktion extrahiert einen skalaren Wert aus einer JSON-Zeichenfolge. Die folgende Abfrage gibt die Dokumente zurück, in denen das JSON-Feld `id` mit dem Wert `AndersenFamily` übereinstimmt, sortiert nach den JSON-Feldern `city` und `state`:

```sql  
SELECT JSON_VALUE(f.doc, '$.id')  AS Name, 
       JSON_VALUE(f.doc, '$.address.city') AS City,
       JSON_VALUE(f.doc, '$.address.county') AS County
FROM Families f 
WHERE JSON_VALUE(f.doc, '$.id') = N'AndersenFamily'
ORDER BY JSON_VALUE(f.doc, '$.address.city') DESC, JSON_VALUE(f.doc, '$.address.state') ASC
```  

Die Ergebnisse dieser Abfrage sind in der folgenden Tabelle aufgeführt:

| Name | City | County |
| --- | --- | --- |
| AndersenFamily | NY | Manhattan |

Weitere Informationen finden Sie unter [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md).  
  
##  <a name="QUERY"></a> Extrahieren eines Objekts oder eines Arrays aus JSON-Text mithilfe der JSON_QUERY-Funktion  

Die **JSON_QUERY**-Funktion extrahiert ein Objekt oder ein Array aus einer JSON-Zeichenfolge. Im folgenden Beispiel wird gezeigt, wie ein JSON-Fragment in den Abfrageergebnissen zurückgegeben wird.  
  
```sql
SELECT JSON_QUERY(f.doc, '$.address') AS Address,
       JSON_QUERY(f.doc, '$.parents') AS Parents,
       JSON_QUERY(f.doc, '$.parents[0]') AS Parent0
FROM Families f 
WHERE JSON_VALUE(f.doc, '$.id') = N'AndersenFamily'
```  
Die Ergebnisse dieser Abfrage sind in der folgenden Tabelle aufgeführt:

| Adresse | Übergeordnete Elemente (Parents) | Übergeordnetes Element 0 (Parent0) |
| --- | --- | --- |
| { "state": "NY", "county": "Manhattan", "city": "NY" } | [{ "familyName": "Wakefield", "givenName": "Robin" }, {"familyName": "Miller", "givenName": "Ben" } ]| { "familyName": "Wakefield", "givenName": "Robin" } |

Weitere Informationen finden Sie unter [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  

## <a name="parse-nested-json-collections"></a>Analysieren geschachtelter JSON-Sammlungen

Mit der `OPENJSON`-Funktion können Sie das JSON-Subarray in das Rowset umwandeln und dann mit dem übergeordneten Element verknüpfen. Als Beispiel können Sie alle Familiendokumente zurückgeben und sie mit ihren `children`-Objekten „verknüpfen“, die als inneres JSON-Array gespeichert sind:

```sql
SELECT JSON_VALUE(f.doc, '$.id')  AS Name, 
       JSON_VALUE(f.doc, '$.address.city') AS City,
       c.givenName, c.grade
FROM Families f
        CROSS APPLY OPENJSON(f.doc, '$.children')
            WITH(grade int, givenName nvarchar(100))  c
```

Die Ergebnisse dieser Abfrage sind in der folgenden Tabelle aufgeführt:

| Name | City | givenName | grade |
| --- | --- | --- | --- |
| AndersenFamily | NY | Jesse | 1 |
| AndersenFamily | NY | Lisa | 8 |

Das Ergebnis sind zwei Zeilen, da eine übergeordnete Zeile mit zwei untergeordneten Zeilen verbunden ist, die durch das Analysieren von zwei Elementen des untergeordneten Subarrays erzeugt werden. Die `OPENJSON`-Funktion analysiert `children`-Fragmente aus der Spalte `doc` und gibt `grade` und `givenName` von jedem Element als Zeilen zurück. Dieses Rowset kann mit dem übergeordneten Dokument verknüpft werden.
 
## <a name="query-nested-hierarchical-json-sub-arrays"></a>Abfragen geschachtelter hierarchischer JSON-Subarrays

Sie können mehrere `CROSS APPLY OPENJSON`-Aufrufe anwenden, um geschachtelte JSON-Strukturen abzufragen. Das in diesem Beispiel verwendete JSON-Dokument verfügt über ein geschachteltes Array namens `children`, bei dem jedes untergeordnete Element ein geschachteltes Array von `pets` aufweist. Mit der folgenden Abfrage werden die untergeordneten Elemente aus den einzelnen Dokumenten analysiert, jedes Arrayobjekt als Zeile zurückgegeben und dann das `pets`-Array analysiert:

```sql
SELECT  familyName,
    c.givenName AS childGivenName,
    c.firstName AS childFirstName,
    p.givenName AS petName 
FROM Families f 
    CROSS APPLY OPENJSON(f.doc) 
        WITH (familyName nvarchar(100), children nvarchar(max) AS JSON)
        CROSS APPLY OPENJSON(children) 
        WITH (givenName nvarchar(100), firstName nvarchar(100), pets nvarchar(max) AS JSON) as c
            OUTER APPLY OPENJSON (pets)
            WITH (givenName nvarchar(100))  as p
```

Der erste `OPENJSON`-Befehl gibt ein Fragment des `children`-Arrays mithilfe der AS JSON-Klausel zurück. Dieses Arrayfragment wird der zweiten `OPENJSON`-Funktion bereitgestellt, die `givenName` zurückgibt, `firstName` jedes untergeordneten Elements, und das Arrays von `pets`. Das Array von `pets` wird der dritten `OPENJSON`-Funktion bereitgestellt, die das `givenName`-Element des Haustiers zurückgibt.
Die Ergebnisse dieser Abfrage sind in der folgenden Tabelle aufgeführt:

| familyName | childGivenName | childFirstName | petName |
| --- | --- | --- | --- |
| AndersenFamily | Jesse | Merriam | Goofy |
| AndersenFamily | Jesse | Merriam | Shadow |
| AndersenFamily | Lisa | Miller| `NULL` |

Das Stammdokument wird mit zwei `children`-Zeilen verknüpft, die beim ersten `OPENJSON(children)`-Aufruf von zwei Zeilen (oder Tupeln) zurückgegeben werden. Anschließend wird jede Zeile mit den neuen Zeilen verknüpft, die von `OPENJSON(pets)` mithilfe des `OUTER APPLY`-Operators generiert werden. Weil Jesse zwei Haustiere hat, ist `(AndersenFamily, Jesse, Merriam)` mit zwei Zeilen verknüpft, die für Goofy und Shadow generiert werden. Lisa hat keine Haustiere, sodass für dieses Tupel keine Zeilen von `OPENJSON(pets)` zurückgegeben werden. Da jedoch `OUTER APPLY` verwendet wird, wird `NULL` in der Spalte zurückgegeben. Wenn `CROSS APPLY` anstelle von `OUTER APPLY` eingesetzt wird, wird Lisa nicht im Ergebnis zurückgegeben, da keine Zeilen für Haustiere vorhanden sind, die mit diesem Tupel verknüpft werden könnten.

##  <a name="JSONCompare"></a> Vergleichen von JSON_VALUE und JSON_QUERY  
Der Hauptunterschied zwischen **JSON_VALUE** und **JSON_QUERY** besteht darin, dass **JSON_VALUE** einen skalaren Wert, wogegen **JSON_QUERY** ein Objekt oder Array zurückgibt.  
  
Betrachten Sie das folgende Beispiel eines JSON-Texts.  
  
```json  
{
    "a": "[1,2]",
    "b": [1, 2],
    "c": "hi"
}  
```  
  
In diesem Beispiel-JSON-Text sind die Datenelemente „a“ und „c“ Zeichenfolgenwerte, während Datenelement „b“ ein Array ist. **JSON_VALUE** und **JSON_QUERY** geben die folgenden Ergebnisse zurück:  
  
|`Path`|**JSON_VALUE** gibt zurück|**JSON_QUERY** gibt zurück|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL oder Fehler|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL oder Fehler|  
|**$.b**|NULL oder Fehler|[1,2]|  
|**$.b[0]**|1|NULL oder Fehler|  
|**$.c**|hi|NULL oder Fehler|  
  
## <a name="test-json_value-and-json_query-with-the-adventureworks-sample-database"></a>Testen von JSON_VALUE und JSON_QUERY mit der AdventureWorks-Beispieldatenbank  
Testen Sie die integrierten Funktionen, die in diesem Thema beschrieben werden, indem Sie die folgenden Beispiele mit der AdventureWorks-Beispieldatenbank ausführen. Informationen zum Herunterladen von AdventureWorks und Informationen zum Hinzufügen von JSON-Daten für Testzwecke durch Ausführen eines Skripts finden Sie unter [Test drive built-in JSON support (Testen des in die JSON-Unterstützung integrierten Laufwerks)](json-data-sql-server.md#test-drive-built-in-json-support-with-the-adventureworks-sample-database).
  
Im folgenden Beispiel enthält die `Info`-Spalte in der Tabelle `SalesOrder_json` den JSON-Text.  
  
### <a name="example-1---return-both-standard-columns-and-json-data"></a>Beispiel 1 – Gib sowohl Standardspalten als auch JSON-Daten zurück  
Die folgende Abfrage gibt sowohl die relationalen Standardspalten sowie Werte aus einer JSON-Spalte zurück.  
  
```sql  
SELECT SalesOrderNumber, OrderDate, Status, ShipDate, Status, AccountNumber, TotalDue,
 JSON_QUERY(Info,'$.ShippingInfo') ShippingInfo,
 JSON_QUERY(Info,'$.BillingInfo') BillingInfo,
 JSON_VALUE(Info,'$.SalesPerson.Name') SalesPerson,
 JSON_VALUE(Info,'$.ShippingInfo.City') City,
 JSON_VALUE(Info,'$.Customer.Name') Customer,
 JSON_QUERY(OrderItems,'$') OrderItems
FROM Sales.SalesOrder_json
WHERE ISJSON(Info) > 0
```  
  
### <a name="example-2--aggregate-and-filter-json-values"></a>Beispiel 2 – Aggregiere und filtere JSON-Werte  
Die folgende Abfrage aggregiert Teilergebnisse nach Kundennamen (im JSON-Format gespeichert), und Status (gespeichert in einer normalen Spalte). Sie filtert dann die Ergebnisse nach Stadt (im JSON-Format gespeichert) und Bestelldatum (gespeichert in einer normalen Spalte).  
  
```sql  
DECLARE @territoryid INT;
DECLARE @city NVARCHAR(32);

SET @territoryid=3;

SET @city=N'Seattle';

SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total
FROM Sales.SalesOrder_json
WHERE TerritoryID=@territoryid
 AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city
 AND OrderDate > '1/1/2015'
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status
HAVING SUM(SubTotal)>1000
```  
  
##  <a name="MODIFY"></a> Aktualisieren von Eigenschaftswerten in JSON-Text mithilfe der JSON_MODIFY-Funktion  
Die **JSON_MODIFY**-Funktion aktualisiert den Wert einer Eigenschaft in einer JSON-Zeichenfolge, und gibt die aktualisierte JSON-Zeichenfolge zurück.  
  
Im folgenden Beispiel wird der Wert einer JSON-Eigenschaft in einer Variable aktualisiert, die JSON enthält.  
  
```sql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')    
```  
  
 Weitere Informationen finden Sie unter [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md).  
  
## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Weitere Informationen zu JSON in SQL Server und Azure SQL-Datenbank  
  
### <a name="microsoft-videos"></a>Microsoft-Videos

Eine visuelle Einführung in die JSON-Unterstützung, die in SQL Server und Azure SQL-Datenbank integriert ist, finden Sie in den folgenden Videos:

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>Weitere Informationen  
 [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)   
 [JSON Path Expressions &#40;SQL Server&#41; (JSON-Pfadausdrücke [SQL Server])](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  
