---
title: 'Schnellstart: Vorhersagen aus R – SQL Server-Machine Learning-Modell'
description: In dieser schnellstartanleitung erfahren Sie mehr zur Bewertung der Verwendung eines vordefinierten Modells in R und SQL Server-Daten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7175b99eb20710f5dd08689bd055d3a4ec93ae92
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046810"
---
# <a name="quickstart-predict-from-model-using-r-in-sql-server"></a>Schnellstart: Vorhersagen Sie aus dem Modell mithilfe von R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Verwenden Sie in diesem Schnellstart das Modell, das Sie im vorherigen Schnellstart zur Bewertung von Vorhersagen für neue Daten erstellt haben. Auszuführende _Bewertung_ mit neuen Daten, eines der trainierten Modelle aus der Tabelle, und rufen Sie dann einen neuen Satz von Daten für die Vorhersagen basieren. Bewertung ist ein Begriff, die manchmal zum Generieren von Vorhersagen, Wahrscheinlichkeiten und andere Werte, die basierend auf neuen Daten, die in einem trainierten Modell eingegeben, bedeutet im Data Science-Prozess verwendet.

## <a name="prerequisites"></a>Erforderliche Komponenten

Dieser Schnellstart ist eine Erweiterung der [Erstellen eines Vorhersagemodells](quickstart-r-create-predictive-model.md).

## <a name="create-the-table-of-new-data"></a>Erstellen der Tabelle mit neuen Daten

Erstellen Sie zunächst eine Tabelle mit neuen Daten an. 

```sql
CREATE TABLE dbo.NewMTCars(
    hp INT NOT NULL
    , wt DECIMAL(10,3) NOT NULL
    , am INT NULL
)
GO

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (110, 2.634)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (72, 3.435)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (220, 5.220)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (120, 2.800)
GO
```

## <a name="predict-manual-transmission"></a>Vorhersagen der manuellen Übertragung

Nun können Ihre `dbo.GLM_models` Tabelle enthält möglicherweise mehrere R-Modelle, alle erstellten mit verschiedenen Parametern oder Algorithmen verwenden oder für unterschiedliche Teilmengen der Daten trainiert.

Um vorhersagen basierend auf einem bestimmten Modell zu erhalten, müssen Sie ein SQL-Skript schreiben, die Folgendes ausführt:

1. Ruft das gewünschte Modell ab
2. Ruft die neuen Eingabedaten ab
3. Ruft eine R-Vorhersagefunktion auf, die mit dem Modell kompatibel ist

In diesem Beispiel verwenden wir das Modell mit dem Namen `default model`.

```sql
DECLARE @glmmodel varbinary(max) = 
    (SELECT model FROM dbo.GLM_models WHERE model_name = 'default model');

EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(glmmodel));
            new <- data.frame(NewMTCars);
            predicted.am <- predict(current_model, new, type = "response");
            str(predicted.am);
            OutputDataSet <- cbind(new, predicted.am);
            '
    , @input_data_1 = N'SELECT hp, wt FROM dbo.NewMTCars'
    , @input_data_1_name = N'NewMTCars'
    , @params = N'@glmmodel varbinary(max)'
    , @glmmodel = @glmmodel
WITH RESULT SETS ((new_hp INT, new_wt DECIMAL(10,3), predicted_am DECIMAL(10,3)));
```

Das obige Skript führt die folgenden Schritte aus:

+ Verwenden Sie eine SELECT-Anweisung, um ein einzelnes Modell aus der Tabelle abzurufen, und übergeben Sie es als Eingabeparameter.

+ Rufen Sie nach dem Abruf des Modells aus der Tabelle die `unserialize`-Funktion auf dem Modell auf.

+ Wenden Sie die `predict`-Funktion mit geeigneten Argumenten auf das Modell an, und stellen Sie die neuen Eingabedaten bereit.

+ Im Beispiel die `str` -Funktion wurde hinzugefügt, während der Testphase, um das Schema der von r zurückgegebenen Daten zu überprüfen Sie können die Anweisung später erneut entfernen.

+ Die im R-Skript verwendeten Spaltennamen sind nicht unbedingt an die Ausgabe der gespeicherten Prozedur übergeben. Hier haben wir die WITH RESULTS-Klausel verwendet, um einige neue Spaltennamen zu definieren.

**Ergebnisse**

![Resultset für die Vorhersage Properbility der manuellen Übertragung](./media/r-predict-am-resultset.png)

Es ist auch möglich, mit der [VORHERSAGEN in Transact-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) um einen vorhergesagten Wert oder die Bewertung auf Grundlage eines gespeicherten Modells generieren.

## <a name="next-steps"></a>Nächste Schritte

Die Integration von R mit SQL Server erleichtert das Bereitstellen skalierbarer R-Lösungen durch Nutzung der besten Funktionen von R und relationalen Datenbanken für Datenverarbeitung mit hoher Leistung und schnelle R-Analysen. 

Weitere Informationen zu Lösungen, die mithilfe von R mit SQL Server-End-to-End-Szenarien, die von den Entwicklungsteams von Microsoft Data Science und R Services erstellt.

> [!div class="nextstepaction"]
> [SQL Server-R-Lernprogramme](sql-server-r-tutorials.md)
