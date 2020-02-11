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
ms.openlocfilehash: 14837bc5ba3368fbb0d33680ee1c54936ab0a224
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898849"
---
# <a name="sqlgetinfo-visual-foxpro-odbc-driver"></a>SQLGetInfo (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 1  
  
 Gibt allgemeine Informationen über den Visual FoxPro-ODBC-Treiber und die Datenquelle zurück, die einem Verbindungs Handle, *hdbc*, zugeordnet sind. Die folgende Liste zeigt den Wert, der vom Visual FoxPro-ODBC-Treiber für jedes *finfotype* -Argument zurückgegeben wird, sowie Kommentare zu den zurückgegebenen Werten.  
  
 Weitere Informationen finden Sie unter [SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md) in der *ODBC Programmer es Reference*.  
  
## <a name="a"></a>Ein  
 SQL_ACCESSIBLE_PROCEDURES gibt "N" zurück.  
  
 SQL_ACCESSIBLE_TABLES gibt "Y" zurück.  
  
 SQL_ACTIVE_CONNECTIONS gibt 0 zurück.  
  
 SQL_ACTIVE_STATEMENTS gibt 0 zurück.  
  
 SQL_ALTER_TABLE gibt entweder SQL_AT_ADD_COLUMN oder SQL_AT_DROP_COLUMN zurück.  
  
## <a name="b"></a>B  
 SQL_BOOKMARK_PERSISTENCE gibt SQL_BP_SCROLL zurück.  
  
## <a name="c"></a>C  
 SQL_COLUMN_ALIAS gibt "Y" zurück.  
  
 SQL_CONCAT_NULL_BEHAVIOR gibt SQL_CB_NULL zurück.  
  
 SQL_CONVERT_BIGINT gibt 0 zurück. *Bigint*wird vom Visual FoxPro-ODBC-Treiber nicht unterstützt.  
  
 SQL_CONVERT_BINARY gibt 0 zurück.  
  
 SQL_CONVERT_BIT gibt 0 zurück.  
  
 SQL_CONVERT_CHAR gibt 0 zurück.  
  
 SQL_CONVERT_DATE gibt 0 zurück.  
  
 SQL_CONVERT_DECIMAL gibt 0 zurück.  
  
 SQL_CONVERT_DOUBLE gibt 0 zurück.  
  
 SQL_CONVERT_FLOAT gibt 0 zurück.  
  
 SQL_CONVERT_INTEGER gibt 0 zurück.  
  
 SQL_CONVERT_LONGVARBINARY gibt 0 zurück.  
  
 SQL_CONVERT_LONGVARCHAR gibt 0 zurück.  
  
 SQL_CONVERT_NUMERIC gibt 0 zurück.  
  
 SQL_CONVERT_REAL gibt 0 zurück.  
  
 SQL_CONVERT_SMALLINT gibt 0 zurück.  
  
 SQL_CONVERT_TIME gibt 0 zurück.  
  
 SQL_CONVERT_TIMESTAMP gibt 0 zurück.  
  
 SQL_CONVERT_TINYINT gibt 0 zurück.  
  
 SQL_CONVERT_VARBINARY gibt 0 zurück.  
  
 SQL_CONVERT_VARCHAR gibt 0 zurück.  
  
 SQL_CONVERT_FUNCTIONS gibt 0 zurück.  
  
 SQL_CORRELATION_NAME gibt SQL_CN_ANY zurück.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR gibt SQL_CB_PRESERVE zurück.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR gibt SQL_CB_PRESERVE zurück.  
  
## <a name="d"></a>D  
 SQL_DATA_SOURCE_NAME gibt den als DSN an [SQLCONNECT](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)oder [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md); weiter gegebenen Wert zurück. gibt eine leere Zeichenfolge zurück, wenn kein DSN angegeben ist.  
  
 SQL_DATA_SOURCE_READ_ONLY gibt "N" zurück.  
  
 SQL_DATABASE_NAME gibt einen vollständigen UNC-Pfad zur aktuellen Datenbank zurück, wenn es sich bei der Datenquelle um eine [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md)handelt. Wenn die Datenquelle eine Verbindung mit einem Verzeichnis von [Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)herstellt, gibt die Funktion den Pfad zum Verzeichnis zurück.  
  
 SQL_DBMS_NAME gibt "Visual FoxPro" zurück.  
  
 SQL_DBMS_VER gibt "03.00.0000" zurück.  
  
 SQL_DEFAULT_TXN_ISOLATION gibt SQL_TXN_READ_COMMITTED zurück. Dirty Reads sind nicht möglich, aber nicht wiederholbare Lese-und Phantom Vorgänge sind möglich.  
  
 SQL_DRIVER_HDBC wird vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_HENV wird vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_HLIB wird vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_HSTMT wird vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_NAME gibt "vfpodbc. dll" zurück.  
  
 SQL_DRIVER_ODBC_VER gibt "02,50" (SQL_SPEC_MAJOR, SQL_SPEC_MINOR) zurück.  
  
 SQL_DRIVER_VER gibt "01.00.0000" zurück.  
  
