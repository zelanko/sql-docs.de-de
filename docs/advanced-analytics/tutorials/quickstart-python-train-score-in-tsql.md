---
title: Schnellstart für Python-Modelle für das Trainieren und Vorhersagen mithilfe von gespeicherten Prozeduren – SQL Server-Machine Learning
description: Einbetten von Python-Code in SQL Server gespeicherte Prozeduren zu erstellen, Trainieren und verwenden ein Python-Modell mit dem klassischen Iris-DataSet. Speichern Sie ein trainiertes Modell in SQL Server, und dann verwenden Sie, um die vorhergesagten Ergebnisse zu generieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e8bacc383eba1148c1b357c344bc483e824df99b
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046816"
---
# <a name="quickstart-create-train-and-use-a-python-model-with-stored-procedures-in-sql-server"></a>Schnellstart: Erstellen Sie, Trainieren Sie und verwenden Sie ein Python-Modell mit gespeicherten Prozeduren in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser schnellstartanleitung mithilfe von Python Sie erstellen und Ausführen von zwei gespeicherten Prozeduren. Der erste verwendet das klassische Iris Flower DataSet und generiert eine Naïve Bayes-Modell, um ein Iris-Arten basierend auf Blume Merkmalen vorherzusagen. Das zweite Verfahren ist für die Bewertung. Er ruft das Modell im ersten Verfahren zur Ausgabe einer Reihe von Vorhersagen generiert. Platzieren Sie Code in einer gespeicherten Prozedur, sind Vorgänge von anderen gespeicherten Prozeduren und die Client-Anwendungen enthaltene, wiederverwendbare und aufgerufen. 

Nach Abschluss dieser schnellstartanleitung, lernen Sie Folgendes:

> [!div class="checklist"]
> * Gewusst wie: Einbetten von Python-Code in einer gespeicherten Prozedur
> * Wie Sie Eingaben in Ihrem Code über Eingaben für die gespeicherte Prozedur übergeben.
> * Wie gespeicherte Prozeduren, zum operationalisieren von Modellen verwendet werden

## <a name="prerequisites"></a>Erforderliche Komponenten

Einen vorherigen schnellstartanleitung [Python überprüfen, die in SQL Server vorhanden ist](quickstart-python-verify.md), enthält Informationen und links für das Einrichten der Python-Umgebung, die im Rahmen dieser schnellstartanleitung benötigt.

Die Beispieldaten, die in dieser Übung verwendet die [ **Irissql** ](demo-data-iris-in-sql.md) Datenbank.

## <a name="create-a-stored-procedure-that-generates-models"></a>Erstellen einer gespeicherten Prozedur, die Modelle generiert.

Ein häufiges Muster in der SQL Server-Entwicklung ist um programmierbare Vorgänge in verschiedene gespeicherte Prozeduren zu organisieren. In diesem Schritt erstellen Sie eine gespeicherte Prozedur, die ein Modell für Vorhersagen von Ergebnissen generiert. 

1. Öffnen Sie ein neues Abfragefenster in Management Studio verbunden die **Irissql** Datenbank. 

    ```sql
    USE irissql
    GO
    ```

