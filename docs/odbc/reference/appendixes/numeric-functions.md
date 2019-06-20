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
manager: craigg
ms.openlocfilehash: 47711a7e974373e9da4ac8068295029d88accaf6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181301"
---
# <a name="numeric-functions"></a>Numerische Funktionen
Die folgende Tabelle beschreibt die numerische Funktionen, die in der ODBC-Skalarfunktion Menge enthalten sind. Durch Aufrufen von **SQLGetInfo** mit einer *Informationstyp* des SQL_NUMERIC_FUNCTIONS, kann eine Anwendung bestimmen, welche numerischen Funktionen vom Treiber unterstützt werden.  
  
 Alle numerische Funktionen Rückgabewerte des Datentyps SQL_FLOAT mit Ausnahme von ABS, ROUND, TRUNCATE, anmelden, FLOOR und CEILING, die Rückgabewerte der gleichen Daten geben Sie als Eingabeparameter.  
  
 Argumente schulungsausgabe als *Numeric_exp* kann der Name einer Spalte, die das Ergebnis einer anderen Skalarfunktion sein oder ein *numerische-Litera*l, in denen der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_ dargestellt werden kann Dezimal SQL_TINYINT SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL oder SQL_DOUBLE.  
  
 Argumente schulungsausgabe als *Float_exp* kann der Name einer Spalte, die das Ergebnis einer anderen Skalarfunktion sein oder ein *numerischen Literalen*, in denen der zugrunde liegende Datentyp als SQL_FLOAT dargestellt werden können.  
  
 Argumente schulungsausgabe als *Integer_exp* kann der Name einer Spalte, die das Ergebnis einer anderen Skalarfunktion sein oder ein *numerischen Literalen*, wo der zugrunde liegende Datentyp als SQL_TINYINT, SQL_ dargestellt werden können SMALLINT, SQL_INTEGER oder SQL_BIGINT.  
  
 Die CURRENT_DATE CURRENT_TIME und CURRENT_TIMESTAMP skalaren Funktionen wurden in ODBC 3.0 an einer Verbindung mit SQL-92 hinzugefügt.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|**ABS (** _Numeric_exp_ **)** (ODBC-1.0)|Gibt den absoluten Wert des *Numeric_exp*.|  
|**ACOS (** _Float_exp_ **)** (ODBC-1.0)|Gibt den Arkuskosinus *Float_exp* als Winkel, ausgedrückt in Bogenmaß.|  
|**ASIN (** _Float_exp_ **)** (ODBC-1.0)|Gibt den Arkussinus von *Float_exp* als Winkel, ausgedrückt in Bogenmaß.|  
|**ATAN (** _Float_exp_ **)** (ODBC-1.0)|Gibt den Arkustangens der *Float_exp* als Winkel, ausgedrückt in Bogenmaß.|  
|**ATAN2(** _float_exp1_, _float_exp2_ **)**  (ODBC 2.0)|Gibt den Arkustangens der *x* und *y* , die angegebenen Koordinaten *float_exp1* und *float_exp2*jeweils als ein Winkel ausgedrückt in Bogenmaß.|  
|**CEILING(** _numeric_exp_ **)**  (ODBC 1.0)|Gibt die kleinste ganze Zahl zurück, größer als oder gleich *Numeric_exp*. Der Rückgabewert ist von den gleichen Datentyp wie der Eingabeparameter.|  
|**COS (** _Float_exp_ **)** (ODBC-1.0)|Gibt den Kosinus des *Float_exp*, wobei *Float_exp* einen Winkel im Bogenmaß (Radiant) ausgedrückt wird.|  
|**COT (** _Float_exp_ **)** (ODBC-1.0)|Gibt den Kotangens eines *Float_exp*, wobei *Float_exp* einen Winkel im Bogenmaß (Radiant) ausgedrückt wird.|  
|**Grad (** _Numeric_exp_ **)** (ODBC 2.0)|Gibt die Anzahl der aus konvertiert Grad *Numeric_exp* Bogenmaß (Radiant).|  
|**EXP (** _Float_exp_ **)** (ODBC-1.0)|Gibt den Exponentialwert des *Float_exp*.|  
|**FLOOR (** _Numeric_exp_ **)** (ODBC-1.0)|Gibt der größten ganze Zahl kleiner als oder gleich *Numeric_exp*. Der Rückgabewert ist von den gleichen Datentyp wie der Eingabeparameter.|  
|**LOG (** _Float_exp_ **)** (ODBC-1.0)|Gibt den natürlichen Logarithmus der *Float_exp*.|  
|**LOG10 (** _Float_exp_ **)** (ODBC 2.0)|Gibt die Basis-10-Logarithmus des *Float_exp*.|  
|**MOD(** _integer_exp1_, _integer_exp2_ **)**  (ODBC 1.0)|Gibt den Rest (Modulo) *integer_exp1* geteilt durch *integer_exp2*.|  
|**PI( )**  (ODBC 1.0)|Gibt den konstanten Wert von Pi als einen Gleitkommawert zurück.|  
|**POWER (** _Numeric_exp_, _Integer_exp_ **)** (ODBC 2.0)|Gibt den Wert der *Numeric_exp* mit *Integer_exp*.|  
|**RADIANS(** _numeric_exp_ **)**  (ODBC 2.0)|Gibt die Anzahl der Bogenmaß konvertiert aus *Numeric_exp* Grad.|  
|**RAND(** [*integer_exp*] **)**  (ODBC 1.0)|Gibt eine zufällige Gleitkommawert mit *Integer_exp* als optionale Startwert.|  
|**ROUND (** _Numeric_exp_, _Integer_exp_ **)** (ODBC 2.0)|Gibt *Numeric_exp* auf gerundet *Integer_exp* wird rechts neben dem Dezimaltrennzeichen an. Wenn *Integer_exp* ist negativ, *Numeric_exp* auf gerundet &#124; *Integer_exp* &#124; wird links neben dem Dezimaltrennzeichen an.|  
|**SIGN (** _Numeric_exp_ **)** (ODBC-1.0)|Gibt einen Indikator, der das Vorzeichen des *Numeric_exp*. Wenn *Numeric_exp* kleiner als NULL,-1 zurückgegeben. Wenn *Numeric_exp* gleich NULL ist, wird 0 zurückgegeben. Wenn *Numeric_exp* ist größer als 0 (null), wird 1 zurückgegeben.|  
|**SIN (** _Float_exp_ **)** (ODBC-1.0)|Gibt den Sinus des *Float_exp*, wobei *Float_exp* einen Winkel im Bogenmaß (Radiant) ausgedrückt wird.|  
|**SQRT (** _Float_exp_ **)** (ODBC-1.0)|Gibt die Quadratwurzel von *Float_exp*.|  
|**TAN (** _Float_exp_ **)** (ODBC-1.0)|Gibt den Tangens des *Float_exp*, wobei *Float_exp* einen Winkel im Bogenmaß (Radiant) ausgedrückt wird.|  
|**TRUNCATE (** _Numeric_exp_, _Integer_exp_ **)** (ODBC 2.0)|Gibt *Numeric_exp* abgeschnitten und *Integer_exp* wird rechts neben dem Dezimaltrennzeichen an. Wenn *Integer_exp* ist negativ, *Numeric_exp* auf abgeschnitten &#124; *Integer_exp* &#124; wird links neben dem Dezimaltrennzeichen an.|
