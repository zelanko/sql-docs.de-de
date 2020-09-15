---
title: 'Schnellstart: Python-Funktionen'
titleSuffix: SQL machine learning
description: In diesem Schnellstart wird beschrieben, wie Sie mathematische Python-Funktionen und Hilfsfunktionen mit SQL-Machine Learning verwenden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/21/2020
ms.topic: quickstart
author: cawrites
ms.author: chadam
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: a432ce08cb0c4e2f0788188dacf6676083e38990
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88178515"
---
# <a name="quickstart-python-functions-with-sql-machine-learning"></a>Schnellstart: Python-Funktionen mit SQL-Machine Learning
[!INCLUDE [SQL Server 2017 SQL MI](../../includes/applies-to-version/sqlserver2017-asdbmi.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
In diesem Schnellstart wird beschrieben, wie Sie mathematische Funktionen und Hilfsfunktionen in Python mit [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) oder in [Big Data-Clustern](../../big-data-cluster/machine-learning-services.md) verwenden. Die Implementierung von statistischen Funktionen mit T-SQL ist oft kompliziert, kann aber in Python mit nur wenigen Codezeilen durchgeführt werden.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
In diesem Schnellstart wird beschrieben, wie Sie mathematische Funktionen und Hilfsfunktionen in Python mit [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) verwenden. Die Implementierung von statistischen Funktionen mit T-SQL ist oft kompliziert, kann aber in Python mit nur wenigen Codezeilen durchgeführt werden.
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
In diesem Schnellstart wird beschrieben, wie Sie mathematische Funktionen und Hilfsfunktionen in Python mit [Machine Learning Services in Azure SQL Managed Instance](/azure/azure-sql/managed-instance/machine-learning-services-overview) verwenden. Die Implementierung von statistischen Funktionen mit T-SQL ist oft kompliziert, kann aber in Python mit nur wenigen Codezeilen durchgeführt werden.
::: moniker-end

## <a name="prerequisites"></a>Voraussetzungen

Zum Durchführen dieser Schnellstartanleitung benötigen Sie folgende Voraussetzungen.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
- SQL Server Machine Learning Services. Informationen zur Installation von Machine Learning Services finden Sie im [Windows-Installationshandbuch](../install/sql-machine-learning-services-windows-install.md) oder im [Linux-Installationshandbuch](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json). Sie können auch [Machine Learning Services in Big Data-Clustern unter SQL Server aktivieren](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
- SQL Server Machine Learning Services. Informationen zur Installation von Machine Learning Services finden Sie im [Windows-Installationshandbuch](../install/sql-machine-learning-services-windows-install.md). 
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
- Machine Learning Services in Azure SQL Managed Instance. In der Übersicht [Machine Learning Services in Azure SQL Managed Instance (Vorschauversion)](/azure/azure-sql/managed-instance/machine-learning-services-overview) finden Sie Informationen zur Registrierung.
::: moniker-end

- Ein Tool zum Ausführen von SQL-Abfragen, die Python-Skripts enthalten. In dieser Schnellstartanleitung wird [Azure Data Studio](../../azure-data-studio/what-is.md) verwendet.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Erstellen einer gespeicherten Prozedur zum Generieren von Zufallszahlen

Der Einfachheit halber verwenden wir das Python-Paket `numpy`, das standardmäßig installiert und geladen wird. Das Paket enthält Hunderte von Funktionen für allgemeine statistische Aufgaben, darunter die `random.normal`-Funktion, die eine bestimmte Anzahl von Zufallszahlen mithilfe der normalen Verteilung bei angegebener Standardabweichung und Mittelwert generiert.

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

Wie gehen Sie vor, wenn Sie das Erstellen eines anderen Satzes von Zufallszahlen vereinfachen möchten? Sie definieren eine gespeicherte Prozedur, die Argumente vom Benutzer abruft, und übergeben diese Argumente dann als Variablen an das Python-Skript.

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

Orientieren Sie sich an dem folgenden Schnellstart, um ein Machine Learning-Modell mithilfe von Python mit SQL-Machine Learning zu erstellen:

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen und Bewerten eines Vorhersagemodells in Python](quickstart-python-train-score-model.md)
