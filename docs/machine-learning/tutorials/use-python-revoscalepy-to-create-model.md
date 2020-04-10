---
title: Erstellen eines Python-Modells – revoscalepy
description: Schreiben Sie ein Python-Skript mithilfe von revoscalepy-Funktionen, um Data Science-Modelle zu erstellen, die remote in SQL Server ausgeführt werden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5faa8688f3036f80b947ccc5d99c09c4612f26fb
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116023"
---
# <a name="use-python-with-revoscalepy-to-create-a-model-that-runs-remotely-on-sql-server"></a>Verwenden von Python mit revoscalepy, um ein Modell zu erstellen, das remote auf SQL Server ausgeführt wird.
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)-Python-Bibliothek von Microsoft stellt Data Science-Algorithmen für das Durchsuchen von Daten, Visualisierung, Transformationen und Analysen bereit. Diese Bibliothek hat in Python-Integrationsszenarien in SQL Server strategische Bedeutung. Auf einem Multi-Core-Server können **revoscalepy**-Funktionen parallel ausgeführt werden. In einer verteilten Architektur mit einem zentralen Server und Clientarbeitsstationen (separate physische Computer, die alle über dieselbe **revoscalepy**-Bibliothek verfügen), können Sie Python-Code schreiben, der lokal startet, aber dann die Ausführung auf eine Remote-SQL Server-Instanz verlagert, auf der sich die Daten befinden.

Sie finden **revoscalepy** in den folgenden Microsoft-Produkten und -Distributionen:

