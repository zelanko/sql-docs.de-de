---
title: Numerische Funktionen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6e744d3de177197923540fc3101c58dcbb4d3490
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990726"
---
# <a name="numeric-functions"></a>Numerische Funktionen
In der folgenden Tabelle werden numerische Funktionen beschrieben, die in der ODBC-skalarfunktionsmenge enthalten sind. Durch den Aufruf von **SQLGetInfo** mit dem *Informationstyp* SQL_NUMERIC_FUNCTIONS kann eine Anwendung bestimmen, welche numerischen Funktionen von einem Treiber unterstützt werden.  
  
 Alle numerischen Funktionen geben Werte des Datentyps zurück SQL_FLOAT mit Ausnahme von ABS, Round, TRUNCATE, Sign, Floor und Ceiling, die Werte desselben Datentyps wie die Eingabeparameter zurückgeben.  
  
 Argumente, die als *numeric_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder eine *numerische Litera*l sein, wobei der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL oder SQL_DOUBLE dargestellt werden könnte.  
  
 Argumente, die als *float_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *numerisches Literale*sein, wobei der zugrunde liegende Datentyp als SQL_FLOAT dargestellt werden kann.  
  
 Argumente, die als *integer_exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein *numerisches Literale*sein, wobei der zugrunde liegende Datentyp als SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER oder SQL_BIGINT dargestellt werden kann.  
  
 Die CURRENT_DATE-, CURRENT_TIME-und CURRENT_TIMESTAMP skalaren Funktionen wurden in ODBC 3,0 hinzugefügt, um Sie an SQL-92 auszurichten.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|**Abs (** _numeric_exp_ **)** (ODBC 1,0)|Gibt den absoluten Wert *numeric_exp*zurück.|  
|**ACOS (** _float_exp_ **)** (ODBC 1,0)|Gibt den Arkus Kosinus *float_exp* als Winkel im Bogenmaße zurück.|  
|**ASIN (** _float_exp_ **)** (ODBC 1,0)|Gibt den Arkus Sinus *float_exp* als Winkel im Bogenmaße zurück.|  
|**Atan (** _float_exp_ **)** (ODBC 1,0)|Gibt den Arkus Tangens *float_exp* als Winkel im Bogenmaße zurück.|  
|**Atan2 (** _float_exp1_, _float_exp2_**)** (ODBC 2,0)|Gibt den Arkus Tangens der *x* -und *y* -Koordinaten zurück, angegeben durch *float_exp1* und *float_exp2*bzw. als Winkel, ausgedrückt als Bogenlicht.|  
|**Ceiling (** _numeric_exp_ **)** (ODBC 1,0)|Gibt die kleinste ganze Zahl zurück, die größer oder gleich *numeric_exp*ist. Der Rückgabewert ist vom selben Datentyp wie der Eingabeparameter.|  
|**Cos (** _float_exp_ **)** (ODBC 1,0)|Gibt den Kosinus *float_exp*zurück, wobei *float_exp* ein Winkel ist, der im Bogenmaße ausgedrückt wird.|  
|**COT (** _float_exp_ **)** (ODBC 1,0)|Gibt den Kotangens von *float_exp*zurück, wobei *float_exp* ein Winkel im Bogenmaße ist.|  
|**Grad (** _numeric_exp_ **)** (ODBC 2,0)|Gibt die Anzahl der Grade zurück, die aus *numeric_exp* Bogenmaß konvertiert wurden.|  
|**Exp (** _float_exp_ **)** (ODBC 1,0)|Gibt den Exponentialwert *float_exp*zurück.|  
|**Floor (** _numeric_exp_ **)** (ODBC 1,0)|Gibt die größte ganze Zahl zurück, die kleiner oder gleich *numeric_exp*ist. Der Rückgabewert ist vom selben Datentyp wie der Eingabeparameter.|  
|**Log (** _float_exp_ **)** (ODBC 1,0)|Gibt den natürlichen Logarithmus von *float_exp*zurück.|  
|**Log10 (** _float_exp_ **)** (ODBC 2,0)|Gibt den Logarithmus zur Basis 10 von *float_exp*zurück.|  
|**Mod (** _integer_exp1_, _integer_exp2_**)** (ODBC 1,0)|Gibt den Rest (Modulus) der *integer_exp1* dividiert durch *integer_exp2*zurück.|  
|**PI ()** (ODBC 1,0)|Gibt den konstanten Wert von Pi als Gleit Komma Wert zurück.|  
|**Power (** _numeric_exp_, _integer_exp_**)** (ODBC 2,0)|Gibt den Wert von *numeric_exp* *integer_exp*zurück.|  
|**Radiane (** _numeric_exp_ **)** (ODBC 2,0)|Gibt die Anzahl der aus *numeric_exp* Grad konvertierten radiane zurück.|  
|**Rand (**[*integer_exp*]**)** (ODBC 1,0)|Gibt einen zufälligen Gleit Komma Wert zurück, indem *integer_exp* als optionaler Ausgangswert verwendet wird.|  
|**Round (** _numeric_exp_, _integer_exp_**)** (ODBC 2,0)|Gibt *numeric_exp* auf *integer_exp* Stellen rechts vom Dezimaltrennzeichen gerundet zurück. Wenn *integer_exp* negativ ist, wird *numeric_exp* auf &#124;*integer_exp*&#124; stellen auf der linken Seite des Dezimal Trennzeichens gerundet.|  
|**Sign (** _numeric_exp_ **)** (ODBC 1,0)|Gibt einen Indikator für das Vorzeichen *numeric_exp*zurück. Wenn *numeric_exp* kleiner als 0 (null) ist, wird-1 zurückgegeben. Wenn *numeric_exp* gleich 0 (null) ist, wird 0 zurückgegeben. Wenn *numeric_exp* größer als 0 (null) ist, wird 1 zurückgegeben.|  
|**Sin (** _float_exp_ **)** (ODBC 1,0)|Gibt den Sinus des *float_exp*zurück, bei dem *float_exp* ein Winkel im Bogenmaße ist.|  
|**Sqrt (** _float_exp_ **)** (ODBC 1,0)|Gibt die Quadratwurzel *float_exp*zurück.|  
|**Tan (** _float_exp_ **)** (ODBC 1,0)|Gibt den Tangens von *float_exp*zurück, wobei *float_exp* ein Winkel im Bogenmaße ist.|  
|**Truncate (** _numeric_exp_, _integer_exp_**)** (ODBC 2,0)|Gibt *numeric_exp* abgeschnitten, um an *integer_exp* Stellen rechts vom Dezimaltrennzeichen abgeschnitten. Wenn *integer_exp* negativ ist, wird *numeric_exp* abgeschnitten, um *integer_exp*&#124; Stellen links vom Dezimaltrennzeichen &#124;.|
