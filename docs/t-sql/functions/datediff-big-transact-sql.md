---
title: DATEDIFF_BIG (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATEDIFF_BIG
- DATEDIFF_BIG_TSQL
helpviewer_keywords:
- DATEDIFF_BIG function [SQL Server]
- dates [SQL Server]. functions
- date and time [SQL Server], DATEDIFF_BIG
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: 19ac1693-3cfa-400d-bf83-20a9cb46599a
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 26ea16e8e80fd2b8febf8a95c848490b41f0408a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744099"
---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt die Anzahl (große ganze Zahl mit Vorzeichen) der angegebenen *datepart*-Begrenzungen zurück, die zwischen den angegebenen Werten für *startdate* und *enddate* überschritten wurden.
  
Unter [Datums- und Uhrzeitdatentypen und zugehörige Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md) finden Sie eine Übersicht über alle [!INCLUDE[tsql](../../includes/tsql-md.md)] Datums- und Uhrzeitdatentypen und zugehörige Funktionen.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Argumente  
*datepart*  
Der Teil von *startdate* und *enddate*, der den Typ der überschrittenen Begrenzung angibt. `DATEDIFF_BIG` akzeptiert keine benutzerdefinierten Variablenentsprechungen. In der folgenden Tabelle werden alle gültigen *datepart*-Argumente aufgeführt.

> [!NOTE]
> `DATEDIFF_BIG` akzeptiert keine benutzerdefinierten Variablenentsprechungen für die *datepart*-Argumente.
  
|*datepart*|Abkürzungen|  
|---|---|
|**year**|**yy, yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy, y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**hh**|  
|**minute**|**mi, n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
Ein Ausdruck, der in einen der folgenden Werte aufgelöst werden kann:

+ **Datum**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **Uhrzeit**

Bei *date* akzeptiert `DATEDIFF_BIG` einen Spaltenausdruck, einen Ausdruck, ein Zeichenfolgenliteral oder eine benutzerdefinierte Variable. Ein Zeichenfolgenliteralwert muss in ein **datetime**-Argument aufgelöst werden. Um Mehrdeutigkeiten zu vermeiden, sollten Sie vierstellige Jahreszahlen verwenden. `DATEDIFF_BIG` subtrahiert *enddate* von *startdate*. Um Mehrdeutigkeiten zu vermeiden, sollten Sie vierstellige Jahreszahlen verwenden. Unter [Konfigurieren der Serverkonfigurationsoption „Umstellungsjahr für Angaben mit zwei Ziffern“](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md) finden Sie weitere Informationen zu zweistelligen Jahreszahlen.
  
*enddate*  
Weitere Informationen finden Sie unter *startdate*.
  
## <a name="return-type"></a>Rückgabetyp  

Signierter **bigint**-Wert  
  
## <a name="return-value"></a>Rückgabewert  
Gibt die Anzahl (große ganze Zahl mit Vorzeichen) der angegebenen „datepart“-Begrenzungen zurück, die zwischen den angegebenen Werten für „startdate“ und „enddate“ überschritten wurden.
-   Alle spezifischen *datepart*-Werte und die Abkürzungen für diese *datepart*-Werte geben den gleichen Wert zurück.  
  
Bei einem Rückgabewert, der sich außerhalb des gültigen Bereichs für **bigint** (-9,223,372,036,854,775,808 bis 9,223,372,036,854,775,807) befindet, gibt `DATEDIFF_BIG` einen Fehler zurück. Der maximale Unterschied zwischen *startdate* und *enddate* beträgt für **millisecond** 24 Tage, 20 Stunden, 31 Minuten und 23,647 Sekunden. Für **second** beträgt der maximale Unterschied 68 Jahre.
  
Wenn *startdate* und *enddate* jeweils nur ein Uhrzeitwert zugewiesen ist und *datepart* kein Zeit-*datepart* ist, gibt `DATEDIFF_BIG` 0 (null) zurück.
  
Beim Berechnen des Rückgabewerts verwendet `DATEDIFF_BIG` keine Komponente von *startdate* oder *enddate* für den Zeitzonenoffset.
  
Bei einem **smalldatetime**-Wert, der für *startdate* oder *enddate* verwendet wird, legt `DATEDIFF_BIG` die Sekunden und Millisekunden im Rückgabewert immer auf 0 (null) fest, da [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) nur auf die Minute genaue Werte enthält.
  
Wenn der Variablen eines Datumsdatentyps nur ein Uhrzeitwert zugewiesen ist, legt `DATEDIFF_BIG` den Wert des fehlenden Datumsteils auf den Standardwert fest: 1900-01-01. Wenn der Variablen eines Uhrzeit- oder Datumsdatentyps nur ein Datumswert zugewiesen ist, legt `DATEDIFF_BIG` für den Wert des fehlenden Uhrzeitteils den Standardwert fest: 00:00:00. Wenn entweder *startdate* oder *enddate* nur über einen Uhrzeitteil und der andere nur über einen Datumsteil verfügt, legt `DATEDIFF_BIG` für die fehlenden Uhrzeit- und Datumstypen die Standardwerte fest.
  
Wenn *startdate* und *enddate* unterschiedliche Datumsdatentypen aufweisen und ein Datentyp mehr Uhrzeitteile oder eine höhere Genauigkeit bezüglich der Bruchteile von Sekunden aufweist als der andere Teil, legt `DATEDIFF_BIG` für die fehlenden Teile des anderen Datentyps 0 (null) fest.
  
## <a name="datepart-boundaries"></a>datepart-Begrenzungen
Die folgenden Anweisungen weisen bei *startdate* und *enddate* den gleichen Wert auf. Die Datumsangaben folgen aufeinander und unterscheiden sich in der Uhrzeit um 0,0000001 Sekunden. Der Unterschied zwischen *startdate* und *enddate* in jeder Anweisung überschreitet eine Kalender- oder Uhrzeitbegrenzung des zugehörigen *datepart*. Jede Anweisung gibt 1 zurück. Wenn *startdate* und *enddate* unterschiedliche Jahreswerte aufweisen, die Kalenderwochenwerte jedoch identisch sind, gibt `DATEDIFF_BIG` für den *datepart*-Wert **week** 0 (null) zurück.

```sql
SELECT DATEDIFF_BIG(year, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(quarter, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(month, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(dayofyear, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(day, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(week, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(hour, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(minute, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(second, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Remarks  
`DATEDIFF_BIG` kann in den Klauseln SELECT <list>, WHERE, HAVING, GROUP BY und ORDER BY verwendet werden.
  
`DATEDIFF_BIG` wandelt Zeichenfolgenliterale implizit in den **datetime2**-Typ um. Daher unterstützt `DATEDIFF_BIG` das Format YDM nicht, wenn das Datum als Zeichenfolge übergeben wird. Sie müssen die Zeichenfolge explizit in den Typ **datetime** oder **smalldatetime** umwandeln, um das YDM-Format zu verwenden.
  
Die Angabe von SET DATEFIRST hat keine Auswirkungen auf `DATEDIFF_BIG`. `DATEDIFF_BIG` verwendet immer Sonntag als ersten Wochentag, um sicherzustellen, dass die Funktion deterministisch ist.
  
## <a name="examples"></a>Beispiele 
  
### <a name="specifying-columns-for-startdate-and-enddate"></a>Angeben von Spalten für startdate und enddate  
In diesem Beispiel werden verschiedene Typen von Ausdrücken als Argumente für die Parameter *startdate* und *enddate* verwendet. Die Anzahl der Tagesbegrenzungen wird berechnet, die von den Datumsangaben in zwei Spalten in einer Tabelle überschritten wurden.
  
```sql
CREATE TABLE dbo.Duration  
    (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT DATEDIFF_BIG(day,startDate,endDate) AS 'Duration'  
FROM dbo.Duration;  
-- Returns: 1  
```  

Weitere vergleichbare Beispiele finden Sie unter [DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md).
  
## <a name="see-also"></a>Siehe auch
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md)
  
  
