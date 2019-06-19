---
title: Verwenden von SQLGetDiagRec und SQLGetDiagField | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 4f486bb1-fad8-4064-ac9d-61f2de85b68b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1db402e7c015ef50ce47b5137e670d9f1836a326
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208434"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Verwenden von SQLGetDiagRec und SQLGetDiagField
-Anwendungen rufen **SQLGetDiagRec** oder **SQLGetDiagField** zum Abrufen von Diagnoseinformationen zu erhalten. Diese Funktionen akzeptieren eine Umgebung, Verbindung, Anweisung oder -Deskriptor-Handle und Diagnose von der Funktion, die zuletzt verwendet von diesem Handle zurück. Die Diagnose in einem bestimmten Handle protokolliert werden verworfen, wenn eine neue Funktion mit diesem Handle aufgerufen wird. Wenn die Funktion mehrere DiagnoseDatensätze zurückgegeben wird, ruft die Anwendung dieser Funktionen mehrmals; Die Gesamtzahl der Statusdatensätze wird abgerufen, durch den Aufruf **SQLGetDiagField** für den Headerdatensatz (Datensatz 0), mit der Option SQL_DIAG_NUMBER.  
  
 Anwendungen rufen Sie einzelne Diagnosefelder durch den Aufruf **SQLGetDiagField** und Angeben des abzurufenden Felds. Keine Bedeutung für bestimmte Arten von Handles keine bestimmten Feldern. Eine Liste von Feldern und ihre Bedeutungen, finden Sie unter den [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) funktionsbeschreibung.  
  
 Der SQLSTATE, systemeigener Fehlercode und diagnosemeldung in einem einzigen Aufruf Anwendungen abzurufen, durch Aufrufen **SQLGetDiagRec**; **SQLGetDiagRec** nicht zum Abrufen von Informationen aus der Headerdatensatz verwendet werden.  
  
 Beispielsweise wird der folgende Code fordert den Benutzer zu einer SQL-Anweisung und ausgeführt. Wenn Sie sämtliche Diagnoseinformationen zurückgegeben wurde, ruft es **SQLGetDiagField** beim Abrufen der Anzahl der Statusdatensätze und **SQLGetDiagRec** abzurufenden die SQLSTATE, systemeigener Fehlercode und diagnosemeldung aus Datensätze.  
  
```  
SQLCHAR       SqlState[6], SQLStmt[100], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLINTEGER    NativeError;  
SQLSMALLINT   i, MsgLen;  
SQLRETURN     rc1, rc2;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement.  
GetSQLStmt(SQLStmt);  
  
// Execute the SQL statement and return any errors or warnings.  
rc1 = SQLExecDirect(hstmt, SQLStmt, SQL_NTS);  
if ((rc1 == SQL_SUCCESS_WITH_INFO) || (rc1 == SQL_ERROR)) {
   SQLLEN numRecs = 0;
   SQLGetDiagField(SQL_HANDLE_STMT, hstmt, 0, SQL_DIAG_NUMBER, &numRecs, 0, 0);
   // Get the status records.
   i = 1;  
   while (i <= numRecs && (rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
            Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState,NativeError,Msg,MsgLen);  
      i++;  
   }  
}  
  
if ((rc1 == SQL_SUCCESS) || (rc1 == SQL_SUCCESS_WITH_INFO)) {  
   // Process statement results, if any.  
}  
```
