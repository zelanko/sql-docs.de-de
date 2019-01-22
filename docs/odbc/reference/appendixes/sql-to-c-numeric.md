---
title: 'SQL zu C: Numerische | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC], numeric
- numeric data type [ODBC], converting
- converting data from SQL to C types [ODBC], numeric
ms.assetid: 76f8b5d5-4bd0-4dcb-a90a-698340e0d36e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9abd536110222f8e30a781b6d648402335837f61
ms.sourcegitcommit: 480961f14405dc0b096aa8009855dc5a2964f177
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2019
ms.locfileid: "54420005"
---
# <a name="sql-to-c-numeric"></a>SQL zu C: Numerisch

Der Bezeichner für die numerische ODBC-SQL-Datentypen sind die folgenden:

- SQL_DECIMAL  
- SQL_BIGINT  
- SQL_NUMERIC  
- SQL_REAL  
- SQL_TINYINT  
- SQL_FLOAT  
- SQL_SMALLINT  
- SQL_DOUBLE SQL_INTEGER  

Die folgende Tabelle zeigt die ODBC-C-Datentypen, die in denen numerische SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typ-ID|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Zeichen-Byte-Länge < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) > = *Pufferlänge*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Länge der Daten in bytes<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Zeichenlänge < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) > = *Pufferlänge*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_NUMERIC|Daten konvertiert werden, ohne Abschneiden [a]<br /><br /> Daten konvertiert werden, mit dem Abschneiden der Dezimalstellen [a]<br /><br /> Konvertierung von Daten führt zu Verlust insgesamt (im Gegensatz zu Bruch) Ziffern [a]|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Anzahl der C-Datentyp<br /><br /> Anzahl der C-Datentyp<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE|Daten sind innerhalb des Bereichs des Datentyps, der die Zahl konvertiert wird wird [a]<br /><br /> Daten sind außerhalb des Bereichs des Datentyps, der die Zahl konvertiert wird wird [a]|Daten<br /><br /> Nicht definiert|Anzahl der C-Datentyp<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_BIT|Daten sind 0 oder 1 [a]<br /><br /> Daten ist größer als 0 ist, kleiner als 2, und nicht gleich-1 [a]<br /><br /> Daten ist kleiner als 0 oder größer als oder gleich 2 [a]|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|1[b]<br /><br /> 1[b]<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_BINARY|Die Bytelänge der Daten < = *Pufferlänge*<br /><br /> Die Bytelänge der Daten > *Pufferlänge*|Daten<br /><br /> Nicht definiert|Länge der Daten<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_INTERVAL_MONTH [c] SQL_C_INTERVAL_YEAR [c] SQL_C_INTERVAL_DAY [c] [c]-SQL_C_INTERVAL_HOUR SQL_C_INTERVAL_MINUTE [c] SQL_C_INTERVAL_SECOND [c]|Daten wurden nicht abgeschnitten.<br /><br /> Bereich der Sekundenbruchteile abgeschnitten<br /><br /> Gesamte Teil der Zahl, die abgeschnitten|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Länge der Daten in bytes<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_INTERVAL_YEAR_TO_MONTH SQL_C_INTERVAL_DAY_TO_HOUR SQL_C_INTERVAL_DAY_TO_MINUTE SQL_C_INTERVAL_DAY_TO_SECOND SQL_C_INTERVAL_HOUR_TO_MINUTE SQL_C_INTERVAL_HOUR_TO_SECOND|Gesamte Teil der Zahl, die abgeschnitten|Nicht definiert|Nicht definiert|22015|  
  
 [a] den Wert der *Pufferlänge* für diese Konvertierung ignoriert wird. Der Treiber setzt voraus, dass die Größe des **TargetValuePtr* ist die Größe der C-Datentyp.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyp.  
  
 [c++] diese Konvertierung wird nur für die genaue numerische Datentypen (SQL_DECIMAL, SQL_NUMERIC, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER und SQL_BIGINT) unterstützt. Es wird für die ungefähre numerische Datentypen (SQL_REAL, SQL_FLOAT oder SQL_DOUBLE) nicht unterstützt.  

## <a name="sqlcnumeric-and-sqlsetdescfield"></a>SQL_C_NUMERIC und SQLSetDescField

 Die [SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md) ist erforderlich, um die manuelle Bindung mit SQL_C_NUMERIC Werten auszuführen. (Beachten Sie, dass SQLSetDescField ODBC 3.0 hinzugefügt wurde.) Zum manuellen Bindung durchführen zu können, müssen Sie zunächst die Deskriptorhandles abrufen.  

```cpp
if (fCType == SQL_C_NUMERIC) {   
   // special processing required for NUMERIC to get right scale & precision  
   // Modify the fields in the implicit application parameter descriptor  
   SQLHDESC hdesc=NULL;  
  
   // Use SQL_ATTR_APP_ROW_DESC for calls to SQLBindCol()  
   // Use SQL_ATTR_APP_PARAM_DESC for calls to SQLBindParameter()  
   //  
   // retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_ROW_DESC, &hdesc, 0, NULL);  
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_PARAM_DESC, &hdesc, 0, NULL);  
   if (!ODBC_CALL_SUCCESS(retcode)) {  
      printf ("\nSQLGetStmtAttr failed");  
      i = 1;  
      sqlstate[7] = '\0';  
      while (SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, sqlstate, &NativeError, wrkbuf, sizeof(wrkbuf), &len) != SQL_NO_DATA) {  
         printf("\niTestCase = %d Failed...Precision = %d, Scale = %d\nNativeError=%d, State=%s, \n  Message=%s",   
            iTestCase, Precision, Scale, NativeError, sqlstate, wrkbuf);  
         i++;  
      }  
      continue;  
   }  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_TYPE, (SQLPOINTER) SQL_C_NUMERIC, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_PRECISION, (SQLPOINTER)num.precision, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_SCALE, (SQLPOINTER)num.scale, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_DATA_PTR, (SQLPOINTER) &(num), sizeof(num));  
```
