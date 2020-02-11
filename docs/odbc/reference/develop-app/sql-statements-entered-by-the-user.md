---
title: Vom Benutzer eingegebene SQL-Anweisungen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086076"
---
# <a name="sql-statements-entered-by-the-user"></a>Vom Benutzer eingegebene SQL-Anweisungen
Anwendungen, die eine Ad-hoc-Analyse durchführen, ermöglichen es auch häufig, SQL-Anweisungen direkt einzugeben. Beispiel:  
  
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
  
 Dieser Ansatz vereinfacht die Anwendungs Codierung. die Anwendung basiert auf dem Benutzer, um die SQL-Anweisung zu erstellen, und auf der Datenquelle, um die Gültigkeit der Anweisung zu überprüfen. Da es schwierig ist, eine grafische Benutzeroberfläche zu schreiben, die die Feinheiten von SQL adäquat verfügbar macht, ist es möglicherweise eine bevorzugte Alternative, den Benutzer aufzufordern, den Text der SQL-Anweisung einzugeben. Dies erfordert jedoch, dass der Benutzer nicht nur SQL, sondern auch das Schema der Datenquelle kennt, die abgefragt wird. Einige Anwendungen stellen eine grafische Benutzeroberfläche bereit, mit der der Benutzer eine einfache SQL-Anweisung erstellen und eine Textschnittstelle bereitstellen kann, mit der der Benutzer Sie ändern kann.
