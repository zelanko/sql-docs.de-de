---
title: Schnellstart zum Erstellen eines Vorhersagemodells mithilfe von R
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie ein Modell in R erstellen, indem Sie SQL Server Daten zum Zeichnen von Vorhersagen verwenden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f902bd7325e84f07d50196c19338d9c05b3503d8
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715447"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>Schnellstart: Erstellen eines Vorhersagemodells mithilfe von R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Schnellstartanleitung erfahren Sie, wie Sie ein Modell mit R trainieren und das Modell dann in einer Tabelle in SQL Server speichern. Das Modell ist ein einfaches generalisiertes lineares Modell (GLM), das die Wahrscheinlichkeit vorhersagt, dass ein Fahrzeug mit einer manuellen Übertragung ausgestattet wurde. Sie verwenden das `mtcars` in R enthaltene DataSet.

## <a name="prerequisites"></a>Vorraussetzungen

Eine vorherige Schnellstartanleitung, [überprüfen, ob R in SQL Server vorhanden](quickstart-r-verify.md)ist, enthält Informationen und Links zum Einrichten der r-Umgebung, die für diesen Schnellstart erforderlich ist.

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

Fügen Sie dann die Daten aus dem Build in das DataSet `mtcars`ein.

```SQL
INSERT INTO dbo.MTCars
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'MTCars <- mtcars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'MTCars';
```

+ Einige Benutzer möchten temporäre Tabellen verwenden, aber beachten Sie, dass einige R-Clients Sitzungen zwischen Batches trennen.

+ Viele kleine und große Datasets sind in der R-Laufzeit enthalten. Geben Sie aus einer R-Eingabeaufforderung heraus `library(help="datasets")` ein, um eine Liste der mit R installierten Datasets anzuzeigen.

## <a name="create-a-model"></a>Erstellen eines Modells

Die Auto Geschwindigkeitsdaten enthalten zwei Spalten: numerisch, Pferdestärke`hp`() und Gewichtung`wt`(). Aus diesen Daten erstellen Sie ein generalisiertes lineares Modell (GLM), das die Wahrscheinlichkeit schätzt, dass ein Fahrzeug mit einer manuellen Übertragung ausgestattet wurde.

Um das Modell zu erstellen, definieren Sie die Formel in Ihrem R-Code und übergeben die Daten als Eingabeparameter.

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

+ Das erste Argument für `glm` ist der *Formel* Parameter, der als `am` abhängig von `hp + wt`definiert wird.
+ Die Eingabedaten werden in der Variable `MTCarsData` gespeichert, die durch die SQL-Abfrage aufgefüllt wird. Wenn Sie Ihren Eingabedaten keinen spezifischen Namen zuweisen, ist der Standardvariablenname _InputDataSet_.

## <a name="create-a-table-for-the-model"></a>Erstellen einer Tabelle für das Modell

Als nächstes speichern Sie das Modell, damit Sie es erneut trainieren oder für Vorhersagen verwenden können. Die Ausgabe eines R-Pakets, das ein Modell erstellt, ist normalerweise ein **binäres Objekt**. Daher muss in der Tabelle, in der das Modell gespeichert wird, eine Spalte vom Typ **varbinary (max)** bereitgestellt werden.

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

Beachten Sie, dass Sie diesen Fehler erhalten, wenn Sie diesen Code ein zweites Mal ausführen:

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

Nachdem Sie nun über ein Modell verfügen, erfahren Sie im letzten Schnellstart, wie Sie Vorhersagen daraus generieren und die Ergebnisse zeichnen.

> [!div class="nextstepaction"]
> [Schnellstart: Vorhersagen und zeichnen aus dem Modell](quickstart-r-predict-from-model.md)