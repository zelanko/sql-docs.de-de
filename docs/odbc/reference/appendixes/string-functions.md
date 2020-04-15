---
title: String-Funktionen | Microsoft Docs
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
ms.openlocfilehash: d9323809028ad170a4811b1af8b6e276cdbb4293
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302841"
---
# <a name="string-functions"></a>Zeichenfolgenfunktionen
In der folgenden Tabelle sind Die Funktionen zur Zeichenfolgenmanipulation aufgeführt. Eine Anwendung kann bestimmen, welche Zeichenfolgenfunktionen von einem Treiber unterstützt werden, indem **sie SQLGetInfo** mit einem *Informationstyp* von SQL_STRING_FUNCTIONS aufruft.  
  
## <a name="remarks"></a>Bemerkungen  
 Argumente, die als *string_exp* bezeichnet werden, können der Name einer Spalte, ein *Zeichenfolgenliteral*oder das Ergebnis einer anderen Skalarfunktion sein, bei der der zugrunde liegende Datentyp als SQL_CHAR, SQL_VARCHAR oder SQL_LONGVARCHAR dargestellt werden kann.  
  
 Argumente, die als *character_exp* bezeichnet werden, sind eine Zeichenfolge mit variabler Länge.  
  
 Argumente, die als *start*, *length*oder *count* bezeichnet werden, können ein *numerisches Literal* oder das Ergebnis einer anderen skalaren Funktion sein, wobei der zugrunde liegende Datentyp als SQL_TINYINT, SQL_SMALLINT oder SQL_INTEGER dargestellt werden kann.  
  
 Die hier aufgeführten Zeichenfolgenfunktionen sind 1-basiert; das heißt, das erste Zeichen in der Zeichenfolge ist Zeichen 1.  
  
 Die BIT_LENGTH-, CHAR_LENGTH-, CHARACTER_LENGTH-, OCTET_LENGTH- und POSITION-Zeichenfolgen-Skalafunktionen wurden in ODBC 3.0 hinzugefügt, um sql-92 auszurichten.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|**ASCII(** _string_exp_ **)** (ODBC 1.0)|Gibt den ASCII-Codewert des linksletzten Zeichens *von string_exp* als Ganzzahl zurück.|  
