---
title: Verwenden Sie ein Python-Modell in SQL Server, für das Trainieren und Vorhersagen | Microsoft-Dokumentation
description: Erstellen und Trainieren eines Modells mit Python und das klassische Iris-DataSet. Speichern Sie das Modell in SQL Server, und dann verwenden Sie, um die vorhergesagten Ergebnisse zu generieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 839bcecdeaf7b5e2a7ea1297fe941353bffed20e
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461836"
---
# <a name="use-a-python-model-in-sql-server-for-training-and-scoring"></a>Verwenden Sie ein Python-Modell in SQL Server für das Trainieren und bewerten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Erfahren Sie in dieser Übung Python ein häufiges Muster für das Erstellen, Trainieren und verwenden ein Modell in SQL Server aus. In dieser Übung erstellt zwei gespeicherte Prozeduren. Das erste Abonnement generiert eine Naïve Bayes-Modell, um ein Iris-Arten basierend auf Blume Merkmalen vorherzusagen. Das zweite Verfahren ist für die Bewertung. Er ruft das Modell im ersten Verfahren zur Ausgabe einer Reihe von Vorhersagen generiert. In dieser Übung zu durchlaufen, erfahren Sie grundlegende Verfahren, die grundlegende Python-Code auf einer Instanz von SQL Server-Datenbank-Engine ausgeführt werden.

In dieser Übung verwendeten Beispieldaten sind die [Iris-Dataset](demo-data-iris-in-sql.md) in die **Irissql** Datenbank.

## <a name="create-a-model-using-a-sproc"></a>Erstellen eines Modells mithilfe einer gespeicherten Prozedur

1. Öffnen Sie ein neues Abfragefenster in Management Studio verbunden die **Irissql** Datenbank. 

    ```sql
    USE irissql
    GO
    ```

2. Führen Sie den folgenden Code in einem neuen Abfragefenster die gespeicherte Prozedur zu erstellen, die erstellt und trainiert ein Modell, aus. Modelle, die für die Wiederverwendung in SQL Server gespeichert sind, werden als Byte-Stream serialisiert und in einer varbinary(max)-Spalte in einer Datenbanktabelle gespeichert. Nachdem das Modell erstellt wurde, kann trainiert, serialisiert und in einer Datenbank gespeichert es von anderen Prozeduren oder von der VORHERSAGEN für T-SQL-Funktion in die Bewertung von Workloads aufgerufen werden.

   Dieser Code verwendet die Pickle zum Serialisieren des Modells und Scikit Naïve Bayes-Algorithmus bereitstellen. Das Modell trainiert, mit Daten aus Spalten von 0 bis 4 aus der **Iris_data** Tabelle. Formulieren Sie die Parameter, die Sie im zweiten Teil der Prozedur finden Sie unter Dateneingaben und modellausgaben vorhanden. 

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

3. Stellen Sie sicher, dass die gespeicherte Prozedur vorhanden ist. Wenn das T-SQL-Skript aus dem vorherigen Schritt ohne Fehler ausgeführt haben, eine neue gespeicherte Prozedur aufgerufen wird **Generate_iris_model** wird erstellt und hinzugefügt werden, um die **Irissql** Datenbank. Gespeicherte Prozeduren finden Sie in Management Studio **Objekt-Explorer**unter **Programmierbarkeit**.

## <a name="execute-the-sproc-to-create-and-train-models"></a>Ausführen der gespeicherten Prozedur zum Erstellen und Trainieren von Modellen

1. Nachdem die gespeicherte Prozedur erstellt wurde, führen Sie den folgenden Code, die unten, um sie auszuführen. Die spezifische Anweisung für die Ausführung einer gespeicherten Prozedur ist `EXEC` in der fünften Zeile.

   Dieses Skript löscht ein vorhandenes Modell mit dem gleichen Namen ("Naive Bayes") um Platz für neue Dateien erstellt, indem Sie das gleiche Verfahren ausführen zu machen. Ohne Modell löschen tritt der Fehler darauf hinweist, dass das Objekt bereits vorhanden ist. 

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes '
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

