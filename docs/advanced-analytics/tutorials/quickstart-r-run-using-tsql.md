---
title: Schnellstart für eine "Hallo Welt" grundlegende R-Codeausführung in T-SQL
description: Schnellstart für R-Skript in SQL Server. Erlernen Sie die Grundlagen zum Aufrufen von R-Skripts mithilfe der gespeicherten System Prozedur sp_execute_external_script in einer Hello-World-Übung.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 61b1959b9b3b0769e080a2a4a44b1d4d10ef2b61
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345976"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Schnellstart: "Hello World" R-Skript in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Schnellstart lernen Sie die wichtigsten Konzepte kennen, indem Sie ein "Hallo Welt" R-Skript int-SQL mit einer Einführung in die gespeicherte System Prozedur **sp_execute_external_script** ausführen. 

## <a name="prerequisites"></a>Vorraussetzungen

Eine vorherige Schnellstartanleitung, [überprüfen, ob R in SQL Server vorhanden](quickstart-r-verify.md)ist, enthält Informationen und Links zum Einrichten der r-Umgebung, die für diesen Schnellstart erforderlich ist.

## <a name="basic-r-interaction"></a>Grundlegende R-Interaktion

Es gibt zwei Möglichkeiten zum Ausführen von R-Code in SQL-Datenbank:

+ Fügen Sie ein R-Skript als Argument der gespeicherten System Prozedur hinzu, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).
+ Stellen Sie von einem [Remote-R-Client](https://docs.microsoft.com/sql/advanced-analytics/r/set-up-a-data-science-client)aus eine Verbindung mit Ihrer SQL-Datenbank her, und führen Sie Code mithilfe der SQL-Datenbank als computekontext aus.

Die folgende Übung konzentriert sich auf das erste Interaktionsmodell: übergeben von R-Code an eine gespeicherte Prozedur.

1. Ausführen eines einfachen Skripts, um zu sehen, wie ein R-Skript in der SQL-Datenbank ausgeführt wird.

    ```sql
    EXECUTE sp_execute_external_script
    @language = N'R',
    @script = N'
    a <- 1
    b <- 2
    c <- a/b
    d <- a*b
    print(c(c, d))
    '
    ```

2. Vorausgesetzt, dass alles ordnungsgemäß eingerichtet ist, wird das richtige Ergebnis berechnet, und `print` die R-Funktion gibt das Ergebnis an das Fenster **Meldungen** zurück.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    Während das erhalten **von stdout** -Nachrichten beim Testen Ihres Codes nützlich ist, müssen Sie die Ergebnisse häufiger im tabellarischen Format zurückgeben, damit Sie es in einer Anwendung verwenden oder in eine Tabelle schreiben können. Siehe [Schnellstart: Behandeln von Eingaben und Ausgaben mithilfe von R](rtsql-working-with-inputs-and-outputs.md) in SQL Server, um weitere Informationen zu finden.

Beachten Sie, dass alles `@script` innerhalb des Arguments gültiger R-Code sein muss.

## <a name="run-a-hello-world-script"></a>Ausführen eines Hallo Welt Skripts

In der folgenden Übung werden weitere einfache R-Skripts ausgeführt.

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'OutputDataSet<-InputDataSet',
  @input_data_1 =N'SELECT 1 AS hello'
  WITH RESULT SETS (([Hello World] int));
GO
```

Zu den Eingaben für diese gespeicherte Prozedur gehören:

+ *@language* der Parameter definiert die aufzurufende Spracherweiterung, in diesem Fall R.
+ *@script* Parameter definiert die Befehle, die an die R-Laufzeit übergeben werden. Ihr gesamtes R-Skript muss von diesem Argument als Unicode-Text umschlossen sein. Sie können den Text auch einer Variablen des Typs **nvarchar** hinzufügen und die Variable anschließend aufrufen.
+ *@input_data_1* die von der Abfrage zurückgegebenen Daten, die an die R-Laufzeit zurückgegeben werden, die die Daten zurückgibt, die als Datenrahmen SQL Server werden.
+ WITH Result Sets-Klausel definiert das Schema der zurückgegebenen Datentabelle für SQL Server, wobei "Hallo Welt" als Spaltenname " **int** " für den Datentyp hinzugefügt wird.

**Ergebnisse**

| Hello World |
|-------------|
| 1 |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun einige einfache R-Skripts ausgeführt haben, sehen Sie sich die Strukturierung von Eingaben und Ausgaben genauer an.

> [!div class="nextstepaction"]
> [Schnellstart: Behandeln von Eingaben und Ausgaben](quickstart-r-inputs-and-outputs.md)
