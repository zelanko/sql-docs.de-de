---
title: Schnellstart für die Vorhersage aus dem Modell mithilfe von R
description: In dieser Schnellstartanleitung erfahren Sie mehr über die Bewertung mithilfe eines vorgefertigten Modells in R und SQL Server Daten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: e81731683fb71b074ed754ab6ab4eaab40d08c20
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345409"
---
# <a name="quickstart-predict-from-model-using-r-in-sql-server"></a>Schnellstart: Vorhersagen aus dem Modell mithilfe von R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser Schnellstartanleitung verwenden Sie das Modell, das Sie im vorherigen Schnellstart erstellt haben, um Vorhersagen für neue Daten zu bewerten. Um die _Bewertung_ mithilfe neuer Daten auszuführen, sollten Sie eines der trainierten Modelle aus der Tabelle abrufen und dann einen neuen Satz von Daten abrufen, auf denen Vorhersagen basieren sollen. Die Bewertung ist ein Begriff, der manchmal in Data Science verwendet wird, um Vorhersagen, Wahrscheinlichkeiten oder andere Werte basierend auf neuen Daten zu generieren, die in ein trainiertes Modell eingespeist werden.

## <a name="prerequisites"></a>Vorraussetzungen

Dieser Schnellstart ist eine Erweiterung der [Erstellung eines Vorhersagemodells](quickstart-r-create-predictive-model.md).

## <a name="create-the-table-of-new-data"></a>Erstellen der Tabelle mit neuen Daten

Erstellen Sie zunächst eine Tabelle mit neuen Daten. 

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

## <a name="predict-manual-transmission"></a>Prognose der manuellen Übertragung

Nun kann Ihre Tabelle `dbo.GLM_models` mehrere R-Modelle enthalten, die alle mit unterschiedlichen Parametern oder Algorithmen erstellt wurden oder auf unterschiedlichen Teilmengen von Daten trainiert wurden.

Um Vorhersagen basierend auf einem bestimmten Modell zu erhalten, müssen Sie ein SQL-Skript schreiben, das Folgendes bewirkt:

1. Ruft das gewünschte Modell ab
2. Ruft die neuen Eingabedaten ab
3. Ruft eine R-Vorhersagefunktion auf, die mit dem Modell kompatibel ist

In diesem Beispiel wird das Modell mit dem Namen `default model`verwendet.

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

+ Im Beispiel wird die `str` -Funktion während der Testphase hinzugefügt, um das Schema der von R zurückgegebenen Daten zu überprüfen. Sie können die Anweisung später entfernen.

+ Die Spaltennamen, die im R-Skript verwendet werden, werden nicht notwendigerweise an die Ausgabe der gespeicherten Prozedur übermittelt. Hier haben wir die with results-Klausel verwendet, um einige neue Spaltennamen zu definieren.

**Ergebnisse**

![Resultset für die Vorhersage der Zulässigkeit der manuellen Übertragung](./media/r-predict-am-resultset.png)

Es ist auch möglich, die [Vorhersage in Transact-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) zu verwenden, um einen vorhergesagten Wert oder eine Bewertung auf der Grundlage eines gespeicherten Modells zu generieren.

## <a name="next-steps"></a>Nächste Schritte

Die Integration von R mit SQL Server erleichtert das Bereitstellen skalierbarer R-Lösungen durch Nutzung der besten Funktionen von R und relationalen Datenbanken für Datenverarbeitung mit hoher Leistung und schnelle R-Analysen. 

Erfahren Sie mehr über Lösungen mithilfe von R und SQL Server durch End-to-End-Szenarios, die von den Entwicklungsteams von Microsoft Data Science und r Services erstellt werden.

> [!div class="nextstepaction"]
> [SQL Server-R-Lernprogramme](sql-server-r-tutorials.md)
