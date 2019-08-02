---
title: Verwenden von Python mit revoscalepy zum Erstellen eines Modells
description: Schreiben Sie ein Python-Skript mithilfe von revoscalepy-Funktionen, um Data Science Modelle zu erstellen, die Remote in SQL Server ausgeführt werden
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 596e5f6b5145dc258c781ca7b88a69fc962d7021
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714712"
---
# <a name="use-python-with-revoscalepy-to-create-a-model-that-runs-remotely-on-sql-server"></a>Verwenden Sie python mit revoscalepy, um ein Modell zu erstellen, das Remote auf SQL Server ausgeführt wird.
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) -Python-Bibliothek von Microsoft stellt Data Science Algorithmen für das Durchsuchen von Daten, Visualisierung, Transformationen und Analysen bereit. Diese Bibliothek hat strategische Wichtigkeit in python-Integrationsszenarien in SQL Server. Auf einem Server mit mehreren Kernen können **revoscalepy** -Funktionen parallel ausgeführt werden. In einer verteilten Architektur mit einem zentralen Server und Client Arbeitsstationen (separate physische Computer, die alle dieselbe **revoscalepy** -Bibliothek aufweisen) können Sie Python-Code schreiben, der lokal gestartet wird, aber dann die Ausführung auf eine Remote SQL Server Instanz verlagert. Speicherort der Daten.

Sie finden **revoscalepy** in den folgenden Microsoft-Produkten und-Distributionen:

