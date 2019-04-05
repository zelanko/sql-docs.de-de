---
title: Schnellstart für eine einfache "Hello World"-Python-code der Ausführung in T-SQL – SQL Server-Machine Learning
description: Schnellstart für Python-Skript in SQL Server. Enthält die Grundlagen des Aufrufens von Python-Skript mit der gespeicherten Systemprozedur Sp_execute_external_script in einer Hallo-Welt-Übung.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: f5e93ce5261d79acf5bf5a7419992c81c872d680
ms.sourcegitcommit: 3cfedfeba377560d460ca3e42af1e18824988c07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2019
ms.locfileid: "59042219"
---
# <a name="quickstart-hello-world-python-script-in-sql-server"></a>Schnellstart: "Hello World"-Python-Skript in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser schnellstartanleitung erfahren Sie, wichtige Konzepte, die durch Ausführen einer "Hello World"-Python script InT-SQL, um eine Einführung in die **Sp_execute_external_script** gespeicherten Systemprozedur. 

## <a name="prerequisites"></a>Erforderliche Komponenten

Einen vorherigen schnellstartanleitung [Python überprüfen, die in SQL Server vorhanden ist](quickstart-python-verify.md), enthält Informationen und links für das Einrichten der Python-Umgebung, die im Rahmen dieser schnellstartanleitung benötigt.

## <a name="basic-python-interaction"></a>Grundlegende Python-Interaktion

Es gibt zwei Möglichkeiten zum Ausführen von Python-Code in SQL Server:

+ Fügen Sie ein Python-Skript als Argument der gespeicherten Systemprozedur, [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Aus einer [Python-Remoteclient](../python/setup-python-client-tools-sql.md), Verbinden mit SQL Server und Code mithilfe von SQL Server als Compute Context ausführen. Dies erfordert [Revoscalepy](../python/ref-py-revoscalepy.md).

In der folgenden Übung konzentriert sich auf das erste Interaktionsmodell: wie Python-Code an eine gespeicherte Prozedur übergeben.

1. Führen Sie Beispielcode dahingehend, wie Daten zwischen SQL Server und Python hin und her übergeben werden.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c(c, d))
    '
    ```

2. Vorausgesetzt, dass alles ordnungsgemäß eingerichtet haben, und Python und SQL Server sind miteinander reden, das richtige Ergebnis wird berechnet, und die Python- `print` Funktionsergebnis ist das Ergebnis der **Nachrichten** Windows.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    Beim Abrufen der **"stdout"** Nachrichten ist nützlich, beim Testen Ihres Codes, häufig müssen Sie die Ergebnisse in tabellarischer Form vorliegen, zurückgeben, damit Sie in einer Anwendung verwenden können, oder in einer Tabelle zu schreiben.

Denken Sie jetzt an diese Regeln:

+ Alles innerhalb der `@script` Argument muss ein gültiger Python-Code sein. 
+ Der Code muss es sich um alle Python-Regeln in Bezug auf den Einzug, Variablennamen usw. entsprechen. Wenn Sie eine Fehlermeldung erhalten, überprüfen Sie die Leerzeichen und die Groß-/Kleinschreibung aus.
+ Zwischen Programmiersprachen Python ist eine der flexibelsten im Hinblick auf die einfachen Anführungszeichen und doppelte Anführungszeichen eingeschlossen werden. Diese sind ziemlich austauschbar. T-SQL verwendet jedoch einfache Anführungszeichen für die nur bestimmte Dinge, und die `@script` Argument verwendet einfache Anführungszeichen, um den Python-Code als Unicode-Zeichenfolge einzuschließen. Aus diesem Grund müssen Sie zum Überprüfen von Python-Code, und ändern Sie einige einfache Anführungszeichen in doppelte Anführungszeichen.
+ Wenn Sie alle Bibliotheken verwenden, die nicht standardmäßig geladen werden, müssen Sie eine Import-Anweisung am Anfang des Skripts verwenden, um sie zu laden. SQL Server fügt verschiedene produktspezifische-Bibliotheken hinzu. Weitere Informationen finden Sie unter [Python-Bibliotheken](../python/python-libraries-and-data-types.md).
+ Wenn die Bibliothek noch nicht installiert ist, beenden Sie, und installieren Sie das Python-Paket außerhalb von SQL Server, wie hier beschrieben: [Installieren neuer Python-Pakete unter SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="run-a-hello-world-script"></a>Ausführen eines Hello World-Skripts

In der folgenden Übung wird einen anderen einfachen Python-Skripts ausgeführt.

```sql
EXEC sp_execute_external_script
@language =N'Python',
@script=N'OutputDataSet = InputDataSet',
@input_data_1 =N'SELECT 1 AS hello'
WITH RESULT SETS (([Hello World] int));
GO
```

Eingaben für diese gespeicherte Prozedur gehören:

+ *@language* der Parameter definiert die spracherweiterung, in diesem Fall Python aufrufen.
+ *@script* der Parameter definiert die Befehle an der Python-Laufzeit übergeben. Ihre gesamte Python-Skript muss diesem Argument als Unicode-Text eingeschlossen werden. Sie können den Text auch einer Variablen des Typs **nvarchar** hinzufügen und die Variable anschließend aufrufen.
+ *@input_data_1* werden Daten, die von der Python-Laufzeit, die die Daten mit SQL Server als dataframe zurückgibt, die an der Abfrage zurückgegeben wird.
+ WITH RESULT SETS-Klausel definiert das Schema der zurückgegeben Datentabelle für SQL Server, Hinzufügen von "Hello World" als den Namen der Spalte, **Int** für den Datentyp.

**Ergebnisse**

| Hallo Welt |
|-------------|
| 1 |

## <a name="next-steps"></a>Nächste Schritte

Nun, dass Sie eine Reihe von einfachen Python-Skripts ausgeführt haben, nehmen Sie einen genaueren Blick auf die Strukturierung von Eingaben und Ausgaben.

> [!div class="nextstepaction"]
> [Schnellstart: Arbeiten mit Eingaben und Ausgaben](quickstart-python-inputs-and-outputs.md)
