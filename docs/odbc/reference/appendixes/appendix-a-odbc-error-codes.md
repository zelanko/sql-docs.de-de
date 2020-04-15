---
title: 'Anhang A: ODBC-Fehlercodes | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error codes [ODBC]
- SQLSTATE [ODBC]
- error codes [ODBC], SQLSTATE
ms.assetid: c06902e4-721d-42e2-b818-05f0e18e4ce0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af288cf9f0564f6fe0dbef14f66143667120c656
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307521"
---
# <a name="appendix-a-odbc-error-codes"></a>Anhang A: ODBC-Fehlercodes
In diesem Thema werden SQLSTATE-Werte für ODBC 3 erläutert. *x*. Weitere Informationen zu ODBC 3. *x* SQLSTATE-Werte, siehe [SQLSTATE-Zuordnungen](../../../odbc/reference/develop-app/sqlstate-mappings.md).  
  
 **SQLGetDiagRec** oder **SQLGetDiagField** gibt SQLSTATE-Werte zurück, wie sie von Open Group *Data Management: Structured Query Language (SQL), Version 2* (März 1995) definiert sind. SQLSTATE-Werte sind Zeichenfolgen, die fünf Zeichen enthalten. In der folgenden Tabelle sind SQLSTATE-Werte aufgeführt, die ein Treiber für **SQLGetDiagRec**zurückgeben kann.  
  
 Der für einen SQLSTATE zurückgegebene Zeichenfolgenwert besteht aus einem klassenwert mit zwei Zeichen, gefolgt von einem dreistelligen Unterklassenwert. Der Klassenwert "01" gibt eine Warnung an und wird von einem Rückgabecode SQL_SUCCESS_WITH_INFO begleitet. Andere Klassenwerte als "01" mit Ausnahme der Klasse "IM" weisen auf einen Fehler hin und werden von einem Rückgabewert von SQL_ERROR begleitet. Die Klasse "IM" ist spezifisch für Warnungen und Fehler, die sich aus der Implementierung von ODBC selbst ergeben. Der Unterklassenwert "000" in jeder Klasse gibt an, dass es keine Unterklasse für diese SQLSTATE gibt. Die Zuweisung von Klassen- und Unterklassenwerten wird durch SQL-92 definiert.  
  
> [!NOTE]  
>  Obwohl die erfolgreiche Ausführung einer Funktion normalerweise durch einen Rückgabewert von SQL_SUCCESS angezeigt wird, zeigt sqlSTATE 00000 auch den Erfolg an.  
  
