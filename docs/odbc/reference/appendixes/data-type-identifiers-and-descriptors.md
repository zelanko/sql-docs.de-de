---
title: Datentyp-IDs und Deskriptoren | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 748f2452d20b618ae0011e2e1ac4e24af098ac06
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019047"
---
# <a name="data-type-identifiers-and-descriptors"></a>Datentypbezeichner und Deskriptoren
Die Datentypen aufgelistet, der [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) und [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) Abschnitten weiter oben in diesem Anhang werden "präzise"-Datentypen: Jeder Bezeichner verweist auf einen single-Datentyp. Es ist zwischen den Bezeichner und den Datentyp aus. Deskriptoren, jedoch implementieren das Automatisierungsmodell nicht in allen Fällen einen einzelnen Wert verwenden, um die Identifizierung von Datentypen. In einigen Fällen verwenden sie einen Datentyp für die "verbose" und ein Untercode Typ. Für alle Datentypen mit Ausnahme von "DateTime" "und" Interval-Datentypen entspricht der ausführlichen Typbezeichner der präzise Typ-ID, und der Wert in SQL_DESC_DATETIME_INTERVAL_CODE gleich 0 ist. Für Datetime "und" Interval-Datentypen jedoch ein ausführlichen Typ (SQL_DATETIME oder SQL_INTERVAL) befindet sich in SQL_DESC_TYPE, ein präziser in SQL_DESC_CONCISE_TYPE gespeichert ist und ein Untercode für jeden präzise in SQL_DESC_DATETIME_INTERVAL_CODE gespeichert. Eines dieser Felder wirkt sich auf die anderen. Weitere Informationen zu diesen Feldern finden Sie unter den [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) funktionsbeschreibung.  
  
 Wenn das Feld SQL_DESC_TYPE oder SQL_DESC_CONCISE_TYPE für einige Datentypen festgelegt ist, werden die Felder SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION und SQL_DESC_SCALE auf die Standardwerte für die Daten ggf. automatisch festgelegt Geben Sie ein. Weitere Informationen finden Sie unter der Beschreibung des Felds SQL_DESC_TYPE in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Wenn eine der festgelegten Standardwerte nicht geeignet, sollte die Anwendung explizit das Deskriptorfeld durch einen Aufruf von festgelegt **SQLSetDescField**.  
  
 Die folgende Tabelle zeigt die präzise Typbezeichner, ausführlichen Typbezeichner und Typ Subcode für jede "DateTime" und die SQL-Zeitintervall und die C-Typ-ID. Wie diese Tabelle gibt an, für Datetime "und" Interval-Datentypen, haben die SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE Felder die gleichen Manifestkonstanten für die SQL-Datentypen (in der Implementierung Deskriptoren) und C-Datentypen (in-Anwendung Deskriptoren).  
  
|Präzise SQL-Typ|Präzise C-Typ|Verbose-Typ|DATETIME_INTERVAL_CODE|  
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
