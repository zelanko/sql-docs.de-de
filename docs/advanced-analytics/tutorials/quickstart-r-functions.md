---
title: 'Schnellstart: Schreiben von R-Funktionen'
titleSuffix: SQL Server Machine Learning Services
description: In diesem Schnellstart erfahren Sie, wie Sie eine R-Funktion für erweiterte statistische Berechnungen mit SQL Server Machine Learning Services schreiben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e725282aaacde748b43a37a317037b5471efd009
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73726885"
---
# <a name="quickstart-write-advanced-r-functions-with-sql-server-machine-learning-services"></a>Schnellstart: Schreiben erweiterter R-Funktionen mit SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Schnellstart wird beschrieben, wie Sie mathematische und Hilfsfunktionen von R mit SQL Server Machine Learning Services in eine gespeicherte SQL-Prozedur einbetten. Erweiterte statistische Funktionen, deren Implementierung mit T-SQL kompliziert ist, können in R mit einer einzigen Codezeile durchgeführt werden.

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

Sie möchten es vereinfachen, einen anderen Satz von Zufallszahlen zu generieren?

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

- Die erste Zeile definiert alle SQL-Eingabeparameter, die erforderlich sind, wenn die gespeicherte Prozedur ausgeführt wird.

- Die Zeile, die mit `@params` beginnt, definiert alle vom R-Code verwendeten Variablen und die entsprechenden SQL-Datentypen.

- Die unmittelbar folgenden Zeilen ordnen die SQL-Parameternamen den entsprechenden R-Variablennamen zu.

Nun haben Sie die R-Funktion in einer gespeicherten Prozedur eingeschlossen und können sie ganz einfach aufrufen und ihr andere Werte übergeben:

```sql
EXECUTE MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>Verwenden von R-Hilfsfunktionen für die Problembehandlung

Das standardmäßig installierte Paket **utils** bietet eine Vielzahl von Hilfsfunktionen zum Untersuchen der aktuellen R-Umgebung. Diese Funktionen können sich als nützlich erweisen, wenn Sie Diskrepanzen bei der Leistung Ihres R-Codes in SQL Server und externen Umgebungen feststellen.

Sie können zum Beispiel die R-`memory.limit()`-Funktion verwenden, um Arbeitsspeicher für die aktuelle R-Umgebung abzurufen. Da das `utils`-Paket standardmäßig installiert, aber nicht geladen wird, müssen Sie es zuerst mit der `library()`-Funktion laden.

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

- [Was ist SQL Server Machine Learning Services (Python und R)?](../what-is-sql-server-machine-learning.md)
