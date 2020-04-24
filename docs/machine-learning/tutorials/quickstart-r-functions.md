---
title: 'Schnellstart: R-Funktionen'
description: In diesem Schnellstart wird beschrieben, wie Sie mathematische R-Funktionen und Hilfsfunktionen mit SQL Server Machine Learning Services verwenden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fd3c3326fe0b186ade24cbcf95f587abba1cb6bc
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487280"
---
# <a name="quickstart-r-functions-with-sql-server-machine-learning-services"></a>Schnellstart: R-Funktionen mit SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Schnellstart wird beschrieben, wie Sie mathematische R-Funktionen und Hilfsfunktionen mit SQL Server Machine Learning Services verwenden. Die Implementierung von statistischen Funktionen mit T-SQL ist oft kompliziert, kann aber in R mit nur wenigen Codezeilen durchgeführt werden.

## <a name="prerequisites"></a>Voraussetzungen

- Für diesen Schnellstart benötigen Sie Zugriff auf eine SQL Server-Instanz mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), in der die R-Sprache installiert ist.

  Ihre SQL Server-Instanz kann sich auf einem virtuellen Azure-Computer oder einem lokalen Computer befinden. Achten Sie darauf, dass das externe Skripterstellungsfeature standardmäßig deaktiviert ist. Sie müssen die [externe Skripterstellung](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) also möglicherweise aktivieren und überprüfen, ob das **SQL Server-Launchpad** ausgeführt wird, bevor Sie beginnen.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die R-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Tool für die Datenbankverwaltung oder -abfrage verwalten, sofern dieses eine Verbindung mit SQL Server-Instanzen herstellen und T-SQL-Abfragen oder gespeicherte Prozeduren ausführen kann. Für diesen Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) verwendet.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Erstellen einer gespeicherten Prozedur zum Generieren von Zufallszahlen

Der Einfachheit halber verwenden Sie das R-Paket `stats`, das standardmäßig in SQL Server Machine Learning Services mit R installiert und geladen ist. Das Paket enthält Hunderte von Funktionen für allgemeine statistische Aufgaben, darunter die `rnorm`-Funktion, die eine bestimmte Anzahl von Zufallszahlen mithilfe der normalen Verteilung bei angegebener Standardabweichung und Mittelwert generiert.

Der folgende R-Code gibt beispielsweise 100 Zahlen mit einem Mittelwert von 50 bei einer Standardabweichung von 3 zurück.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Fügen Sie die R-Funktion wie folgt in den R-Skriptparameter `sp_execute_external_script` ein, um diese R-Codezeile über T-SQL aufzurufen:

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Wie gehen Sie vor, wenn Sie das Erstellen eines anderen Satzes von Zufallszahlen vereinfachen möchten?

In Kombination mit SQL Server ist dies ganz einfach. Sie definieren eine gespeicherte Prozedur, die Argumente vom Benutzer abruft, und übergeben diese Argumente dann als Variablen an das R-Skript.

```sql
CREATE PROCEDURE MyRNorm (
    @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- Die erste Zeile definiert alle SQL-Eingabeparameter, die beim Ausführen der gespeicherten Prozedur erforderlich sind.

- In der mit `@params` beginnenden Zeile werden alle Variablen, die im R-Code verwendet werden, und die zugehörigen SQL-Datentypen definiert.

- Die unmittelbar darauf folgenden Zeilen ordnen die SQL-Parameternamen den entsprechenden R-Variablennamen zu.

Nachdem Sie die R-Funktion in eine gespeicherte Prozedur eingeschlossen haben, können die Funktion ganz einfach wie folgt aufrufen und dabei jeweils andere Werte übergeben:

```sql
EXECUTE MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>Verwenden von R-Hilfsfunktionen für die Problembehandlung

Das standardmäßig installierte Paket **utils** bietet eine Vielzahl von Hilfsfunktionen zum Untersuchen der aktuellen R-Umgebung. Diese Funktionen können sich als nützlich erweisen, wenn Sie Diskrepanzen bei der Leistung Ihres R-Codes in SQL Server und externen Umgebungen feststellen.

Sie können z. B. die R-Funktion `memory.limit()` verwenden, um den Arbeitsspeicher für die aktuelle R-Umgebung abzurufen. Da das Paket `utils` installiert ist, aber nicht standardmäßig geladen wird, laden Sie es zunächst mit der `library()`-Funktion.

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
        library(utils);
        mymemory <- memory.limit();
        OutputDataSet <- as.data.frame(mymemory);'
    , @input_data_1 = N' ;'
WITH RESULT SETS (([Col1] int not null));
```

> [!TIP]
> Viele Benutzer verwenden die R-Funktionen für die Systemzeitsteuerung, z. B. `system.time` und `proc.time`, um den Zeitaufwand von R-Prozessen zu erfassen und Leistungsprobleme zu analysieren. Im Tutorial [Erstellen von Datenfeatures](../tutorials/walkthrough-create-data-features.md) finden Sie ein Beispiel, bei dem Zeitsteuerungsfunktionen von R in die Lösung eingebettet sind.

## <a name="next-steps"></a>Nächste Schritte

Befolgen Sie den folgenden Schnellstart, um ein Machine Learning-Modell mithilfe von R in SQL Server zu erstellen:

> [!div class="nextstepaction"]
> [Erstellen und Bewerten eines Vorhersagemodells in R mit SQL Server Machine Learning Services](quickstart-r-train-score-model.md)

Weitere Informationen zu SQL Server Machine Learning Services finden Sie unter:

- [Was ist SQL Server Machine Learning Services (Python und R)?](../sql-server-machine-learning-services.md)
