---
title: Behandeln von Fehlern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 535881ed3ece30996390af6c9a22568d49bc6d3e
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "55736965"
---
# <a name="handling-errors"></a>Behandlung von Fehlern
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] verwenden, werden alle Datenbankfehlerbedingungen mit der [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md)-Klasse als Ausnahmen an die Java-Anwendung übergeben. Die folgenden Methoden der SQLServerException-Klasse werden von „java.sql.SQLException“ und „java.lang.Throwable“ geerbt. Mit ihnen können spezielle Informationen zum aufgetretenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehler zurückgegeben werden:  
  
-   `getSQLState()` gibt den normalen X/Open- oder SQL99-Statuscode der Ausnahme zurück.
  
-   `getErrorCode()` gibt die jeweilige Datenbankfehlernummer zurück.
  
-   `getMessage()` gibt den vollständigen Text der Ausnahme zurück. Der Text der Fehlermeldung beschreibt das Problem und enthält häufig Platzhalter für Informationen wie Objektnamen, die in die angezeigte Fehlermeldung eingefügt werden.
  
-   `getNextException()` gibt das nächste `SQLServerException`-Objekt oder NULL zurück, wenn keine weiteren Ausnahmeobjekte mehr vorhanden sind.

-   `getSQLServerError()` Gibt die `SQLServerError` Objekt, das ausführliche Informationen zur Ausnahme enthält, von SQL Server empfangen. Diese Methode gibt null, wenn kein Serverfehler aufgetreten ist.

Die folgenden Methoden der der `SQLServerError` Klasse kann verwendet werden, um weitere Details zu den vom Server generierten Fehler abzurufen.

-   `SQLServerError.getErrorMessage()` Gibt die Fehlermeldung zurück, wie vom Server empfangen.

-   `SQLServerError.getErrorNumber()` Gibt eine Zahl, die den Typ des Fehlers identifiziert.

-   `SQLServerError.getErrorState()` Gibt einen numerischen Fehlercode von SQL Server, die einen Fehler, Warnung oder "keine Daten gefunden"-Meldung darstellt.

-   `SQLServerError.getErrorSeverity()` Gibt den Schweregrad des Fehlers erhalten.

-   `SQLServerError.getServerName()` Gibt zurück, der der Namen des Computers, auf denen einer Instanz von SQL Server wird der Fehler generiert.

-   `SQLServerError.getProcedureName()` Gibt den Namen der gespeicherten Prozedur oder einen Remoteprozeduraufruf (RPC), die den Fehler generiert hat.

-   `SQLServerError.getLineNumber()` Gibt die Zeilennummer in der Transact-SQL-Befehlsbatch oder die gespeicherte Prozedur, der den Fehler generiert hat.
  
 Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben und eine fehlerhafte SQL-Anweisung ohne FROM-Klausel erstellt. Anschließend werden die Anweisung ausgeführt und eine SQL-Ausnahme verarbeitet.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagnostizieren von Problemen mit dem JDBC-Treiber](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
