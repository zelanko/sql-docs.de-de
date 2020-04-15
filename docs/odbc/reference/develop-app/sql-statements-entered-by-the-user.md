---
title: VOM Benutzer eingegebene SQL-Anweisungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf2f8cf36be392cb42a970fa2fb0b19c35daeb39
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301961"
---
# <a name="sql-statements-entered-by-the-user"></a>Vom Benutzer eingegebene SQL-Anweisungen
Anwendungen, die Ad-hoc-Analysen durchführen, ermöglichen es dem Benutzer auch häufig, SQL-Anweisungen direkt einzugeben. Beispiel:  
  
```  
SQLCHAR *     Statement, SqlState[6], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLSMALLINT   i, MsgLen;  
SQLINTEGER    NativeError;  
SQLRETURN     rc1, rc2;  
  
// Prompt user for SQL statement.  
GetSQLStatement(Statement);  
  
// Execute the statement directly. Because it will be executed only once,  
// do not prepare it.  
rc1 = SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Process any errors or returned information.  
if ((rc1 == SQL_ERROR) || rc1 == SQL_SUCCESS_WITH_INFO) {  
   i = 1;  
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
         Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState, NativeError, Msg, MsgLen);  
      i++;  
   }  
}  
```  
  
 Dieser Ansatz vereinfacht die Anwendungscodierung. Die Anwendung verlässt sich auf den Benutzer, um die SQL-Anweisung zu erstellen, und auf die Datenquelle, um die Gültigkeit der Anweisung zu überprüfen. Da es schwierig ist, eine grafische Benutzeroberfläche zu schreiben, die die Feinheiten von SQL angemessen verfügbar macht, kann es eine vorzuziehende Alternative sein, den Benutzer einfach zur Eingabe des SQL-Anweisungstextes aufzufordern. Dies erfordert jedoch, dass der Benutzer nicht nur SQL, sondern auch das Schema der abgefragten Datenquelle kennt. Einige Anwendungen bieten eine grafische Benutzeroberfläche, über die der Benutzer eine grundlegende SQL-Anweisung erstellen und auch eine Textoberfläche bereitstellen kann, mit der der Benutzer sie ändern kann.
