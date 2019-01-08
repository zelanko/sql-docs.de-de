---
title: 'Schnellstart: erstellen ein Vorhersagemodells mit R – SQL Server-Machine Learning'
description: Erfahren Sie in dieser schnellstartanleitung, wie zum Erstellen eines Modells in R mit SQL Server-Daten, um vorhersagen zu zeichnen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 278eba1189b376b57f2dec7249a378832c18095c
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046789"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>Schnellstart: Erstellen eines Vorhersagemodells mit R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser schnellstartanleitung haben Sie erfahren, wie Sie das Trainieren eines Modells mit R, und klicken Sie dann das Modell in einer Tabelle in SQL Server speichern. Das Modell ist ein einfaches Verallgemeinertes Lineares Modell ("glm"), das Wahrscheinlichkeit vorhergesagt, dass ein Fahrzeug mit einer manuellen Übertragung angepasst wurde. Verwenden Sie die `mtcars` Dataset enthalten, die mit R.

## <a name="prerequisites"></a>Erforderliche Komponenten

Einen vorherigen schnellstartanleitung [R stellen Sie sicher, die in SQL Server vorhanden ist](quickstart-r-verify.md), enthält Informationen und links für das Einrichten der R-Umgebung, die im Rahmen dieser schnellstartanleitung benötigt.

## <a name="create-the-source-data"></a>Erstellen der Quelldaten

Erstellen Sie zuerst eine Tabelle zum Speichern der Trainingsdaten.

```sql
CREATE TABLE dbo.MTCars(
    mpg decimal(10, 1) NOT NULL,
    cyl int NOT NULL,
    disp decimal(10, 1) NOT NULL,
    hp int NOT NULL,
    drat decimal(10, 2) NOT NULL,
    wt decimal(10, 3) NOT NULL,
    qsec decimal(10, 2) NOT NULL,
    vs int NOT NULL,
    am int NOT NULL,
    gear int NOT NULL,
    carb int NOT NULL
);
```

Als Nächstes fügen Sie die Daten aus dem Build im Dataset `mtcars`.

```SQL
INSERT INTO dbo.MTCars
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'MTCars <- mtcars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'MTCars';
```

+ Einige Benutzer möchten gern temporäre Tabellen verwenden, aber beachten Sie, dass einige R Clients Sitzungen zwischen Batches trennen.

+ Viele kleine und große Datasets sind in der R-Laufzeit enthalten. Geben Sie aus einer R-Eingabeaufforderung heraus `library(help="datasets")` ein, um eine Liste der mit R installierten Datasets anzuzeigen.

## <a name="create-a-model"></a>Erstellen eines Modells

Daten der autogeschwindigkeit enthält zwei Spalten: beide numerisch, pferdestärke (`hp`) und Gewichtung (`wt`). Aus diesen Daten erstellen Sie ein Verallgemeinertes Lineares Modell ("glm"), das die Wahrscheinlichkeit schätzt, dass ein Fahrzeug mit einer manuellen Übertragung angepasst wurde.

Um das Modell zu erstellen, Sie definieren die Formel in Ihrem R-Code und die Daten als Eingabeparameter übergeben.

```sql
DROP PROCEDURE IF EXISTS generate_GLM;
GO
CREATE PROCEDURE generate_GLM
AS
BEGIN
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'carsModel <- glm(formula = am ~ hp + wt, data = MTCarsData, family = binomial);
        trained_model <- data.frame(payload = as.raw(serialize(carsModel, connection=NULL)));'
    , @input_data_1 = N'SELECT hp, wt, am FROM MTCars'
    , @input_data_1_name = N'MTCarsData'
    , @output_data_1_name = N'trained_model'
    WITH RESULT SETS ((model VARBINARY(max)));
END;
GO
```

+ Das erste Argument für `glm` ist die *Formel* -Parameter, der definiert, `am` als abhängig `hp + wt`.
+ Die Eingabedaten werden in der Variable `MTCarsData` gespeichert, die durch die SQL-Abfrage aufgefüllt wird. Wenn Sie Ihren Eingabedaten keinen spezifischen Namen zuweisen, ist der Standardvariablenname _InputDataSet_.

## <a name="create-a-table-for-the-model"></a>Erstellen Sie eine Tabelle für das Modell

Speichern Sie als Nächstes das Modell auf, damit Sie erneut zu trainieren oder für Vorhersagen verwenden können. Die Ausgabe eines R-Pakets, das ein Modell erstellt, ist normalerweise ein **binäres Objekt**. Aus diesem Grund muss in der Tabelle, in dem Sie das Modell speichern, eine Spalte angeben **'varbinary(max)'** Typ.

```sql
CREATE TABLE GLM_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
```

## <a name="save-the-model"></a>Speichern des Modells

Führen Sie zum Speichern des Modells die folgende Transact-SQL-Anweisung aus, um die gespeicherte Prozedur aufzurufen, das Modell zu generieren und es in einer Tabelle zu speichern.

```sql
INSERT INTO GLM_models(model)
EXEC generate_GLM;
```

Beachten Sie, wenn Sie diesen Code ein zweites Mal ausführen, erhalten Sie diesen Fehler:

```sql
Violation of PRIMARY KEY constraint...Cannot insert duplicate key in object dbo.stopping_distance_models
```

Eine Möglichkeit zur Vermeidung dieses Fehlers besteht darin, den Namen für jedes neue Modell zu aktualisieren. Sie können den Namen z.B. in einen aussagekräftigeren Namen ändern und den Modelltyp, den Erstellungstag usw. mit aufnehmen.

```sql
UPDATE GLM_models
SET model_name = 'GLM_' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
WHERE model_name = 'default model'
```

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie ein Modell, in die letzte Schnellstart verfügen, erfahren Sie wie Sie darauf basierende Vorhersagen trifft und die Ergebnisse darstellt.

> [!div class="nextstepaction"]
> [Schnellstart: Vorhersagen und zeichnen ausgehend vom Modell](quickstart-r-predict-from-model.md)