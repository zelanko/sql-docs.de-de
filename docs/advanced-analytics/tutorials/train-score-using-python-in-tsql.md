---
title: Verwenden von Python-Modell in SQL für training und Bewertung | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 02ffd5a25c076ef5a65a6e3a998aae485e37d982
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085022"
---
# <a name="use-python-model-in-sql-for-training-and-scoring"></a>Verwenden von Python-Modell in SQL für training und Bewertung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In der [vorherigen Lektion](wrap-python-in-tsql-stored-procedure.md), haben Sie gelernt, das allgemeine Muster für die Verwendung von Python sowie SQL. Sie haben gelernt, dass Ihre Python-Code eine klar definierte Datenrahmen (Data.Frame) ausgegeben werden soll, und können optional mehrere Variablen von skalare oder binäre Ausgabe. Sie haben gelernt, dass die gespeicherte Prozedur von SQL entworfen werden soll, übergeben die richtige Art der Daten in Python und Verarbeiten der Ergebnisse.

In diesem Abschnitt verwenden dieses Muster zum Trainieren eines Modells aus, für die Daten, die Sie in SQL Server hinzugefügt haben, und das Modell in einer SQL Server-Tabelle speichern:

+ Entwerfen Sie eine gespeicherte Prozedur, die ein Python-Machine learning-Funktion aufruft.
+ Die gespeicherte Prozedur benötigt Daten aus SQL Server beim Trainieren des Modells verwenden.
+ Die gespeicherte Prozedur gibt ein trainiertes Modell als eine binäre Variable. 
+ Sie speichern das trainierte Modell, indem Sie Variable Modell in eine Tabelle einzufügen. 

## <a name="create-the-stored-procedure-and-train-a-python-model"></a>Erstellen Sie die gespeicherte Prozedur und Trainieren Sie ein Python-Modell

1. Führen Sie den folgenden Code in SQL Server Management Studio zum Erstellen der gespeicherten Prozedur, die ein Modell erstellt.

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python',
    @script = N'
    import pickle
    from sklearn.naive_bayes import GaussianNB
    GNB = GaussianNB()
    trained_model = pickle.dumps(GNB.fit(iris_data[[0,1,2,3]], iris_data[[4]]))
    '
    , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@trained_model varbinary(max) OUTPUT'
    , @trained_model = @trained_model OUTPUT;
    END;
    GO
    ```

2. Wenn dieser Befehl ohne Fehler ausgeführt wird, wird eine neue gespeicherte Prozedur erstellt und der Datenbank hinzugefügt. Gespeicherte Prozeduren finden Sie in Management Studio **Objekt-Explorer**unter **Programmierbarkeit**.

3. Führen Sie nun die gespeicherte Prozedur.

    ```sql
    EXEC generate_iris_model
    ```

    Sie sollten einen Fehler erhalten, da Sie bereitgestellt haben, dass die Eingabe der gespeicherten Prozedur erforderlich ist.

    "Prozedur oder Funktion 'Generate_iris_model" erwartet Parameter "\@Trained_model", der nicht bereitgestellt wurde. "

4. Zum Generieren des Modells mit erforderlichen Eingaben, und speichern es in einer Tabelle müssen einige zusätzlichen Anweisungen ein:

    ```sql
    DECLARE @model varbinary(max);
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values('Naive Bayes', @model);
    ```

5. Nun versuchen Sie, den Modell-Generation-Code einmal ausführen. 

    Erhalten Sie die Fehlermeldung: "Verletzung der PRIMARY KEY-Einschränkung kann keine doppelten Schlüssel in das Objekt"dbo.iris_models"eingefügt. Der doppelte Schlüsselwert ist (Naive Bayes) ".

    Das ist, da der Name des Modells durch die manuelle Eingabe in "Naive Bayes" als Teil der INSERT-Anweisung angegeben wurde. Vorausgesetzt, dass Sie viele Modelle erstellen möchten, verwenden verschiedene Parameter oder andere Algorithmen bei jeder Ausführung, sollten das Einrichten eines Metadaten-Schemas Sie so, dass Sie Modelle automatisch benennen können und weitere sie ganz einfach identifizieren.

6. Um diesen Fehler zu umgehen, können Sie einige geringfügigen Änderungen der SQL-Wrapper vornehmen. In diesem Beispiel wird einen eindeutige Namen durch Anhängen der aktuellen Datum und Uhrzeit generiert:

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes ' + CAST(GETDATE()as varchar)
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    ```

7. Um die Modelle anzuzeigen, führen Sie eine einfache SELECT-Anweisung.

    ```sql
    SELECT * FROM iris_models;
    GO
    ```

    **Ergebnisse**

    |Modellname | model |
    |------|------|
    | Naive Bayes | 0x800363736B6C656172... |
    | Naive Bayes Jan 01 2018, 9:39 Uhr | 0x800363736B6C656172... |
    | Naive Bayes Feb 01 2018 10:51 Uhr | 0x800363736B6C656172... |

