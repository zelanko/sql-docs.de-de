---
title: Erstellen eines Modells in SQL Server mithilfe von Python mit Revoscalepy | Microsoft-Dokumentation
description: Schreiben Sie Python-Skript mithilfe von Revoscalepy-Funktionen zum Erstellen von Data Science-Modelle, die in SQL Server remote ausführen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f554badcba282bad7fb386daf8c4c0f4106804b4
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100161"
---
# <a name="use-python-with-revoscalepy-to-create-a-model-that-runs-remotely-on-sql-server"></a>Verwenden von Python mit Revoscalepy zum Erstellen eines Modells, das per Remotezugriff auf SQL Server ausgeführt wird
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die [Revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) Python-Bibliothek von Microsoft bietet Data Science-Algorithmen für das Durchsuchen von Daten, Visualisierung, Analyse und Transformationen. Diese Bibliothek enthält die strategische Bedeutung in Integrationsszenarien für Python in SQL Server. Auf einem Server mit mehreren Kernen **Revoscalepy** Funktionen parallel ausgeführt werden können. In einer verteilten Architektur mit einem zentralen Server und Client-Arbeitsstationen (trennen Sie die physischen Computer, die alle den gleichen **Revoscalepy** Bibliothek), können Sie Python-Code, der lokal gestartet, aber dann verschiebt der Ausführung Schreiben einer Remote SQL Server-Instanz, in dem Daten gespeichert.

Sie finden die **Revoscalepy** in der folgenden Microsoft-Produkte und -Distributionen:

+ [SQL Server Machine Learning-Dienste (datenbankintern)](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server (nicht-SQL, eigenständiger Server)](https://docs.microsoft.com/machine-learning-server/index)
+ [Der clientseitigen Python-Bibliotheken (für Entwicklungsarbeitsstationen)](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) 

In dieser Übung veranschaulicht, wie ein lineares Regressionsmodell basierend auf [Rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), einen der Algorithmen in **Revoscalepy** , computekontext als Eingabe akzeptiert. Der Code in dieser Übung Sie führen verschiebt die Ausführung von Code aus einer lokalen, um remote Compute-Umgebung, aktiviert, indem **Revoscalepy** Funktionen, mit denen eine Remote-computekontext.

Nach Abschluss dieses Lernprogramms erfahren Sie, wie Sie:

> [!div class="checklist"]
> * Verwendung **Revoscalepy** zum Erstellen eines linearen Modells
> * Shift-Vorgänge von "lokal" auf dem entfernten computekontext

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser Übung verwendeten Beispieldaten sind die [ **Flightdata** ](demo-data-airlinedemo-in-sql.md) Datenbank.

Sie benötigen eine IDE zum Ausführen des Beispielcodes in diesem Artikel, und die IDE mit der ausführbaren Python-Datei verknüpft werden muss.

Um die Verwendung eine Compute-Schicht Kontext üben möchten, müssen Sie eine [lokalen Arbeitsstation](../python/setup-python-client-tools-sql.md) und eine SQL Server-Datenbank-Engine-Instanz mit [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) und Python aktiviert. 

> [!Tip]
> Wenn Sie nicht über zwei Computer verfügen, können Sie einen remotecomputekontext auf einem physischen Computer simulieren, durch die Installation von relevanten Anwendungen. Zunächst wird eine Installation von [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) als "remote"-Instanz ausgeführt wird. Sekunde, eine Installation von der [Python-Clientbibliotheken arbeitet](../python/setup-python-client-tools-sql.md) wie der Client. Sie haben zwei Kopien der gleichen Python-Distribution und Microsoft Python-Bibliotheken auf dem gleichen Computer. Sie müssen zum Nachverfolgen Dateipfade und welcher Kopie der Python.exe Verwendung in dieser Übung erfolgreich abgeschlossen.

## <a name="remote-compute-contexts-and-revoscalepy"></a>Remotecomputekontexte "und" revoscalepy

Dieses Beispiel veranschaulicht den Prozess zum Erstellen einer Python-Modell in einem remotecomputekontext, wodurch Sie von einem Client zu arbeiten, aber wählen Sie eine remote-Umgebung, z. B. SQL Server, Spark und Machine Learning-Server, in denen die Vorgänge tatsächlich ausgeführt werden. Remotecomputekontext wird, schalten die Berechnung an, in dem sich die Daten befinden.

Zum Ausführen von Python-Code in SQL Server erfordert die **Revoscalepy** Paket. Dies ist eine spezielle Python-Paket bereitgestellt, die von Microsoft, ähnlich wie die **RevoScaleR** -Paket für die R-Sprache. Die **Revoscalepy** Paket unterstützt die Erstellung von berechneten Kontexten und stellt die Infrastruktur für die Übergabe von Daten und Modelle zwischen einer lokalen Arbeitsstation und einem Remoteserver. Die **Revoscalepy** Funktion, die codeausführung in der Datenbank wird unterstützt [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

In dieser Lektion verwenden Sie Daten in SQL Server zum Trainieren eines linearen Modells basierend auf [Rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), einer Funktion in **Revoscalepy** , Regression sehr großer Datasets unterstützt. 

In dieser Lektion wird auch die Grundlagen zum Einrichten und verwenden Sie dann eine **SQL Server-computekontext** in Python. Eine Erläuterung der computekontexte arbeiten mit anderen Plattformen und dem berechnetem Kontext verwendet werden, finden Sie unter [computekontext für die Ausführung des Skripts in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).


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

Eine Datenquelle unterscheidet sich von einem rechenkontext. Die *Datenquelle* definiert die Daten in Ihrem Code verwendet. Der computekontext definiert, in dem der Code ausgeführt wird. Jedoch verwenden einige der Informationen:

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

Dieser rechenkontext wird im Aufruf wiederverwendet [Rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Festlegen eines computekontexts explizit mit rx_set_compute_context

Die Funktion [Rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) können Sie zwischen computekontexte, die bereits definiert wurden.

Nachdem Sie festgelegt haben der aktiven computekontext, er bleibt aktiv, bis Sie ihn ändern.

### <a name="using-parallel-processing-and-streaming"></a>Mithilfe von parallelen Verarbeitung und streaming

Wenn Sie den computekontext definieren, können Sie auch Parameter dieses Steuerelements festlegen wie die Daten von den computekontext verarbeitet werden. Diese Parameter variieren je nach Typ der Datenquelle.

Sie können für SQL Server-rechenkontext legen Sie die Batchgröße oder Hinweise gibt den Grad an Parallelität in ausgeführten Aufgaben verwenden.

+ Ausführen des Beispiels wurde auf einem Computer mit vier Prozessoren, sodass die `num_tasks` -Parameter auf 4 festgelegt ist, um maximale Nutzung von Ressourcen zu ermöglichen. 
+ Wenn Sie diesen Wert auf 0 festlegen, verwendet SQL Server Standard, um so viele Aufgaben parallel ausgeführt werden, wie möglich in den aktuellen MAXDOP-Einstellungen für den Server an. Allerdings hängt die genaue Anzahl der Aufgaben, die möglicherweise viele andere Faktoren, z. B. Server-Einstellungen und andere Aufträge, die ausgeführt werden.

## <a name="next-steps"></a>Nächste Schritte

Diese zusätzliche Python-Beispiele und Tutorials zeigen die End-to-End-Szenarien, die mit komplexen Datenquellen sowie die Verwendung von remotecomputekontexte.

+ [In-Database Python für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md)
+ [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
