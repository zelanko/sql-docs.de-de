---
title: Zeichen folgen Funktionen (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
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
ms.openlocfilehash: db1fbaffbee0f74625f4a11cad3b961f194e3829
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948778"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Zeichenfolgenfunktionen (Visual FoxPro-ODBC-Treiber)
In der folgenden Tabelle sind die vom Visual FoxPro-ODBC-Treiber unterstützten Funktionen der ODBC-Zeichen folgen Bearbeitung aufgeführt. Wenn die Visual FoxPro-Grammatik für dieselbe Funktion von der ODBC-Syntax abweicht, wird die Entsprechung von Visual FoxPro aufgeführt.  
  
|ODBC-Grammatik|Visual FoxPro-Grammatik|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|Char *(Code)*|Chr *(string_exp)*|  
|Concat *(string_exp1, string_exp2)*|*string_exp1 + string_exp2*|  
|Differenz *(string_exp1 string_exp2)*||  
|INSERT *(string_exp1, Start, length, string_exp2)*|Zeug *(string_exp1, Start, length, string_exp2)*|  
|LCase *(string_exp)*|Niedriger *(string_exp)*|  
|Left *(string_exp, count)*||  
|Länge *(string_exp)*|LEN *(string_exp)*|  
|LTrim *(string_exp)*||  
|Wiederholen *(string_exp, Anzahl)*|Replizieren *(string_exp, Anzahl)*|  
|Replace *(string_exp1, string_exp2, string_exp3)*|"Straume" *(string_exp1, string_exp2, string_exp3)*|  
|Right *(string_exp, count)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|Leerraum *(Anzahl)*||  
|Teil Zeichenfolge *(string_exp, Start, Länge)*|Substr *(string_exp, Start, Länge)*|  
|UCase *(string_exp)*|Upper *(string_exp)*|
