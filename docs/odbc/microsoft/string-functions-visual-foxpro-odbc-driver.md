---
title: String-Funktionen (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 988ba23b95f6b138148b1fa17ad303d7aa2dc895
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299190"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Zeichenfolgenfunktionen (Visual FoxPro-ODBC-Treiber)
In der folgenden Tabelle sind ODBC-Zeichenfolgenmanipulationsfunktionen aufgeführt, die vom Visual FoxPro ODBC-Treiber unterstützt werden. Wenn sich die Visual FoxPro-Grammatik für dieselbe Funktion von der ODBC-Syntax unterscheidet, wird das Visual FoxPro-Äquivalent aufgelistet.  
  
|ODBC-Grammatik|Visuelle FoxPro-Grammatik|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(Code)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2)*|*string_exp1 + string_exp2*|  
|DIFFERENZ *(string_exp1, string_exp2)*||  
|INSERT *(string_exp1, Start, Länge, string_exp2)*|STUFF *(string_exp1, Start, Länge, string_exp2)*|  
|LCASE *(string_exp)*|LOWER *(string_exp)*|  
|LINKS *(string_exp, Anzahl)*||  
|LÄNGE *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|REPEAT *(string_exp, Anzahl)*|REPLICATE *(string_exp, Anzahl)*|  
|REPLACE *(string_exp1, string_exp2, string_exp3)*|STRTRAN *(string_exp1, string_exp2, string_exp3)*|  
|RECHTS *(string_exp, Zählen)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|SPACE *(Anzahl)*||  
|SUBSTRING *(string_exp, Start, Länge)*|SUBSTR *(string_exp, Start, Länge)*|  
|UCASE *(string_exp)*|UPPER *(string_exp)*|
