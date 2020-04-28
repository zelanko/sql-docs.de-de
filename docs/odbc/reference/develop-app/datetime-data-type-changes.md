---
title: DateTime-Datentyp Änderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- compatibility [ODBC], datetime data types
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4f186047dd31aa2c4b66ec1ce73c8cb9fae31c04
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304643"
---
# <a name="datetime-data-type-changes"></a>Änderungen des Datentyps „datetime“
In ODBC *3. x*wurden die Bezeichner für die SQL-Datentypen date, Time und Zeitstempel von SQL_DATE, SQL_TIME und SQL_TIMESTAMP (mit Instanzen von **#define** in der Header Datei 9, 10 und 11) in SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP (mit Instanzen von **#define** in der Header Datei 91, 92 und 93) geändert. Die entsprechenden C-Typbezeichner wurden von SQL_C_DATE, SQL_C_TIME und SQL_C_TIMESTAMP in SQL_C_TYPE_DATE, SQL_C_TYPE_TIME bzw. SQL_C_TYPE_TIMESTAMP geändert.  
  
 Die Spaltengröße und die Dezimalstellen, die für die SQL-datetime-Datentypen in ODBC *3. x* zurückgegeben werden, sind identisch mit der für Sie in ODBC *2. x*zurückgegebenen Genauigkeit und Skalierung. Diese Werte unterscheiden sich von den Werten in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE Deskriptor. (Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).)  
  
 Diese Änderungen wirken sich auf **SQLDescribeCol**, **SQLDescribeParam**und **SQLColAttribute**aus. **SQLBindCol**, **SQLBindParameter**und **SQLGetData**; und **SQLColumns**, **SQLGetTypeInfo**, **sqlprocedurecolumschlag NS**, **SQLStatistics**und **SQLSpecialColumns**.  
  
 In der folgenden Tabelle wird gezeigt, wie der ODBC *3. x* -Treiber-Manager die Zuordnung der in den *TargetType* -Argumenten von **SQLBindCol** und **SQLGetData** oder des *ValueType* -Arguments von **SQLBindParameter**eingegebenen Datums-, Uhrzeit-und Zeitstempel-C-Datentypen ausführt.  
  
|Datentyp<br /><br /> eingegebener Code|*2. x* -APP zu<br /><br /> *2. x* -Treiber|*2. x* -APP zu<br /><br /> *3. x* -Treiber|*3. x* -APP zu<br /><br /> *2. x* -Treiber|*3. x* -APP zu<br /><br /> *3. x* -Treiber|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|Keine Zuordnung|SQL_C_TYPE_DATE (91)|Keine Zuordnung [1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|Fehler (von DM)|Fehler (von DM)|SQL_C_DATE (9)|Keine Zuordnung [2]|  
|SQL_C_TIME (10)|Keine Zuordnung|SQL_C_TYPE_TIME (92)|Keine Zuordnung [1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|Fehler (von DM)|Fehler (von DM)|SQL_C_TIME (10)|Keine Zuordnung [2]|  
|SQL_C_TIMESTAMP (11)|Keine Zuordnung|SQL_C_TYPE_TIMESTAMP (93)|Keine Zuordnung [1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|Fehler (von DM)|Fehler (von DM)|SQL_C_TIMESTAMP (11)|Keine Zuordnung [2]|  
  
 [1] Daher kann eine ODBC *3. x* -Anwendung, die mit einem ODBC *2. x* -Treiber arbeitet, die Datums-, Uhrzeit-oder Zeitstempel Codes verwenden, die in den Resultsets zurückgegeben werden, die von den-Katalog Funktionen zurückgegeben werden.  
  
 [2] Folglich kann eine ODBC *3. x* -Anwendung, die mit einem ODBC *3. x* -Treiber arbeitet, die Datums-, Uhrzeit-oder Zeitstempel Codes verwenden, die in den Resultsets zurückgegeben werden, die von den-Katalog Funktionen zurückgegeben werden.  
  
 In der folgenden Tabelle wird gezeigt, wie der ODBC *3. x* -Treiber-Manager die Zuordnung der im *Parameter Type* -Argument von **SQLBindParameter** oder des *DataType* -Arguments von **SQLGetTypeInfo**eingegebenen Datums-, Uhrzeit-und Zeitstempel-SQL-Datentypen ausführt.  
  
|Datentyp<br /><br /> eingegebener Code|*2. x* -APP zu<br /><br /> *2. x* -Treiber|*2. x* -APP zu<br /><br /> *3. x* -Treiber|*3. x* -APP zu<br /><br /> *2. x* -Treiber|*3. x* -APP zu<br /><br /> *3. x* -Treiber|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|Keine Zuordnung|SQL_TYPE_DATE (91)|Keine Zuordnung [1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|Fehler (von DM)|Fehler (von DM)|SQL_DATE (9)|Keine Zuordnung [2]|  
|SQL_TIME (10)|Keine Zuordnung|SQL_TYPE_TIME (92)|Keine Zuordnung [1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|Fehler (von DM)|Fehler (von DM)|SQL_TIME (10)|Keine Zuordnung [2]|  
|SQL_TIMESTAMP (11)|Keine Zuordnung|SQL_TYPE_TIMESTAMP (93)|Keine Zuordnung [1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|Fehler (von DM)|Fehler (von DM)|SQL_TIMESTAMP (11)|Keine Zuordnung [2]|  
  
 [1] Daher kann eine ODBC *3. x* -Anwendung, die mit einem ODBC *2. x* -Treiber arbeitet, die Datums-, Uhrzeit-oder Zeitstempel Codes verwenden, die in den Resultsets zurückgegeben werden, die von den-Katalog Funktionen zurückgegeben werden.  
  
 [2] Folglich kann eine ODBC *3. x* -Anwendung, die mit einem ODBC *3. x* -Treiber arbeitet, die Datums-, Uhrzeit-oder Zeitstempel Codes verwenden, die in den Resultsets zurückgegeben werden, die von den-Katalog Funktionen zurückgegeben werden.
