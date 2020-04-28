---
title: C-Intervall Struktur | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02c86ebe24a0e12531e355f95185b01f3089a31b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292152"
---
# <a name="c-interval-structure"></a>C-Intervallstruktur
Jeder der im Abschnitt [c-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) aufgelisteten Datentypen im c-Intervall verwendet die gleiche Struktur, um die Intervall Daten zu enthalten. Wenn **SQLFetch**, **SQLFetchScroll**oder **SQLGetData** aufgerufen wird, der Treiber gibt Daten in die SQL_INTERVAL_STRUCT Struktur zurück, verwendet den Wert, der von der Anwendung für die C-Datentypen (im Befehl **SQLBindCol**, **SQLGetData**oder **SQLBindParameter**) festgelegt wurde, um den Inhalt SQL_INTERVAL_STRUCT zu interpretieren, und füllt das *interval_type* Feld der Struktur mit dem Enumerationswert *, der dem* C-Typ entspricht. Beachten Sie, dass Treiber das *interval_type* Feld nicht lesen, um den Typ des Intervalls zu bestimmen. Sie rufen den Wert des SQL_DESC_CONCISE_TYPE deskriptorfelds ab. Wenn die Struktur für Parameterdaten verwendet wird, verwendet der Treiber den Wert, der von der Anwendung im SQL_DESC_CONCISE_TYPE-Feld des APD angegeben wird, um den Inhalt von SQL_INTERVAL_STRUCT zu interpretieren, auch wenn die Anwendung den Wert des *interval_type* Felds auf einen anderen Wert festlegt.  
  
 Diese Struktur ist wie folgt definiert:  
  
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
  
 Das *interval_type* -Feld des SQL_INTERVAL_STRUCT gibt der Anwendung an, welche Struktur in der Union enthalten ist und welche Member der Struktur relevant sind. Das Feld *interval_sign* hat den Wert SQL_FALSE, wenn das führende Intervall nicht signiert ist. Wenn Sie SQL_TRUE, ist das führende Feld negativ. Der Wert im führenden Feld selbst ist unabhängig vom Wert *interval_sign*immer unsigniert. Das *interval_sign* Feld fungiert als Signier Bit.
