---
title: Schnellstart zum Vorhersagen und zeichnen ausgehend vom Modell mithilfe von R in SQL Server-Machine Learning | Microsoft-Dokumentation
description: In dieser schnellstartanleitung erfahren Sie mehr zur Bewertung der Verwendung eines vordefinierten Modells in R und SQL Server-Daten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 60e152948945f4e86cc1114ae7b20c0e48b403bf
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086652"
---
# <a name="quickstart-predict-and-plot-from-model-using-r-in-sql-server"></a>Schnellstart: Vorhersagen und zeichnen ausgehend vom Modell mithilfe von R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Verwenden Sie in diesem Schnellstart das Modell, das Sie im vorherigen Schnellstart zur Bewertung von Vorhersagen für neue Daten erstellt haben. Auszuführende _Bewertung_ mit neuen Daten, eines der trainierten Modelle aus der Tabelle, und rufen Sie dann einen neuen Satz von Daten für die Vorhersagen basieren. Bewertung ist ein Begriff, die manchmal zum Generieren von Vorhersagen, Wahrscheinlichkeiten und andere Werte, die basierend auf neuen Daten, die in einem trainierten Modell eingegeben, bedeutet im Data Science-Prozess verwendet.

## <a name="prerequisites"></a>Erforderliche Komponenten

Dieser Schnellstart ist eine Erweiterung der [Erstellen eines Vorhersagemodells](rtsql-create-a-predictive-model-r.md).

## <a name="create-the-table-of-new-speeds"></a>Erstellen der Tabelle mit neuen Geschwindigkeiten

Haben Sie bemerkt, dass die ursprünglichen Trainingsdaten bei einer Geschwindigkeit von 25 Meilen pro Stunde enden? Das liegt daran, dass die ursprünglichen Daten auf einem Experiment von 1920 basierten!

Sie fragen sich vielleicht, wie lange ein Auto aus den 1920ern zum Anhalten brauchte, wenn wir davon ausgehen, dass es bis zu 60 oder sogar 100 Meilen pro Stunde schnell werden konnte? Um diese Frage zu beantworten, müssen Sie einige neue Geschwindigkeitswerte angeben.

```sql
CREATE TABLE [dbo].[NewCarSpeed]([speed] [int] NOT NULL,
    [distance] [int]  NULL) ON [PRIMARY]
GO
INSERT [dbo].[NewCarSpeed] (speed)
VALUES (40),  (50),  (60), (70), (80), (90), (100)
```

## <a name="predict-stopping-distance"></a>Vorhersagen des Anhaltewegs

Mittlerweile enthält Ihre Tabelle möglicherweise mehrere R-Modelle, die alle verschiedene Parameter oder Algorithmen verwenden oder mit verschiedenen Teilmengen von Daten trainiert wurden.

![rsql_basictut_listofmodels](media/rsql-basictut-listofmodels.png)

Um vorhersagen basierend auf einem bestimmten Modell zu erhalten, müssen Sie ein SQL-Skript schreiben, die Folgendes ausführt:

1. Ruft das gewünschte Modell ab
2. Ruft die neuen Eingabedaten ab
3. Ruft eine R-Vorhersagefunktion auf, die mit dem Modell kompatibel ist

In diesem Beispiel, da das Modell basiert die **RxLinMod** Algorithmus, die als Teil der **RevoScaleR** Paket, rufen Sie die [RxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) -Funktion, statt auf den generische R `predict` Funktion.

