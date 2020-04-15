---
title: Numerische Funktionen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], numeric functions
- numeric functions [ODBC]
ms.assetid: 4fa548dc-e8b0-4179-92ff-81d6a79d10c3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 03da5b6644e0f7df3dc4e5e16a211cb503023bad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299870"
---
# <a name="numeric-functions"></a>Numerische Funktionen
In der folgenden Tabelle werden numerische Funktionen beschrieben, die im ODBC-Skalarfunktionssatz enthalten sind. Durch Aufrufen von **SQLGetInfo** mit einem *Informationstyp* von SQL_NUMERIC_FUNCTIONS kann eine Anwendung bestimmen, welche numerischen Funktionen von einem Treiber unterstützt werden.  
  
 Alle numerischen Funktionen geben Werte des Datentyps SQL_FLOAT mit Ausnahme von ABS, ROUND, TRUNCATE, SIGN, FLOOR und CEILING zurück, die Werte desselben Datentyps wie die Eingabeparameter zurückgeben.  
  
 Argumente, die als *numeric_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *numerisches Litera*l sein, wobei der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL oder SQL_DOUBLE dargestellt werden könnte.  
  
 Argumente, die als *float_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *numerisches Literal*sein, bei dem der zugrunde liegende Datentyp als SQL_FLOAT dargestellt werden kann.  
  
 Argumente, die als *integer_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *numerisches Literal*sein, wobei der zugrunde liegende Datentyp als SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER oder SQL_BIGINT dargestellt werden kann.  
  
 Die CURRENT_DATE-, CURRENT_TIME- und CURRENT_TIMESTAMP Skalarfunktionen wurden in ODBC 3.0 hinzugefügt, um sql-92 auszurichten.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|**ABS(** _numeric_exp_ **)** (ODBC 1.0)|Gibt den absoluten Wert von *numeric_exp zurück.*|  
|**ACOS(** _float_exp_ **)** (ODBC 1.0)|Gibt den Arccosin *von float_exp* als Winkel zurück, ausgedrückt in Bogenmaß.|  
|**ASIN(** _float_exp_ **)** (ODBC 1.0)|Gibt den Bogensinus von *float_exp* als Winkel zurück, ausgedrückt in Bogenmaß.|  
|**ATAN(** _float_exp_ **)** (ODBC 1.0)|Gibt die Bogentangente von *float_exp* als Winkel zurück, ausgedrückt in Bogenmaß.|  
|**ATAN2(** _float_exp1_, _float_exp2_**)** (ODBC 2.0)|Gibt die Bogentangente der *x-* und *y-Koordinaten* zurück, die durch *float_exp1* bzw. *float_exp2*als Winkel angegeben werden, ausgedrückt in Bogenmaß.|  
|**CEILING(** _numeric_exp_ **)** (ODBC 1.0)|Gibt die kleinste ganze Zahl größer oder gleich *numeric_exp*zurück. Der Rückgabewert hat denselben Datentyp wie der Eingabeparameter.|  
|**COS(** _float_exp_ **)** (ODBC 1.0)|Gibt den Kosinus von *float_exp zurück,* wobei *float_exp* ein Winkel ist, der in Bogenmaß ausgedrückt wird.|  
|**COT(** _float_exp_ **)** (ODBC 1.0)|Gibt den Kotangens von *float_exp zurück,* wobei *float_exp* ein Winkel ist, der in Bogenmaß enthinen wird.|  
|**DEGREES(** _numeric_exp_ **)** (ODBC 2.0)|Gibt die Anzahl der Grad zurück, die aus *numeric_exp* Bogenmaß en konvertiert wurden.|  
|**EXP(** _float_exp_ **)** (ODBC 1.0)|Gibt den Exponentialwert *von float_exp*zurück.|  
|**FLOOR(** _numeric_exp_ **)** (ODBC 1.0)|Gibt die größte ganze Zahl kleiner oder gleich *numeric_exp*zurück. Der Rückgabewert hat denselben Datentyp wie der Eingabeparameter.|  
|**LOG(** _float_exp_ **)** (ODBC 1.0)|Gibt den natürlichen Logarithmus von *float_exp zurück.*|  
|**LOG10(** _float_exp_ **)** (ODBC 2.0)|Gibt den Basis-10-Logarithmus von *float_exp zurück.*|  
|**MOD(** _integer_exp1_, _integer_exp2_**)** (ODBC 1.0)|Gibt den Rest (Modul) von *integer_exp1* dividiert durch *integer_exp2*zurück.|  
|**PI( )** (ODBC 1.0)|Gibt den konstanten Wert von pi als Gleitkommawert zurück.|  
|**POWER(** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|Gibt den Wert von *numeric_exp* an die Stärke *von integer_exp*zurück.|  
|**RADIANS(** _numeric_exp_ **)** (ODBC 2.0)|Gibt die Anzahl der Bogenmaßer zurück, die von *numeric_exp* Grad konvertiert wurden.|  
|**RAND(**[*integer_exp*]**)** (ODBC 1.0)|Gibt einen zufälligen Gleitkommawert zurück, der *integer_exp* als optionalen Ausgangswert verwendet.|  
|**ROUND(** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|Gibt *numeric_exp* gerundet auf *integer_exp* Stellen rechts vom Dezimaltrennzeichen zurück. Wenn *integer_exp* negativ ist, wird *numeric_exp* auf &#124;*integer_exp*&#124; Stellen links vom Dezimaltrennzeichen gerundet.|  
|**SIGN(** _numeric_exp_ **)** (ODBC 1.0)|Gibt einen Indikator für das Zeichen von *numeric_exp zurück.* Wenn *numeric_exp* kleiner als Null ist, wird -1 zurückgegeben. Wenn *numeric_exp* gleich Null ist, wird 0 zurückgegeben. Wenn *numeric_exp* größer als Null ist, wird 1 zurückgegeben.|  
|**SIN(** _float_exp_ **)** (ODBC 1.0)|Gibt den Sinus von *float_exp*zurück, wobei *float_exp* ein Winkel ist, der in Bogenmaß enthinen wird.|  
|**SQRT(** _float_exp_ **)** (ODBC 1.0)|Gibt die Quadratwurzel von *float_exp*zurück.|  
|**TAN(** _float_exp_ **)** (ODBC 1.0)|Gibt die Tangente von *float_exp zurück,* wobei *float_exp* ein Winkel ist, der in Bogenmaß ausgedrückt wird.|  
|**TRUNCATE(** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|Gibt *numeric_exp* auf *integer_exp* Stellen rechts vom Dezimaltrennzeichen abgeschnitten. Wenn *integer_exp* negativ ist, wird *numeric_exp* abgeschnitten, um *integer_exp&#124;* Stellen links vom Dezimaltrennzeichen zu &#124;.|
