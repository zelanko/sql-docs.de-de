---
title: 'Anhang A: ODBC-Fehler Codes | Microsoft-Dokumentation'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307521"
---
# <a name="appendix-a-odbc-error-codes"></a>Anhang A: ODBC-Fehlercodes
In diesem Thema werden SQLSTATE-Werte für ODBC 3 erläutert. *x*. Weitere Informationen zu ODBC 3. zu den *x* SQLSTATE-Werten finden Sie unter [SQLSTATE](../../../odbc/reference/develop-app/sqlstate-mappings.md)-Zuordnungen.  
  
 **SQLGetDiagRec** oder **SQLGetDiagField** gibt SQLSTATE-Werte zurück, wie von Open Group *Datenverwaltung: strukturierte Abfragesprache (SQL), Version 2* (März 1995) definiert. SQLSTATE-Werte sind Zeichen folgen, die fünf Zeichen enthalten. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von einem Treiber für **SQLGetDiagRec**zurückgegeben werden können.  
  
 Der Zeichen folgen Wert, der für einen SQLSTATE zurückgegeben wird, besteht aus einem zweistelligen Klassen Wert, gefolgt von einem Unterklassen Wert mit drei Zeichen. Der Klassen Wert "01" gibt eine Warnung an und wird von einem Rückgabecode SQL_SUCCESS_WITH_INFO begleitet. Andere Klassen Werte als "01", mit Ausnahme der Klasse "im", weisen auf einen Fehler hin und werden von einem Rückgabewert von SQL_ERROR begleitet. Die Klasse "im" ist spezifisch für Warnungen und Fehler, die von der Implementierung von ODBC selbst abgeleitet werden. Der Unterklasse-Wert "000" in einer beliebigen Klasse gibt an, dass keine Unterklasse für diesen SQLSTATE vorhanden ist. Die Zuweisung von Klassen-und Unterklassen Werten wird von SQL-92 definiert.  
  
> [!NOTE]  
>  Obwohl die erfolgreiche Ausführung einer Funktion normalerweise durch den Rückgabewert SQL_SUCCESS angegeben wird, ist SQLSTATE 00000 auch ein Erfolg.  
  
