---
title: Verwenden von Python zum Erstellen eines Modells mit Revoscalepy | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5c8ff387c3abda3f147700dce6349009a027a778
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461956"
---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Verwenden von Python mit Revoscalepy zum Erstellen eines Modells
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser Lektion erfahren Sie, wie Sie Python-Code von einem Remotecomputer aus zum Entwickeln-Client, zum Erstellen eines linearen Regressionsmodells in SQL Server ausführen. 

## <a name="prerequisites"></a>Erforderliche Komponenten

+ In dieser Lektion werden unterschiedliche Daten als die vorherigen Lektionen verwendet. Sie müssen nicht die vorherigen Lektionen abgeschlossen. Jedoch wenn Sie die vorherigen Lektionen abgeschlossen haben und einen Server, führen Sie Python bereits konfiguriert haben, verwenden Sie dieses Servers und der Datenbank als computekontext.
+ Zum Ausführen von Python-Code mithilfe von SQL Server als ein Compute erfordert Kontext für SQLServer 2017 oder höher. Darüber hinaus müssen Sie explizit installieren und aktivieren dann das Feature, **Machine Learning Services**, die Python-Language-Option auswählen.

    Wenn Sie eine Vorabversion von SQL Server 2017 installiert haben, sollten Sie auf mindestens die RTM-Version aktualisieren. Spätere Dienstversionen wurde weiter erweitern und die Python-Funktionen. Einige Funktionen in diesem Tutorial funktionieren möglicherweise nicht in frühen Vorabversionen.

+ Dieses Beispiel verwendet eine vordefinierte Python-Umgebung, mit dem Namen `PYTEST_SQL_SERVER`. Die Umgebung konfiguriert wurde, dass enthalten **Revoscalepy** und anderen erforderlichen Bibliotheken. 

    Wenn Sie keine Umgebung zum Ausführen von Python konfiguriert haben, müssen Sie das separat dafür. Eine Erläuterung zum Erstellen oder ändern die Python-Umgebungen ist außerhalb des gültigen Bereichs für dieses Tutorial. Weitere Informationen zum Einrichten einer Python-Client, der die richtigen Bibliotheken enthält, finden Sie unter [Installieren von Python-Client](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) und [Link Python Tools](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools).

## <a name="remote-compute-contexts-and-revoscalepy"></a>Remotecomputekontexte "und" revoscalepy

In diesem Beispiel wird veranschaulicht, wie erstellen ein Python-Modell in einem _compute Context verwenden_, mit dem Sie arbeiten, die von einem Client, jedoch eine Remoteumgebung, z. B. SQL Server, Spark und Machine Learning-Server, in dem die Vorgänge werden tatsächlich ausgeführt werden. Mithilfe von berechneten Kontexten erleichtert es, Code einmal schreiben und in jeder Umgebung bereitstellen.

