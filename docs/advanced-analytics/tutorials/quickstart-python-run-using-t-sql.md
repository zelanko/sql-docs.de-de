---
title: Schnellstart für eine "Hallo Welt" grundlegende python-Codeausführung in T-SQL
description: Schnellstart für das Python-Skript in SQL Server. Lernen Sie die Grundlagen zum Aufrufen eines python-Skripts mithilfe der gespeicherten System Prozedur sp_execute_external_script in einer Hello-World-Übung kennen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/10/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: caa462fa6449d4d130ace629f99c8061c7b8a35f
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345497"
---
# <a name="quickstart-hello-world-python-script-in-sql-server"></a>Schnellstart: "Hello World"-Python-Skript in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Schnellstart lernen Sie wichtige Konzepte durch Ausführen eines "Hallo Welt"-python-Skripts int-SQL mit einer Einführung in die gespeicherte System Prozedur **sp_execute_external_script** . 

## <a name="prerequisites"></a>Vorraussetzungen

Eine vorherige Schnellstartanleitung: [überprüfen, ob python in SQL Server vorhanden](quickstart-python-verify.md)ist, enthält Informationen und Links zum Einrichten der für diese Schnellstartanleitung erforderlichen python-Umgebung.

## <a name="basic-python-interaction"></a>Grundlegende python-Interaktion

Es gibt zwei Möglichkeiten, um Python-Code in SQL Server auszuführen:

+ Fügen Sie ein Python-Skript als Argument der gespeicherten System Prozedur hinzu, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Stellen Sie von einem [python-Remote Client](../python/setup-python-client-tools-sql.md)aus eine Verbindung mit SQL Server her, und führen Sie Code mithilfe der SQL Server als computekontext aus. Dies erfordert [revoscalepy](../python/ref-py-revoscalepy.md).

Die folgende Übung konzentriert sich auf das erste Interaktionsmodell: übergeben von Python-Code an eine gespeicherte Prozedur.

1. Führen Sie einfachen Code aus, um zu sehen, wie Daten zwischen SQL Server und python hin-und hergeleitet werden.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

2. Vorausgesetzt, dass alles ordnungsgemäß eingerichtet ist, und Python und SQL Server miteinander kommunizieren, wird das richtige Ergebnis berechnet, und die python `print` -Funktion gibt das Ergebnis an die Fenster **Nachrichten** zurück.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    Während das erhalten **von stdout** -Nachrichten beim Testen Ihres Codes nützlich ist, müssen Sie die Ergebnisse häufiger im tabellarischen Format zurückgeben, damit Sie es in einer Anwendung verwenden oder in eine Tabelle schreiben können.

Beachten Sie vorerst die folgenden Regeln:

+ Alles innerhalb des `@script` Arguments muss gültiger Python-Code sein. 
+ Der Code muss alle python-Regeln bezüglich Einzug, Variablennamen usw. befolgen. Wenn Sie einen Fehler erhalten, überprüfen Sie Ihren Leerraum und die Schreibweise.
+ In Programmiersprachen ist Python eine der flexibelsten in Bezug auf einfache Anführungszeichen und doppelte Anführungszeichen. Sie sind sehr austauschbar. Allerdings verwendet T-SQL einfache Anführungszeichen nur für bestimmte Dinge, und `@script` das Argument verwendet einfache Anführungszeichen, um den Python-Code als Unicode-Zeichenfolge einzuschließen. Daher müssen Sie möglicherweise Ihren Python-Code überprüfen und einfache Anführungszeichen in doppelte Anführungszeichen ändern.
+ Wenn Sie Bibliotheken verwenden, die nicht standardmäßig geladen werden, müssen Sie eine Import-Anweisung am Anfang des Skripts verwenden, um Sie zu laden. SQL Server fügt mehrere produktspezifische Bibliotheken hinzu. Weitere Informationen finden Sie unter [python-Bibliotheken](../python/python-libraries-and-data-types.md).
+ Wenn die Bibliothek nicht bereits installiert ist, können Sie das Python-Paket wie hier beschrieben außerhalb SQL Server abbrechen und installieren: [Installieren neuer Python-Pakete unter SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="run-a-hello-world-script"></a>Ausführen eines Hallo Welt Skripts

In der folgenden Übung werden weitere einfache python-Skripts ausgeführt.

```sql
EXEC sp_execute_external_script
@language =N'Python',
@script=N'OutputDataSet = InputDataSet',
@input_data_1 =N'SELECT 1 AS hello'
WITH RESULT SETS (([Hello World] int));
GO
```

Zu den Eingaben für diese gespeicherte Prozedur gehören:

+ *@language* der Parameter definiert die aufzurufende Spracherweiterung, in diesem Fall python.
+ *@script* Parameter definiert die Befehle, die an die python-Laufzeit übergeben werden. Das gesamte Python-Skript muss in dieses Argument als Unicode-Text eingeschlossen werden. Sie können den Text auch einer Variablen des Typs **nvarchar** hinzufügen und die Variable anschließend aufrufen.
+ *@input_data_1* die von der Abfrage zurückgegebenen Daten, die an die python-Laufzeit übermittelt werden, die die Daten zurückgibt, die als Datenrahmen SQL Server werden.
+ WITH Result Sets-Klausel definiert das Schema der zurückgegebenen Datentabelle für SQL Server, wobei "Hallo Welt" als Spaltenname " **int** " für den Datentyp hinzugefügt wird.

**Ergebnisse**

| Hello World |
|-------------|
| 1 |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun einige einfache python-Skripts ausgeführt haben, sehen Sie sich die Strukturierung von Eingaben und Ausgaben genauer an.

> [!div class="nextstepaction"]
> [Schnellstart: Behandeln von Eingaben und Ausgaben](quickstart-python-inputs-and-outputs.md)
