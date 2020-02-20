---
title: Behandlung von Fehlern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6277b3ecf0160078fa47bc79994d31f64519d9b7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028030"
---
# <a name="handling-errors"></a>Behandlung von Fehlern
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] verwenden, werden alle Datenbankfehlerbedingungen mit der [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md)-Klasse als Ausnahmen an die Java-Anwendung übergeben. Die folgenden Methoden der SQLServerException-Klasse werden von „java.sql.SQLException“ und „java.lang.Throwable“ geerbt. Mit ihnen können spezielle Informationen zum aufgetretenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehler zurückgegeben werden:  
  
-   `getSQLState()` gibt den normalen X/Open- oder SQL99-Statuscode der Ausnahme zurück.
  
-   `getErrorCode()` gibt die jeweilige Datenbankfehlernummer zurück.
  
-   `getMessage()` gibt den vollständigen Text der Ausnahme zurück. Der Text der Fehlermeldung beschreibt das Problem und enthält häufig Platzhalter für Informationen wie Objektnamen, die in die angezeigte Fehlermeldung eingefügt werden.
  
-   `getNextException()` gibt das nächste `SQLServerException`-Objekt oder NULL zurück, wenn keine weiteren Ausnahmeobjekte mehr vorhanden sind.

-   `getSQLServerError()` gibt das `SQLServerError`-Objekt zurück, das ausführliche von SQL Server empfangene Informationen zur Ausnahme enthält. Diese Methode gibt NULL zurück, wenn kein Serverfehler aufgetreten ist.

Die folgenden Methoden der `SQLServerError`-Klasse können zum Abrufen zusätzlicher Informationen über den Fehler verwendet werden, der vom Server generiert wurde.

-   `SQLServerError.getErrorMessage()` gibt die vom Server empfangene Fehlermeldung zurück.

-   `SQLServerError.getErrorNumber()` gibt eine Zahl zurück, die zur Identifikation des Fehlertyps dient.

-   `SQLServerError.getErrorState()` gibt einen numerischen Fehlercode von SQL Server zurück, der einen Fehler, eine Warnung oder die Meldung „no data found“ (Keine Daten gefunden) darstellt.

-   `SQLServerError.getErrorSeverity()` gibt den Schweregrad des Fehlers zurück.

-   `SQLServerError.getServerName()` gibt den Namen des Computers zurück, auf dem die SQL Server-Instanz ausgeführt wird, die den Fehler generiert hat.

-   `SQLServerError.getProcedureName()` gibt den Namen der gespeicherten Prozedur oder des Remoteprozeduraufrufs zurück, der den Fehler generiert hat.

-   `SQLServerError.getLineNumber()` gibt die Zeilennummer im Transact-SQL-Befehlsbatch oder in der gespeicherten Prozedur zurück, die den Fehler generiert hat.
  
 Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben und eine fehlerhafte SQL-Anweisung ohne FROM-Klausel erstellt. Anschließend werden die Anweisung ausgeführt und eine SQL-Ausnahme verarbeitet.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagnostizieren von Problemen mit dem JDBC-Treiber](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
