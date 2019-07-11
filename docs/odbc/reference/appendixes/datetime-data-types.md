---
title: DateTime-Datentypen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 13cb433da64b78a8b5e70f28642fd576f6803ed5
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792587"
---
# <a name="datetime-data-types"></a>datetime-Datentypen
In ODBC *3.x*, die Bezeichner für date, Time und Timestamp SQL-Datentypen von SQL_DATE, SQL_TIME und SQL_TIMESTAMP geändert haben (mit Instanzen von **#define** in der Headerdatei, 9, 10 und 11), SQL_ TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP (mit Instanzen von **#define** in der Headerdatei 91, 92 und 93) an. Der entsprechenden IDs wurden geändert aus SQL_C_DATE SQL_C_TIME und SQL_C_TIMESTAMP SQL_C_TYPE_DATE SQL_C_TYPE_TIME und SQL_C_TYPE_TIMESTAMP bzw. C-Typ, und die Instanzen der **#define** wurden geändert entsprechend.  
  
 Die Spaltengröße und die Dezimalstellen zurückgegeben, für die SQL-Datetime-Datentypen in ODBC *3.x* sind identisch mit der Genauigkeit und Dezimalstellenanzahl für diese zurückgegeben, in ODBC *2.x*. Diese Werte unterscheiden sich die Werte in die deskriptorfelder SQL_DESC_PRECISION und SQL_DESC_SCALE zur Verfügung. (Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Die Datentypen.)  
  
 Diese Änderungen wirken sich auf **SQLDescribeCol**, **SQLDescribeParam**, und **SQLColAttributes**; **SQLBindCol**, **SQLBindParameter**, und **SQLGetData**; und **SQLColumns**, **SQLGetTypeInfo** , **SQLProcedureColumns**, **SQLStatistics**, und **SQLSpecialColumns**.  
  
 ODBC *3.x* Treiber verarbeitet, ruft die Funktion, die im vorherigen Absatz gemäß der Einstellung des umgebungsattributs SQL_ATTR_ODBC_VERSION aufgeführt. Für **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLSpecialColumns**, und **SQLStatistics** , wenn SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 fest, die Funktionen, die Rückgabe SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP in das Feld "DATA_TYPE" festgelegt ist. Die COLUMN_SIZE-Spalte (im Resultset zurückgegebenes **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, und **SQLSpecialColumns**) enthält die Binary-Genauigkeit für den ungefähren numerischen Typ an. Die Spalte NUM_PREC_RADIX (im Resultset zurückgegebenes **SQLColumns**, **SQLGetTypeInfo**, und **SQLProcedureColumns**) den Wert 2 enthält. Wenn SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2 und dann die Funktionen return SQL_DATE, SQL_TIME und SQL_TIMESTAMP in das Feld "DATA_TYPE" festgelegt ist, enthält die COLUMN_SIZE-Spalte die dezimale Genauigkeit für den ungefähren numerischen Typ und die Spalte NUM_PREC_RADIX enthält einen Wert von 10.  
  
 Wenn alle Datentypen werden in einem Aufruf von angefordert **SQLGetTypeInfo**, das von der Funktion zurückgegebene Resultset enthält sowohl SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP gemäß ODBC *3.x*, und SQL_DATE, SQL_TIME und SQL_TIMESTAMP gemäß ODBC *2.x*.  
  
 Aufgrund der Verwendung der ODBC *3.x* -Treiber-Manager führt die Zuordnung der Date, Time und Timestamp-Datentypen, ODBC- *3.x* Treiber müssen nur erkennen **#defines** von 91, 92, und 93 für das Datum, Uhrzeit und Timestamp-C-Datentypen eingegeben haben, der *TargetType* Argumente **SQLBindCol** und **SQLGetData** oder  *ValueType* Argument **SQLBindParameter**, und Sie müssen nur erkennen **#defines** von 91, 92 und 93 für das Datum, Uhrzeit und Zeitstempel SQL-Datentypen in der *ParameterType* Argument **SQLBindParameter** oder *DataType* Argument **SQLGetTypeInfo**. Weitere Informationen finden Sie unter [Änderungen des Datentyps "DateTime"](../../../odbc/reference/develop-app/datetime-data-type-changes.md).
