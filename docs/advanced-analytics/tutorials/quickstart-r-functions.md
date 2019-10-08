---
title: Schreiben von erweiterten R-Funktionen
titleSuffix: SQL Server Machine Learning Services
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie eine R-Funktion für die erweiterte statistische Berechnung mit SQL Server Machine Learning Services schreiben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 747a6b06d1c9ad198971ff50068ac48d862a83da
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72006028"
---
# <a name="quickstart-write-advanced-r-functions-with-sql-server-machine-learning-services"></a>Schnellstart: Schreiben von erweiterten R-Funktionen mit SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Schnellstart wird beschrieben, wie Sie mathematische R-und Hilfsfunktionen in eine gespeicherte SQL-Prozedur mit SQL Server Machine Learning Services einbetten. Erweiterte statistische Funktionen, die in T-SQL schwierig zu implementieren sind, können in R nur mit einer einzigen Codezeile durchgeführt werden.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Diese Schnellstartanleitung erfordert Zugriff auf eine Instanz von SQL Server mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) , auf der die R-Sprache installiert ist.

  Ihre SQL Server Instanz kann sich auf einem virtuellen Azure-Computer oder lokal befinden. Beachten Sie, dass das Feature für die externe Skripterstellung standardmäßig deaktiviert ist. Daher müssen Sie möglicherweise [externe Skripterstellung aktivieren](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) und überprüfen, ob **SQL Server-Launchpad-Dienst** ausgeführt wird, bevor Sie beginnen.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die R-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Daten Bank Verwaltungs-oder Abfrage Tool ausführen, solange eine Verbindung mit einer SQL Server Instanz hergestellt und eine T-SQL-Abfrage oder eine gespeicherte Prozedur ausgeführt werden kann. In diesem Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)verwendet.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Erstellen einer gespeicherten Prozedur zum Generieren von Zufallszahlen

Der Einfachheit halber verwenden wir das R-`stats`-Paket, das standardmäßig in SQL Server Machine Learning Services installiert und geladen wird, auf dem r installiert ist. Das Paket enthält Hunderte von Funktionen für allgemeine statistische Aufgaben, darunter die `rnorm`-Funktion, die eine bestimmte Anzahl von Zufallszahlen mithilfe der normalen Verteilung bei angegebener Standardabweichung und Mittelwert generiert.

Der folgende R-Code gibt z. b. 100 Zahlen auf einem Mittelwert von 50 zurück, wenn eine Standardabweichung von 3 angegeben wird.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Um diese Zeile von R aus T-SQL aufzurufen, fügen Sie die r-Funktion im R-Skript Parameter von `sp_execute_external_script` hinzu, wie folgt:

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Sie möchten es vereinfachen, einen anderen Satz von Zufallszahlen zu generieren?

Das ist ganz einfach, wenn Sie mit SQL Server kombiniert werden. Sie definieren eine gespeicherte Prozedur, die die Argumente vom Benutzer abruft und diese Argumente dann als Variablen an das R-Skript übergibt.

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

Das standardmäßig installierte **utils** -Paket stellt eine Reihe von Hilfsprogrammfunktionen zum Untersuchen der aktuellen R-Umgebung bereit. Diese Funktionen können nützlich sein, wenn Sie Abweichungen in der Art und Weise finden, in der Ihr R-Code in SQL Server und in externen Umgebungen funktioniert.

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
> Viele Benutzer verwenden die systemzeitsteuerungs-Funktionen in r, wie z. b. `system.time` und `proc.time`, um die von R-Prozessen verwendete Zeit zu erfassen und Leistungsprobleme zu analysieren. Ein Beispiel finden Sie im Tutorial [Erstellen von Datenfunktionen](../tutorials/walkthrough-create-data-features.md) , bei denen R-Zeit Steuerungsfunktionen in die Lösung eingebettet sind.

## <a name="next-steps"></a>Nächste Schritte

Um ein Machine Learning-Modell mithilfe von R in SQL Server zu erstellen, befolgen Sie diese Schnellstartanleitung:

> [!div class="nextstepaction"]
> [Erstellen und bewerten eines Vorhersagemodells in R mit SQL Server Machine Learning Services](quickstart-r-train-score-model.md)

Weitere Informationen zum SQL Server Machine Learning Services finden Sie unter:

- [Was ist SQL Server Machine Learning Services (python und R)?](../what-is-sql-server-machine-learning.md)