|**BIT_LENGTH(** _string_exp_ **)** (ODBC 3.0)|Gibt die Länge des Zeichenfolgenausdrucks in Bits zurück.<br /><br /> Funktioniert nicht nur für Zeichenfolgendatentypen, konvertiert daher nicht implizit *string_exp* in Zeichenfolge, sondern gibt die (interne) Größe des angegebenen Datentyps zurück.|  
|**CHAR(** _Code_ **)** (ODBC 1.0)|Gibt das Zeichen zurück, das den ASCII-Codewert hat, der durch *Code*angegeben ist. Der Wert des *Codes* sollte zwischen 0 und 255 liegen; Andernfalls ist der Rückgabewert von der Datenquelle abhängig.|  
|**CHAR_LENGTH(** _string_exp_ **)** (ODBC 3.0)|Gibt die Länge in Zeichen des Zeichenfolgenausdrucks zurück, wenn der Zeichenfolgenausdruck von einem Zeichendatentyp ist; Andernfalls gibt die Länge in Bytes des Zeichenfolgenausdrucks zurück (die kleinste ganze Zahl nicht kleiner als die Anzahl der Bits geteilt durch 8). (Diese Funktion ist die gleiche wie die CHARACTER_LENGTH Funktion.)|  
|**CHARACTER_LENGTH(** _string_exp_ **)** (ODBC 3.0)|Gibt die Länge in Zeichen des Zeichenfolgenausdrucks zurück, wenn der Zeichenfolgenausdruck von einem Zeichendatentyp ist; Andernfalls gibt die Länge in Bytes des Zeichenfolgenausdrucks zurück (die kleinste ganze Zahl nicht kleiner als die Anzahl der Bits geteilt durch 8). (Diese Funktion entspricht der CHAR_LENGTH Funktion.)|  
|**CONCAT(** _string_exp1_,_string_exp2_**)** (ODBC 1.0)|Gibt eine Zeichenfolge zurück, die das Ergebnis der Ververketteung von *string_exp2* mit *string_exp1*ist. Die Ergebniszeichenfolge hängt vom DBMS ab. Wenn z. B. die von *string_exp1* dargestellte Spalte einen NULL-Wert enthält, gibt DB2 NULL zurück, sql Server die Zeichenfolge nicht NULL.|  
|**DIFFERENZ(** _string_exp1_,_string_exp2_**)** (ODBC 2.0)|Gibt einen Ganzzahlwert zurück, der die Differenz zwischen den Werten angibt, die von der SOUNDEX-Funktion für string_exp1 zurückgegeben *werden,* und *string_exp2*.|  
|**INSERT(** _string_exp1_, *start*, *length*, _string_exp2_**)** (ODBC 1.0)|Gibt eine Zeichenfolge zurück, in der *Längenzeichen* aus *string_exp1*gelöscht wurden, beginnend mit *Anfang*, und wo *string_exp2* in string_exp eingefügt *wurde,* beginnend mit *Anfang*.|  
|**LCASE(** _string_exp_ **)** (ODBC 1.0)|Gibt eine Zeichenfolge zurück, die der in *string_exp*entspricht, wobei alle Großbuchstaben in Kleinbuchstaben konvertiert werden.|  
|**LINKS(** _string_exp_, _zählen_**)** (ODBC 1.0)|Gibt die linkshöchsten *Zählzeichen* *von string_exp*zurück.|  
|**LÄNGE(** _string_exp_ **)** (ODBC 1.0)|Gibt die Anzahl der Zeichen in *string_exp zurück,* ohne nachfolgende Leerzeichen.<br /><br /> **LENGTH** akzeptiert nur Zeichenfolgen. Konvertiert daher implizit *string_exp* in eine Zeichenfolge und gibt die Länge dieser Zeichenfolge zurück (nicht die interne Größe des Datentyps).|  
|**LOCATE(** _string_exp1_, *string_exp2*[, *start*]**)** (ODBC 1.0)|Gibt die Startposition des ersten Vorkommens von *string_exp1* innerhalb *string_exp2*zurück. Die Suche nach dem ersten Vorkommen von *string_exp1* beginnt mit der ersten Zeichenposition in *string_exp2* es sei denn, das optionale Argument *start*wird angegeben. Wenn *Start* angegeben ist, beginnt die Suche mit der Zeichenposition, die durch den Wert von *start*angegeben wird. Die erste Zeichenposition in *string_exp2* wird durch den Wert 1 angezeigt. Wenn *string_exp1* nicht in *string_exp2*gefunden wird, wird der Wert 0 zurückgegeben.<br /><br /> Wenn eine Anwendung die locate-Skalarfunktion mit den *Argumenten string_exp1*, *string_exp2*und *start* aufrufen kann, gibt der Treiber SQL_FN_STR_LOCATE zurück, wenn **SQLGetInfo** mit einer *Option* der SQL_STRING_FUNCTIONS aufgerufen wird. Wenn die Anwendung die LOCATE-Skalafunktion nur mit den *Argumenten string_exp1* und *string_exp2* aufrufen kann, gibt der Treiber SQL_FN_STR_LOCATE_2 zurück, wenn **SQLGetInfo** mit einer *Option* der SQL_STRING_FUNCTIONS aufgerufen wird. Treiber, die das Aufrufen der LOCATE-Funktion mit zwei oder drei Argumenten unterstützen, geben sowohl SQL_FN_STR_LOCATE als auch SQL_FN_STR_LOCATE_2 zurück.|  
|**LTRIM(** _string_exp_ **)** (ODBC 1.0)|Gibt die Zeichen von *string_exp*zurück, wobei führende Leerzeichen entfernt werden.|  
|**OCTET_LENGTH(** _string_exp_ **)** (ODBC 3.0)|Gibt die Länge des Zeichenfolgenausdrucks in Bytes zurück. Das Ergebnis ist die kleinste ganze Zahl, die nicht kleiner ist als die Anzahl der Bits dividiert durch 8.<br /><br /> Funktioniert nicht nur für Zeichenfolgendatentypen, konvertiert daher nicht implizit *string_exp* in Zeichenfolge, sondern gibt die (interne) Größe des angegebenen Datentyps zurück.|  
|**POSITION(** _character_exp_ **IN** _character_exp_**)** (ODBC 3.0)|Gibt die Position des ersten Zeichenausdrucks im zweiten Zeichenausdruck zurück. Das Ergebnis ist eine exakte numerische mit einer implementierungsdefinierten Genauigkeit und einer Skala von 0.|  
|**REPEAT(** _string_exp,_ _Anzahl_**)** (ODBC 1.0)|Gibt eine Zeichenfolge zurück, die aus *string_exp* wiederholten *Anzahl* mal besteht.|  
|**REPLACE(** _string_exp1_, *string_exp2*, _string_exp3_**)** (ODBC 1.0)|Suchen Sie *string_exp1* nach Ereignissen von *string_exp2*, und ersetzen Sie sie durch *string_exp3*.|  
|**RECHTS(** _string_exp_, _zählen_**)** (ODBC 1.0)|Gibt die rechten *Zählzeichen* *von string_exp*zurück.|  
|**RTRIM(** _string_exp_ **)** (ODBC 1.0)|Gibt die Zeichen von *string_exp* zurück, bei denen nachfolgende Leerzeichen entfernt wurden.|  
|**SOUNDEX(** _string_exp_ **)** (ODBC 2.0)|Gibt eine datenquellenabhängige Zeichenfolge zurück, die den Klang der Wörter in *string_exp*darstellt. SQL Server gibt z. B. einen 4-stelligen SOUNDEX-Code zurück. Oracle gibt eine phonetische Darstellung jedes Wortes zurück.|  
|**SPACE(** _Anzahl_ **)** (ODBC 2.0)|Gibt eine Zeichenfolge zurück, die aus *Zählräumen* besteht.|  
|**SUBSTRING(** _string_exp_, *start*, length **)** (ODBC 1.0)|Gibt eine Zeichenkette zurück, die von *string_exp*abgeleitet wird, beginnend an der Zeichenposition, die durch *Den Anfang* für *Längenzeichen* angegeben wird.|  
|**UCASE(** _string_exp_ **)** (ODBC 1.0)|Gibt eine Zeichenfolge zurück, die der in *string_exp*entspricht, wobei alle Kleinbuchstaben in Großbuchstaben konvertiert werden.|