|SQLSTATE|Fehler|Kann zurückgegeben werden von|  
|--------------|-----------|--------------------------|  
|01000|Allgemeine Warnung|Alle ODBC-Funktionen mit Ausnahme von:<br /><br /> **SQLError**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|01001|Konflikt beim Cursor Vorgang|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01002|Fehler beim Trennen|**SQLDisconnect**|  
|01003|NULL-Wert in Set-Funktion entfernt|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **Sqlnative**<br /><br /> **SQL SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetCursorName**|  
|01006|Berechtigung nicht widerrufen|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01007|Berechtigung nicht erteilt|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01S00|Ungültiges Verbindungs Zeichen folgen Attribut.|**SQLBrowseConnect**<br /><br /> **Sqldriverconnecc**|  
|01s01|Fehler in Zeile|**SQLBulkOperations**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLSetPos**|  
|01s02 entsprechen|Optionswert geändert|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|01s06|Es wurde versucht, abzurufen, bevor das Resultset das erste Rowset zurückgegeben hat|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|01S07|Abschneiden von Sekundenbruchteilen|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01s08|Fehler beim Speichern des Datei-DSN|**SQLDriverConnect**|  
|01s09|Ungültiges Schlüsselwort|**SQLDriverConnect**|  
|07001|Falsche Anzahl von Parametern.|**SQLExecDirect**<br /><br /> **SQLExecute**|  
|07002|Anzahl Feld falsch|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|07005|Die vorbereitete Anweisung ist keine *Cursor Spezifikation* .|**SQLColAttribute**<br /><br /> **SQLDescribeCol**|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|07009|Ungültiger deskriptorindex.|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**<br /><br /> **Sqlsetdescrecsqlsetpos**|  
|07S01|Ungültige Verwendung des Standard Parameters.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**|  
|08001|Der Client kann keine Verbindung herstellen.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08002|Der Verbindungs Name wird verwendet.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|08003|Verbindung nicht geöffnet|**SQLAllocHandle**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLSetConnectAttr**|  
|08004|Der Server hat die Verbindung abgelehnt.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08007|Verbindungsfehler während der Transaktion.|**SQLEndTran**|  
|08S01|Kommunikations Verbindungsfehler|**SQLBrowseConnect**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **Sqlcopyde SC**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNativeSql**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|21s01|Die einfügewertliste stimmt nicht mit der Spaltenliste|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|21s02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein.|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|22001|Zeichen folgen Daten, rechts abgeschnitten|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetPos**|  
|22002|Die Indikator Variable ist erforderlich, aber nicht angegeben.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**|  
|22003|Numerischer Wert außerhalb des zulässigen Bereichs|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22007|Ungültiges datetime-Format.|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22008|Überlauf bei DateTime-Feld|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **Qlparamdata**<br /><br /> **SQLPutData**|  
|22012|Division durch Null|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLPutData**|  
|22015|Überlauf des Intervall Felds|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22019|Ungültiges Escapezeichen|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22025|Ungültige Escape-Sequenz|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22026|Zeichenfolgendaten, nicht übereinstimmende Länge|**SQLParamData**|  
|23000|Verletzung der Integritäts Einschränkung|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|24.000|Ungültiger Cursorstatus|**SQLBulkOperations**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|25000|Ungültiger Transaktionsstatus|**SQLDisconnect**|  
|25s01|Transaktionsstatus|**SQLEndTran**|  
|25s02|Die Transaktion ist noch aktiv.|**SQLEndTran**|  
|25s03|Für Transaktion wird ein Rollback ausgeführt|**SQLEndTran**|  
|28000|Ungültige Autorisierungs Spezifikation|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|34000|Ungültiger Cursorname|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetCursorName**|  
|3c000|Doppelter Cursor Name|**SQLSetCursorName**|  
|3D000|Ungültiger Katalog Name.|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**|  
|3F-|Ungültiger Schema Name.|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|40001|Serialisierungsfehler|**SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLParamData**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|40002|Verletzung der Integritäts Einschränkung|**SQLEndTran**|  
|40003|Anweisungs Vervollständigung unbekannt|**SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|42000|Syntax Fehler oder Zugriffsverletzung|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|42s01|Die Basistabelle oder-Sicht ist bereits vorhanden.|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42s02|Die Basistabelle oder-Sicht wurde nicht gefunden.|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42s11|Index ist bereits vorhanden.|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42s12|Index nicht gefunden.|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42s21|Spalte ist bereits vorhanden.|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42s22|Spalte nicht gefunden|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|44000|WITH CHECK OPTION-Verstoß|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY000|Allgemeiner Fehler|Alle ODBC-Funktionen mit Ausnahme von:<br /><br /> **SQLError**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY001|Fehler bei der Speicher Belegung|Alle ODBC-Funktionen mit Ausnahme von:<br /><br /> **SQLError**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY003|Ungültiger Anwendungs Puffertyp.|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLGetData**|  
|HY004|Ungültiger SQL-Datentyp.|**SQLBindParameter**<br /><br /> **SQLGetTypeInfo**|  
|HY007|Die zugehörige Anweisung ist nicht vorbereitet.|**Sqlcopyde SC**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**|  
|HY008|Vorgang abgebrochen|Alle ODBC-Funktionen, die asynchron verarbeitet werden können:<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY009|Ungültige Verwendung des NULL-Zeigers|**SQLAllocHandle**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY010|Funktions Sequenz Fehler|**SQLAllocHandle**<br /><br /> **SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **Sqlcopyde SC**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLFreeHandle**<br /><br /> **'SQLFreeStmt'**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLRowCount**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY011|Das Attribut kann jetzt nicht festgelegt werden|**SQLBulkOperations**<br /><br /> **SQLParamData**<br /><br /> **Qlsetpos**<br /><br /> **SQLSetStmtAttr**|  
|HY012|Ungültiger Transaktions Vorgangs Code.|**SQLEndTran**|  
|HY013|Speicher Verwaltungsfehler|Alle ODBC-Funktionen mit Ausnahme von:<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY014|Limit für die Anzahl von Handles überschritten|**SQLAllocHandle**|  
|HY015|Kein Cursor Name verfügbar.|**SQLGetCursorName**|  
|HY016|Ein Implementierungs Zeilen Deskriptor kann nicht geändert werden.|**Sqlcopyde SC**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY017|Ungültige Verwendung eines automatisch zugeordneten Deskriptorhandles.|**SQLFreeHandle**<br /><br /> **SQLSetStmtAttr**|  
|HY018|Der Server hat die Abbruch Anforderung abgelehnt|**SQLCancel**|  
|HY019|In Teile gesendete nicht-Zeichen-und nicht-Binärdaten|**SQLPutData**|  
|HY020|Es wurde versucht, einen NULL-Wert zu verketten.|**SQLPutData**|  
|HY021|Inkonsistente Deskriptorinformationen|**SQLBindParameter**<br /><br /> **Sqlcopyde SC**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY024|Ungültiger Attribut Wert|**SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetInfo**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY091|Ungültiger Deskriptorfeldbezeichner.|**SQLColAttribute**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**|  
|HY092|Ungültiger Attribut/Options Bezeichner|**SQLAllocHandle**<br /><br /> **Qlbulkoperations**<br /><br /> **Sqlcopyde SC**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **'SQLFreeStmt'**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetEnvAttr**<br /><br /> **Qlparamdata**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**|  
|HY095|Funktionstyp außerhalb des gültigen Bereichs|**SQLGetFunctions**|  
|HY096|Ungültiger Informationstyp.|**SQLGetInfo**|  
|HY097|Spaltentyp außerhalb des gültigen Bereichs|**'SQLSpecialColumns'**|  
|HY098|Bereichstyp außerhalb des gültigen Bereichs|**'SQLSpecialColumns'**|  
|HY099|Nullable-Typ außerhalb des gültigen Bereichs|**'SQLSpecialColumns'**|  
|HY100|Eindeutigkeits Optionstyp außerhalb des gültigen Bereichs|**'SQLStatistics'**|  
|HY101|Genauigkeits Optionstyp außerhalb des gültigen Bereichs|**'SQLStatistics'**|  
|HY103|Ungültiger Abruf Code|**SQLDataSources**<br /><br /> **SQLDrivers**|  
|HY104|Ungültiger Wert für Genauigkeit oder Dezimalwert|**SQLBindParameter**|  
|HY105|Ungültiger Parametertyp|**SQLBindParameter**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**|  
|HY106|FETCH-Typ außerhalb des gültigen Bereichs|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HY107|Zeilen Wert außerhalb des zulässigen Bereichs|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLSetPos**|  
|HY109|Ungültige Cursorposition|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLGetData**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY110|Ungültiger Treiber Abschluss.|**SQLDriverConnect**|  
|HY111|Ungültiger Lesezeichen Wert|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HYC00|Optionales Feature nicht implementiert|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **'SQLGetStmtAttr'**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT00|Timeout abgelaufen|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **'SQLProcedures'**<br /><br /> **SQLSetPos**<br /><br /> **'SQLSpecialColumns'**<br /><br /> **'SQLStatistics'**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT01|Verbindungs Timeout abgelaufen|Alle ODBC-Funktionen mit Ausnahme von:<br /><br /> **SQLDrivers**<br /><br /> **SQLDataSources**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLSetEnvAttr**|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|Alle ODBC-Funktionen mit Ausnahme von:<br /><br /> **SQLAllocHandle**<br /><br /> **SQLDataSources**<br /><br /> **SQLDrivers**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLGetFunctions**|  
|IM002|Datenquellen Name wurde nicht gefunden, und es wurde kein Standardtreiber angegeben.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM003|Der angegebene Treiber konnte nicht geladen werden.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM004|Fehler beim Treiber " **sqlzugewiesene CHandle** " auf SQL_HANDLE_ENV|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM005|Fehler beim Treiber " **sqlzugewiesene CHandle** " auf SQL_HANDLE_DBC|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM006|Fehler bei ' **SQLSetConnectAttr** ' des Treibers.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM007|Es wurden keine Datenquellen oder Treiber angegeben. Dialogfeld unzulässig|**SQLDriverConnect**|  
|IM008|Dialog Fehler|**SQLDriverConnect**|  
|IM009|Übersetzungs-DLL kann nicht geladen werden.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|IM010|Der Datenquellen Name ist zu lang.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM011|Der Treiber Name ist zu lang.|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM012|Syntax Fehler für Treiber Schlüsselwort|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM013|Fehler bei Ablauf Verfolgungs Datei|Alle ODBC-Funktionen.|  
|IM014|Ungültiger Name des Datei-DSN.|**SQLDriverConnect**|  
|IM015|Beschädigte Datei Datenquelle|**SQLDriverConnect**|
