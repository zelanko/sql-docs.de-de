---
title: Verwenden von SQLGetDiagRec und SQLGetDiagField | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306751"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Verwenden von SQLGetDiagRec und SQLGetDiagField
Anwendungen rufen **SQLGetDiagRec** oder **SQLGetDiagField** auf, um Diagnoseinformationen abzurufen. Diese Funktionen akzeptieren ein Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptorhandle und geben Diagnosen von der Funktion zurück, die dieses Handle zuletzt verwendet hat. Die Diagnose, die an einem bestimmten Handle protokolliert wird, wird verworfen, wenn eine neue Funktion mit diesem Handle aufgerufen wird. Wenn die Funktion mehrere Diagnosedatensätze zurückgegeben hat, ruft die Anwendung diese Funktionen mehrmals auf. Die Gesamtzahl der Statusdatensätze wird abgerufen, indem **SQLGetDiagField** für den Headerdatensatz (Datensatz 0) mit der Option SQL_DIAG_NUMBER aufgerufen wird.  
  
 Anwendungen rufen einzelne Diagnosefelder ab, indem sie **SQLGetDiagField** aufrufen und das abzurufende Feld angeben. Bestimmte Diagnosefelder haben für bestimmte Handletypen keine Bedeutung. Eine Liste der Diagnosefelder und deren Bedeutung finden Sie in der [SQLGetDiagField-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
 Anwendungen rufen SQLSTATE, systemeigenen Fehlercode und Diagnosemeldung in einem einzigen Aufruf ab, indem sie **SQLGetDiagRec**aufrufen. **SQLGetDiagRec** kann nicht zum Abrufen von Informationen aus dem Headerdatensatz verwendet werden.  
  
 Der folgende Code fordert den Benutzer beispielsweise zur Eingabe einer SQL-Anweisung auf und führt sie aus. Wenn Diagnoseinformationen zurückgegeben wurden, ruft es **SQLGetDiagField** auf, um die Anzahl der Statusdatensätze und **SQLGetDiagRec** abzufragen, um SQLSTATE, systemeigenen Fehlercode und Diagnosemeldung von diesen Datensätzen abzusenden.  
  
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
