---
title: Datetime-Datentypen | Microsoft Docs
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
- data types [ODBC], date
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- data types [ODBC], timestamp
- data types [ODBC], backward compatibility
- compatibility [ODBC], datetime data types
- data types [ODBC], time
ms.assetid: 6b9363c9-04bf-4492-a210-7aa15dea4af8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10626c4f0bf2e33c70322a0eb49af6c3e01e4303
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307061"
---
# <a name="datetime-data-types"></a>datetime-Datentypen
In ODBC *3.x*haben sich die Bezeichner für Datum, Uhrzeit und Zeitstempel SQL-Datentypen von SQL_DATE, SQL_TIME und SQL_TIMESTAMP (mit Instanzen von **#define** in der Headerdatei 9, 10 und 11) in SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP (mit Instanzen von **#define** in der Headerdatei 91, 92 und 93) geändert. Die entsprechenden C-Typ-Bezeichner haben sich von SQL_C_DATE, SQL_C_TIME und SQL_C_TIMESTAMP in SQL_C_TYPE_DATE, SQL_C_TYPE_TIME und SQL_C_TYPE_TIMESTAMP geändert, und die Instanzen von **#define** haben sich entsprechend geändert.  
  
 Die Spaltengröße und die Dezimalstellen, die für die SQL datetime-Datentypen in ODBC *3.x* zurückgegeben werden, entsprechen der Genauigkeit und Skalierung, die für sie in ODBC *2.x*zurückgegeben werden. Diese Werte unterscheiden sich von den Werten in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE. (Weitere Informationen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.)  
  
 Diese Änderungen wirken sich auf **SQLDescribeCol**, **SQLDescribeParam**und **SQLColAttributes**aus. **SQLBindCol**, **SQLBindParameter**und **SQLGetData**; und **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLStatistics**und **SQLSpecialColumns**.  
  
 Ein ODBC *3.x-Treiber* verarbeitet die im vorherigen Absatz aufgeführten Funktionsaufrufe gemäß der Einstellung des SQL_ATTR_ODBC_VERSION-Umgebungsattributs. Für **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLSpecialColumns**und **SQLStatistics**, wenn SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 festgelegt ist, geben die Funktionen SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP im Feld DATA_TYPE zurück. Die COLUMN_SIZE Spalte (in dem von **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**und **SQLSpecialColumns**) zurückgegebenen Resultset enthält die binäre Genauigkeit für den ungefähren numerischen Typ. Die NUM_PREC_RADIX Spalte (in dem von **SQLColumns**, **SQLGetTypeInfo**und **SQLProcedureColumns**zurückgegebenen Resultset ) enthält den Wert 2. Wenn SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC2 festgelegt ist, geben die Funktionen SQL_DATE, SQL_TIME und SQL_TIMESTAMP im Feld DATA_TYPE zurück, die Spalte COLUMN_SIZE enthält die Dezimalgenauigkeit für den ungefähren numerischen Typ, und die NUM_PREC_RADIX Spalte enthält den Wert 10.  
  
 Wenn alle Datentypen in einem Aufruf von **SQLGetTypeInfo**angefordert werden, enthält das von der Funktion zurückgegebene Resultset sowohl SQL_TYPE_DATE, SQL_TYPE_TIME als auch SQL_TYPE_TIMESTAMP wie in ODBC *3.x*definiert und SQL_DATE, SQL_TIME und SQL_TIMESTAMP wie in ODBC *2.x*definiert.  
  
 Aufgrund der Art und Weise, wie der ODBC *3.x* Driver Manager die Zuordnung der Datentypen Datum, Uhrzeit und Zeitstempel durchführt, ODBC *3.x-Treiber* müssen nur **#defines** von 91, 92 und 93 für die Datentypen Datum, Uhrzeit und Zeitstempel C erkennen, die in den *TargetType-Argumenten* von **SQLBindCol** und **SQLGetData** oder dem *ValueType-Argument* von **SQLBindParameter**eingegeben wurden, und nur **#defines** von 91, 92 und 93 für die im *ParameterType-Argument* von **SQLBindParameter** oder dem *DataType-Argument* von **SQL.00** Weitere Informationen finden Sie unter [Datetime-Datentypänderungen](../../../odbc/reference/develop-app/datetime-data-type-changes.md).