+ [SQL Server Machine Learning Services (datenbankintern)](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server (eigenständig)](https://docs.microsoft.com/machine-learning-server/index)
+ [Installieren von Python-Clientbibliotheken für Remotezugriff auf einen Machine Learning-Server](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) 

Diese Übung veranschaulicht, wie ein lineares Regressionsmodell erstellt wird, das auf [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) basiert, einem der Algorithmen in **revoscalepy**, der Computekontext als Eingabe akzeptiert. Der Code, den Sie in dieser Übung ausführen, verschiebt die Codeausführung von einer lokalen in eine Remotecomputingumgebung, die durch **revoscalepy**-Funktionen aktiviert wird, die einen Remotecomputekontext aktivieren.

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Verwenden von **revoscalepy** zum Erstellen eines linearen Modells
> * Verschieben von Vorgängen von lokalem zu Remotecomputekontext

## <a name="prerequisites"></a>Voraussetzungen

Die Beispieldaten werden in dieser Übung der [**flightdata**](demo-data-airlinedemo-in-sql.md)-Datenbank entnommen.

Sie benötigen eine IDE, um den Beispielcode in diesem Artikel auszuführen, und die IDE muss mit der ausführbaren Python-Datei verknüpft werden.

Um eine Verschiebung des Computekontexts zu üben, benötigen Sie eine [lokale Arbeitsstation](../python/setup-python-client-tools-sql.md) und eine SQL Server-Datenbank-Engine-Instanz, auf denen [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) und Python aktiviert sind. 

> [!Tip]
> Wenn Sie nicht über zwei Computer verfügen, können Sie einen Remotecomputekontext auf einem physischen Computer simulieren, indem Sie relevante Anwendungen installieren. Zuerst fungiert eine Installation von [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) als „Remoteinstanz“. Zweitens fungiert eine Installation der [Python-Clientbibliotheken](../python/setup-python-client-tools-sql.md) als Client. Auf demselben Computer verfügen Sie über zwei Kopien derselben Python-Distribution und Microsoft Python-Bibliotheken. Sie müssen Dateipfade nachverfolgen, und welche Kopie von „Python.exe“ Sie zum erfolgreichen Abschluss der Übung verwenden.

## <a name="remote-compute-contexts-and-revoscalepy"></a>Remotecomputekontexte und revoscalepy

Dieses Beispiel veranschaulicht den Prozess der Erstellung eines Python-Modells in einem Remotecomputekontext, in dem Sie von einem Client aus arbeiten, aber eine Remoteumgebung wie z. B. SQL Server, Spark oder Machine Learning Server auswählen, in der die Vorgänge tatsächlich ausgeführt werden. Das Ziel des Remotecomputekontexts besteht darin, die Berechnung an den Speicherort der Daten zu bringen.

Zum Ausführen von Python-Code in SQL Server ist das **revoscalepy**-Paket erforderlich. Dabei handelt es sich um ein von Microsoft bereitgestelltes spezielles Python-Paket, das dem **RevoScaleR**-Paket für die Sprache R ähnelt. Das **revoscalepy**-Paket unterstützt die Erstellung von Computekontexten und stellt die Infrastruktur zur Übergabe von Daten und Modellen zwischen einer lokalen Arbeitsstation und einem Remoteserver bereit. Die **revoscalepy**-Funktion, die die datenbankinterne Codeausführung unterstützt, ist [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

In dieser Lektion verwenden Sie Daten in SQL Server, um ein lineares Modell basierend auf [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) zu trainieren, einer Funktion in **revoscalepy**, die die Regression über sehr große Datasets unterstützt. 

Diese Lektion veranschaulicht auch die Grundlagen der Einrichtung und anschließenden Verwendung eines **SQL Server-Computekontexts** in Python. Eine Erläuterung dazu, wie Computekontexte mit anderen Plattformen funktionieren, und welche Computekontexte unterstützt werden, finden Sie unter [Computekontext für die Skriptausführung in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).


## <a name="run-the-sample-code"></a>Ausführen des Beispiels

Nachdem Sie die Datenbank vorbereitet und die Daten für das Training in einer Tabelle gespeichert haben, öffnen Sie eine Python-Entwicklungsumgebung, und führen Sie das Codebeispiel aus.

Der Code führt die folgenden Schritte aus:

1. Importieren der erforderlichen Bibliotheken und Funktionen.
2. Erstellen einer Verbindung mit SQL Server. Erstellen von **Datenquellen**-Objekten zum Arbeiten mit den Daten.
3. Ändern der Daten mithilfe von **Transformationen**, sodass sie vom logistischen Regressionsalgorithmus verwendet werden können.
4. Aufrufen von `rx_lin_mod` und Definieren der Formel zum Anpassen des Modells.
5. Generieren eines Satzes von Vorhersagen basierend auf den ursprünglichen Daten.
6. Erstellen einer Zusammenfassung basierend auf den vorhergesagten Werten.

Alle Vorgänge werden mithilfe einer Instanz von SQL Server als Computekontext ausgeführt.

> [!NOTE]
> Eine Demonstration dieses Beispiels, das in der Befehlszeile ausgeführt wird, finden Sie in diesem Video: [SQL Server 2017 Advanced Analytics mit Python](https://www.youtube.com/watch?v=FcoY795jTcc)

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

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>Definieren einer Datenquelle im Vergleich zum Definieren eines Computekontexts

Eine Datenquelle unterscheidet sich von einem Computekontext. Die *Datenquelle* definiert die Daten, die in Ihrem Code verwendet werden. Der Computekontext definiert, wo der Code ausgeführt wird. Dabei werden jedoch einige identische Informationen verwendet:

+ Python-Variablen wie `sql_query` und `sql_connection_string` definieren die Quelle der Daten. 

    Übergeben Sie diese Variablen an den [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata)-Konstruktor, um das **Datenquellenobjekt** mit dem Namen `data_source` zu implementieren.

+ Sie erstellen ein **Computekontextobjekt** mithilfe des [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver)-Konstruktors. Das resultierende **Computekontextobjekt** heißt `sql_cc`.

    In diesem Beispiel wird die Verbindungszeichenfolge wiederverwendet, die Sie in der Datenquelle verwendet haben, wobei angenommen wird, dass sich die Daten auf derselben SQL Server-Instanz befinden, die Sie als Computekontext verwenden. 
    
    Die Datenquelle und der Computekontext könnten sich jedoch auf unterschiedlichen Servern befinden.
 
### <a name="changing-compute-contexts"></a>Ändern von Computekontexten

Nachdem Sie einen Computekontext definiert haben, müssen Sie den **aktiven Computekontext** festlegen. 

Standardmäßig werden die meisten Vorgänge lokal ausgeführt. Dies bedeutet, dass die Daten aus der Datenquelle abgerufen werden und der Code in Ihrer aktuellen Python-Umgebung ausgeführt wird, wenn Sie keinen anderen Computekontext angeben.

Es gibt zwei Möglichkeiten, um den aktiven Computekontext festzulegen:
+ Als Argument einer Methode oder Funktion
+ Durch Aufrufen von `rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Festlegen des Computekontexts als Argument einer Methode oder Funktion

In diesem Beispiel legen Sie den Computekontext fest, indem Sie ein Argument der individuellen **rx**-Funktion verwenden.
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Dieser Computekontext wird im Aufruf von [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) wiederverwendet:

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rx_set_compute_context"></a>Explizites Festlegen eines Computekontexts mit „rx_set_compute_context“

Die Funktion [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) ermöglicht Ihnen das Umschalten zwischen bereits definierten Computekontexten.

Nachdem Sie den aktiven Computekontext angegeben haben, bleibt er aktiv, bis Sie ihn ändern.

### <a name="using-parallel-processing-and-streaming"></a>Verwenden von paralleler Verarbeitung und Streaming

Wenn Sie den Computekontext definieren, können Sie auch Parameter festlegen, mit denen gesteuert wird, wie die Daten vom Computekontext verarbeitet werden. Diese Parameter unterscheiden sich je nach Datenquellentyp.

Für SQL Server-Computekontexte können Sie die Batchgröße festlegen oder Hinweise zum Grad der Parallelität angeben, die für die Ausführung von Tasks verwendet werden soll.

+ Das Beispiel wurde auf einem Computer mit vier Prozessoren ausgeführt, sodass der `num_tasks`-Parameter auf 4 festgelegt ist, um die maximale Verwendung von Ressourcen zu ermöglichen. 
+ Wenn Sie diesen Wert auf 0 festlegen, folgt SQL Server dem Standard, d. h., dass unter den aktuellen MAXDOP-Einstellungen für den Server so viele Aufgaben wie möglich parallel ausgeführt werden. Die genaue Anzahl von Aufgaben, die zugeordnet werden könnten, hängt jedoch von vielen anderen Faktoren ab, z. B. von Servereinstellungen und anderen Aufträgen, die ausgeführt werden.

## <a name="next-steps"></a>Nächste Schritte

Diese zusätzlichen Python-Beispiele und Tutorials veranschaulichen End-to-End-Szenarien, in denen komplexere Datenquellen verwendet werden, sowie die Verwendung von Remotecomputekontexten.

+ [Python-Datenanalyse für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md)
+ [Build a predictive model using Python and SQL Server ML Services](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) (Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server Machine Learning Services)
