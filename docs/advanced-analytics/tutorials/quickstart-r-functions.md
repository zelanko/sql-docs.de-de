---
title: Schnellstart zur Anzeige von R-Funktionen-SQL Server Machine Learning
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie eine R-Funktion für die erweiterte statistische Berechnung schreiben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c8c8f69391db2e1028a0da33dbaf77fd60eafd8f
ms.sourcegitcommit: 75fe364317a518fcf31381ce6b7bb72ff6b2b93f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2019
ms.locfileid: "70909202"
---
# <a name="quickstart-use-r-functions"></a>Schnellstart: Verwenden von R-Funktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Wenn Sie die vorherigen Schnellstarts abgeschlossen haben, sind Sie mit grundlegenden Vorgängen vertraut und bereit für etwas komplexeres, z. b. statistische Funktionen. Erweiterte statistische Funktionen, die in T-SQL schwierig zu implementieren sind, können in R nur mit einer einzigen Codezeile durchgeführt werden.

In dieser Schnellstartanleitung Betten Sie die mathematischen und Hilfsfunktionen von R in eine gespeicherte Prozedur SQL Server ein.

## <a name="prerequisites"></a>Erforderliche Komponenten

Eine vorherige Schnellstartanleitung, [überprüfen, ob R in SQL Server vorhanden](quickstart-r-verify.md)ist, enthält Informationen und Links zum Einrichten der r-Umgebung, die für diesen Schnellstart erforderlich ist.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Erstellen einer gespeicherten Prozedur zum Generieren von Zufallszahlen

Der Einfachheit halber verwenden wir das R `stats` -Paket, das standardmäßig installiert und geladen wird, wenn Sie die Unterstützung von R-Funktionen in SQL Server installieren. Das Paket enthält Hunderte von Funktionen für allgemeine statistische Aufgaben, darunter die `rnorm`-Funktion, die eine bestimmte Anzahl von Zufallszahlen mithilfe der normalen Verteilung bei angegebener Standardabweichung und Mittelwert generiert.

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

Das ist ganz einfach, wenn Sie mit SQL Server kombiniert werden: definieren Sie eine gespeicherte Prozedur, die die Argumente vom Benutzer abruft. Übergeben Sie dann diese Argumente als Variablen an das R-Skript.

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

Standardmäßig umfasst eine Installation von R das `utils` -Paket, das eine Reihe von Hilfsprogrammfunktionen zum Untersuchen der aktuellen R-Umgebung bereitstellt. Dies kann nützlich sein, wenn Sie bei der Ausführung Ihres R-Codes in SQL Server und externen Umgebungen Diskrepanzen feststellen.

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

Viele Benutzer verwenden die systemzeitsteuerungs `system.time` -Funktionen in r, wie z. b. und `proc.time`, um die von R-Prozessen verwendete Zeit zu erfassen und Leistungsprobleme zu analysieren.

Ein Beispiel finden Sie in diesem Tutorial: [Erstellen von Datenfunktionen](../tutorials/walkthrough-create-data-features.md). In dieser exemplarischen Vorgehensweise werden R-Zeit Steuerungsfunktionen in die Lösung eingebettet, um die Leistung von zwei Methoden zum Erstellen von Features aus Daten zu vergleichen: R-Funktionen im Vergleich zu T-SQL-Funktionen.

## <a name="next-steps"></a>Nächste Schritte

Als Nächstes erstellen Sie mithilfe von R in SQL Server ein Vorhersagemodell.

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen eines Vorhersagemodells](quickstart-r-create-predictive-model.md)
