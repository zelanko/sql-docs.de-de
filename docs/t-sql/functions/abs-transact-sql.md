---
title: ABS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ABS_TSQL
- ABS
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], positive
- values [SQL Server], absolute
- ABS function
- absolute positive value
ms.assetid: e2ea7a6d-3e2f-472c-afbc-437d3b835c03
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0bf5385adf8be483b569b7fc2f3213b73ba284b3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948221"
---
# <a name="abs-transact-sql"></a>ABS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Eine mathematische Funktion, die den absoluten (positiven) Wert des angegebenen numerischen Ausdrucks zurückgibt. (`ABS` ändert negative Werte in positive Werte. `ABS` wirkt sich nicht auf Nullwerte oder positive Werte aus.)
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
ABS ( numeric_expression )  
```  
  
## <a name="arguments"></a>Argumente  
*numeric_expression*  
Ein Ausdruck der genauen numerischen oder ungefähren numerischen Datentypkategorie.
  
## <a name="return-types"></a>Rückgabetypen  
Gibt denselben Typ wie *Numerischer Ausdruck*zurück.
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel werden die Ergebnisse dargestellt, die zurückgegeben werden, wenn die `ABS`-Funktion auf drei verschiedene Zahlen angewendet wird.
  
```sql
SELECT ABS(-1.0), ABS(0.0), ABS(1.0);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---- ---- ----  
1.0  .0   1.0  
```  
  
Die `ABS`-Funktion kann einen Überlauffehler zur Folge haben, wenn der absolute Wert einer Zahl größer ist als die größte Zahl, die von dem angegebenen Datentyp dargestellt werden kann. Beispielsweise hat der Datentyp `int` einen Wertebereich von `-2,147,483,648` bis `2,147,483,647`. Durch das Berechnen des absoluten Werts für die ganze Zahl mit Vorzeichen, `-2,147,483,648`, tritt ein Überlauffehler auf, da der absolute Wert größer ist als der positive Bereich für den `int`-Datentyp.
  
```sql
DECLARE @i int;  
SET @i = -2147483648;  
SELECT ABS(@i);  
GO  
```  
  
Gibt die folgende Fehlermeldung zurück:
  
"Meldung 8115, Ebene 16, Status 2, Zeile 3"
  
"Arithmetischer Überlauffehler beim Konvertieren des Ausdrucks in den Datentyp int."

  
## <a name="see-also"></a>Siehe auch
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Mathematische Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
[Integrierte Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)
  
  

