---
title: SQLGetInfo (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: fbc39e3d-67d9-4331-bf5f-76dbd74c4c45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 015ea45d1383e6813973aeb1e4c86451a506a2aa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63213330"
---
# <a name="sqlgetinfo-visual-foxpro-odbc-driver"></a>SQLGetInfo (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Vollständig  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Gibt allgemeine Informationen zu den Visual FoxPro-ODBC-Treiber und ein Verbindungshandle zugeordnete Datenquelle *Hdbc*. Die folgende Liste enthält den Rückgabewert, die von der Visual FoxPro-ODBC-Treiber für die einzelnen *fInfoType* Argument und Kommentare in Bezug auf die zurückgegebenen Werte.  
  
 Weitere Informationen finden Sie unter [SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md) in die *ODBC Programmer's Reference*.  
  
## <a name="a"></a>A  
 SQL_ACCESSIBLE_PROCEDURES returns 'N'.  
  
 SQL_ACCESSIBLE_TABLES gibt "Y" zurück.  
  
 SQL_ACTIVE_CONNECTIONS returns 0.  
  
 SQL_ACTIVE_STATEMENTS gibt 0 zurück.  
  
 SQL_ALTER_TABLE gibt SQL_AT_ADD_COLUMN oder SQL_AT_DROP_COLUMN zurück.  
  
## <a name="b"></a>B  
 SQL_BOOKMARK_PERSISTENCE gibt SQL_BP_SCROLL zurück.  
  
## <a name="c"></a>c  
 SQL_COLUMN_ALIAS gibt "Y" zurück.  
  
 SQL_CONCAT_NULL_BEHAVIOR gibt SQL_CB_NULL zurück.  
  
 SQL_CONVERT_BIGINT gibt 0 zurück. Der Visual FoxPro-ODBC-Treiber unterstützt keine *BigInt*.  
  
 SQL_CONVERT_BINARY gibt 0 zurück.  
  
 SQL_CONVERT_BIT gibt 0 zurück.  
  
 SQL_CONVERT_CHAR gibt 0 zurück.  
  
 SQL_CONVERT_DATE returns 0.  
  
 SQL_CONVERT_DECIMAL returns 0.  
  
 SQL_CONVERT_DOUBLE returns 0.  
  
 SQL_CONVERT_FLOAT returns 0.  
  
 SQL_CONVERT_INTEGER returns 0.  
  
 SQL_CONVERT_LONGVARBINARY returns 0.  
  
 SQL_CONVERT_LONGVARCHAR returns 0.  
  
 SQL_CONVERT_NUMERIC returns 0.  
  
 SQL_CONVERT_REAL returns 0.  
  
 SQL_CONVERT_SMALLINT gibt 0 zurück.  
  
 SQL_CONVERT_TIME returns 0.  
  
 SQL_CONVERT_TIMESTAMP returns 0.  
  
 SQL_CONVERT_TINYINT gibt 0 zurück.  
  
 SQL_CONVERT_VARBINARY returns 0.  
  
 SQL_CONVERT_VARCHAR gibt 0 zurück.  
  
 SQL_CONVERT_FUNCTIONS returns 0.  
  
 SQL_CORRELATION_NAME gibt SQL_CN_ANY zurück.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR gibt SQL_CB_PRESERVE zurück.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR gibt SQL_CB_PRESERVE zurück.  
  
## <a name="d"></a>D  
 SQL_DATA_SOURCE_NAME gibt den Wert, der als DSN zum übergeben [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), oder [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md); eine leere Zeichenfolge zurück, wenn keine DSN angegeben ist.  
  
 SQL_DATA_SOURCE_READ_ONLY returns 'N'.  
  
 SQL_DATABASE_NAME gibt einen vollständigen UNC-Pfad der aktuellen Datenbank zurück, wenn die Datenquelle ist eine [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md). Wenn die Datenquelle in einem Verzeichnis verbunden [Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md), die Funktion gibt den Pfad zu dem Verzeichnis zurück.  
  
 SQL_DBMS_NAME returns "Visual FoxPro".  
  
 SQL_DBMS_VER returns "03.00.0000".  
  
 SQL_DEFAULT_TXN_ISOLATION gibt SQL_TXN_READ_COMMITTED zurück. Unsauberes lesen, sind nicht möglich, aber nicht wiederholbarer Lesevorgänge und Phantome geben sind möglich.  
  
 SQL_DRIVER_HDBC wird vom Treiber-Manager implementiert werden.  
  
 SQL_DRIVER_HENV wird vom Treiber-Manager implementiert werden.  
  
 SQL_DRIVER_HLIB wird vom Treiber-Manager implementiert werden.  
  
 SQL_DRIVER_HSTMT wird vom Treiber-Manager implementiert werden.  
  
 SQL_DRIVER_NAME returns "vfpodbc.dll".  
  
 SQL_DRIVER_ODBC_VER gibt "02.50" (SQL_SPEC_MAJOR, SQL_SPEC_MINOR) zurück.  
  
 SQL_DRIVER_VER returns "01.00.0000".  
  
## <a name="e"></a>E  
 Gibt zurück, SQL_EXPRESSIONS_IN_ORDERBY ' n '.  
  
## <a name="f"></a>V  
 SQL_FETCH_DIRECTION zurückgegeben:  
  
-   SQL_FD_FETCH_NEXT  
  
-   SQL_FD_FETCH_FIRST  
  
-   SQL_FD_FETCH_LAST  
  
-   SQL_FD_FETCH_PRIOR  
  
-   SQL_FD_FETCH_ABSOLUTE  
  
-   SQL_FD_FETCH_RELATIVE  
  
-   SQL_FD_FETCH_BOOKMARK.  
  
 SQL_FILE_USAGE SQL_FILE_QUALIFIER sowohl für Datenbank (DBC-Datei) zurückgegeben und kostenlos Tabelle Datenquellen (DBF-Datei).  
  
## <a name="g-h"></a>G-H  
 SQL_GETDATA_EXENSIONS returns:  
  
-   SQL_GD_ANY_COLUMN  
  
-   SQL_GD_ANY_BLOCK  
  
-   SQL_GD_ANY_BOUND  
  
-   SQL_GD_ANY_ORDER  
  
 SQL_GROUP_BY gibt SQL_GB_NO_RELATION zurück.  
  
## <a name="i-j"></a>ICH + J  
 SQL_IDENTIFIER_CASE gibt SQL_IC_MIXED zurück.  
  
 SQL_IDENTIFIER_QUOTE_CHAR returns `.  
  
## <a name="k"></a>K  
 SQL_KEYWORDS returns "".  
  
## <a name="l"></a>L  
 SQL_LIKE_ESCAPE_CLAUSE returns 'N'.  
  
 SQL_LOCK_TYPES gibt SQL_LCK_NO_CHANGE zurück.  
  
## <a name="m"></a>M  
 SQL_MAX_BINARY_LITERAL_LEN gibt 0 zurück.  
  
 SQL_MAX_CHAR_LITERAL_LEN gibt 254 zurück.  
  
 SQL_MAX_COLUMN_NAME_LEN returns 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY gibt 16 zurück.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY returns 16.  
  
 SQL_MAX_COLUMNS_IN_INDEX gibt 0 zurück.  
  
 SQL_MAX_COLUMNS_IN_SELECT gibt 254 zurück.  
  
 SQL_MAX_COLUMNS_IN_TABLE gibt 254 zurück.  
  
 SQL_MAX_CURSOR_NAME_LEN gibt 254 zurück.  
  
 SQL_MAX_INDEX_SIZE returns 0.  
  
 SQL_MAX_OWNER_NAME_LEN returns 0.  
  
 SQL_MAX_PROCEDURE_NAME_LEN returns 0. Der Visual FoxPro-ODBC-Treiber lässt keine direkten Zugriff auf Visual FoxPro-gespeicherte Prozeduren.  
  
 SQL_MAX_QUALIFIER_NAME_LEN gibt die Pfadlänge des Betriebssystems zurück.  
  
 SQL_MAX_ROW_SIZE returns 254^2.  
  
 Gibt zurück, SQL_MAX_ROW_SIZE_INCLUDES_LONG ' n '.  
  
 SQL_MAX_STATEMENT_LEN gibt 8192 zurück.  
  
 SQL_MAX_TABLE_NAME_LEN returns 128.  
  
 SQL_MAX_TABLES_IN_SELECT returns 16.  
  
 SQL_MAX_USER_NAME_LEN returns 0.  
  
 SQL_MULT_RESULT_SETS gibt "Y" zurück.  
  
 SQL_MULTIPLE_ACTIVE_TXN returns 'Y'. Mehrere Verbindungen können mehrere Transaktionen gleichzeitig geöffnet haben.  
  
## <a name="n"></a>N  
 SQL_NEED_LONG_DATA_LEN returns 'N'.  
  
 SQL_NON_NULLABLE_COLUMNS gibt SQL_NNC_NON_NULL zurück.  
  
 SQL_NULL_COLLATION gibt SQL_NC_LOW zurück.  
  
 SQL_NUMERIC_FUNCTIONS gibt alle Funktionen außer SQL_FN_NUM_POWER, die von der Visual FoxPro-ODBC-Treiber nicht unterstützt wird. Die folgenden Funktionen werden unterstützt:  
  
-   SQL_FN_NUM_ABS  
  
-   SQL_FN_NUM_ACOS  
  
-   SQL_FN_NUM_ASIN  
  
-   SQL_FN_NUM_ATAN  
  
-   SQL_FN_NUM_ATAN2  
  
-   SQL_FN_NUM_CELING  
  
-   SQL_FN_NUM_COS  
  
-   SQL_FN_NUM_COT  
  
-   SQL_FN_NUM_DEGREES  
  
-   SQL_FN_NUM_EXP  
  
-   SQL_FN_NUM_FLOOR  
  
-   SQL_FN_NUM_LOG  
  
-   SQL_FN_NUM_LOG10  
  
-   SQL_FN_NUM_MOD  
  
-   SQL_FN_NUM_PI  
  
-   SQL_FN_NUM_RADIANS  
  
-   SQL_FN_NUM_RAND  
  
-   SQL_FN_NUM_ROUND  
  
-   SQL_FN_NUM_SIGN  
  
-   SQL_FN_NUM_SIN  
  
-   SQL_FN_NUM_SQRT  
  
-   SQL_FN_NUM_TAN  
  
## <a name="o"></a>O  
 SQL_ODBC_API_CONFORMANCE gibt SQL_OAC_LEVEL1 zurück.  
  
 SQL_ODBC_SAG_CLI_CONFORMANCE returns SQL_OSCC_COMPLIANT.  
  
 SQL_ODBC_SQL_CONFORMANCE returns SQL_OSC_MINIMUM. Minimale SQL-Syntax wird unterstützt.  
  
 SQL_ODBC_SQL_OPT_IEF returns "N".  
  
 SQL_ODBC_VER wird vom Treiber-Manager implementiert werden.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT returns "N".  
  
 SQL_OUTER_JOINS gibt "N".  
  
 SQL_OWNER_TERM gibt "". Der Visual FoxPro-ODBC-Treiber unterstützt die Besitzer für seine Objekte nicht.  
  
 SQL_OWNER_USAGE gibt 0 zurück. Der Visual FoxPro-ODBC-Treiber unterstützt die Besitzer für seine Objekte nicht.  
  
## <a name="p"></a>P  
 SQL_POS_OPERATIONS gibt SQL_POS_POSITION zurück.  
  
 SQL_POSITIONED_STATEMENTS gibt 0 zurück.  
  
 SQL_PROCEDURE_TERM returns "".  
  
 Gibt zurück, SQL_PROCEDURES ' n '.  
  
## <a name="q"></a>Q  
 SQL_QUALIFIER_LOCATION gibt SQL_QL_START zurück.  
  
 SQL_QUALIFIER_NAME_SEPARATOR gibt "!" oder "\\". Das Trennzeichen zwischen Datenbank und Tabelle ist '!' für Datenquellen verbunden [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md), und "\\" für Datenquellen, die Verzeichnisse sind [kostenlose Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 SQL_QUALIFIER_TERM gibt "Datenbank" oder "Directory" zurück. Der Qualifizierer für Datenquellen verbunden ist "database" [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md), und "Verzeichnis" für Datenquellen, die Verzeichnisse sind [kostenlose Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 SQL_QUALIFIER_USAGE wird SQL_QU_PRIVILEGE_DEFINITION nicht unterstützt werden. Es gibt SQL_QU_DML_STATEMENT oder SQL_QU_TABLE_DEFINITION zurück.  
  
 SQL_QUOTED_IDENTIFIER_CASE gibt SQL_IC_MIXED zurück.  
  
## <a name="r"></a>R  
 SQL_ROW_UPDATES returns "N". Der Visual FoxPro-ODBC-Treiber unterstützt nur statische und forward Cursor.  
  
## <a name="s"></a>S  
 SQL_SCROLL_CONCURRENCY gibt SQL_SCCO_READ_ONLY zurück.  
  
 SQL_SCROLL_OPTIONS gibt SQL_SO_STATIC oder SQL_SO_READONLY zurück.  
  
 Gibt zurück, SQL_SEARCH_PATTERN_ESCAPE "\\".  
  
 SQL_SERVER_NAME returns "".  
  
 SQL_SPECIAL_CHARACTERS returns "~@#$%^".  
  
 SQL_STATIC_SENSITIVITY gibt 0 zurück. Der Visual FoxPro-ODBC-Treiber ist nicht mit Feldern fester Breite Updates unterstützt.  
  
 SQL_STRING_FUNCTIONS unterstützt keine SQL_FN_STR_INSERT SQL_FN_STR_LOCATE, SQL_FN_STR_LOCATE_2 oder SQL_FN_STR_SOUNDEX.  
  
 Wird zurückgegeben:  
  
-   SQL_FN_STR_ASCII  
  
-   SQL_FN_STR_CHAR  
  
-   SQL_FN_STR_CONCAT  
  
-   SQL_FN_STR_DIFFERENCE  
  
-   SQL_FN_STR_LCASE  
  
-   SQL_FN_STR_LEFT  
  
-   SQL_FN_STR_LENGTH  
  
-   SQL_FN_STR_LTRIM  
  
-   SQL_FN_STR_REPEAT  
  
-   SQL_FN_STR_REPLACE  
  
-   SQL_FN_STR_RIGHT  
  
-   SQL_FN_STR_RTRIM  
  
-   SQL_FN_STR_SUBSTRING  
  
-   SQL_FN_STR_UCASE  
  
-   SQL_FN_STR_SPACE.  
  
 SQL_SUBQUERIES zurückgegeben:  
  
-   SQL_SQ_CORRELATED_SUBQUERIES  
  
-   SQL_SQ_COMPARISON  
  
-   SQL_SQ_EXISTS  
  
-   SQL_SQ_IN  
  
-   SQL_SQ_QUANTIFIED.  
  
 SQL_SYSTEM_FUNCTIONS returns:  
  
-   SQL_FN_SYS_DBNAME  
  
-   SQL_FN_SYS_IFNULL  
  
 aber nicht:  
  
-   SQL_FN_SYS_USERNAME  
  
## <a name="t"></a>T  
 SQL_TABLE_TERM gibt "Table" zurück.  
  
 SQL_TIMEDATE_ADD_INTERVALS zurückgegeben:  
  
-   SQL_FN_TSI_ SECOND  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 aber nicht:  
  
-   SQL_FN_TSI_FRAC_SECOND  
  
-   SQL_FN_TSI_WEEK  
  
-   SQL_FN_TSI_QUARTER  
  
 SQL_TIMEDATE_DIFF_INTERVALS zurückgegeben:  
  
-   SQL_FN_TSI_ SECOND  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 SQL_TIMEDATE_FUNCTIONS unterstützt keine SQL_FN_TD_QUARTER SQL_FN_TD_TIMESTAMPADD, SQL_FN_TD_DAYOFYEAR oder SQL_FN_TD_WEEK.  
  
 Wird zurückgegeben:  
  
-   SQL_FN_TD_CURDATE  
  
-   SQL_FN_TD_CURTIME  
  
-   SQL_FN_TD_DAYNAME  
  
-   SQL_FN_TD_DAYOFMONTH  
  
-   SQL_FN_TD_DAYOFWEEK  
  
-   SQL_FN_TD_HOUR  
  
-   SQL_FN_TD_MINUTE  
  
-   SQL_FN_TD_MONTH  
  
-   SQL_FN_TD_MONTHNAME  
  
-   SQL_FN_TD_NOW  
  
-   SQL_FN_TD_SECOND  
  
-   SQL_FN_TD_TIMESTAMPDIFF  
  
-   SQL_FN_TD_YEAR .  
  
 SQL_TXN_CAPABLE returns SQL_TC_DML.  
  
 SQL_TXN_ISOLATION_OPTION returns SQL_TXN_READ_COMMITTED.  
  
## <a name="u-z"></a>U-Z  
 SQL_UNION gibt SQL_U_UNION oder SQL_U_UNION_ALL zurück.  
  
 Gibt zurück, SQL_USER_NAME \<leer >.
