---
title: Datentyp Bezeichner und Deskriptoren | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284483"
---
# <a name="data-type-identifiers-and-descriptors"></a>Datentypbezeichner und Deskriptoren
Die in den Abschnitten SQL- [Daten](../../../odbc/reference/appendixes/sql-data-types.md) Typen und [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) weiter oben in diesem Anhang aufgeführten Datentypen sind "präzise" Datentypen: jeder Bezeichner verweist auf einen einzelnen Datentyp. Zwischen dem Bezeichner und dem Datentyp besteht eine eins-zu-eins-Entsprechung. Deskriptoren verwenden jedoch nicht in allen Fällen einen einzelnen Wert, um Datentypen zu identifizieren. In einigen Fällen verwenden Sie den Datentyp "Verbose" und einen typsubcode. Für alle Datentypen mit Ausnahme von DateTime-und interval-Datentypen ist der ausführliche Typbezeichner identisch mit dem präzisen Typbezeichner, und der Wert in SQL_DESC_DATETIME_INTERVAL_CODE gleich 0 (null) ist. Für DateTime-und interval-Datentypen wird jedoch ein ausführlicher Typ (SQL_DATETIME oder SQL_INTERVAL) in SQL_DESC_TYPE gespeichert, ein präziser Typ wird in SQL_DESC_CONCISE_TYPE gespeichert, und ein Subcode für jeden präzisen Typ wird in SQL_DESC_DATETIME_INTERVAL_CODE gespeichert. Das Festlegen eines dieser Felder wirkt sich auf die anderen Felder aus. Weitere Informationen zu diesen Feldern finden Sie in der Beschreibung der [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) -Funktion.  
  
 Wenn das Feld SQL_DESC_TYPE oder SQL_DESC_CONCISE_TYPE für einige Datentypen festgelegt ist, werden die Felder SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION und SQL_DESC_SCALE automatisch auf die Standardwerte festgelegt, die für den-Datentyp gelten. Weitere Informationen finden Sie in der Beschreibung des SQL_DESC_TYPE-Felds in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Wenn einer der Standardwerte festgelegt ist, sollte die Anwendung das Deskriptorfeld explizit durch einen **SQLSetDescField**-Befehl festlegen.  
  
 In der folgenden Tabelle werden die präzisere Typkennung, der ausführliche Typbezeichner und der typsubcode für jeden DateTime-und Interval-SQL-und C-Typbezeichner angezeigt. Wie diese Tabelle zeigt, haben die Felder SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE für DateTime-und interval-Datentypen die gleichen Manifest-Konstanten sowohl für SQL-Datentypen (in Implementierungs Deskriptoren) als auch für C-Datentypen (in Anwendungs Deskriptoren).  
  
|Präziser SQL-Typ|Präziser C-Typ|Verbose-Typ|DATETIME_INTERVAL_CODE|  
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