|SQLSTATE|Fehler|Kann von|  
|--------------|-----------|--------------------------|  
|01000|Allgemeine Warnung|Alle ODBC-Funktionen außer:<br /><br /> **Sqlerror**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|01001|Cursor-Operation-Konflikt|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01002|Trennfehler|**SQLDisconnect**|  
|01003|NULL-Wert in Set-Funktion eliminiert|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLNative**<br /><br /> **Sql SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetCursorName**|  
|01006|Berechtigung nicht widerrufen|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01007|Privileg nicht gewährt|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01S00|Ungültiges Verbindungszeichenfolgenattribut|**SQLBrowseConnect**<br /><br /> **SQLDriverConnec**|  
|01S01|Fehler in Zeile|**SQLBulkOperations**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLSetPos**|  
|01S02|Optionswert geändert|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|01S06|Versuch, abzurufen, bevor das Resultset das erste Rowset zurückgibt|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|01S07|Bruchschnitt|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01S08|Fehler beim Speichern von Datei-DSN|**SQLDriverConnect**|  
|01S09|Ungültiges Schlüsselwort|**SQLDriverConnect**|  
|07001|Falsche Anzahl von Parametern|**SQLExecDirect**<br /><br /> **SQLExecute**|  
|07002|COUNT-Feld falsch|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|07005|Vorbereitete Anweisung keine *Cursorspezifikation*|**SQLColAttribute**<br /><br /> **SQLDescribeCol**|  
|07006|Verletzung des eingeschränkten Datentypattributs|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|07009|Ungültiger Deskriptorindex|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRecSQLSetPos**|  
|07S01|Ungültige Verwendung des Standardparameters|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**|  
|08001|Client kann keine Verbindung herstellen|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08002|Verbindungsname wird verwendet|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|08003|Verbindung nicht geöffnet|**SQLAllocHandle**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLSetConnectAttr**|  
|08004|Server hat die Verbindung abgelehnt|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08007|Verbindungsfehler während der Transaktion|**SQLEndTran**|  
|08S01|Kommunikationsverbindungsfehler|**SQLBrowseConnect**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLCopyDesc**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNativeSql**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|21S01|Wertliste einfügen stimmt nicht mit der Spaltenliste überein|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|21S02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|22001|Zeichenfolgendaten, rechts abgeschnitten|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetPos**|  
|22002|Indikatorvariable erforderlich, aber nicht mitgeliefert|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**|  
|22003|Numerischer Wert aofc|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22007|Ungültiges Datumszeitformat|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22008|Datetime-Feldüberlauf|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **QLParamData**<br /><br /> **SQLPutData**|  
|22012|Division durch Null|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLPutData**|  
|22015|Intervallfeldüberlauf|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22019|Ungültiges Escapezeichen|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22025|Ungültige Escapesequenz|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22026|Zeichenfolgendaten, nicht übereinstimmende Länge|**SQLParamData**|  
|23000|Verletzung der Integritätseinschränkung|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|24.000|Ungültiger Cursorstatus|**SQLBulkOperations**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|25000|Ungültiger Transaktionsstatus|**SQLDisconnect**|  
|25S01|Transaktionsstatus|**SQLEndTran**|  
|25S02|Transaktion ist noch aktiv|**SQLEndTran**|  
|25S03|Transaktion wird zurückgesetzt|**SQLEndTran**|  
|28000|Ungültige Autorisierungsspezifikation|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|34000|Ungültiger Cursorname|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetCursorName**|  
|3C000|Duplikat-Cursorname|**SQLSetCursorName**|  
|3D000|Ungültiger Katalogname|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**|  
|3F000|Ungültiger Schemaname|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|40001|Serialisierungsfehler|**SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLParamData**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|40002|Verletzung der Integritätseinschränkung|**SQLEndTran**|  
|40003|Anweisungsvervollständigung unbekannt|**SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|42000|Syntaxfehler oder Zugriffsverletzung|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|42S01|Basistabelle oder -ansicht ist bereits vorhanden|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S02|Basistabelle oder Ansicht nicht gefunden|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S11|Index ist bereits vorhanden|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S12|Index nicht gefunden|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S21|Spalte ist bereits vorhanden|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S22|Spalte nicht gefunden|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|44000|WITH CHECK OPTION-Verstoß|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY000|Allgemeiner Fehler|Alle ODBC-Funktionen außer:<br /><br /> **Sqlerror**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY001|Speicherzuweisungsfehler|Alle ODBC-Funktionen außer:<br /><br /> **Sqlerror**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY003|Ungültiger Anwendungspuffertyp|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLGetData**|  
|HY004|Ungültiger SQL-Datentyp|**SQLBindParameter**<br /><br /> **SQLGetTypeInfo**|  
|HY007|Zugehörige Anweisung ist nicht vorbereitet|**SQLCopyDesc**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**|  
|HY008|Vorgang abgebrochen|Alle ODBC-Funktionen, die asynchron verarbeitet werden können:<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY009|Ungültige Verwendung des NULL-Zeigers|**SQLAllocHandle**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY010|Funktionssequenzfehler|**SQLAllocHandle**<br /><br /> **SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLCopyDesc**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLFreeHandle**<br /><br /> **'SQLFreeStmt'**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLRowCount**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY011|Attribut kann jetzt nicht festgelegt werden|**SQLBulkOperations**<br /><br /> **SQLParamData**<br /><br /> **QLSetPos**<br /><br /> **SQLSetStmtAttr**|  
|HY012|Ungültiger Transaktionsvorgangscode|**SQLEndTran**|  
|HY013|Speicherverwaltungsfehler|Alle ODBC-Funktionen außer:<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY014|Grenzwert für die Anzahl der überschrittenen Griffe|**SQLAllocHandle**|  
|HY015|Kein Cursorname verfügbar|**SQLGetCursorName**|  
|HY016|Eine Implementierungszeilenbeschreibung kann nicht geändert werden.|**SQLCopyDesc**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY017|Ungültige Verwendung eines automatisch zugewiesenen Deskriptor-Handles|**SQLFreeHandle**<br /><br /> **SQLSetStmtAttr**|  
|HY018|Server hat Abbruchanforderung abgelehnt|**SQLCancel**|  
|HY019|Nicht-Zeichen- und nicht-binäre Daten werden in Stücken gesendet|**SQLPutData**|  
|HY020|Versuch, einen NULL-Wert zu verketten|**SQLPutData**|  
|HY021|Inkonsistente Deskriptorinformationen|**SQLBindParameter**<br /><br /> **SQLCopyDesc**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY024|Ungültiger Attributwert|**SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetInfo**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY091|Ungültiger Deskriptorfeldbezeichner|**SQLColAttribute**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|**SQLAllocHandle**<br /><br /> **QLBulkOperations**<br /><br /> **SQLCopyDesc**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **'SQLFreeStmt'**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetEnvAttr**<br /><br /> **QLParamData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**|  
|HY095|Funktionstyp aunter Bereich|**SQLGetFunctions**|  
|HY096|Ungültiger Informationstyp|**SQLGetInfo**|  
|HY097|Spaltentyp a-range|**'SQLSpecialColumns'**|  
|HY098|Scope-Typ a-range|**'SQLSpecialColumns'**|  
|HY099|Nullabler Typ a-range|**'SQLSpecialColumns'**|  
|HY100|Eindeutigkeitsoption atyp a-range|**'SQLStatistics'**|  
|HY101|Genauigkeitsoptionstyp a-range|**'SQLStatistics'**|  
|HY103|Ungültiger Abrufcode|**SQLDataSources**<br /><br /> **SQLDrivers**|  
|HY104|Ungültiger Genauigkeits- oder Skalierungswert|**SQLBindParameter**|  
|HY105|Ungültiger Parametertyp|**SQLBindParameter**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**|  
|HY106|Abruftyp anicht in Reichweite|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HY107|Zeilenwert a-range|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLSetPos**|  
|HY109|Ungültige Cursorposition|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLGetData**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY110|Ungültiger Treiberabschluss|**SQLDriverConnect**|  
|HY111|Ungültiger Lesezeichenwert|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HYC00|Optionale Funktion nicht implementiert|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT00|Timeout abgelaufen|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT01|Verbindungstimeout abgelaufen|Alle ODBC-Funktionen außer:<br /><br /> **SQLDrivers**<br /><br /> **SQLDataSources**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLSetEnvAttr**|  
|IM001|Treiber unterstützt diese Funktion nicht|Alle ODBC-Funktionen außer:<br /><br /> **SQLAllocHandle**<br /><br /> **SQLDataSources**<br /><br /> **SQLDrivers**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLGetFunctions**|  
|IM002|Datenquellenname nicht gefunden und kein Standardtreiber angegeben|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM003|Der angegebene Treiber konnte nicht geladen werden.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM004|**SQLAllocHandle** des Treibers auf SQL_HANDLE_ENV fehlgeschlagen|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM005|**SQLAllocHandle** des Treibers auf SQL_HANDLE_DBC fehlgeschlagen|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM006|**SQLSetConnectAttr** des Treibers fehlgeschlagen|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM007|Es wurde keine Datenquelle oder ein Treiber angegeben; Dialog verboten|**SQLDriverConnect**|  
|IM008|Dialog fehlgeschlagen|**SQLDriverConnect**|  
|IM009|Übersetzungs-DLL kann nicht geladen werden|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|IM010|Datenquellenname zu lang|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM011|Treibername zu lang|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM012|DRIVER-Schlüsselwortsyntaxfehler|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM013|Ablaufverfolgungsdateifehler|Alle ODBC-Funktionen.|  
|IM014|Ungültiger Name der Datei DSN|**SQLDriverConnect**|  
|IM015|Beschädigte Dateidatenquelle|**SQLDriverConnect**|
