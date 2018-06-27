---
title: DATETIMEOFFSETFROMPARTS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATETIMEOFFSETFROMPARTS_TSQL
- DATETIMEOFFSETFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEOFFSETFROMPARTS function
ms.assetid: 463da1f4-b4b6-45a3-9a95-ea1f99575542
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 09e705fd426963018eadae7351df1046d3d1ef0c
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2018
ms.locfileid: "35698271"
---
# <a name="datetimeoffsetfromparts-transact-sql"></a>DATETIMEOFFSETFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Diese Funktion gibt einen **datetimeoffset**-Wert für die angegebenen Argumente für Datum und Zeit zurück. Die Genauigkeit des Rückgabewerts wird vom precision-Argument angegeben, und Offsets werden von den Argumenten „hour_offset“ und „minute_offset“ bestimmt.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DATETIMEOFFSETFROMPARTS ( year, month, day, hour, minute, seconds, fractions, hour_offset, minute_offset, precision )  
```  
  
## <a name="arguments"></a>Argumente  
*year*  
Ein ganzzahliger Ausdruck, der ein Jahr angibt.
  
*month*  
Ein ganzzahliger Ausdruck, der einen Monat angibt.
  
*day*  
Ein ganzzahliger Ausdruck, der einen Tag angibt.
  
*hour*  
Ein ganzzahliger Ausdruck, der Stunden angibt.
  
*minute*  
Ein ganzzahliger Ausdruck, der Minuten angibt.
  
*Sekunden*  
Ein ganzzahliger Ausdruck, der Sekunden angibt.
  
*fractions*  
Ein ganzzahliger Ausdruck, der einen Dezimalstellenwert angibt.
  
*hour_offset*  
Ein ganzzahliger Ausdruck, der den Stundenteil des Zeitzonenoffsets angibt.
  
*minute_offset*  
Ein ganzzahliger Ausdruck, der den Minutenteil des Zeitzonenoffsets angibt.
  
*precision*  
Ein ganzzahliges Literal, das die Genauigkeit des **datetimeoffset**-Werts angibt, der von `DATETIMEOFFSETFROMPARTS` zurückgegeben wird.
  
## <a name="return-types"></a>Rückgabetypen
**datetimeoffset(** *Genauigkeit* **)**
  
## <a name="remarks"></a>Remarks  
`DATETIMEOFFSETFROMPARTS` gibt einen vollständig initialisierten **datetimeoffset**-Datentyp zurück. `DATETIMEOFFSETFROMPARTS` verwendet die Offsetargumente, um den Zeitzonenoffset darzustellen. Wenn die Offsetargumente ausgelassen werden, geht `DATETIMEOFFSETFROMPARTS` von einem Zeitzonenoffset von 00:00 (also kein Zeitzonenoffset) aus. Bei angegebenen Offsetargumenten erwartet `DATETIMEOFFSETFROMPARTS` Werte für beide Argumente, und beide Werte für diese Argumente müssen entweder positiv oder negativ sein. Für ein angegebenes *minute_offset*-Argument ohne angegebenen *hour_offset*-Wert löst `DATETIMEOFFSETFROMPARTS` einen Fehler aus. Wenn andere Argumente über ungültige Werte verfügen, löst `DATETIMEOFFSETFROMPARTS` einen Fehler aus. `DATETIMEOFFSETFROMPARTS` gibt NULL zurück, wenn mindestens ein erforderliches Argument den Wert NULL enthält. Wenn das *precision*-Argument jedoch einen NULL-Wert enthält, löst `DATETIMEOFFSETFROMPARTS` einen Fehler aus.
  
Das *fractions*-Argument ist vom *precision*-Argument abhängig. Wenn *precision* beispielsweise den Wert 7 aufweist, stellt jeder Bruchteil 100 Nanosekunden dar. Wenn *precision* jedoch den Wert 3 aufweist, stellt jeder Bruchteil eine Millisekunde dar. Wenn der Wert von *precision* 0 (null) ist, muss auch der Wert von *fractions* 0 (null) sein; andernfalls löst `DATETIMEOFFSETFROMPARTS` einen Fehler aus.

Diese Funktion unterstützt das Remoting zu [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Servern und höher. Sie unterstützt nicht das Remoting zu Servern mit einer Version unter [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-an-example-without-fractions-of-a-second"></a>A. Ein Beispiel ohne Sekundenbruchteile  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2010, 12, 31, 14, 23, 23, 0, 12, 0, 7 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------------------------  
2010-12-07 00:00:00.0000000 +00:00  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Beispiel mit Sekundenbruchteilen  
Dieses Beispiel zeigt die Verwendung der Parameter *fractions* und *precision*:
1.   Wenn *fractions* den Wert 5 und *precision* den Wert 1 hat, stellt der Wert von *fractions* 5/10 einer Sekunde dar.  
1.   Wenn *fractions* den Wert 50 und *precision* den Wert 2 hat, stellt der Wert von *fractions* 50/100 einer Sekunde dar.  
1.   Wenn *fractions* den Wert 500 und *precision* den Wert 3 hat, stellt der Wert von *fractions* 500/1000 einer Sekunde dar.  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 5, 12, 30, 1 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 50, 12, 30, 2 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 500, 12, 30, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------------------  
2011-08-15 14:30:00.5 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.50 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.500 +12:30  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Siehe auch
[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
[AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  


