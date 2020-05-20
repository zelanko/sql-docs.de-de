---
title: 'Schnellstart: Python-Funktionen'
description: In diesem Schnellstart wird beschrieben, wie Sie mathematische Funktionen und Hilfsfunktionen in Python mit SQL Server Machine Learning Services verwenden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/28/2020
ms.topic: quickstart
author: cawrites
ms.author: chadam
ms.reviewer: garye
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6afe1685956c43e30ace59f3e5cc794a2abbd88f
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606704"
---
# <a name="quickstart-python-functions-with-sql-server-machine-learning-services"></a>Schnellstart: Python-Funktionen mit SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
In diesem Schnellstart wird beschrieben, wie Sie mathematische Funktionen und Hilfsfunktionen in Python mit [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) oder in [Big Data-Clustern](../../big-data-cluster/machine-learning-services.md) verwenden. Die Implementierung von statistischen Funktionen mit T-SQL ist oft kompliziert, kann aber in Python mit nur wenigen Codezeilen durchgeführt werden.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
In diesem Schnellstart wird beschrieben, wie Sie mathematische Funktionen und Hilfsfunktionen in Python mit [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) verwenden. Die Implementierung von statistischen Funktionen mit T-SQL ist oft kompliziert, kann aber in Python mit nur wenigen Codezeilen durchgeführt werden.
::: moniker-end

## <a name="prerequisites"></a>Voraussetzungen

- Für diesen Schnellstart benötigen Sie Zugriff auf eine SQL Server-Instanz mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), für die die Python-Sprache installiert ist.

  Ihre SQL Server-Instanz kann sich auf einem virtuellen Azure-Computer oder einem lokalen Computer befinden. Achten Sie darauf, dass das externe Skripterstellungsfeature standardmäßig deaktiviert ist. Sie müssen die [externe Skripterstellung](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) also möglicherweise aktivieren und überprüfen, ob das **SQL Server-Launchpad** ausgeführt wird, bevor Sie beginnen.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die Python-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Tool für die Datenbankverwaltung oder -abfrage verwalten, sofern dieses eine Verbindung mit SQL Server-Instanzen herstellen und T-SQL-Abfragen oder gespeicherte Prozeduren ausführen kann. In dieser Schnellstartanleitung wird [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download-azure-data-studio) verwendet.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Erstellen einer gespeicherten Prozedur zum Generieren von Zufallszahlen

Der Einfachheit halber verwenden Sie das Python-Paket `numpy`, das standardmäßig in SQL Server Machine Learning Services mit Python installiert und geladen ist. Das Paket enthält Hunderte von Funktionen für allgemeine statistische Aufgaben, darunter die `random.normal`-Funktion, die eine bestimmte Anzahl von Zufallszahlen mithilfe der normalen Verteilung bei angegebener Standardabweichung und Mittelwert generiert.

Der folgende Python-Code gibt beispielsweise 100 Zahlen mit einem Mittelwert von 50 bei einer Standardabweichung von 3 zurück.

```Python
numpy.random.normal(size=100, loc=50, scale=3)
```

Fügen Sie die Python-Funktion in den Python-Skriptparameter `sp_execute_external_script` ein, um diese Python-Codezeile über T-SQL aufzurufen. Die Ausgabe erwarten einen Datenrahmen, verwenden sie also `pandas`, um ihn zu konvertieren.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=100, loc=50, scale=3));
'
    , @input_data_1 = N'   ;'
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

Wie gehen Sie vor, wenn Sie das Erstellen eines anderen Satzes von Zufallszahlen vereinfachen möchten?

In Kombination mit SQL Server ist dies ganz einfach. Sie definieren eine gespeicherte Prozedur, die Argumente vom Benutzer abruft, und übergeben diese Argumente dann als Variablen an das Python-Skript.

```sql
CREATE PROCEDURE MyPyNorm (
      @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=mynumbers, loc=mymean, scale=mysd));
'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- Die erste Zeile definiert alle SQL-Eingabeparameter, die beim Ausführen der gespeicherten Prozedur erforderlich sind.

- Die Zeile, die mit `@params` beginnt, definiert alle vom Python-Code verwendeten Variablen und die entsprechenden SQL-Datentypen.

- Die unmittelbar folgenden Zeilen ordnen die SQL-Parameternamen den entsprechenden Python-Variablennamen zu.

Nun haben Sie die Python-Funktion in eine gespeicherte Prozedur eingeschlossen und können sie wie folgt ganz einfach aufrufen und ihr andere Werte übergeben:

```sql
EXECUTE MyPyNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-python-utility-functions-for-troubleshooting"></a>Verwenden von Python-Hilfsfunktionen für die Problembehandlung

Python-Pakete bieten eine Vielzahl verschiedener Hilfsfunktionen zur Untersuchung der aktuellen Python-Umgebung. Diese Funktionen können sich als nützlich erweisen, wenn Sie Diskrepanzen bei der Leistung Ihres Python-Codes in SQL Server und externen Umgebungen feststellen.

Beispielsweise können Sie Funktionen für die Systemzeitsteuerung im `time`-Paket verwenden, um den Zeitaufwand von Python-Prozessen zu erfassen und Leistungsprobleme zu analysieren.

```sql
EXECUTE sp_execute_external_script
      @language = N'Python'
    , @script = N'
import time
start_time = time.time()

# Run Python processes

elapsed_time = time.time() - start_time
'
    , @input_data_1 = N' ;';
```

## <a name="next-steps"></a>Nächste Schritte

Befolgen Sie den folgenden Schnellstart, um ein Machine Learning-Modell mithilfe von Python in SQL Server zu erstellen:

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen und Bewerten eines Vorhersagemodells in Python mit SQL Server Machine Learning Services](quickstart-python-train-score-model.md)

Weitere Informationen zu SQL Server Machine Learning Services finden Sie unter:

- [Was ist SQL Server Machine Learning Services (Python und R)?](../sql-server-machine-learning-services.md)
