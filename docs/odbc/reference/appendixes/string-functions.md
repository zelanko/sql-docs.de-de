---
description: Zeichenfolgenfunktionen
title: Zeichen folgen Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], string functions
- string functions [ODBC]
ms.assetid: 270f669e-8aab-4db0-95a4-f2b3c69538b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 42a5301f49a033dbc6e84a5fe43d68c794a76e84
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386476"
---
# <a name="string-functions"></a>Zeichenfolgenfunktionen
In der folgenden Tabelle sind die Funktionen der Zeichen folgen Bearbeitung aufgeführt Eine Anwendung kann ermitteln, welche Zeichen folgen Funktionen von einem Treiber unterstützt werden, indem **SQLGetInfo** mit dem *Informationstyp* SQL_STRING_FUNCTIONS aufgerufen wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Argumente, die als *string_exp* bezeichnet werden, können der Name einer Spalte, eine *Zeichenfolge Literale*oder das Ergebnis einer anderen Skalarfunktion sein, wobei der zugrunde liegende Datentyp als SQL_CHAR, SQL_VARCHAR oder SQL_LONGVARCHAR dargestellt werden kann.  
  
 Argumente, die als *character_exp* bezeichnet werden, sind eine Zeichenfolge mit variabler Länge.  
  
 Argumente, die als " *Start*", " *length*" oder " *count* " bezeichnet werden, können eine *numerische Literale* oder das Ergebnis einer anderen Skalarfunktion sein, wobei der zugrunde liegende Datentyp als SQL_TINYINT, SQL_SMALLINT oder SQL_INTEGER dargestellt werden kann.  
  
 Die hier aufgeführten Zeichen folgen Funktionen sind 1-basiert. Das heißt, das erste Zeichen in der Zeichenfolge ist Zeichen 1.  
  
 Die Skalarfunktionen BIT_LENGTH, CHAR_LENGTH, CHARACTER_LENGTH, OCTET_LENGTH und Positions Zeichenfolgen wurden in ODBC 3,0 hinzugefügt, um Sie an SQL-92 auszurichten.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|**ASCII (** _string_exp_ **)**  (ODBC 1,0)|Gibt den ASCII-Codewert des äußersten linken Zeichens *string_exp* als ganze Zahl zurück.|  
