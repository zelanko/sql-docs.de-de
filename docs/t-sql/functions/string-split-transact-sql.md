---
title: STRING_SPLIT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STRING_SPLIT
- STRING_SPLIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_SPLIT function
ms.assetid: 3273dbf3-0b4f-41e1-b97e-b4f67ad370b9
author: MikeRayMSFT
ms.author: mikeray
monikerRange: = azuresqldb-current||=azure-sqldw-latest||>= sql-server-2016 || >= sql-server-linux-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 20580d1c746a678771ff3be0e67bab72e2b72be8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "77179271"
---
# <a name="string_split-transact-sql"></a>STRING_SPLIT (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md.md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Eine Tabellenwertfunktion, die eine Zeichenfolge basierend auf einem angegebenen Trennzeichen in Zeilen mit Teilzeichenfolgen unterteilt.

#### <a name="compatibility-level-130"></a>Kompatibilitätsgrad 130

Für STRING_SPLIT ist mindestens der Kompatibilitätsgrad 130 erforderlich. Bei einem Grad unter 130 kann SQL Server die STRING_SPLIT-Funktion nicht finden.

Unter [Anzeigen oder Ändern des Kompatibilitätsgrads einer Datenbank](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) finden Sie Informationen zum Ändern des Datenbank-Kompatibilitätsgrads.

![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  

```
STRING_SPLIT ( string , separator )  
```

## <a name="arguments"></a>Argumente

 *string*  
 Ist ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines beliebigen Zeichentyps (z.B. **nvarchar**, **varchar**, **nchar** oder **char**).  
  
 *Trennzeichen*  
 Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) mit einem einzelnen Zeichen jedes beliebigen Zeichentyps (z.B. **nvarchar(1)** , **varchar(1)** , **nchar(1)** oder **char(1)** ), der als Trennzeichen für verkettete Teilzeichenfolgen verwendet wird.  
  
## <a name="return-types"></a>Rückgabetypen  

Gibt eine einspaltige Tabelle zurück, deren Zeilen die Teilzeichenfolgen sind. Der Name der Spalte ist **value**. Gibt **nvarchar** zurück, wenn eines der Eingabeargumente entweder **nvarchar** oder **nchar** ist, andernfalls wird **varchar** zurückgegeben. Die Länge des Rückgabetyps unterscheidet sich nicht von der Länge des Zeichenfolgenarguments.  
  
## <a name="remarks"></a>Bemerkungen  

**STRING_SPLIT** gibt eine Zeichenfolge mit getrennten Teilzeichenfolgen und ein Zeichen ein, das als Trennzeichen oder Trennlinie verwendet werden kann. STRING_SPLIT gibt eine einspaltige Tabelle aus, deren Zeilen die Teilzeichenfolgen enthalten. Der Name der Ausgabespalte ist **value**.

Die Ausgabezeilen können in beliebiger Reihenfolge sein. Die Reihenfolge ist _nicht_ stimmt nicht garantiert mit der Reihenfolge der Teilzeichenfolgen in der Eingabezeichenfolge überein. Sie können die endgültige Sortierreihenfolge überschreiben, indem Sie in der SELECT-Anweisung (`ORDER BY value`) eine ORDER BY-Klausel verwenden.

0x0000 (**char(0)** ) ist ein nicht definiertes Zeichen in Windows-Sortierungen und kann nicht in SPRING_SPLIT enthalten sein.

Leere Teilzeichenfolgen der Länge null sind vorhanden, wenn die Eingabezeichenfolge zwei oder mehr aufeinanderfolgende Vorkommen des Trennzeichens enthält. Leere Teilzeichenfolgen werden genauso behandelt wie normale Teilzeichenfolgen. Sie können alle Zeilen, die die leere Teilzeichenfolge enthalten, mit der WHERE-Klausel (`WHERE value <> ''`) herausfiltern. Wenn die Eingabezeichenfolge NULL ist, gibt die Tabellenwertfunktion STRING_SPLIT eine leere Tabelle zurück.  

Beispielsweise wird in der folgenden SELECT-Anweisung das Leerzeichen als Trennzeichen verwendet:

```sql
SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');
```

Bei einer praktischen Ausführung hat die vorstehende SELECT-Anweisung die folgende Ergebnistabelle zurückgegeben:  
  
|value|  
| :-- |  
|Lorem|  
|ipsum|  
|dolor|  
|sit|  
|amet.|  
| &nbsp; |

## <a name="examples"></a>Beispiele  
  
