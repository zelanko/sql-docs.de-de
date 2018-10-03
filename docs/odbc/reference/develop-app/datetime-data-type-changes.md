---
title: Änderungen des Datentyps "DateTime" | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5a87a1cbfbdff5eb428e73d74cdd1199955d673
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834008"
---
# <a name="datetime-data-type-changes"></a>Änderungen des Datentyps „datetime“
In ODBC 3. *x*, die Bezeichner für date, Time und Timestamp SQL-Datentypen von SQL_DATE, SQL_TIME und SQL_TIMESTAMP geändert haben (mit Instanzen von **#define** in der Headerdatei, 9, 10 und 11), SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP (mit Instanzen von **#define** in der Headerdatei 91, 92 und 93) an. Die entsprechenden C-Typ-IDs haben bzw. von SQL_C_DATE SQL_C_TIME und SQL_C_TIMESTAMP SQL_C_TYPE_DATE SQL_C_TYPE_TIME und SQL_C_TYPE_TIMESTAMP geändert.  
  
 Die Spaltengröße und die Dezimalstellen für die SQL-Datetime-Datentypen in ODBC 3. zurückgegeben. *x* sind identisch mit der Genauigkeit und Dezimalstellenanzahl für sie in ODBC 2. zurückgegeben. *X*. Diese Werte unterscheiden sich die Werte in die deskriptorfelder SQL_DESC_PRECISION und SQL_DESC_SCALE zur Verfügung. (Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).)  
  
 Diese Änderungen wirken sich auf **SQLDescribeCol**, **SQLDescribeParam**, und **SQLColAttribute**; **SQLBindCol**, **SQLBindParameter**, und **SQLGetData**; und **SQLColumns**, **SQLGetTypeInfo** , **SQLProcedureColumns**, **SQLStatistics**, und **SQLSpecialColumns**.  
  
 Die folgende Tabelle zeigt, wie die ODBC 3.*.x* -Treiber-Manager führt die Zuordnung der Date, Time und Timestamp C-Datentypen in eingegebenen der *TargetType* Argumente **SQLBindCol**und **SQLGetData** oder in der *ValueType* Argument **SQLBindParameter**.  
  
|Datentyp<br /><br /> Code wurde eingegeben|2.*x* -app<br /><br /> 2.*x* Treiber|2.*x* -app<br /><br /> 3.*x* Treiber|3.*x* -app<br /><br /> 2.*x* Treiber|3.*x* -app<br /><br /> 3.*x* Treiber|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|Keine Zuordnung|SQL_C_TYPE_DATE (91)|Keine Zuordnung [1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|Fehler (DM)|Fehler (DM)|SQL_C_DATE (9)|Keine Zuordnung [2]|  
|SQL_C_TIME (10)|Keine Zuordnung|SQL_C_TYPE_TIME (92)|Keine Zuordnung [1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|Fehler (DM)|Fehler (DM)|SQL_C_TIME (10)|Keine Zuordnung [2]|  
|SQL_C_TIMESTAMP (11)|Keine Zuordnung|SQL_C_TYPE_TIMESTAMP (93)|Keine Zuordnung [1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|Fehler (DM)|Fehler (DM)|SQL_C_TIMESTAMP (11)|Keine Zuordnung [2]|  
  
 [1] als Ergebnis des dies, eine ODBC-3. *x* Anwendung mit einer ODBC 2. *X* Treiber können auf das Datum, Uhrzeit oder Zeitstempel-Codes, die zurückgegeben werden, in den Resultsets, die durch die Katalogfunktionen zurückgegeben werden.  
  
 [2] als Ergebnis des dies, eine ODBC-3. *x* Anwendung mit einer ODBC 3. *X* Treiber können auf das Datum, Uhrzeit oder Zeitstempel-Codes, die zurückgegeben werden, in den Resultsets, die durch die Katalogfunktionen zurückgegeben werden.  
  
 Die folgende Tabelle zeigt, wie die ODBC 3.*.x* -Treiber-Manager führt die Zuordnung der Date, Time und Timestamp SQL-Datentypen in eingegebenen der *ParameterType* Argument **SQLBindParameter**  oder in der *DataType* Argument **SQLGetTypeInfo**.  
  
|Datentyp<br /><br /> Code wurde eingegeben|2.*x* -app<br /><br /> 2.*x* Treiber|2.*x* -app<br /><br /> 3.*x* Treiber|3.*x* -app<br /><br /> 2.*x* Treiber|3.*x* -app<br /><br /> 3.*x* Treiber|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|Keine Zuordnung|SQL_TYPE_DATE (91)|Keine Zuordnung [1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|Fehler (DM)|Fehler (DM)|SQL_DATE (9)|Keine Zuordnung [2]|  
|SQL_TIME (10)|Keine Zuordnung|SQL_TYPE_TIME (92)|Keine Zuordnung [1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|Fehler (DM)|Fehler (DM)|SQL_TIME (10)|Keine Zuordnung [2]|  
|SQL_TIMESTAMP (11)|Keine Zuordnung|SQL_TYPE_TIMESTAMP (93)|Keine Zuordnung [1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|Fehler (DM)|Fehler (DM)|SQL_TIMESTAMP (11)|Keine Zuordnung [2]|  
  
 [1] als Ergebnis des dies, eine ODBC-3. *x* Anwendung mit einer ODBC 2. *X* Treiber können auf das Datum, Uhrzeit oder Zeitstempel-Codes, die zurückgegeben werden, in den Resultsets, die durch die Katalogfunktionen zurückgegeben werden.  
  
 [2] als Ergebnis des dies, eine ODBC-3. *x* Anwendung mit einer ODBC 3. *X* Treiber können auf das Datum, Uhrzeit oder Zeitstempel-Codes, die zurückgegeben werden, in den Resultsets, die durch die Katalogfunktionen zurückgegeben werden.
