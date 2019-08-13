---
title: Ergebnisse werden verarbeitet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: rene-ye
ms.author: v-reye
manager: kenvh
ms.openlocfilehash: 163055a630f8e37678f99359a244bf211b035e7e
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68894072"
---
# <a name="parsing-the-results"></a>Analysieren der Ergebnisse

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

In diesem Artikel wird beschrieben, wie SQL Server erwartet, dass Benutzer von einer beliebigen Abfrage zurückgegebene Ergebnisse vollständig verarbeiten.

## <a name="update-counts-and-result-sets"></a>Aktualisieren von Zählungen und Resultsets

In diesem Abschnitt werden die beiden häufigsten Ergebnisse erläutert, die von SQL Server: Update count und Resultset zurückgegeben werden. Im Allgemeinen führt jede von einem Benutzer ausgeführte Abfrage dazu, dass eines dieser Ergebnisse zurückgegeben wird. Benutzer werden davon ausgehen, beide bei der Verarbeitung von Ergebnissen zu verarbeiten.

Der folgende Code ist ein Beispiel dafür, wie ein Benutzer alle Ergebnisse vom Server durchlaufen kann:
```java
try (Connection connection = DriverManager.getConnection(URL); Statement statement = connection.createStatement()) {
    boolean resultsAvailable = statement.execute(USER_SQL);
    int updateCount = -2;
    while (true) {
        updateCount = statement.getUpdateCount();
        if (!resultsAvailable && updateCount == -1)
            break;
        if (resultsAvailable) {
            // handle ResultSet
        } else {
            // handle Update Count
        }
        resultsAvailable = statement.getMoreResults();
    }
}
```

## <a name="exceptions"></a>Ausnahmen
Wenn Sie eine Anweisung ausführen, die zu einem Fehler oder einer Informations Meldung führt, reagieren SQL Server abhängig davon, ob ein Ausführungsplan generiert werden kann, unterschiedlich. Die Fehlermeldung kann sofort nach der Ausführung der Anweisung ausgelöst werden, da Sie möglicherweise ein separates Resultset erfordert. Im letzteren Fall müssen die Anwendungen das Resultset analysieren, um die Ausnahme abzurufen.

Wenn SQL Server keinen Ausführungsplan generieren kann, wird die Ausnahme sofort ausgelöst.

```java
String SQL = "SELECT * FROM nonexistentTable;";
try (Statement statement = connection.createStatement();) {
    statement.execute(SQL);
} catch (SQLException e) {
    e.printStackTrace();
}
```

Wenn SQL Server eine Fehlermeldung in einem Resultset zurückgibt, muss das Resultset verarbeitet werden, um die Ausnahme abzurufen.

```java
String SQL = "SELECT 1/0;";
try (Statement statement = connection.createStatement();) {
    boolean hasResult = statement.execute(SQL);
    if (hasResult) {
        try (ResultSet rs = statement.getResultSet()) {
            // Exception is thrown on next().
            while (rs.next()) {}
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

Wenn bei der Anweisungs Ausführung mehrere Resultsets generiert werden, muss jedes Resultset verarbeitet werden, bis das mit der Ausnahme erreicht wird.

```java
String SQL = "SELECT 1; SELECT * FROM nonexistentTable;";
try (Statement statement = connection.createStatement();) {
    // Does not throw an exception on execute().
    boolean hasResult = statement.execute(SQL);
    while (hasResult) {
        try (ResultSet rs = statement.getResultSet()) {
            while (rs.next()) {
                System.out.println(rs.getString(1));
            }
        }
        // Moves the next result set that generates the exception.
        hasResult = statement.getMoreResults();
    }
} catch (SQLException e) {
    e.printStackTrace();
}
```

Im Fall von `String SQL = "SELECT * FROM nonexistentTable; SELECT 1;";`wird die Ausnahme `execute()` sofort ausgelöst und `SELECT 1` überhaupt nicht ausgeführt.

Wenn der Fehler von SQL Server den Schweregrad `0` `9`hat, wird er als Informations Meldung betrachtet und als `SQLWarning`zurückgegeben.

```java
String SQL = "RAISERROR ('WarningLevel5', 5, 2);";
try (Statement statement = connection.createStatement();) {
    boolean hasResult = statement.execute(SQL);
    SQLWarning warning = statement.getWarnings();
    System.out.println(warning);
}
```

## <a name="see-also"></a>Siehe auch

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)