### <a name="a-split-comma-separated-value-string"></a>A. Teilen einer Zeichenfolge mit durch Trennzeichen getrennten Werten (CSV)

Analysieren einer durch Komma getrennten Liste von Werten und Zurückgeben aller nicht leeren Token:  

```sql
DECLARE @tags NVARCHAR(400) = 'clothing,road,,touring,bike'  
  
SELECT value  
FROM STRING_SPLIT(@tags, ',')  
WHERE RTRIM(value) <> '';
```

STRING_SPLIT gibt eine leere Zeichenfolge zurück, wenn zwischen dem Trennzeichen nichts vorhanden ist. Die Bedingung RTRIM(value) <> '' entfernt leere Token.  
  
### <a name="b-split-comma-separated-value-string-in-a-column"></a>B. Teilen einer Zeichenfolge mit durch Trennzeichen getrennten Werten in einer Spalte

Die Produkttabelle verfügt über eine Spalte mit einer durch Komma getrennte Liste von Tags, wie in diesem Beispiel dargestellt wird:  
  
|ProductId|Name|`Tags`|  
|---------------|----------|----------|  
|1|Full-Finger Gloves|clothing,road,touring,bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike,mountain|  
  
Die folgende Abfrage wandelt jede Tagliste um und verknüpft sie mit der ursprünglichen Zeile:  

```sql  
SELECT ProductId, Name, value  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',');  
```

 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|ProductId|Name|value|  
|---------------|----------|-----------|  
|1|Full-Finger Gloves|clothing|  
|1|Full-Finger Gloves|Straße|  
|1|Full-Finger Gloves|touring|  
|1|Full-Finger Gloves|bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike|  
|3|HL Mountain Frame|mountain|  

  >[!NOTE]
  > Die Reihenfolge der Ausgabe kann abweichen, da diese _nicht_ zwangsläufig mit der Reihenfolge der Teilzeichenfolgen in der Eingabezeichenfolge übereinstimmt.
  
### <a name="c-aggregation-by-values"></a>C. Aggregation nach Werten

Benutzer müssen einen Bericht erstellen, der die Anzahl der Produkte pro Tag anzeigt, die nach der Anzahl der Produkte geordnet ist, und sie dürfen nur die Tags mit mehr als zwei Produkten filtern.  

```sql  
SELECT value as tag, COUNT(*) AS [Number of articles]  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',')  
GROUP BY value  
HAVING COUNT(*) > 2  
ORDER BY COUNT(*) DESC;  
```

### <a name="d-search-by-tag-value"></a>D: Nach Tagwert suchen

Entwickler müssen Abfragen erstellen, die Artikel nach Schlüsselwörtern finden. Sie können folgende Abfragen verwenden:  
  
Um Produkte mit einem einzelnen Tag zu finden (clothing):  

```sql
SELECT ProductId, Name, Tags  
FROM Product  
WHERE 'clothing' IN (SELECT value FROM STRING_SPLIT(Tags, ','));  
```

Produkte mit zwei angegebenen Tags finden (clothing und road):  

```sql  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE EXISTS (SELECT *  
    FROM STRING_SPLIT(Tags, ',')  
    WHERE value IN ('clothing', 'road'));  
```

### <a name="e-find-rows-by-list-of-values"></a>E. Suchen nach Zeilen nach einer Liste von Werten

Entwickler müssen eine Abfrage erstellen, die Artikel nach einer Liste von IDs sucht. Sie können die folgende Abfrage verwenden:  

```sql  
SELECT ProductId, Name, Tags  
FROM Product  
JOIN STRING_SPLIT('1,2,3',',')
    ON value = ProductId;  
```  

Die vorhergehende Verwendung von STRING_SPLIT ist ein Ersatz für ein gängiges Antimuster. Ein solches Antimuster kann die Erstellung einer dynamischen SQL-Zeichenfolge auf der Anwendungsschicht oder in Transact-SQL mit einbeziehen. Ein Antimuster kann auch mit dem LIKE-Operator erreicht werden. Siehe das folgende Beispiel einer SELECT-Anweisung:

```sql  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE ',1,2,3,' LIKE '%,' + CAST(ProductId AS VARCHAR(20)) + ',%';  
```

## <a name="see-also"></a>Weitere Informationen

[LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)<br />
[LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)<br />
[RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)<br />
[RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)<br />
[SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)<br />
[TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)<br />
[String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/string-functions-transact-sql.md)
