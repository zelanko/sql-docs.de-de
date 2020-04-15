---
title: 'SQL zu C: Numerisch | Microsoft Docs'
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296410"
---
# <a name="sql-to-c-numeric"></a>SQL zu C: numerisch

Die Bezeichner für die numerischen ODBC SQL-Datentypen lauten wie folgt:

- SQL_DECIMAL  
- SQL_BIGINT  
- SQL_NUMERIC  
- SQL_REAL  
- SQL_TINYINT  
- SQL_FLOAT  
- SQL_SMALLINT  
- SQL_DOUBLE SQL_INTEGER  

Die folgende Tabelle zeigt die ODBC C-Datentypen, in die numerische SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typ-Idonid|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Zeichenbytelänge < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu bruchstückhzu- ) Ziffern < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu fraktionierten) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Zeichenlänge < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu bruchstückhzu- ) Ziffern < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu fraktionierten) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_NUMERIC|Daten ohne Abschneiden konvertiert[a]<br /><br /> Daten, die mit Abschneiden von Bruchziffern konvertiert werden[a]<br /><br /> Die Konvertierung von Daten würde zu einem Verlust ganzer (im Gegensatz zu fraktionierten) Ziffern führen[a]|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des Datentyps C<br /><br /> Größe des Datentyps C<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE|Die Daten liegen im Bereich des Datentyps, in den die Nummer konvertiert wird[a]<br /><br /> Die Daten liegen außerhalb des Bereichs des Datentyps, in den die Nummer konvertiert wird[a]|Daten<br /><br /> Nicht definiert|Größe des Datentyps C<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_BIT|Die Daten sind 0 oder 1[a]<br /><br /> Die Daten sind größer als 0, kleiner als 2 und nicht gleich 1[a]<br /><br /> Die Daten sind kleiner als 0 oder größer oder gleich 2[a]|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|1[b]<br /><br /> 1[b]<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_BINARY|Bytelänge der Daten <= *BufferLength*<br /><br /> Byte-Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_INTERVAL_MONTH[c] SQL_C_INTERVAL_YEAR[c] SQL_C_INTERVAL_DAY[c] SQL_C_INTERVAL_HOUR[c] SQL_C_INTERVAL_MINUTE[c] SQL_C_INTERVAL_SECOND[c]|Daten nicht abgeschnitten<br /><br /> Bruchsekunden-Teil abgeschnitten<br /><br /> Ganzer Teil der Anzahl abgeschnitten|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_INTERVAL_YEAR_TO_MONTH SQL_C_INTERVAL_DAY_TO_HOUR SQL_C_INTERVAL_DAY_TO_MINUTE SQL_C_INTERVAL_DAY_TO_SECOND SQL_C_INTERVAL_HOUR_TO_MINUTE SQL_C_INTERVAL_HOUR_TO_SECOND|Ganzer Teil der Anzahl abgeschnitten|Nicht definiert|Nicht definiert|22015|  
  
 [a] Der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **TargetValuePtr* die Größe des C-Datentyps ist.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyps.  
  
 [c] Diese Konvertierung wird nur für die genauen numerischen Datentypen (SQL_DECIMAL, SQL_NUMERIC, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER und SQL_BIGINT) unterstützt. Sie wird für die ungefähren numerischen Datentypen (SQL_REAL, SQL_FLOAT oder SQL_DOUBLE) nicht unterstützt.  

## <a name="sql_c_numeric-and-sqlsetdescfield"></a>SQL_C_NUMERIC und SQLSetDescField

 Die [SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md) ist erforderlich, um eine manuelle Bindung mit SQL_C_NUMERIC Werten durchzuführen. (Beachten Sie, dass SQLSetDescField in ODBC 3.0 hinzugefügt wurde.) Um eine manuelle Bindung durchzuführen, müssen Sie zuerst das Deskriptor-Handle abrufen.  

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
