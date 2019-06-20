---
title: C-Intervall-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- interval data type [ODBC], structure
- C data types [ODBC], interval
ms.assetid: 52b42b56-50aa-4ce6-8d79-0963c7a71437
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bbd920b77fd44eaf4765f0983d7d16feb31a4d91
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026592"
---
# <a name="c-interval-structure"></a>C-Intervallstruktur
Jede von der C-Interval-Datentypen aufgeführt, der [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) Abschnitt verwendet die gleiche Struktur, um die Intervalldaten enthalten. Wenn **SQLFetch**, **SQLFetchScroll**, oder **SQLGetData** wird aufgerufen, der Treiber gibt Daten zurück, in die Struktur SQL_INTERVAL_STRUCT und verwendet den Wert, der vom angegeben wurde. den Anwendung für die C-Datentypen (im Aufruf von **SQLBindCol**, **SQLGetData**, oder **SQLBindParameter**) zum Interpretieren des Inhalts der SQL_INTERVAL_STRUCT , und füllt die *Interval_type* -Feld der Struktur mit der *Enum* -Wert, des C-Typs entspricht. Beachten Sie, dass die Treiber nicht gelesen werden die *Interval_type* Feld, um zu bestimmen, den Typ des Intervalls; sie rufen Sie den Wert des Felds SQL_DESC_CONCISE_TYPE-Deskriptor. Wenn die Struktur für Parameterdaten verwendet wird, der Treiber verwendet den angegebenen Wert von der Anwendung in das Feld "SQL_DESC_CONCISE_TYPE" der APD zum Interpretieren des Inhalts der SQL_INTERVAL_STRUCT, auch wenn die Anwendung den Wert für setzt die  *Interval_type* Feld auf einen anderen Wert.  
  
 Diese Struktur ist folgendermaßen definiert:  
  
```  
typedef struct tagSQL_INTERVAL_STRUCT  
{  
   SQLINTERVAL interval_type;   
   SQLSMALLINT interval_sign;  
   union {  
         SQL_YEAR_MONTH_STRUCT   year_month;  
         SQL_DAY_SECOND_STRUCT   day_second;  
         } intval;  
} SQL_INTERVAL_STRUCT;  
typedef enum   
{  
   SQL_IS_YEAR = 1,  
   SQL_IS_MONTH = 2,  
   SQL_IS_DAY = 3,  
   SQL_IS_HOUR = 4,  
   SQL_IS_MINUTE = 5,  
   SQL_IS_SECOND = 6,  
   SQL_IS_YEAR_TO_MONTH = 7,  
   SQL_IS_DAY_TO_HOUR = 8,  
   SQL_IS_DAY_TO_MINUTE = 9,  
   SQL_IS_DAY_TO_SECOND = 10,  
   SQL_IS_HOUR_TO_MINUTE = 11,  
   SQL_IS_HOUR_TO_SECOND = 12,  
   SQL_IS_MINUTE_TO_SECOND = 13  
} SQLINTERVAL;  
  
typedef struct tagSQL_YEAR_MONTH  
{  
   SQLUINTEGER year;  
   SQLUINTEGER month;   
} SQL_YEAR_MONTH_STRUCT;  
  
typedef struct tagSQL_DAY_SECOND  
{  
   SQLUINTEGER day;  
   SQLUINTEGER hour;  
   SQLUINTEGER minute;  
   SQLUINTEGER second;  
   SQLUINTEGER fraction;  
} SQL_DAY_SECOND_STRUCT;  
```  
  
 Die *Interval_type* Feld von der SQL_INTERVAL_STRUCT gibt an, an die Anwendung in welcher Struktur in der Union gehalten wird, und welche Member der Struktur sind auch relevant. Die *Interval_sign* Feld hat den Wert SQL_FALSE aus, wenn das Feld für anführenden Intervallwert, nicht signiert ist, ist dies SQL_TRUE, ist das führende Feld negativ. Der Wert im Feld führende selbst ist immer unsigniert, unabhängig vom Wert der *Interval_sign*. Die *Interval_sign* Feld fungiert als Vorzeichenbit.
