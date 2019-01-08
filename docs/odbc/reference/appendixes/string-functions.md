---
title: Zeichenfolgenfunktionen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 948e22d9a4514e4ed7b211398ac28a7338b1c0ed
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591604"
---
# <a name="string-functions"></a>Zeichenfolgenfunktionen
Die folgende Tabelle enthält die Funktionen zur Zeichenfolgenmanipulation. Eine Anwendung kann bestimmen, welche Funktionen für Zeichenfolgen durch einen Treiber unterstützt werden, durch den Aufruf **SQLGetInfo** mit einer *Informationstyp* von SQL_STRING_FUNCTIONS.  
  
## <a name="remarks"></a>Hinweise  
 Argumente schulungsausgabe als *String_exp* möglich, dass der Name einer Spalte, eine *Zeichen-Zeichenfolgenliteral*, oder das Ergebnis von einem anderen Skalarfunktion, in denen der zugrunde liegende Datentyp als SQL_CHAR, SQL_ dargestellt werden kann VARCHAR oder SQL_LONGVARCHAR.  
  
 Argumente schulungsausgabe als *Character_exp* bestehen aus einer Zeichenfolge variabler Länge.  
  
 Argumente schulungsausgabe als *starten*, *Länge*, oder *Anzahl* kann eine *numerischen Literalen* oder das Ergebnis von einem anderen skalaren Funktion, in dem die zugrunde liegende Datentyp kann als SQL_TINYINT, SQL_SMALLINT oder SQL_INTEGER dargestellt werden.  
  
 Die hier aufgeführten Zeichenfolgenfunktionen sind 1-basiert. Das heißt, ist das erste Zeichen in der Zeichenfolge Zeichen 1.  
  
 Die Zeichenfolge-Skalarfunktionen BIT_LENGTH, CHAR_LENGTH, CHARACTER_LENGTH, OCTET_LENGTH und POSITION wurden ODBC 3.0 an SQL-92 ausgerichtet hinzugefügt.  
  