+ [SQL Server Machine Learning Services (in-Database)](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server (nicht-SQL, eigenständiger Server)](https://docs.microsoft.com/machine-learning-server/index)
+ [Client seitige python-Bibliotheken (für Entwicklungs Arbeitsstationen)](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) 

Diese Übung veranschaulicht, wie ein lineares Regressionsmodell erstellt wird, das auf [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)basiert, einem der Algorithmen in **revoscalepy** , der computekontext als Eingabe akzeptiert. Der Code, den Sie in dieser Übung ausführen, verschiebt die Codeausführung von einer lokalen in eine Remote Computerumgebung, die durch **revoscalepy** -Funktionen ermöglicht wird, die einen remotecomputekontext ermöglichen.

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Verwenden von **revoscalepy** zum Erstellen eines linearen Modells
> * Verschiebe Vorgänge von lokalem zu remotecomputekontext

## <a name="prerequisites"></a>Vorraussetzungen

Die in dieser Übung verwendeten Beispiel Daten sind die [**FlightData**](demo-data-airlinedemo-in-sql.md) -Datenbank.

Sie benötigen eine IDE, um den Beispielcode in diesem Artikel auszuführen, und die IDE muss mit der ausführbaren python-Datei verknüpft werden.

Zum Üben einer Rechen Kontext Schicht benötigen Sie eine [lokale Arbeits](../python/setup-python-client-tools-sql.md) Station und eine SQL Server Datenbank-Engine-Instanz mit aktiviertem [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) und python. 

> [!Tip]
> Wenn Sie nicht über zwei Computer verfügen, können Sie einen remotecomputekontext auf einem physischen Computer simulieren, indem Sie relevante Anwendungen installieren. Zuerst wird eine Installation von [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) als "Remote Instanz" fungiert. Zweitens fungiert eine Installation der [Python-Client Bibliotheken](../python/setup-python-client-tools-sql.md) als Client. Auf demselben Computer verfügen Sie über zwei Kopien derselben Python-Distribution und Microsoft python-Bibliotheken. Sie müssen die Dateipfade und die Kopie der Python. exe-Datei, die Sie zum erfolgreichen Abschluss der Übung verwenden, nachverfolgen.

## <a name="remote-compute-contexts-and-revoscalepy"></a>Remotecomputekontexte und revoscalepy

Dieses Beispiel veranschaulicht den Prozess der Erstellung eines python-Modells in einem remotecomputekontext, mit dem Sie von einem Client aus arbeiten können, aber eine Remote Umgebung auswählen können, wie z. b. SQL Server, Spark oder Machine Learning Server, in der die Vorgänge tatsächlich ausgeführt werden. Das Ziel des remotecomputekontexts besteht darin, die Berechnung an den Speicherort der Daten zu übertragen.

Zum Ausführen von Python-Code in SQL Server ist das **revoscalepy** -Paket erforderlich. Dies ist ein spezielles Python-Paket, das von Microsoft bereitgestellt wird, ähnlich dem **revoscaler** -Paket für die Sprache R. Das **revoscalepy** -Paket unterstützt die Erstellung von computekontexten und stellt die Infrastruktur für das Übergeben von Daten und Modellen zwischen einer lokalen Arbeitsstation und einem Remote Server bereit. Die **revoscalepy** -Funktion, die die Ausführung von in-Database-Code unterstützt, ist [rxinsqlserver](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

In dieser Lektion verwenden Sie Daten in SQL Server, um ein lineares Modell auf der Grundlage von [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)zu trainieren, eine Funktion in **revoscalepy** , die die Regression über sehr große Datasets unterstützt. 

Diese Lektion veranschaulicht auch die Grundlagen der Einrichtung und Verwendung eines **SQL Server computekontexts** in Python. Eine Erläuterung dazu, wie computekontexte mit anderen Plattformen funktionieren und welche computekontexte unterstützt werden, finden Sie unter [computekontext für die Skriptausführung in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).


## <a name="run-the-sample-code"></a>Ausführen des Beispielcodes

Nachdem Sie die Datenbank vorbereitet und die Daten für das Training in einer Tabelle gespeichert haben, öffnen Sie eine python-Entwicklungsumgebung, und führen Sie das Codebeispiel aus.

Der Code führt die folgenden Schritte aus:

1. Importiert die erforderlichen Bibliotheken und Funktionen.
2. Erstellt eine Verbindung mit SQL Server. Erstellt **Datenquellen** Objekte zum Arbeiten mit den Daten.
3. Ändert die Daten mithilfe von **Transformationen** , sodass Sie vom Logistic Regression-Algorithmus verwendet werden können.
4. Ruft `rx_lin_mod` auf und definiert die Formel, die für das Modell geeignet ist.
5. Generiert einen Satz von Vorhersagen basierend auf den ursprünglichen Daten.
6. Erstellt eine Zusammenfassung basierend auf den vorhergesagten Werten.

Alle Vorgänge werden mithilfe einer Instanz von SQL Server als computekontext ausgeführt.

> [!NOTE]
> Eine Demonstration dieses Beispiels, das in der Befehlszeile ausgeführt wird, finden Sie in diesem Video: [Erweiterte Analyse SQL Server 2017 mit python](https://www.youtube.com/watch?v=FcoY795jTcc)

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

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>Definieren einer Datenquelle im Vergleich zum Definieren eines computekontexts

Eine Datenquelle unterscheidet sich von einem computekontext. Die *Datenquelle* definiert die Daten, die in Ihrem Code verwendet werden. Der computekontext definiert, wo der Code ausgeführt wird. Dabei werden jedoch einige der gleichen Informationen verwendet:

+ Mit python `sql_query` -Variablen, wie `sql_connection_string`z. b. und, wird die Quelle der Daten definiert. 

    Übergeben Sie diese Variablen an den [rxsqlserverdata](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) -Konstruktor, um das **Datenquellen Objekt** mit dem Namen `data_source`zu implementieren.

+ Sie erstellen ein **computecontext-Objekt** , indem Sie den [rxinsqlserver](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) -Konstruktor verwenden. Das resultierende **computecontext-Objekt** hat `sql_cc`den Namen.

    In diesem Beispiel wird die gleiche Verbindungs Zeichenfolge wieder verwendet, die Sie in der Datenquelle verwendet haben, wobei angenommen wird, dass sich die Daten auf derselben SQL Server Instanz befinden, die Sie als computekontext verwenden. 
    
    Die Datenquelle und der computekontext können sich jedoch auf unterschiedlichen Servern befinden.
 
### <a name="changing-compute-contexts"></a>Ändern von computekontexten

Nachdem Sie einen computekontext definiert haben, müssen Sie den **aktiven computekontext**festlegen. 

Standardmäßig werden die meisten Vorgänge lokal ausgeführt. Dies bedeutet, dass die Daten aus der Datenquelle abgerufen werden, wenn Sie keinen anderen computekontext angeben und der Code in Ihrer aktuellen python-Umgebung ausgeführt wird.

Es gibt zwei Möglichkeiten, den aktiven computekontext festzulegen:
+ Als Argument einer Methode oder Funktion
+ Durch Aufrufen von`rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Festlegen des computekontexts als Argument einer Methode oder Funktion

In diesem Beispiel legen Sie den computekontext mit einem Argument der einzelnen **RX** -Funktion fest.
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Dieser computekontext wird im [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary)-Befehl wieder verwendet:

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Explizites Festlegen eines computekontexts mithilfe von rx_set_compute_context

Mit der [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) -Funktion können Sie zwischen computekontexten umschalten, die bereits definiert wurden.

Nachdem Sie den aktiven computekontext festgelegt haben, bleibt er aktiv, bis Sie ihn ändern.

### <a name="using-parallel-processing-and-streaming"></a>Verwenden von paralleler Verarbeitung und Streaming

Wenn Sie den computekontext definieren, können Sie auch Parameter festlegen, mit denen gesteuert wird, wie die Daten vom computekontext verarbeitet werden. Diese Parameter unterscheiden sich je nach Daten Quellentyp.

Für SQL Server computekontexte können Sie die Batch Größe festlegen oder Hinweise zum Grad der Parallelität angeben, die für die Ausführung von Tasks verwendet werden soll.

+ Das Beispiel wurde auf einem Computer mit vier Prozessoren ausgeführt, sodass der `num_tasks` -Parameter auf 4 festgelegt ist, um die maximale Verwendung von Ressourcen zu ermöglichen. 
+ Wenn Sie diesen Wert auf 0 festlegen, verwendet SQL Server den Standardwert, mit dem so viele Aufgaben parallel wie möglich unter den aktuellen MAXDOP-Einstellungen für den Server ausgeführt werden. Die genaue Anzahl von Tasks, die zugeordnet werden können, hängt jedoch von vielen anderen Faktoren ab, z. b. von Servereinstellungen und anderen Aufträgen, die ausgeführt werden.

## <a name="next-steps"></a>Nächste Schritte

Diese zusätzlichen python-Beispiele und-Lernprogramme veranschaulichen End-to-End-Szenarien, in denen komplexere Datenquellen verwendet werden, sowie die Verwendung von remotecomputekontexten.

+ [In-Database python für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md)
+ [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