## <a name="generate-scores-from-the-model"></a>Generieren von Bewertungen aus dem Modell

Abschließend sehen wir laden Sie dieses Modell aus der Tabelle in eine Variable, und übergeben es an Python zum Generieren von Bewertungen.

1. Führen Sie den folgenden Code zum Erstellen der gespeicherten Prozedur, die Bewertung ausführt. 

    ```sql
    CREATE PROCEDURE predict_species (@model varchar(100))
    AS
    BEGIN
    DECLARE @nb_model varbinary(max) = (SELECT model FROM iris_models WHERE model_name = @model);
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    import pickle
    irismodel = pickle.loads(nb_model)
    species_pred = irismodel.predict(iris_data[[1,2,3,4]])
    iris_data["PredictedSpecies"] = species_pred
    OutputDataSet = iris_data.query( ''PredictedSpecies != SpeciesId'' )[[0, 5, 6]]
    print(OutputDataSet)
    '
    , @input_data_1 = N'select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@nb_model varbinary(max)'
    , @nb_model = @nb_model
    WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));
    END;
    GO
    ```

    Die gespeicherte Prozedur ruft das Naïve Bayes-Modell aus der Tabelle ab und verwendet die Funktionen, die mit dem Modell verbundenen zum Generieren von Bewertungen. In diesem Beispiel ruft die gespeicherte Prozedur das Modell aus der Tabelle mit den Modellnamen ab. Allerdings je nachdem, welche Art von Metadaten Sie mit dem Modell speichern, können Sie auch das neueste Modell oder das Modell mit der höchsten Genauigkeit abrufen.

2. Führen Sie die folgenden Zeilen ein, um den Modellnamen "Naive Bayes" an die gespeicherte Prozedur zu übergeben, das die Bewertung Code ausführt. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    Wenn Sie die gespeicherte Prozedur ausführen, wird ein Python-Datenrahmen (Data.Frame) zurückgegeben. Diese Zeile von T-SQL gibt an, das Schema für die zurückgegebenen Ergebnisse: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`

    Sie können die Ergebnisse in eine neue Tabelle einfügen, oder gibt sie an einer Anwendung zurück.

    In diesem Beispiel verfügt über einfache vorgenommen wurden, indem Sie die Daten aus dem Python-Iris-Dataset für die Bewertung. (Finden Sie unter der Zeile `iris_data[[1,2,3,4]])`.) Allerdings in der Regel würde Ausführen eine SQL-Abfrage, um die neuen Daten zu erhalten und übergeben Sie ihn an Python als `InputDataSet`. 

### <a name="remarks"></a>Hinweise

Wenn Sie mit der Arbeit in Python werden verwendet, können Sie zum Laden von Daten, erstellen einige Zusammenfassungen und Diagramme, und klicken Sie dann das Trainieren eines Modells und Generieren von Bewertungen in der gleichen 250 Codezeilen vertraut sein.

Wenn Ihr Ziel ist den Prozess (Erstellung des Modells, Bewertung, usw.) in SQL Server zu operationalisieren, ist es jedoch wichtig, die Art und Weise berücksichtigen, dass Sie den Prozess in repeatable Schritte trennen können, die mithilfe der Parameter geändert werden kann. So weit wie möglich, sollten Sie die Python-Code, den Sie, in einer gespeicherten Prozedur eindeutig definiert haben ausführen, Eingaben und Ausgaben, die gespeicherte Prozedur Eingaben und Ausgaben zugeordnet, wird.

Sie können darüber hinaus im Allgemeinen Leistung verbessern, durch die Trennung der Untersuchung von Daten von den Prozessen Trainieren eines Modells oder Generieren von Bewertungen. 

Scoring und Training-Prozesse können häufig optimiert werden durch die Nutzung der Features von SQL Server, z. B. die parallelverarbeitung, oder mithilfe von Algorithmen in [Revoscalepy](../python/what-is-revoscalepy.md) oder [MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) , streaming-Unterstützung und parallele Ausführung, anstatt mithilfe von Python-Standardbibliotheken. 

## <a name="next-lesson"></a>Nächste Lektion

In der abschließenden Lektion führen Sie Python-Code, von einem Remoteclient, mithilfe von SQL Server als computekontext aus. Dieser Schritt ist optional, wenn Sie nicht über eine Python-Client oder nicht Python außerhalb einer gespeicherten Prozedur ausgeführt werden soll.

+ [Erstellen eines Revoscalepy-Modells aus einem Python-client](use-python-revoscalepy-to-create-model.md)
