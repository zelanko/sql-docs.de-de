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
ms.openlocfilehash: 1cb92afa9467717b8a589ddbcaee4ab8a5a529f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130089"
---
# <a name="datetime-data-types"></a>datetime-Datentypen
In ODBC *3. x*wurden die Bezeichner für die SQL-Datentypen date, Time und Zeitstempel von SQL_DATE, SQL_TIME und SQL_TIMESTAMP (mit Instanzen von **#define** in der Header Datei 9, 10 und 11) in SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP (mit Instanzen von **#define** in der Header Datei 91, 92 und 93) geändert. Die entsprechenden C-Typbezeichner wurden von SQL_C_DATE, SQL_C_TIME und SQL_C_TIMESTAMP in SQL_C_TYPE_DATE, SQL_C_TYPE_TIME bzw. SQL_C_TYPE_TIMESTAMP geändert, und die Instanzen von **#define** wurden entsprechend geändert.  
  
 Die Spaltengröße und die Dezimalstellen, die für die SQL-datetime-Datentypen in ODBC *3. x* zurückgegeben werden, sind identisch mit der für Sie in ODBC *2. x*zurückgegebenen Genauigkeit und Skalierung. Diese Werte unterscheiden sich von den Werten in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE Deskriptor. (Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktett-Länge übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.)  
  
 Diese Änderungen wirken sich auf **SQLDescribeCol**, **SQLDescribeParam**und **SQLColAttribute**aus. **SQLBindCol**, **SQLBindParameter**und **SQLGetData**; und **SQLColumns**, **SQLGetTypeInfo**, **sqlprocedurecolumschlag NS**, **SQLStatistics**und **SQLSpecialColumns**.  
  
 Ein ODBC *3. x* -Treiber verarbeitet die im vorherigen Absatz aufgelisteten Funktionsaufrufe entsprechend der Einstellung des SQL_ATTR_ODBC_VERSION Environment-Attributs. Für **SQLColumns**, **SQLGetTypeInfo**, **sqlprocedurecolrens**, **SQLSpecialColumns**und **SQLStatistics**geben die Funktionen SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP im data_type Feld zurück, wenn SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 festgelegt ist. Die COLUMN_SIZE Spalte (in dem von **SQLColumns**, **SQLGetTypeInfo**, **sqlprocedurecolumschlag**und **SQLSpecialColumns**zurückgegebenen Resultset) enthält die binäre Genauigkeit für den ungefähren numerischen Typ. Die NUM_PREC_RADIX Spalte (im Resultset, das von **SQLColumns**, **SQLGetTypeInfo**und **sqlprocedurecolumschlag**zurückgegeben wurde) enthält den Wert 2. Wenn SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC2 festgelegt ist, geben die Funktionen SQL_DATE, SQL_TIME und SQL_TIMESTAMP im Feld data_type zurück, die Spalte COLUMN_SIZE enthält die Dezimal Genauigkeit für den ungefähren numerischen Typ und die NUM_PREC_RADIX Spalte. enthält den Wert 10.  
  
 Wenn alle Datentypen beim Aufrufen von **SQLGetTypeInfo**angefordert werden, enthält das Resultset, das von der Funktion zurückgegeben wird, sowohl SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP, wie in ODBC *3. x*definiert, als auch SQL_DATE, SQL_TIME und SQL_TIMESTAMP, wie in ODBC *2. x*definiert.  
  
 Aufgrund der Art und Weise, wie der ODBC *3. x* -Treiber-Manager die Zuordnung der Datums-, Uhrzeit-und Zeitstempel-Datentypen durchführt, müssen ODBC *3. x* -Treiber nur **#defines** von 91 erkennen. 92 und 93 für die Datentypen "Date", "Time" und "Zeitstempel C", die in den *TargetType* -Argumenten von **SQLBindCol** und **SQLGetData** oder dem *ValueType* -Argument von **SQLBindParameter**eingegeben wurden, und müssen nur **#defines** von 91, 92 und 93 für die im *ParameterType* -Argument von **SQLBindParameter** oder das *DataType* -Argument von **SQLGetTypeInfo**. Weitere Informationen finden Sie unter [DateTime-Datentyp Änderungen](../../../odbc/reference/develop-app/datetime-data-type-changes.md).
