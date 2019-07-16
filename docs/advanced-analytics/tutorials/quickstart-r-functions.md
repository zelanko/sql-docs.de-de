---
title: In dieser Schnellstartanleitung R-Funktionen – SQL Server-Machine Learning
description: Erfahren Sie in dieser schnellstartanleitung, wie eine R-Funktion für erweiterte statistische Berechnungen zu schreiben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: fa2d47729641e8efd13e9e30be7a61186a892b5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962011"
---
# <a name="quickstart-using-r-functions"></a>Schnellstart: Verwenden von R-Funktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Wenn Sie die vorherigen Schnellstarts abgeschlossen haben, können Sie mit grundlegenden Vorgängen vertraut sind und etwas komplexer, z. B. statistische Funktionen bereit. Erweiterte statistische Funktionen, die in T-SQL implementiert kompliziert sind in R mit nur eine einzige Zeile Code möglich.

Klicken Sie in dieser schnellstartanleitung betten Sie mathematische R, und Hilfsfunktionen, die in einer SQL Server gespeicherten Prozedur.

## <a name="prerequisites"></a>Vorraussetzungen

Einen vorherigen schnellstartanleitung [R stellen Sie sicher, die in SQL Server vorhanden ist](quickstart-r-verify.md), enthält Informationen und links für das Einrichten der R-Umgebung, die im Rahmen dieser schnellstartanleitung benötigt.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Erstellen einer gespeicherten Prozedur zum Generieren von Zufallszahlen

Der Einfachheit halber verwenden wir den R `stats` Paket, das installiert wird und das standardmäßig geladen, wenn Sie Unterstützung von R-Funktionen in SQL Server installieren. Das Paket enthält Hunderte von Funktionen für allgemeine statistische Aufgaben, darunter die `rnorm`-Funktion, die eine bestimmte Anzahl von Zufallszahlen mithilfe der normalen Verteilung bei angegebener Standardabweichung und Mittelwert generiert.

Bei einer Standardabweichung von 3 gibt dieser R-Code beispielsweise 100 Zahlen mit einem Mittelwert von 50 zurück.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Führen Sie zum Aufrufen dieser R-Zeile von T-SQL sp_execute_external_script aus, und fügen Sie die R-Funktion wie folgt im R-Skriptparameter hinzu:

```sql
EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Sie möchten es vereinfachen, einen anderen Satz von Zufallszahlen zu generieren?

Das ist ganz einfach in Kombination mit SQL Server: definieren eine gespeicherte Prozedur, die die Argumente des Benutzers abruft. Übergeben Sie dann diese Argumente als Variablen an das R-Skript.

```sql
CREATE PROCEDURE MyRNorm (@param1 int, @param2 int, @param3 int)
AS
    EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
    WITH RESULT SETS (([Density] float NOT NULL));
```

+ Die erste Zeile definiert alle SQL-Eingabeparameter, die erforderlich sind, wenn die gespeicherte Prozedur ausgeführt wird.

+ Die Zeile, die mit `@params` beginnt, definiert alle vom R-Code verwendeten Variablen und die entsprechenden SQL-Datentypen.

+ Die unmittelbar folgenden Zeilen ordnen die SQL-Parameternamen den entsprechenden R-Variablennamen zu.

Nun haben Sie die R-Funktion in einer gespeicherten Prozedur eingeschlossen und können sie ganz einfach aufrufen und ihr andere Werte übergeben:

```sql
EXEC MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>Verwenden von R-Hilfsfunktionen für die Problembehandlung

Standardmäßig enthält eine Installation von R die `utils` -Paket, das eine Vielzahl von Hilfsfunktionen für die Untersuchung der aktuellen R-Umgebung enthält. Dies kann nützlich sein, wenn Sie bei der Ausführung Ihres R-Codes in SQL Server und externen Umgebungen Diskrepanzen feststellen.

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

Viele Benutzer haben Lust sich die Systemfunktionen für die zeitliche Steuerung in R verwenden, z. B. `system.time` und `proc.time`, um die vom R-Prozessen verwendete Zeit zu erfassen und Leistungsprobleme analysieren.

Ein Beispiel finden Sie im Tutorial: [Erstellen von Datenfunktionen](../tutorials/walkthrough-create-data-features.md). In dieser exemplarischen Vorgehensweise werden R Funktionen zur zeitlichen Steuerung in der Projektmappe, um die Leistung von zwei Methoden zum Erstellen von Merkmalen aus Daten vergleichen eingebettet: R-Funktionen im Vergleich zu T-SQL-Funktionen.

## <a name="next-steps"></a>Nächste Schritte

Als Nächstes erstellen Sie mithilfe von R in SQL Server ein Vorhersagemodell.

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen eines Vorhersagemodells](quickstart-r-create-predictive-model.md)