## <a name="e"></a>E  
 SQL_EXPRESSIONS_IN_ORDERBY gibt "N" zurück.  
  
## <a name="f"></a>F  
 SQL_FETCH_DIRECTION gibt Folgendes zurück:  
  
-   SQL_FD_FETCH_NEXT  
  
-   SQL_FD_FETCH_FIRST  
  
-   SQL_FD_FETCH_LAST  
  
-   SQL_FD_FETCH_PRIOR  
  
-   SQL_FD_FETCH_ABSOLUTE  
  
-   SQL_FD_FETCH_RELATIVE  
  
-   SQL_FD_FETCH_BOOKMARK.  
  
 SQL_FILE_USAGE gibt SQL_FILE_QUALIFIER sowohl für die Datenbank (DBC-Datei) als auch für die Datenquellen für die freie Tabelle (DBF-Datei) zurück.  
  
## <a name="g-h"></a>G-H  
 SQL_GETDATA_EXENSIONS gibt Folgendes zurück:  
  
-   SQL_GD_ANY_COLUMN  
  
-   SQL_GD_ANY_BLOCK  
  
-   SQL_GD_ANY_BOUND  
  
-   SQL_GD_ANY_ORDER  
  
 SQL_GROUP_BY gibt SQL_GB_NO_RELATION zurück.  
  
## <a name="i-j"></a>I-J  
 SQL_IDENTIFIER_CASE gibt SQL_IC_MIXED zurück.  
  
 SQL_IDENTIFIER_QUOTE_CHAR gibt "zurück.  
  
## <a name="k"></a>K  
 SQL_KEYWORDS gibt "" zurück.  
  
## <a name="l"></a>L  
 SQL_LIKE_ESCAPE_CLAUSE gibt "N" zurück.  
  
 SQL_LOCK_TYPES gibt SQL_LCK_NO_CHANGE zurück.  
  
## <a name="m"></a>M  
 SQL_MAX_BINARY_LITERAL_LEN gibt 0 zurück.  
  
 SQL_MAX_CHAR_LITERAL_LEN gibt 254 zurück.  
  
 SQL_MAX_COLUMN_NAME_LEN gibt 128 zurück.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY gibt 16 zurück.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY gibt 16 zurück.  
  
 SQL_MAX_COLUMNS_IN_INDEX gibt 0 zurück.  
  
 SQL_MAX_COLUMNS_IN_SELECT gibt 254 zurück.  
  
 SQL_MAX_COLUMNS_IN_TABLE gibt 254 zurück.  
  
 SQL_MAX_CURSOR_NAME_LEN gibt 254 zurück.  
  
 SQL_MAX_INDEX_SIZE gibt 0 zurück.  
  
 SQL_MAX_OWNER_NAME_LEN gibt 0 zurück.  
  
 SQL_MAX_PROCEDURE_NAME_LEN gibt 0 zurück. Der Visual FoxPro-ODBC-Treiber lässt keinen direkten Zugriff auf gespeicherte Prozeduren von Visual FoxPro zu.  
  
 SQL_MAX_QUALIFIER_NAME_LEN gibt die maximale Länge des Betriebssystem Pfads zurück.  
  
 SQL_MAX_ROW_SIZE gibt 254 ^ 2 zurück.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG gibt "N" zurück.  
  
 SQL_MAX_STATEMENT_LEN gibt 8192 zurück.  
  
 SQL_MAX_TABLE_NAME_LEN gibt 128 zurück.  
  
 SQL_MAX_TABLES_IN_SELECT gibt 16 zurück.  
  
 SQL_MAX_USER_NAME_LEN gibt 0 zurück.  
  
 SQL_MULT_RESULT_SETS gibt "Y" zurück.  
  
 SQL_MULTIPLE_ACTIVE_TXN gibt "Y" zurück. Mehrere Verbindungen können mehrere Transaktionen gleichzeitig öffnen.  
  
## <a name="n"></a>N  
 SQL_NEED_LONG_DATA_LEN gibt "N" zurück.  
  
 SQL_NON_NULLABLE_COLUMNS gibt SQL_NNC_NON_NULL zurück.  
  
 SQL_NULL_COLLATION gibt SQL_NC_LOW zurück.  
  
 SQL_NUMERIC_FUNCTIONS gibt alle Funktionen mit Ausnahme von SQL_FN_NUM_POWER zurück, die vom Visual FoxPro-ODBC-Treiber nicht unterstützt wird. Folgende Funktionen werden unterstützt:  
  
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
  
 SQL_ODBC_SAG_CLI_CONFORMANCE gibt SQL_OSCC_COMPLIANT zurück.  
  
 SQL_ODBC_SQL_CONFORMANCE gibt SQL_OSC_MINIMUM zurück. Die minimale SQL-Syntax wird unterstützt.  
  
 SQL_ODBC_SQL_OPT_IEF gibt "N" zurück.  
  
 SQL_ODBC_VER wird vom Treiber-Manager implementiert.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT gibt "N" zurück.  
  
 SQL_OUTER_JOINS gibt "N" zurück.  
  
 SQL_OWNER_TERM gibt "" zurück. Der Visual FoxPro-ODBC-Treiber unterstützt keine Besitzer für seine Objekte.  
  
 SQL_OWNER_USAGE gibt 0 zurück. Der Visual FoxPro-ODBC-Treiber unterstützt keine Besitzer für seine Objekte.  
  
