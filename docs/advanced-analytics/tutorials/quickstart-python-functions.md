---
title: Schreiben erweiterter python-Funktionen
titleSuffix: SQL Server Machine Learning Services
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie eine python-Funktion für die erweiterte statistische Berechnung mit SQL Server Machine Learning Services schreiben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e369e83c99543cc31287932a25949c2ddec98e89
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72007720"
---
# <a name="quickstart-write-advanced-python-functions-with-sql-server-machine-learning-services"></a>Schnellstart: Schreiben erweiterter python-Funktionen mit SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Schnellstart wird beschrieben, wie Sie mathematische python-und Utility-Funktionen in eine gespeicherte SQL-Prozedur mit SQL Server Machine Learning Services einbetten. Erweiterte statistische Funktionen, die in T-SQL schwierig zu implementieren sind, können in python nur mit einer einzigen Codezeile durchgeführt werden.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Diese Schnellstartanleitung erfordert Zugriff auf eine Instanz von SQL Server mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) , auf der die Python-Sprache installiert ist.

  Ihre SQL Server Instanz kann sich auf einem virtuellen Azure-Computer oder lokal befinden. Beachten Sie, dass das Feature für die externe Skripterstellung standardmäßig deaktiviert ist. Daher müssen Sie möglicherweise [externe Skripterstellung aktivieren](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) und überprüfen, ob **SQL Server-Launchpad-Dienst** ausgeführt wird, bevor Sie beginnen.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die python-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Daten Bank Verwaltungs-oder Abfrage Tool ausführen, solange eine Verbindung mit einer SQL Server Instanz hergestellt und eine T-SQL-Abfrage oder eine gespeicherte Prozedur ausgeführt werden kann. In diesem Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)verwendet.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Erstellen einer gespeicherten Prozedur zum Generieren von Zufallszahlen

Der Einfachheit halber verwenden wir das Python-Paket "`numpy`", das standardmäßig in SQL Server Machine Learning Services mit installiertem python installiert und geladen wird. Das Paket enthält Hunderte von Funktionen für allgemeine statistische Aufgaben, darunter die `random.normal`-Funktion, die eine bestimmte Anzahl von Zufallszahlen mithilfe der normalen Verteilung bei angegebener Standardabweichung und Mittelwert generiert.

Der folgende Python-Code gibt z. b. 100 Zahlen auf einem Mittelwert von 50 zurück, wenn eine Standardabweichung von 3 angegeben wird.

```Python
numpy.random.normal(size=100, loc=50, scale=3)
```

Um diese Zeile von python aus T-SQL aufzurufen, fügen Sie die python-Funktion im Python-Skript Parameter von `sp_execute_external_script` hinzu. Die Ausgabe erwartet einen Datenrahmen. verwenden Sie daher `pandas`, um Sie zu konvertieren.

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

Sie möchten es vereinfachen, einen anderen Satz von Zufallszahlen zu generieren?

Das ist ganz einfach, wenn Sie mit SQL Server kombiniert werden. Sie definieren eine gespeicherte Prozedur, die die Argumente vom Benutzer abruft und diese Argumente dann als Variablen an das Python-Skript übergibt.

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

- Die erste Zeile definiert alle SQL-Eingabeparameter, die erforderlich sind, wenn die gespeicherte Prozedur ausgeführt wird.

- Die Zeile, die mit `@params` beginnt, definiert alle Variablen, die vom Python-Code verwendet werden, sowie die entsprechenden SQL-Datentypen.

- Die Zeilen, die unmittelbar folgen, ordnen die SQL-Parameternamen den entsprechenden python-Variablennamen zu.

Nachdem Sie die python-Funktion in einer gespeicherten Prozedur verpackt haben, können Sie die Funktion problemlos aufzurufen und verschiedene Werte wie folgt übergeben:

```sql
EXECUTE MyPyNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-python-utility-functions-for-troubleshooting"></a>Verwenden von python Utility-Funktionen für die Problembehandlung

Python-Pakete bieten eine Reihe von Hilfsprogrammfunktionen zum Untersuchen der aktuellen python-Umgebung. Diese Funktionen können nützlich sein, wenn Sie Abweichungen in der Leistung Ihres python-Codes in SQL Server und in externen Umgebungen finden.

Beispielsweise können Sie die Systemzeit Steuerungsfunktionen im `time`-Paket verwenden, um die von python-Prozessen verwendete Zeit zu messen und Leistungsprobleme zu analysieren.

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

Um ein Machine Learning-Modell mithilfe von python in SQL Server zu erstellen, befolgen Sie diese Schnellstartanleitung:

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen und bewerten eines Vorhersagemodells in Python mit SQL Server Machine Learning Services @ no__t-0

Weitere Informationen zum SQL Server Machine Learning Services finden Sie unter:

- [Was ist SQL Server Machine Learning Services (python und R)?](../what-is-sql-server-machine-learning.md)