|Funktion|Description|  
|--------------|-----------------|  
|**ASCII (** _String_exp_ **)** (ODBC-1.0)|Gibt den ASCII-Codewert des äußeren linken Zeichens des *String_exp* als ganze Zahl.|  
|**BIT_LENGTH (** _String_exp_ **)** (ODBC-Version 3.0)|Gibt die Länge des Zeichenfolgenausdrucks in Bits zurück.<br /><br /> Nur für Zeichenfolgen-Datentypen nicht verwendet werden, aus diesem Grund wird nicht implizit konvertiert *String_exp* , sondern stattdessen eine Zeichenfolge gibt den Datentyp aufweisen, wird ihm, die (interne) Größe zurück.|  
|**CHAR (** _Code_ **)** (ODBC-1.0)|Gibt das Zeichen, die die ASCII-code vom angegebenen Wert *Code*. Der Wert des *Code* muss zwischen 0 und 255 sein; andernfalls ist des Rückgabewerts datenquellenabhängig.|  
|**CHAR_LENGTH (** _String_exp_ **)** (ODBC-Version 3.0)|Gibt die Länge in Zeichen des Zeichenfolgenausdrucks zurück, wenn der Ausdruck einen Zeichendatentyp ist; andernfalls gibt die Länge in Bytes der Zeichenfolgenausdruck (die kleinste ganze Zahl nicht kleiner als die Anzahl der Bits dividiert durch 8) zurück. (Diese Funktion ist identisch mit der CHARACTER_LENGTH-Funktion.)|  
|**CHARACTER_LENGTH (** _String_exp_ **)** (ODBC-Version 3.0)|Gibt die Länge in Zeichen des Zeichenfolgenausdrucks zurück, wenn der Ausdruck einen Zeichendatentyp ist; andernfalls gibt die Länge in Bytes der Zeichenfolgenausdruck (die kleinste ganze Zahl nicht kleiner als die Anzahl der Bits dividiert durch 8) zurück. (Diese Funktion ist die CHAR_LENGTH identisch.)|  
|**CONCAT (** _string_exp1_,_string_exp2 und_**)** (ODBC 1.0)|Gibt eine Zeichenfolge, die das Ergebnis der Verkettung wird *string_exp2 und* zu *string_exp1*. Die Ergebniszeichenfolge hängt vom DBMS ab. Wenn die Spalte durch dargestellt beispielsweise *string_exp1* enthalten einen NULL-Wert, DB2 return NULL aber SQL Server würde die ungleich NULL Zeichenfolge zurück.|  
|**Unterschied (** _string_exp1_,_string_exp2 und_**)** (ODBC 2.0)|Gibt einen ganzzahligen Wert, der den Unterschied zwischen den Werten, die von der SOUNDEX-Funktion für zurückgegebene angibt *string_exp1* und *string_exp2 und*.|  
|**Fügen Sie (** _string_exp1_, *starten*, *Länge*, _string_exp2 und_**)** (ODBC-1.0)|Gibt ein Zeichen, Zeichenfolge Where *Länge* Zeichen aus gelöscht wurden *string_exp1*, beginnend bei *starten*, und wo *string_exp2 und* in eingefügt wurde *String_exp,* beginnend bei *starten*.|  
|**LCASE (** _String_exp_ **)** (ODBC-1.0)|Gibt eine Zeichenfolge zurück, gleich *String_exp*, mit der alle Großbuchstaben in Kleinbuchstaben konvertiert.|  
|**LEFT (** _String_exp_, _Anzahl_**)** (ODBC-1.0)|Gibt zurück, der am weitesten links stehende *Anzahl* Zeichen *String_exp*.|  
|**Länge (** _String_exp_ **)** (ODBC-1.0)|Gibt die Anzahl der Zeichen in *String_exp,* ohne nachstehende Leerzeichen.<br /><br /> **Länge** akzeptiert nur Zeichenfolgen. Aus diesem Grund werden implizit konvertiert *String_exp* auf eine Zeichenfolge ein, und Rückgabe der Länge dieser Zeichenfolge (nicht die interne Größe des Datentyps).|  
|**Suchen (** _string_exp1_, *string_exp2 und*[, *starten*]**)** (ODBC-1.0)|Gibt die Anfangsposition des ersten Vorkommens des *string_exp1* in *string_exp2 und*. Die Suche nach dem ersten Vorkommen des *string_exp1* beginnt mit der Position des ersten Zeichens in *string_exp2 und* , wenn das optionale Argument, *starten*, angegeben ist. Wenn *starten* angegeben ist, wird die Suche beginnt mit der durch den Wert der angegebenen Zeichenposition *starten*. Positionieren Sie das erste Zeichen in *string_exp2 und* wird durch den Wert 1 angegeben. Wenn *string_exp1* befindet sich nicht innerhalb von *string_exp2 und*, wird der Wert 0 zurückgegeben.<br /><br /> Wenn eine Anwendung die suchen-Skalarfunktion mit aufrufen kann die *string_exp1*, *string_exp2 und*, und *starten* Argumente, gibt der Treiber SQL_FN_STR_LOCATE beim  **SQLGetInfo** aufgerufen wird und ein *Option* von SQL_STRING_FUNCTIONS. Wenn die Anwendung die suchen-Skalarfunktion nur aufrufen, kann die *string_exp1* und *string_exp2 und* Argumente, gibt der Treiber SQL_FN_STR_LOCATE_2 beim **SQLGetInfo**aufgerufen wird und ein *Option* von SQL_STRING_FUNCTIONS. Treiber, dass die Suchen-Funktion mit zwei oder drei Argumenten aufrufen Unterstützung sowohl SQL_FN_STR_LOCATE und SQL_FN_STR_LOCATE_2 zurückgeben.|  
|**LTRIM (** _String_exp_ **)** (ODBC-1.0)|Gibt die Zeichen des *String_exp*, mit führenden Leerzeichen entfernt.|  
|**OCTET_LENGTH (** _String_exp_ **)** (ODBC-Version 3.0)|Gibt die Länge des Zeichenfolgenausdrucks in Bytes zurück. Das Ergebnis ist die kleinste ganze Zahl, die nicht kleiner ist als die Anzahl der Bits dividiert durch 8.<br /><br /> Nur für Zeichenfolgen-Datentypen nicht verwendet werden, aus diesem Grund wird nicht implizit konvertiert *String_exp* , sondern stattdessen eine Zeichenfolge gibt den Datentyp aufweisen, wird ihm, die (interne) Größe zurück.|  
|**POSITION (** _Character_exp_ **IN** _Character_exp_**)** (ODBC-Version 3.0)|Gibt die Position des ersten Zeichens Ausdrucks in der zweiten Zeichenausdruck zurück. Das Ergebnis ist ein genauer numerischer Wert mit einer Implementierung definierten Genauigkeit und einer Skala von 0.|  
|**Wiederholen Sie die (** _String_exp,_ _Anzahl_**)** (ODBC-1.0)|Gibt eine Zeichenfolge aus *String_exp* wiederholt *Anzahl* Zeiten.|  
|**Ersetzen (** _string_exp1_, *string_exp2 und*, _string_exp3_**)** (ODBC 1.0)|Suche *string_exp1* Foroccurrences von *string_exp2 und*, und Ersetzen Sie dies durch *string_exp3*.|  
|**RECHTS (** _String_exp_, _Anzahl_**)** (ODBC-1.0)|Gibt zurück, der äußerst rechten *Anzahl* Zeichen *String_exp*.|  
|**RTRIM (** _String_exp_ **)** (ODBC-1.0)|Gibt die Zeichen des *String_exp* mit nachfolgenden Leerzeichen entfernt.|  
|**SOUNDEX (** _String_exp_ **)** (ODBC 2.0)|Eine Data Datenquelle abhängiger neue Zeichenfolge zurückgegeben, das den darstellt der Wörter in *String_exp*. SQL Server gibt z. B. einen 4-stelliger SOUNDEX-Code; Oracle gibt eine Phonetische Darstellung jedes Worts zurück.|  
|**Speicherplatz (** _Anzahl_ **)** (ODBC 2.0)|Gibt eine Zeichenfolge, bestehend aus *Anzahl* Leerzeichen.|  
|**SUBSTRING (** _String_exp_, *starten*, Länge **)** (ODBC-1.0)|Gibt eine Zeichenfolge, die abgeleitet wird *String_exp*, beginnend an der Position des Zeichens gemäß *starten* für *Länge* Zeichen.|  
|**UCASE (** _String_exp_ **)** (ODBC-1.0)|Gibt eine Zeichenfolge zurück, gleich *String_exp*, mit der alle Kleinbuchstaben in Großbuchstaben konvertiert.|
