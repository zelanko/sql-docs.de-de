---
title: Schnellstart für eine "Hello World" grundlegende R-codeausführung in T-SQL – SQL Server-Machine Learning
description: Schnellstart für R-Skript in SQL Server. Enthält die Grundlagen des Aufrufens von R-Skripts mithilfe der gespeicherten Systemprozedur Sp_execute_external_script in einer Hallo-Welt-Übung.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 1c3ee703bca46bf46dba8225e1d28da3174dc932
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59240168"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Schnellstart: "Hello World"-R-Skript in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser schnellstartanleitung erfahren Sie, wichtige Konzepte, die durch Ausführen einer "Hello World" R-Skript InT-SQL, um eine Einführung in die **Sp_execute_external_script** gespeicherten Systemprozedur. 

## <a name="prerequisites"></a>Erforderliche Komponenten

Einen vorherigen schnellstartanleitung [R stellen Sie sicher, die in SQL Server vorhanden ist](quickstart-r-verify.md), enthält Informationen und links für das Einrichten der R-Umgebung, die im Rahmen dieser schnellstartanleitung benötigt.

## <a name="basic-r-interaction"></a>Grundlegende R-Interaktion

Es gibt zwei Möglichkeiten, die Sie R-Code in SQL-Datenbank ausführen können:

+ Hinzufügen von R-Skript als Argument der gespeicherten Systemprozedur, [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).
+ Aus einem [remote-R-Client](https://docs.microsoft.com/sql/advanced-analytics/r/set-up-a-data-science-client), eine Verbindung mit Ihrer SQL-Datenbank herstellen und Code mithilfe der SQL-Datenbank als Compute Context ausführen.

In der folgenden Übung konzentriert sich auf das erste Interaktionsmodell: das R-Code an eine gespeicherte Prozedur übergeben.

1. Führen Sie ein einfaches Skript, um festzustellen, wie ein R-Skript in SQL-Datenbank ausgeführt wird.

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

2. Vorausgesetzt, dass alles ordnungsgemäß zum richtigen Ergebnis eingerichtet haben, wird berechnet, und die R `print` Funktionsergebnis ist das Ergebnis der **Nachrichten** Fenster.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    Beim Abrufen der **"stdout"** Nachrichten ist nützlich, beim Testen Ihres Codes, häufig müssen Sie die Ergebnisse in tabellarischer Form vorliegen, zurückgeben, damit Sie in einer Anwendung verwenden können, oder in einer Tabelle zu schreiben. Finden Sie unter [Schnellstart: Handle Eingaben und Ausgaben mithilfe von R in SQL Server](rtsql-working-with-inputs-and-outputs.md) für Weitere Informationen.

Beachten Sie, dass alles innerhalb der `@script` Argument muss ein gültiger R-Code sein.

## <a name="run-a-hello-world-script"></a>Ausführen eines Hello World-Skripts

In der folgenden Übung wird eine andere einfache R-Skripts ausgeführt.

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'OutputDataSet<-InputDataSet',
  @input_data_1 =N'SELECT 1 AS hello'
  WITH RESULT SETS (([Hello World] int));
GO
```

Eingaben für diese gespeicherte Prozedur gehören:

+ *@language* Parameter definiert, die in diesem Fall r aufrufen, durch die spracherweiterung
+ *@script* der Parameter definiert die Befehle, die an die R-Laufzeit übergeben. Ihr gesamtes R-Skript muss von diesem Argument als Unicode-Text umschlossen sein. Sie können den Text auch einer Variablen des Typs **nvarchar** hinzufügen und die Variable anschließend aufrufen.
+ *@input_data_1* werden Daten, die von der R-Laufzeit, die die Daten mit SQL Server als dataframe zurückgibt, die an der Abfrage zurückgegeben wird.
+ WITH RESULT SETS-Klausel definiert das Schema der zurückgegeben Datentabelle für SQL Server, Hinzufügen von "Hello World" als den Namen der Spalte, **Int** für den Datentyp.

**Ergebnisse**

| Hallo Welt |
|-------------|
| 1 |

## <a name="next-steps"></a>Nächste Schritte

Nun, dass Sie ein paar einfache R-Skripts ausgeführt haben, nehmen Sie einen genaueren Blick auf die Strukturierung von Eingaben und Ausgaben.

> [!div class="nextstepaction"]
> [Schnellstart: Arbeiten mit Eingaben und Ausgaben](quickstart-r-inputs-and-outputs.md)
