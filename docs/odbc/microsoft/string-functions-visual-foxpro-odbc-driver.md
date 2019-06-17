---
title: Zeichenfolgenfunktionen (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a9e1c94eec150cc24522cd6e4c57eb35b4a2126
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270918"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Zeichenfolgenfunktionen (Visual FoxPro-ODBC-Treiber)
In der folgende Tabelle werden die ODBC-Funktionen zur Zeichenfolgenmanipulation von der Visual FoxPro-ODBC-Treiber unterstützt werden. Wenn die Visual FoxPro-Grammatik für die gleiche Funktion aus der ODBC-Syntax unterscheidet, wird der Visual FoxPro-Äquivalent aufgeführt.  
  
|ODBC-Grammatik|Visual FoxPro-Grammatik|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(Code)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2)*|*string_exp1 + string_exp2*|  
|Unterschied *(string_exp2 und string_exp1)*||  
|Fügen Sie *(string_exp1, Start, Länge, string_exp2 und)*|Alles *(string_exp1, Start, Länge, string_exp2 und)*|  
|LCASE *(string_exp)*|NIEDRIGERE *(String_exp)*|  
|Links *(String_exp, Anzahl)*||  
|Länge *(String_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|Wiederholen Sie die *(String_exp, Anzahl)*|Replizieren von *(String_exp, Anzahl)*|  
|Ersetzen Sie dies *(string_exp1, string_exp2 und, string_exp3)*|STRTRAN *(string_exp1, string_exp2, string_exp3)*|  
|RECHTS *(String_exp, Anzahl)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(String_exp)*||  
|Speicherplatz *(Anzahl)*||  
|TEILZEICHENFOLGE *(String_exp, Start, Länge)*|SUBSTR *(String_exp, Start, Länge)*|  
|UCASE *(string_exp)*|OBERE *(String_exp)*|
