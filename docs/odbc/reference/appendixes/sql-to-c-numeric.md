---
title: 'SQL zu C: numerisch | Microsoft-Dokumentation'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36b24da4023a96b686742416b83bb5790e129278
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296410"
---
# <a name="sql-to-c-numeric"></a>SQL zu C: numerisch

Die Bezeichner für die numerischen ODBC-SQL-Datentypen lauten wie folgt:

- SQL_DECIMAL  
- SQL_BIGINT  
- SQL_NUMERIC  
- SQL_REAL  
- SQL_TINYINT  
- SQL_FLOAT  
- SQL_SMALLINT  
- SQL_DOUBLE SQL_INTEGER  

In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die numerische SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typbezeichner|Test|**Targetvalueptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Zeichen Byte Länge < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Zeichen Länge < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_NUMERIC|Konvertierte Daten ohne Abschneiden [a]<br /><br /> Mit Abschneiden von Bruch Ziffern konvertierte Daten [a]<br /><br /> Die Konvertierung von Daten würde zu einem Verlust ganzer (im Gegensatz zu Bruch Ziffern) Ziffern führen. [a]|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des C-Datentyps<br /><br /> Größe des C-Datentyps<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE|Die Daten befinden sich innerhalb des Bereichs des Datentyps, in den die Zahl konvertiert wird [a]<br /><br /> Die Daten liegen außerhalb des Bereichs des Datentyps, in den die Zahl konvertiert wird [a]|Daten<br /><br /> Nicht definiert|Größe des C-Datentyps<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 22003|  
|SQL_C_BIT|Daten sind 0 oder 1 [a]<br /><br /> Daten sind größer als 0 (null), kleiner als 2, nicht gleich 1 [a]<br /><br /> Daten sind kleiner als 0 (null) oder größer oder gleich 2 [a]|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|1 [b]<br /><br /> 1 [b]<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_BINARY|Byte Länge der Daten <= *BufferLength*<br /><br /> Byte Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 22003|  
|SQL_C_INTERVAL_MONTH [c] SQL_C_INTERVAL_YEAR [c] SQL_C_INTERVAL_DAY [c] SQL_C_INTERVAL_HOUR [c] SQL_C_INTERVAL_MINUTE [c] SQL_C_INTERVAL_SECOND [c]|Nicht gekürzte Daten<br /><br /> Teil Bruchteile abgeschnitten<br /><br /> Ganzer Teil der Zahl abgeschnitten|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_INTERVAL_YEAR_TO_MONTH SQL_C_INTERVAL_DAY_TO_HOUR SQL_C_INTERVAL_DAY_TO_MINUTE SQL_C_INTERVAL_DAY_TO_SECOND SQL_C_INTERVAL_HOUR_TO_MINUTE SQL_C_INTERVAL_HOUR_TO_SECOND|Ganzer Teil der Zahl abgeschnitten|Nicht definiert|Nicht definiert|22015|  
  
 [a] der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **targetvalueptr* die Größe des C-Datentyps ist.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyps.  
  
 [c] Diese Konvertierung wird nur für die genauen numerischen Datentypen (SQL_DECIMAL, SQL_NUMERIC, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER und SQL_BIGINT) unterstützt. Sie wird für die ungefähren numerischen Datentypen (SQL_REAL, SQL_FLOAT oder SQL_DOUBLE) nicht unterstützt.  

## <a name="sql_c_numeric-and-sqlsetdescfield"></a>SQL_C_NUMERIC und SQLSetDescField

 Die [SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md) ist erforderlich, um eine manuelle Bindung mit SQL_C_NUMERIC Werten auszuführen. (Beachten Sie, dass SQLSetDescField in ODBC 3,0 hinzugefügt wurde.) Zum Ausführen einer manuellen Bindung müssen Sie zuerst das Deskriptorhandle erhalten.  

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