## <a name="p"></a>P  
 SQL_POS_OPERATIONS gibt SQL_POS_POSITION zurück.  
  
 SQL_POSITIONED_STATEMENTS gibt 0 zurück.  
  
 SQL_PROCEDURE_TERM gibt "" zurück.  
  
 SQL_PROCEDURES gibt "N" zurück.  
  
## <a name="q"></a>Q  
 SQL_QUALIFIER_LOCATION gibt SQL_QL_START zurück.  
  
 SQL_QUALIFIER_NAME_SEPARATOR gibt "!" oder "\\" zurück. Das Trennzeichen zwischen Datenbank und Tabelle ist '! ' für Datenquellen, die mit [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md)verbunden sind, und '\\' für Datenquellen, die Verzeichnisse von [freien Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)sind.  
  
 SQL_QUALIFIER_TERM gibt "Database" oder "Directory" zurück. Der Qualifizierer ist "Database" für Datenquellen, die mit [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md)verbunden sind, und "Directory" für Datenquellen, die Verzeichnisse von [freien Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)sind.  
  
 SQL_QUALIFIER_USAGE unterstützt SQL_QU_PRIVILEGE_DEFINITION nicht. Er gibt entweder SQL_QU_DML_STATEMENT oder SQL_QU_TABLE_DEFINITION zurück.  
  
 SQL_QUOTED_IDENTIFIER_CASE gibt SQL_IC_MIXED zurück.  
  
## <a name="r"></a>R  
 SQL_ROW_UPDATES gibt "N" zurück. Der Visual FoxPro-ODBC-Treiber unterstützt nur statische und Vorwärts Cursor.  
  
## <a name="s"></a>E  
 SQL_SCROLL_CONCURRENCY gibt SQL_SCCO_READ_ONLY zurück.  
  
 SQL_SCROLL_OPTIONS gibt entweder SQL_SO_STATIC oder SQL_SO_READONLY zurück.  
  
 SQL_SEARCH_PATTERN_ESCAPE gibt "\\" zurück.  
  
 SQL_SERVER_NAME gibt "" zurück.  
  
 SQL_SPECIAL_CHARACTERS gibt "~ @ # $% ^" zurück.  
  
 SQL_STATIC_SENSITIVITY gibt 0 zurück. Der Visual FoxPro-ODBC-Treiber unterstützt keine Positions Updates.  
  
 SQL_STRING_FUNCTIONS unterstützt SQL_FN_STR_INSERT, SQL_FN_STR_LOCATE, SQL_FN_STR_LOCATE_2 oder SQL_FN_STR_SOUNDEX nicht.  
  
 Gibt Folgendes zurück:  
  
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
  
 SQL_SUBQUERIES gibt Folgendes zurück:  
  
-   SQL_SQ_CORRELATED_SUBQUERIES  
  
-   SQL_SQ_COMPARISON  
  
-   SQL_SQ_EXISTS  
  
-   SQL_SQ_IN  
  
-   SQL_SQ_QUANTIFIED.  
  
 SQL_SYSTEM_FUNCTIONS gibt Folgendes zurück:  
  
-   SQL_FN_SYS_DBNAME  
  
-   SQL_FN_SYS_IFNULL  
  
 aber nicht:  
  
-   SQL_FN_SYS_USERNAME  
  
## <a name="t"></a>T  
 SQL_TABLE_TERM gibt "Table" zurück.  
  
 SQL_TIMEDATE_ADD_INTERVALS gibt Folgendes zurück:  
  
-   SQL_FN_TSI_ Sekunde  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 aber nicht:  
  
-   SQL_FN_TSI_FRAC_SECOND  
  
-   SQL_FN_TSI_WEEK  
  
-   SQL_FN_TSI_QUARTER  
  
 SQL_TIMEDATE_DIFF_INTERVALS gibt Folgendes zurück:  
  
-   SQL_FN_TSI_ Sekunde  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 SQL_TIMEDATE_FUNCTIONS unterstützt SQL_FN_TD_QUARTER, SQL_FN_TD_TIMESTAMPADD, SQL_FN_TD_DAYOFYEAR oder SQL_FN_TD_WEEK nicht.  
  
 Gibt Folgendes zurück:  
  
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
  
-   SQL_FN_TD_YEAR.  
  
 SQL_TXN_CAPABLE gibt SQL_TC_DML zurück.  
  
 SQL_TXN_ISOLATION_OPTION gibt SQL_TXN_READ_COMMITTED zurück.  
  
## <a name="u-z"></a>U - Z  
 SQL_UNION gibt entweder SQL_U_UNION oder SQL_U_UNION_ALL zurück.  
  
 SQL_USER_NAME gibt \<leere> zurück.