```sql
DECLARE @speedmodel varbinary(max) = (SELECT model FROM [dbo].[stopping_distance_models] WHERE model_name = 'latest model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            str(predicted.distance);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N'SELECT speed FROM [dbo].[NewCarSpeed]'
    , @input_data_1_name = N'NewCarData'
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Verwenden Sie eine SELECT-Anweisung, um ein einzelnes Modell aus der Tabelle abzurufen, und übergeben Sie es als Eingabeparameter.
+ Rufen Sie nach dem Abruf des Modells aus der Tabelle die `unserialize`-Funktion auf dem Modell auf.

    > [!TIP] 
    > Außerdem sehen Sie sich die neue [Serialisierungsfunktionen](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) bereitgestellt, der Unterstützung von RevoScaleR [in Echtzeit bewerten](../real-time-scoring.md).
+  Wenden Sie die `rxPredict`-Funktion mit geeigneten Argumenten auf das Modell an, und stellen Sie die neuen Eingabedaten bereit.
+  Im Beispiel die `str` -Funktion wurde hinzugefügt, während der Testphase, um das Schema der von r zurückgegebenen Daten zu überprüfen Sie können die Anweisung später erneut entfernen.
+ Die im R-Skript verwendeten Spaltennamen sind nicht unbedingt an die Ausgabe der gespeicherten Prozedur übergeben. Hier haben wir die WITH RESULTS-Klausel verwendet, um einige neue Spaltennamen zu definieren.

**Ergebnisse**

![rsql_basictut_scoringresults_smalldata](media/rsql-basictut-scoringresults-smalldata.PNG)

## <a name="perform-scoring-in-parallel"></a>Paralleles Ausführen der Bewertung

Die Vorhersagen für dieses kleine Dataset wurden ziemlich schnell zurückgegeben. Aber was ist, wenn Sie sehr schnell sehr viele Vorhersagen benötigen? Es gibt viele Möglichkeiten, um die Vorgänge im SQL Server, zu beschleunigen, wenn die Vorgänge parallel verarbeitet werden können. Für die Bewertung ist eine einfache Möglichkeit ist, fügen die *@parallel* Parameter von Sp_execute_external_script und legen Sie den Wert **1**.

Nehmen wir an, dass Sie eine viel größere Tabelle möglicher Autogeschwindigkeiten mit Hunderten oder Tausenden von Werten erhalten haben. Es gibt viele T-SQL-Beispielskripts aus der Community, mit deren Hilfe Sie Zahlentabellen generieren können, weshalb wir diese hier nicht wiederholen. Gehen wir einfach davon aus, dass Sie eine Spalte mit vielen Ganzzahlen haben und Sie diese als Eingabe für `speed` im Modell verwenden möchten.

Zu diesem Zweck führen Sie einfach die gleiche Vorhersageabfrage, aber das größere Dataset ersetzen, und Hinzufügen der `@parallel = 1` Argument.

```sql
DECLARE @speedmodel varbinary(max) = (select model from [dbo].[stopping_distance_models] where model_name = 'default model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N' SELECT [speed] FROM [dbo].[HugeTableofCarSpeeds] '
    , @input_data_1_name = N'NewCarData'
    , @parallel = 1
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Paralleler Ausführung bietet im Allgemeinen Vorteile nur bei der Arbeit mit sehr großen Datenmengen. Die SQL-Datenbank-Engine könnten, dass die parallele Ausführung nicht erforderlich ist. Darüber hinaus muss die SQL-Abfrage, die die Daten abruft, einen parallelen Abfrageplan generieren können.

+ Bei Verwendung der Option der parallelen Ausführung **müssen** Sie das Schema der Ausgabeergebnisse im Voraus mit der WITH RESULT SETS-Klausel angeben. Wenn Sie das Ausgabeschema im Voraus angeben, kann SQL Server die Ergebnisse von mehreren parallelen Datasets aggregieren, die andernfalls über unbekannte Schemas verfügen könnten.

+ Wenn Sie sind *Training* eines Modells anstelle von *Bewertung*, diesen Parameter häufig keine Auswirkung. Je nach Modelltyp kann es bei der Erstellung des Modells erforderlich sein, dass alle Zeilen gelesen werden, bevor Zusammenfassungen erstellt werden können.

+ Um die Vorteile der parallelen Verarbeitung beim Trainieren Ihres Modells zu erhalten, es wird empfohlen, die Verwendung eines der **RevoScaleR** Algorithmen. Diese Algorithmen dienen zum Verteilen der Verarbeitung automatisch, auch wenn Sie nicht angeben <code>@parallel =1</code> im Aufruf von `sp_execute_external_script`. Anleitungen dazu, wie Sie die beste Leistung mit RevoScaleR-Algorithmen erzielen, finden Sie unter [verteilte und parallelem computing mit ScaleR in Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).

## <a name="create-an-r-plot-of-the-model"></a>Erstellen eines R-Diagramms des Modells

Viele Clients einschließlich SQL Server Management Studio können mit [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) erstellte Diagramme nicht direkt anzeigen. Stattdessen ist der allgemeine Prozess für das R-Plots generieren, erstellen das Diagramm als Teil des R-Code, und klicken Sie dann das Image in eine Datei schreiben.

Alternativ können Sie die serialisierte binäre Diagrammobjekt an eine beliebige Anwendung zurückgeben, die Bilder anzeigen kann.

Im folgenden Beispiel wird veranschaulicht, wie eine einfache Grafik mit einer Zeichenfunktion erstellt wird, die standardmäßig in R enthalten ist. Das Bild wird an die angegebene Datei ausgegeben. Zudem wird es von der gespeicherten Prozedur in eine SQL-Variable ausgegeben.

```sql
 EXECUTE sp_execute_external_script
 @language = N'R'
 , @script = N'
     imageDir <- ''C:\\temp\\plots'';
     image_filename = tempfile(pattern = "plot_", tmpdir = imageDir, fileext = ".jpg")
     print(image_filename);
     jpeg(filename=image_filename,  width=600, height = 800);
     print(plot(distance~speed, data=InputDataSet, xlab="Speed", ylab="Stopping distance", main = "1920 Car Safety"));
     abline(lm(distance~speed, data = InputDataSet));
     dev.off();
     OutputDataSet <- data.frame(data=readBin(file(image_filename, "rb"), what=raw(), n=1e6));
     '
  , @input_data_1 = N'SELECT speed, distance from [dbo].[CarSpeed]'
  WITH RESULT SETS ((plot varbinary(max)));
```

+ Die `tempfile` Funktionsergebnis ist eine Zeichenfolge, die als Dateiname verwendet werden kann, aber die Datei noch nicht generiert wurde.
+ Für die Argumente `tempfile`, können Sie ein Präfix und der Dateierweiterung sowie das Verzeichnis angeben. Um den vollständigen Dateinamen und den Pfad zu überprüfen, Drucken eine Meldung mit `str()`.
+ Die `jpeg`-Funktion erstellt ein R-Gerät mit den angegebenen Parametern.
+ Nachdem Sie das Diagramm erstellt haben, können Sie weitere visuellen Funktionen darauf hinzufügen. In diesem Fall wird eine Regressionsgerade mit hinzugefügt `abline`.
+ Wenn Sie die Grafikfunktionen hinzugefügt haben, müssen Sie das Grafikgerät mithilfe der `dev.off()`-Funktion schließen.
+ Die `readBin`-Funktion nimmt eine Datei zum Lesen, eine Formatangabe und die Anzahl der Datensätze auf. Die `rb`** "-Schlüsselwort Gibt an, dass die Datei Binärdatei anstatt um Text handelt.

**Ergebnisse**

![rsql_basictut_plotresult_small](media/rsql-basictut-plotresult-small.png)

Wenn Sie detailreichere Diagramme mit einigen der tollen Grafikpakete für R erstellen möchten, empfehlen wir Ihnen diese Artikel. Für beide ist das beliebte **ggplot2**-Paket erforderlich.

+ [Loan Classification using SQL Server 2016 R Services (Krediteinstufung mit SQL Server 2016 R Services)](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/): End-to-End-Szenario basierend auf Versicherungsdaten. Erfordert die **umformen** Paket.
+ [Erstellen von Graphen und Diagrammen mit R](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="next-steps"></a>Nächste Schritte

Die Integration von R mit SQL Server erleichtert das Bereitstellen skalierbarer R-Lösungen durch Nutzung der besten Funktionen von R und relationalen Datenbanken für Datenverarbeitung mit hoher Leistung und schnelle R-Analysen. 

Weitere Informationen zu Lösungen, die mithilfe von R mit SQL Server-End-to-End-Szenarien, die von den Entwicklungsteams von Microsoft Data Science und R Services erstellt.

> [!div class="nextstepaction"]
> [SQL Server-R-Lernprogramme](sql-server-r-tutorials.md)
