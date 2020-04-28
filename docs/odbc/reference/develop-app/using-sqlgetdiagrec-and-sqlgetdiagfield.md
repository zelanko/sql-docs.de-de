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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69a17086253b40469b0ed98cb6f870f319f03f52
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306751"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Verwenden von SQLGetDiagRec und SQLGetDiagField
Anwendungen rufen **SQLGetDiagRec** oder **SQLGetDiagField** auf, um Diagnoseinformationen abzurufen. Diese Funktionen akzeptieren eine Umgebung, eine Verbindung, eine Anweisung oder ein Deskriptorhandle und geben Diagnoseinformationen von der Funktion zurück, die das Handle zuletzt verwendet hat. Die an einem bestimmten handle protokollierte Diagnose wird verworfen, wenn eine neue Funktion mit diesem Handle aufgerufen wird. Wenn die Funktion mehrere Diagnosedaten Sätze zurückgibt, werden diese Funktionen von der Anwendung mehrmals aufgerufen. die Gesamtanzahl der Statusdaten Sätze wird durch Aufrufen von **SQLGetDiagField** für den Header Daten Satz (Datensatz 0) mit der Option SQL_DIAG_NUMBER abgerufen.  
  
 Anwendungen rufen einzelne Diagnose Felder ab, indem Sie **SQLGetDiagField** aufrufen und das abzurufende Feld angeben. Bestimmte Diagnose Felder haben für bestimmte Typen von Handles keine Bedeutung. Eine Liste der Diagnose Felder und ihrer Bedeutungen finden Sie in der Beschreibung der [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) -Funktion.  
  
 Anwendungen rufen SQLSTATE, systemeigenen Fehlercode und Diagnosemeldungen in einem einzigen Aufruf durch Aufrufen von **SQLGetDiagRec**ab. **SQLGetDiagRec** kann nicht zum Abrufen von Informationen aus dem Header Daten Satz verwendet werden.  
  
 Im folgenden Code wird z. b. der Benutzer zur Eingabe einer SQL-Anweisung aufgefordert und ausgeführt. Wenn Diagnoseinformationen zurückgegeben wurden, wird **SQLGetDiagField** aufgerufen, um die Anzahl von Statusdaten Sätzen abzurufen, und **SQLGetDiagRec** , um SQLSTATE, systemeigenen Fehlercode und Diagnosemeldungen aus diesen Datensätzen abzurufen.  
  
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