2. Anzeigen der Ergebnisse im Ausgabebereich. Das Skript enthält eine SELECT-Anweisung zeigt, dass das Modell vorhanden ist. Ist eine weitere Möglichkeit zum Zurückgeben einer Liste mit Modellen `SELECT * FROM iris_models` in **Irissql**.

    **Ergebnisse**

    |   | (kein Spaltenname |
    |---|-----------------|
    | 1 | Naive Bayes     | 


## <a name="create-and-execute-a-sproc-for-generating-predictions"></a>Erstellen Sie und führen Sie einer gespeicherten Prozedur zum Generieren von Vorhersagen aus

Nun, dass Sie erstellt, trainiert, und ein Modell gespeichert, mit dem nächsten Schritt fortfahren: Erstellen einer gespeicherten Prozedur, die generiert Vorhersagen. Sie müssen hierzu durch Aufrufen von Sp_execute_external_script, starten Sie Python aus, und klicken Sie dann im Python-Skript, das ein serialisiertes Modell lädt Sie in der letzten Übung erstellt und weist diesem dann Dateneingaben zu bewertende übergeben.

1. Führen Sie den folgenden Code zum Erstellen der gespeicherten Prozedur, die Bewertung ausführt. Dieses Verfahren wird zur Laufzeit ein binäres Modell zu laden, Spalten `[1,2,3,4]` als Eingabe, und geben Sie Spalten `[0,5,6]` als Ausgabe.

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
    OutputDataSet = iris_data[[0,5,6]] 
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

2. Führen Sie die gespeicherte Prozedur, sodass den Modellnamen "Naive Bayes", damit die Prozedur weiß, welches Modell zu verwenden. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    Wenn Sie die gespeicherte Prozedur ausführen, wird ein Python-Datenrahmen (Data.Frame) zurückgegeben. Diese Zeile von T-SQL gibt das Schema für die zurückgegebenen Ergebnisse: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`. Sie können die Ergebnisse in eine neue Tabelle einfügen, oder gibt sie an einer Anwendung zurück.

    ![Resultset von der Ausführung der gespeicherten Prozedur](media/train-score-using-python-NB-model-results.png)

    Die Ergebnisse sind 150 Vorhersagen darüber gibt, die mithilfe von Blumen Merkmale als Eingaben. Für die meisten der Beobachtungen entspricht die vorhergesagten gibt die tatsächliche Art.

    In diesem Beispiel einfache wurde unter Verwendung des Python-Iris-Datasets für Training und Bewertung. Ein üblicher Ansatz würde beinhalten das Ausführen einer SQL-Abfrage, um die neuen Daten zu erhalten, und übergeben Sie ihn an Python als `InputDataSet`. 

## <a name="conclusion"></a>Fazit

In dieser Übung haben Sie gelernt, wie gespeicherte Prozeduren für verschiedene Aufgaben erstellen, in denen jede gespeicherte Prozedur die gespeicherte Systemprozedur verwendet [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) einen Python-Prozess zu starten. Eingaben für die Python-Prozess werden Sp_execute_external Skript als Parameter übergeben. Sowohl die Datenvariablen in einer SQL Server-Datenbank die Python-Skript selbst werden als Eingaben übergeben.

Wenn Sie mit der Arbeit in Python werden verwendet, können Sie zum Laden von Daten, erstellen einige Zusammenfassungen und Diagramme, und klicken Sie dann das Trainieren eines Modells und Generieren von Bewertungen in der gleichen 250 Codezeilen vertraut sein. In diesem Artikel werden übliche Ansätze unterscheidet, durch die Vorgänge in separate Verfahren zu organisieren. Diese Vorgehensweise ist hilfreich, auf verschiedenen Ebenen.

Ein Vorteil ist, dass Sie Prozesse in repeatable Schritte trennen können, die mithilfe der Parameter geändert werden kann. So weit wie möglich, sollten Sie die Python-Code, den Sie ausführen, in einer gespeicherten Prozedur eindeutig definiert haben, Eingaben und Ausgaben, die Eingaben der gespeicherten Prozedur zuordnen und Ausgaben, die zur Laufzeit übergeben werden kann. In dieser Übung wird Python-Code, der ein Modell (mit dem Namen "Naive Bayes" in diesem Beispiel) erstellt, als Eingabe für eine zweite gespeicherte Prozedur übergeben, die das Modell in einen Bewertungsprozess aufruft.

Ein zweiter Vorteil ist die Trainings- und Prozesse zu bewerten, kann optimiert werden, durch die Nutzung der Features von SQL Server, z. B. die parallelverarbeitung, Ressourcenkontrolle, oder mithilfe von Algorithmen in [Revoscalepy](../python/what-is-revoscalepy.md) oder [MicrosoftML ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) , Unterstützung von streaming und parallele Ausführung. Durch das Trainieren und Bewerten von getrennt, können Sie die Optimierungen für bestimmte arbeitsauslastungen abzielen.

## <a name="next-steps"></a>Nächste Schritte

Vorherigen Tutorials konzentriert sich auf lokale Ausführung. Allerdings können Sie auch Python-Code auf einer Clientarbeitsstation ausführen mithilfe von SQL Server als dem entfernten computekontext. Weitere Informationen zum Einrichten einer Clientarbeitsstation, die mit SQL Server verbunden ist, finden Sie unter [Einrichten von Python-Clienttools](../python/setup-python-client-tools-sql.md).

+ [Erstellen eines Revoscalepy-Modells aus einem Python-client](use-python-revoscalepy-to-create-model.md)
