---
title: SQL-Anweisungen, die vom Benutzer eingegebene | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 78a1653df60b21cde772cbe32a688b3fdef80a42
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086076"
---
# <a name="sql-statements-entered-by-the-user"></a>Vom Benutzer eingegebene SQL-Anweisungen
Anwendungen, die häufig auch Ausführen von ad-hoc-Analysen können Benutzer SQL-Anweisungen direkt eingeben. Zum Beispiel:  
  
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
  
 Dieser Ansatz vereinfacht die Anwendung codieren; die Anwendung basiert auf den Benutzer auf die SQL-Anweisung zu erstellen und für die Datenquelle aus, um die Anweisung die Gültigkeit zu überprüfen. Da es schwierig ist, eine grafische Benutzeroberfläche zu schreiben, die die feinheiten der SQL angemessen verfügbar macht, möglicherweise die einfach den Benutzer auffordert, geben Sie den Text der SQL-Anweisung, dass eine Alternative vorzuziehen. Dies erfordert jedoch die Benutzer wissen, nicht nur SQL, sondern auch das Schema der Datenquelle abgefragt wird. Einige Anwendungen bieten eine grafische Benutzeroberfläche der Benutzer kann nach der Erstellen einer einfachen SQL-Anweisung und bieten auch eine Text-Schnittstelle, die mit der der Benutzer es ändern kann.