|**BIT_LENGTH (** _string_exp_ **)**  (ODBC 3,0)|Gibt die Länge des Zeichenfolgenausdrucks in Bits zurück.<br /><br /> Funktioniert nicht nur für Zeichen folgen-Datentypen und konvertiert daher *string_exp* nicht implizit in eine Zeichenfolge, sondern gibt stattdessen die (interne) Größe eines beliebigen Datentyps zurück.|  
|**Char (** _Code_ **)**  (ODBC 1,0)|Gibt das Zeichen zurück, das über den durch *Code*angegebenen ASCII-Codewert verfügt. Der Wert von *Code* muss zwischen 0 und 255 liegen. Andernfalls ist der Rückgabewert Datenquellen abhängig.|  
|**CHAR_LENGTH (** _string_exp_ **)**  (ODBC 3,0)|Gibt die Länge des Zeichen folgen Ausdrucks in Zeichen zurück, wenn der Zeichen folgen Ausdruck vom Datentyp Zeichen ist. Andernfalls wird die Länge des Zeichen folgen Ausdrucks in Bytes zurückgegeben (die kleinste Ganzzahl ist nicht kleiner als die Anzahl der Bits dividiert durch 8). (Diese Funktion ist mit der CHARACTER_LENGTH-Funktion identisch.)|  
|**CHARACTER_LENGTH (** _string_exp_ **)**  (ODBC 3,0)|Gibt die Länge des Zeichen folgen Ausdrucks in Zeichen zurück, wenn der Zeichen folgen Ausdruck vom Datentyp Zeichen ist. Andernfalls wird die Länge des Zeichen folgen Ausdrucks in Bytes zurückgegeben (die kleinste Ganzzahl ist nicht kleiner als die Anzahl der Bits dividiert durch 8). (Diese Funktion ist mit der CHAR_LENGTH-Funktion identisch.)|  
|**Concat (** _string_exp1_,_string_exp2_**)**  (ODBC 1,0)|Gibt eine Zeichenfolge zurück, die das Ergebnis der Verkettung *string_exp2* mit *string_exp1*ist. Die Ergebniszeichenfolge hängt vom DBMS ab. Wenn z. b. die durch *string_exp1* dargestellte Spalte einen NULL-Wert enthielt, würde DB2 NULL zurückgeben, SQL Server jedoch die Zeichenfolge ungleich NULL zurückgeben würde.|  
|**Differenz (** _string_exp1__string_exp2_**)** (ODBC 2,0)|Gibt einen ganzzahligen Wert zurück, der die Differenz zwischen den Werten angibt, die von der SOUNDEX-Funktion für *string_exp1* und *string_exp2*zurückgegeben werden.|  
|**Insert (** _string_exp1_, *Start*, *length*, _string_exp2_**)**  (ODBC 1,0)|Gibt eine Zeichenfolge zurück, in der *Längen* Zeichen aus *string_exp1*gelöscht wurden, beginnend beim *Start*und wo *string_exp2* in string_exp eingefügt wurde *,* beginnend beim *Start*.|  
|**LCASE (** _string_exp_ **)** (ODBC 1,0)|Gibt eine Zeichenfolge zurück, die in *string_exp*gleich ist, wobei alle Großbuchstaben in Kleinbuchstaben konvertiert wurden.|  
|**Left (** _string_exp_, _count_**)** (ODBC 1,0)|Gibt die *Anzahl* der am weitesten links stehenden Zeichen *string_exp*zurück.|  
|**Länge (** _string_exp_ **)** (ODBC 1,0)|Gibt die Anzahl der Zeichen in *string_exp zurück,* wobei nachfolgende Leerzeichen ausgenommen sind.<br /><br /> **Length** akzeptiert nur Zeichen folgen. Konvertiert *string_exp* daher implizit in eine Zeichenfolge und gibt die Länge dieser Zeichenfolge zurück (nicht die interne Größe des DataType).|  
|**Suchen (** _string_exp1_, *string_exp2*[, *Start*]**)** (ODBC 1,0)|Gibt die Anfangsposition des ersten Vorkommens von *string_exp1* in *string_exp2*zurück. Die Suche nach dem ersten Vorkommen von *string_exp1* beginnt mit der ersten Zeichenposition in *string_exp2* , es sei denn, das optionale Argument, *Start*, wird angegeben. Wenn " *Start* " angegeben wird, beginnt die Suche mit der Zeichenposition, die durch den Wert von " *Start*" angegeben wird. Die erste Zeichenposition in *string_exp2* wird durch den Wert 1 angegeben. Wenn *string_exp1* in *string_exp2*nicht gefunden wird, wird der Wert 0 zurückgegeben.<br /><br /> Wenn eine Anwendung die "Skalarfunktion suchen" mit den Argumenten " *string_exp1*", " *string_exp2*" und " *Start* " aufrufen kann, gibt der Treiber SQL_FN_STR_LOCATE zurück, wenn " **SQLGetInfo** " mit der *Option* SQL_STRING_FUNCTIONS aufgerufen wird. Wenn die Anwendung die Skalarfunktion suchen nur mit den *string_exp1* -und *string_exp2* -Argumenten aufrufen kann, gibt der Treiber SQL_FN_STR_LOCATE_2 zurück, wenn **SQLGetInfo** mit der *Option* SQL_STRING_FUNCTIONS aufgerufen wird. Treiber, die das Aufrufen der Suchfunktion mit zwei oder drei Argumenten unterstützen, geben sowohl SQL_FN_STR_LOCATE als auch SQL_FN_STR_LOCATE_2 zurück.|  
|**LTrim (** _string_exp_ **)** (ODBC 1,0)|Gibt die Zeichen *string_exp*zurück, bei der führende Leerzeichen entfernt wurden.|  
|**OCTET_LENGTH (** _string_exp_ **)** (ODBC 3,0)|Gibt die Länge des Zeichenfolgenausdrucks in Bytes zurück. Das Ergebnis ist die kleinste ganze Zahl, die nicht kleiner ist als die Anzahl der Bits dividiert durch 8.<br /><br /> Funktioniert nicht nur für Zeichen folgen-Datentypen und konvertiert daher *string_exp* nicht implizit in eine Zeichenfolge, sondern gibt stattdessen die (interne) Größe eines beliebigen Datentyps zurück.|  
|**Position (** _character_exp_ **in** _character_exp_**)** (ODBC 3,0)|Gibt die Position des ersten Zeichen Ausdrucks im zweiten Zeichen Ausdruck zurück. Das Ergebnis ist ein genauer numerischer Wert mit einer von der Implementierung definierten Genauigkeit und einer Skala von 0.|  
|**Repeat (** _string_exp,_ _Anzahl_**)** (ODBC 1,0)|Gibt eine Zeichenfolge zurück, die aus *string_exp* wiederholten *Anzahl* von Wiederholungen besteht.|  
|**Replace (** _string_exp1_, *string_exp2*, _string_exp3_**)** (ODBC 1,0)|Suchen Sie nach *string_exp1* Vorkommen von *string_exp2*, und ersetzen Sie durch *string_exp3*.|  
|**Right (** _string_exp_, _count_**)** (ODBC 1,0)|Gibt die ganz *Zahl* Zeichen *string_exp*zurück.|  
|**RTrim (** _string_exp_ **)** (ODBC 1,0)|Gibt die Zeichen *string_exp* zurück, bei der nachfolgende Leerzeichen entfernt wurden.|  
|**SOUNDEX (** _string_exp_ **)** (ODBC 2,0)|Gibt eine Datenquellen abhängige Zeichenfolge zurück, die den Ton der Wörter in *string_exp*darstellt. Beispielsweise gibt SQL Server einen vierstelligen SOUNDEX-Code zurück. Oracle gibt eine phonetische Darstellung jedes Worts zurück.|  
|**Leerraum (** _Anzahl_ **)** (ODBC 2,0)|Gibt eine Zeichenfolge zurück, die aus *count* Spaces besteht.|  
|**SUBSTRING (** _string_exp_, *Start*, length **)** (ODBC 1,0)|Gibt eine Zeichenfolge zurück, die von *string_exp*abgeleitet ist, beginnend an der Zeichenposition, die durch *Start* für *Längen* Zeichen angegeben wird.|  
|**UCase (** _string_exp_ **)** (ODBC 1,0)|Gibt eine Zeichenfolge zurück, die der in *string_exp*entspricht, bei der alle Kleinbuchstaben in Großbuchstaben konvertiert wurden.|