2. Kopieren Sie in den folgenden Code, um eine neue gespeicherte Prozedur zu erstellen. 

   Bei der Ausführung dieser Prozedur aufgerufen [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) eine Python-Sitzung starten. 
   
   Eingaben, die von Ihren Python-Code benötigt werden, werden für diese gespeicherte Prozedur als Eingabeparameter übergeben. Ausgabe werden ein trainiertes Modell, basierend auf den Python **Scikit-erfahren Sie,** -Bibliothek für Machine Learning-Algorithmus. 

   Dieser Code verwendet [ **Pickle** ](https://docs.python.org/2/library/pickle.html) zum Serialisieren des Modells. Das Modell trainiert, mit Daten aus Spalten von 0 bis 4 aus der **Iris_data** Tabelle. 
   
   Formulieren Sie die Parameter, die Sie im zweiten Teil der Prozedur finden Sie unter Dateneingaben und modellausgaben vorhanden. So weit wie möglich, Sie möchten den Python-Code ausgeführt wird, in einer gespeicherten Prozedur eindeutig Eingaben definiert haben und gibt, die gespeicherte Prozedur Eingaben und Ausgaben, die zur Laufzeit übergeben zugeordnet. 

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python',
    @script = N'
    import pickle
    from sklearn.naive_bayes import GaussianNB
    GNB = GaussianNB()
    trained_model = pickle.dumps(GNB.fit(iris_data[[0,1,2,3]], iris_data[[4]].values.ravel()))
    '
    , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@trained_model varbinary(max) OUTPUT'
    , @trained_model = @trained_model OUTPUT;
    END;
    GO
    ```

3. Stellen Sie sicher, dass die gespeicherte Prozedur vorhanden ist. 

   Wenn das T-SQL-Skript aus dem vorherigen Schritt ohne Fehler ausgeführt haben, eine neue gespeicherte Prozedur aufgerufen wird **Generate_iris_model** wird erstellt und hinzugefügt werden, um die **Irissql** Datenbank. Gespeicherte Prozeduren finden Sie in Management Studio **Objekt-Explorer**unter **Programmierbarkeit**.

## <a name="execute-the-procedure-to-create-and-train-models"></a>Führen Sie die Prozedur zum Erstellen und Trainieren von Modellen

Führen Sie in diesem Schritt das Verfahren zum Ausführen des eingebetteten Codes, erstellen ein Modell entsprechend trainiert wurde und serialisiert als Ausgabe. Modelle, die für die Wiederverwendung in SQL Server gespeichert sind, werden als Byte-Stream serialisiert und in einer varbinary(max)-Spalte in einer Datenbanktabelle gespeichert. Sobald das Modell wird erstellt, trainiert, serialisiert und in einer Datenbank gespeichert, aufgerufen werden kann durch andere Prozeduren oder durch die [VORHERSAGEN für T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) -Funktion in arbeitsauslastungen zu bewerten.

1. Kopieren Sie den folgenden Code zum Ausführen der Prozedur. Die spezifische Anweisung für die Ausführung einer gespeicherten Prozedur ist `EXEC` in der fünften Zeile.

   Dieses Skript löscht ein vorhandenes Modell mit dem gleichen Namen ("Naive Bayes") um Platz für neue Dateien erstellt, indem Sie das gleiche Verfahren ausführen zu machen. Ohne Modell löschen tritt der Fehler darauf hinweist, dass das Objekt bereits vorhanden ist. Das Modell gespeichert ist, in eine Tabelle namens **Iris_models**, bereitgestellt werden, bei der Erstellung der **Irissql** Datenbank.

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes'
    EXEC generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

2. Stellen Sie sicher, dass das Modell eingefügte ist eine weitere Möglichkeit zum Zurückgeben einer Liste von Modellen

    ```sql
    SELECT * FROM dbo.iris_models
    ```

    **Ergebnisse**

    | Modellname  | model |
    |---|-----------------|
    | Naive Bayes | 0x800363736B6C6561726E2E6E616976655F62617965730A... | 

## <a name="create-and-execute-a-stored-procedure-for-generating-predictions"></a>Erstellen und Ausführen einer gespeicherten Prozedur zum Generieren von Vorhersagen

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

## <a name="conclusion"></a>Schlussbemerkung

In dieser Übung haben Sie gelernt, wie zum Erstellen gespeicherter Prozeduren, die speziell für verschiedene Aufgaben, die jede gespeicherte Prozedur, in dem die gespeicherte Systemprozedur verwendet [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) einen Python-Prozess zu starten. Eingaben für die Python-Prozess werden Sp_execute_external Skript als Parameter übergeben. Sowohl die Datenvariablen in einer SQL Server-Datenbank die Python-Skript selbst werden als Eingaben übergeben.

Im Allgemeinen sollten Sie nur planen, zur Verwendung von SSMS mit ansprechenden Python-Code oder einfache Python-Code, der zeilenbasierter Ausgabe zurückgibt. Ein Tool das, SSMS unterstützt Abfragesprachen wie T-SQL und vereinfachten Rowsets zurückgibt. Wenn Ihr Code visuelle Ausgabe wie bei einem Punktdiagramm oder ein Histogramm generiert wird, benötigen Sie eine Tool oder Endbenutzer-Anwendung, die das Bild gerendert werden kann.

Für einige Python-Entwickler, die zum Schreiben von umfassenden Skript behandeln eine Reihe von Vorgängen vertraut sind, kann das Organisieren von Aufgaben in separate Verfahren unnötig scheinen mag. Jedoch Modelltraining und die Bewertung über verschiedene Anwendungsfälle. Indem Sie sie trennen, können Sie jede Aufgabe auf anderen Zeitplan und Bereichsberechtigungen Vorgang einfügen.

Ebenso, Sie können auch Ressourcen Funktionen von SQL Server, z. B. die parallelverarbeitung, Ressourcenkontrolle, oder durch das Schreiben Ihrer Skripts zum Verwenden von Algorithmen in [Revoscalepy](../python/ref-py-revoscalepy.md) oder [Microsoftml](../python/ref-py-microsoftml.md) , streaming-Unterstützung, und klicken Sie mit der parallelen Ausführung. Durch das Trainieren und Bewerten von getrennt, können Sie die Optimierungen für bestimmte arbeitsauslastungen abzielen.

Ein letzte Vorteil ist, dass es sich bei Prozessen mithilfe der Parameter geändert werden können. In dieser Übung wurde die Python-Code, der Erstellung des Modells (mit dem Namen "Naive Bayes" in diesem Beispiel) als Eingabe für eine zweite gespeicherte Prozedur aufrufen des Modells in einem Bewertung Prozess übergeben. In dieser Übung verwendet nur ein Modell, aber Sie können sich vorstellen, wie das Modell in einer Bewertung Aufgabe parametrisieren dieses Skript nützlicher werden würde.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie noch nicht mit Python SQL-Entwickler sind, überprüfen Sie die Schritte und Tools für die Arbeit mit Python-Code lokal mit der Möglichkeit, um die Ausführung von lokalen Sitzungen zu einer Remoteinstanz von SQL Server verschoben.

> [!div class="nextstepaction"]
> [Richten Sie eine Python-Clientarbeitsstation](../python/setup-python-client-tools-sql.md).

