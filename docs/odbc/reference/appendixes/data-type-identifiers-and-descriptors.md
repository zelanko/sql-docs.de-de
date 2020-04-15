---
title: Datentyp-Bezeichner und Deskriptoren | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
- descriptors [ODBC], data types
- verbose data types [ODBC]
- data types [ODBC], descriptors
- concise data types [ODBC]
ms.assetid: f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f65bc86213f99112daf17c67a4ca522490d32149
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284483"
---
# <a name="data-type-identifiers-and-descriptors"></a>Datentypbezeichner und Deskriptoren
Die Datentypen, die in den Abschnitten [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) und [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) weiter oben in diesem Anhang aufgeführt sind, sind "präzise" Datentypen: Jeder Bezeichner bezieht sich auf einen einzelnen Datentyp. Es besteht eine 1:1-Entsprechung zwischen dem Bezeichner und dem Datentyp. Deskriptoren verwenden jedoch nicht in allen Fällen einen einzigen Wert, um Datentypen zu identifizieren. In einigen Fällen verwenden sie einen "verbose" Datentyp und einen Typuntercode. Für alle Datentypen außer Datums- und Intervalldatentypen entspricht der ausführliche Typbezeichner dem prägnanten Typbezeichner, und der Wert in SQL_DESC_DATETIME_INTERVAL_CODE gleich 0 ist. Bei Datums- und Intervalldatentypen wird jedoch ein ausführlicher Typ (SQL_DATETIME oder SQL_INTERVAL) in SQL_DESC_TYPE gespeichert, ein prägnanter Typ wird in SQL_DESC_CONCISE_TYPE gespeichert, und ein Untercode für jeden prägnanten Typ wird in SQL_DESC_DATETIME_INTERVAL_CODE gespeichert. Das Festlegen eines dieser Felder wirkt sich auf die anderen Felder aus. Weitere Informationen zu diesen Feldern finden Sie in der [SQLSetDescField-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
 Wenn das Feld SQL_DESC_TYPE oder SQL_DESC_CONCISE_TYPE für einige Datentypen festgelegt ist, werden die Felder SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION und SQL_DESC_SCALE automatisch auf Standardwerte festgelegt, sofern dies für den Datentyp gilt. Weitere Informationen finden Sie in der Beschreibung des Felds SQL_DESC_TYPE in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Wenn einer der gesetzten Standardwerte nicht geeignet ist, sollte die Anwendung das Deskriptorfeld explizit über einen Aufruf von **SQLSetDescField**festlegen.  
  
 Die folgende Tabelle zeigt den prägnanten Typbezeichner, den ausführlichen Typbezeichner und den Typuntercode für jeden SQL- und C-Typbezeichner für Datums- und Intervallzeit. Wie aus dieser Tabelle hervorgeht, weisen die Felder SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE für Datumszeit- und Intervalldatentypen dieselben Manifestkonstanten sowohl für SQL-Datentypen (in Implementierungsdeskriptoren) als auch für C-Datentypen (in Anwendungsdeskriptoren) auf.  
  
|Prägnanter SQL-Typ|Prägnante C-Typ|Ausführlicher Typ|DATETIME_INTERVAL_CODE|  
|----------------------|--------------------|------------------|------------------------------|  
|SQL_TYPE_DATE|SQL_C_TYPE_DATE|SQL_DATETIME|SQL_CODE_DATE|  
|SQL_TYPE_TIME|SQL_C_TYPE_TIME|SQL_DATETIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_DATETIME|SQL_CODE_TIMESTAMP|  
|SQL_INTERVAL_MONTH|SQL_C_INTERVAL_MONTH|SQL_INTERVAL|SQL_CODE_MONTH|  
|SQL_INTERVAL_YEAR|SQL_C_INTERVAL_YEAR|SQL_INTERVAL|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_INTERVAL|SQL_CODE_YEAR_TO_MONTH|  
|SQL_INTERVAL_DAY|SQL_C_INTERVAL_DAY|SQL_INTERVAL|SQL_CODE_DAY|  
|SQL_INTERVAL_HOUR|SQL_C_INTERVAL_HOUR|SQL_INTERVAL|SQL_CODE_HOUR|  
|SQL_INTERVAL_MINUTE|SQL_C_INTERVAL_MINUTE|SQL_INTERVAL|SQL_CODE_MINUTE|  
|SQL_INTERVAL_SECOND|SQL_C_INTERVAL_SECOND|SQL_INTERVAL|SQL_CODE_SECOND|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_C_INTERVAL_DAY_TO_HOUR|SQL_INTERVAL|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE|SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_INTERVAL|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND|SQL_C_INTERVAL_DAY_TO_SECOND|SQL_INTERVAL|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR_TO_MINUTE|SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_INTERVAL|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND|SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_INTERVAL|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE_TO_SECOND|SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_INTERVAL|SQL_CODE_MINUTE_TO_SECOND|
