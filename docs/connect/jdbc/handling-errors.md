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
ms.openlocfilehash: 5bc0e483c70033c8a8132a27879c5616e550ec26
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956533"
---
# <a name="handling-errors"></a>Behandlung von Fehlern
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] verwenden, werden alle Datenbankfehlerbedingungen mit der [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md)-Klasse als Ausnahmen an die Java-Anwendung übergeben. Die folgenden Methoden der SQLServerException-Klasse werden von „java.sql.SQLException“ und „java.lang.Throwable“ geerbt. Mit ihnen können spezielle Informationen zum aufgetretenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehler zurückgegeben werden:  
  
-   `getSQLState()` gibt den normalen X/Open- oder SQL99-Statuscode der Ausnahme zurück.
  
-   `getErrorCode()` gibt die jeweilige Datenbankfehlernummer zurück.
  
-   `getMessage()` gibt den vollständigen Text der Ausnahme zurück. Der Text der Fehlermeldung beschreibt das Problem und enthält häufig Platzhalter für Informationen wie Objektnamen, die in die angezeigte Fehlermeldung eingefügt werden.
  
-   `getNextException()` gibt das nächste `SQLServerException`-Objekt oder NULL zurück, wenn keine weiteren Ausnahmeobjekte mehr vorhanden sind.

-   `getSQLServerError()`Gibt das `SQLServerError` -Objekt zurück, das ausführliche Informationen über die von SQL Server empfangene Ausnahme enthält. Diese Methode gibt NULL zurück, wenn kein Server Fehler aufgetreten ist.

Die folgenden Methoden der `SQLServerError` -Klasse können verwendet werden, um zusätzliche Details zu dem Fehler zu erhalten, der vom Server generiert wurde.

-   `SQLServerError.getErrorMessage()`Gibt die vom Server empfangene Fehlermeldung zurück.

-   `SQLServerError.getErrorNumber()`gibt eine Zahl zurück, die den Typ des Fehlers identifiziert.

-   `SQLServerError.getErrorState()`Gibt einen numerischen Fehlercode aus SQL Server zurück, der einen Fehler, eine Warnung oder eine Meldung "keine Daten gefunden" darstellt.

-   `SQLServerError.getErrorSeverity()`Gibt den Schweregrad des empfangenen Fehlers zurück.

-   `SQLServerError.getServerName()`Gibt den Namen des Computers zurück, auf dem eine Instanz von ausgeführt wird SQL Server der den Fehler generiert hat.

-   `SQLServerError.getProcedureName()`Gibt den Namen der gespeicherten Prozedur oder des Remote Prozedur Aufrufs (RPC) zurück, die den Fehler generiert hat.

-   `SQLServerError.getLineNumber()`Gibt die Zeilennummer im Transact-SQL-Befehls Batch oder in der gespeicherten Prozedur zurück, die den Fehler generiert hat.
  
 Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben und eine fehlerhafte SQL-Anweisung ohne FROM-Klausel erstellt. Anschließend werden die Anweisung ausgeführt und eine SQL-Ausnahme verarbeitet.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagnostizieren von Problemen mit dem JDBC-Treiber](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