Zum Ausführen von Python-Code in SQL Server erfordert die **Revoscalepy** Paket. Dies ist eine spezielle Python-Paket bereitgestellt, die von Microsoft, ähnlich wie die **RevoScaleR** -Paket für die R-Sprache. Die **Revoscalepy** Paket unterstützt die Erstellung von berechneten Kontexten und stellt die Infrastruktur für die Übergabe von Daten und Modelle zwischen einer lokalen Arbeitsstation und einem Remoteserver. Die **Revoscalepy** Funktion, die codeausführung in der Datenbank wird unterstützt [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

In dieser Lektion verwenden Sie Daten in SQL Server zum Trainieren eines linearen Modells basierend auf [Rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), einer Funktion in **Revoscalepy** , Regression sehr großer Datasets unterstützt. 

In dieser Lektion wird auch die Grundlagen zum Einrichten und verwenden Sie dann eine **SQL Server-computekontext** in Python. Eine Erläuterung der computekontexte arbeiten mit anderen Plattformen und dem berechnetem Kontext verwendet werden, finden Sie unter [für die Ausführung des Skripts in Machine Learning Server-Computekontext.](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)

## <a name="prepare-the-database-and-sample-data"></a>Vorbereiten der Daten der Datenbank und Beispiel

1. In dieser Lektion wird die Datenbank verwendet **Sqlpy**. Wenn Sie keine vorherigen Lektionen abgeschlossen haben, können Sie die Datenbank erstellen, durch Ausführen des folgenden Codes:

    ```sql
    CREATE DATABASE sqlpy;
    GO
    USE sqlpy;
    GO
    ```

    > [!IMPORTANT]
    > Wenn Sie eine andere Datenbank verwenden möchten, achten Sie darauf, dass Sie die Beispielcode bearbeiten und den Datenbanknamen in der Verbindungszeichenfolge ändern.

2. Dieses Beispiel verwendet das Fluglinien-Dataset, die in R und Python verfügbar ist. Nachdem Sie eine Datenbank für Ihre Python-Beispiele erstellt haben, eine Tabelle mit Daten füllen, wie hier beschrieben: [Datenstichproben in RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/sample-built-in-data).

3. Ändern Sie den Namen der Umgebung auf dem Client die Verwendung eine Umgebung zur Verfügung.

## <a name="run-the-sample-code"></a>Ausführen des Beispielcodes

Nachdem Sie die Datenbank vorbereitet haben und die Daten für das Training in einer Tabelle gespeichert, öffnen Sie eine Python-Entwicklungsumgebung, und Ausführen des Codebeispiels.

Der Code führt die folgenden Schritte aus:

1. Importiert die erforderlichen Bibliotheken und Funktionen.
2. Erstellt eine Verbindung mit SQL Server. Erstellt **Datenquelle** Objekte für die Arbeit mit den Daten.
3. Ändert die Daten mit **Transformationen** , damit sie von den logistic Regression-Algorithmus verwendet werden kann.
4. Aufrufe `rx_lin_mod` und definiert die Formel verwendet, um das Modell anzupassen.
5. Generiert einen Satz von Vorhersagen basierend auf den ursprünglichen Daten.
6. Eine Zusammenfassung, die basierend auf den vorhergesagten Werten erstellt.

Alle Vorgänge werden mit einer Instanz von SQL Server als Compute Context ausgeführt.

> [!NOTE]
> Eine Demonstration dieses Beispiels über die Befehlszeile ausgeführt wird, finden Sie in diesem Video: [SQL Server 2017-Advanced Analytics mit Python](https://www.youtube.com/watch?v=FcoY795jTcc)

### <a name="sample-code"></a>Beispielcode

```python
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_lin_mod, rx_predict, rx_summary
from revoscalepy import RxOptions, rx_import

import os

def test_linmod_sql():
    sql_server = os.getenv('PYTEST_SQL_SERVER', '.')
    
    sql_connection_string = 'Driver=SQL Server;Server=' + sqlServer + ';Database=sqlpy;Trusted_Connection=True;'
    print("connectionString={0!s}".format(sql_connection_string))

    data_source = RxSqlServerData(
        sql_query = "select top 10 * from airlinedemosmall",
        connection_string = sql_connection_string,

        column_info = {
            "ArrDelay" : { "type" : "integer" },
            "DayOfWeek" : {
                "type" : "factor",
                "levels" : [ "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday" ]
            }
        })

    sql_compute_context = RxInSqlServer(
        connection_string = sql_connection_string,
        num_tasks = 4,
        auto_cleanup = False
        )

    #
    # Run linmod locally
    #
    linmod_local = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source)
    #
    # Run linmod remotely
    #
    linmod = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)

    # Predict results
    # 
    predict = rx_predict(linmod, data = rx_import(input_data = data_source))
    summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)
```

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>Definieren einer Datenquelle und das Definieren eines computekontexts

Eine Datenquelle unterscheidet sich von einem rechenkontext. Die _Datenquelle_ definiert die Daten in Ihrem Code verwendet. Die _computekontext_ definiert, in dem der Code ausgeführt wird. Jedoch verwenden einige der Informationen:

+ Python-Variablen, wie z. B. `sql_query` und `sql_connection_string`, definieren Sie die Quelle der Daten. 

    Diese Variablen zum Übergeben der [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) Konstruktor implementieren die **Datenquellenobjekt** mit dem Namen `data_source`.

+ Sie erstellen eine **computekontext-Objekt** mithilfe der [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata) Konstruktor. Die resultierende **computekontext-Objekt** heißt `sql_cc`.

    Dieses Beispiel verwendet die gleiche Verbindungszeichenfolge, mit dem Sie erneut in der Datenquelle, auf der Annahme, die die Daten auf dieselbe SQL Server-Instanz, die Sie als Compute Context verwenden möchten. 
    
    Allerdings können die Datenquelle und den computekontext auf verschiedenen Servern sein.
 
### <a name="changing-compute-contexts"></a>Ändern von berechneten Kontexten

Nachdem Sie einen computekontext definiert haben, müssen Sie festlegen der **aktiven computekontext**. 

In der Standardeinstellung die meisten Vorgänge werden lokal ausgeführt wird, was bedeutet, dass, wenn Sie einen anderen computekontext nicht angeben, die Daten werden aus der Datenquelle abgerufen werden und der Code in die aktuelle Python-Umgebung ausgeführt wird.

Es gibt zwei Möglichkeiten, den aktiven computekontext festzulegen:
+ Als Argument einer Methode oder Funktion
+ Durch den Aufruf `rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Festlegen des computekontexts als Argument einer Methode oder Funktion

In diesem Beispiel ist Sie den computekontext festlegen, indem Sie mit dem Argument der einzelnen **Rx** Funktion.
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Dieser rechenkontext wird im Aufruf wiederverwendet [Rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):.

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Festlegen eines computekontexts explizit mit rx_set_compute_context

Die Funktion [Rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) können Sie zwischen computekontexte, die bereits definiert wurden.

Nachdem Sie festgelegt haben der aktiven computekontext, er bleibt aktiv, bis Sie ihn ändern.

### <a name="using-parallel-processing-and-streaming"></a>Mithilfe von parallelen Verarbeitung und streaming

Wenn Sie den computekontext definieren, können Sie auch Parameter dieses Steuerelements festlegen wie die Daten von den computekontext verarbeitet werden. Diese Parameter variieren je nach Typ der Datenquelle.

Sie können für SQL Server-rechenkontext legen Sie die Batchgröße oder Hinweise gibt den Grad an Parallelität in ausgeführten Aufgaben verwenden.

+ Ausführen des Beispiels wurde auf einem Computer mit vier Prozessoren, sodass die `num_tasks` -Parameter auf 4 festgelegt ist, um maximale Nutzung von Ressourcen zu ermöglichen. 
+ Wenn Sie diesen Wert auf 0 festlegen, verwendet SQL Server Standard, um so viele Aufgaben parallel ausgeführt werden, wie möglich in den aktuellen MAXDOP-Einstellungen für den Server an. Allerdings hängt die genaue Anzahl der Aufgaben, die möglicherweise viele andere Faktoren, z. B. Server-Einstellungen und andere Aufträge, die ausgeführt werden.

## <a name="related-samples"></a>Beispiele

Diese zusätzliche Python-Beispiele und Tutorials zeigen die End-to-End-Szenarien, die mit komplexen Datenquellen sowie die Verwendung von remotecomputekontexte.

+ [In-Database Python für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md)
+ [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
