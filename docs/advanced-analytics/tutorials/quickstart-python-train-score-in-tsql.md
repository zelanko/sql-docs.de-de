---
title: Schnellstart für python-Modelle für Schulungen und Vorhersagen mithilfe gespeicherter Prozeduren
description: Integrieren Sie Python-Code in SQL Server gespeicherte Prozeduren, um ein python-Modell mit dem klassischen IRIS-DataSet zu erstellen, zu trainieren und zu verwenden. Speichern Sie ein trainiertes Modell in SQL Server, und verwenden Sie es dann, um vorhergesagte Ergebnisse zu generieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: c2c36c5aa81da098064885fd5b006d78494cd962
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345767"
---
# <a name="quickstart-create-train-and-use-a-python-model-with-stored-procedures-in-sql-server"></a>Schnellstart: Erstellen, trainieren und Verwenden eines python-Modells mit gespeicherten Prozeduren in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser Schnellstartanleitung verwenden Sie Python, um zwei gespeicherte Prozeduren zu erstellen und auszuführen. Der erste verwendet das klassische IRIS-Blumen DataSet und generiert ein Naive Bayes-Modell, um auf der Grundlage der Blumen Merkmale eine IRIS-Art vorherzusagen. Das zweite Verfahren dient der Bewertung. Das Modell wird aufgerufen, das in der ersten Prozedur generiert wurde, um einen Satz von Vorhersagen auszugeben. Wenn Sie Code in einer gespeicherten Prozedur platzieren, sind Vorgänge enthalten, können wiederverwendbar und von anderen gespeicherten Prozeduren und Client Anwendungen aufgerufen werden. 

Durch die Durchführung dieses Schnellstarts lernen Sie Folgendes:

> [!div class="checklist"]
> * Einbetten von Python-Code in eine gespeicherte Prozedur
> * Übergeben von Eingaben an Ihren Code mithilfe von Eingaben für die gespeicherte Prozedur
> * Verwenden gespeicherter Prozeduren zum operationalisieren von Modellen

## <a name="prerequisites"></a>Vorraussetzungen

Eine vorherige Schnellstartanleitung: [überprüfen, ob python in SQL Server vorhanden](quickstart-python-verify.md)ist, enthält Informationen und Links zum Einrichten der für diese Schnellstartanleitung erforderlichen python-Umgebung.

Die in dieser Übung verwendeten Beispiel Daten sind die [**irissql**](demo-data-iris-in-sql.md) -Datenbank.

## <a name="create-a-stored-procedure-that-generates-models"></a>Erstellen einer gespeicherten Prozedur, die Modelle generiert

Ein gängiges Muster in SQL Server Entwicklung besteht darin, programmierbare Vorgänge in unterschiedlichen gespeicherten Prozeduren zu organisieren. In diesem Schritt erstellen Sie eine gespeicherte Prozedur, die ein Modell zur Vorhersage von Ergebnissen generiert. 

1. Öffnen Sie ein neues Abfragefenster in Management Studio, das mit der **irissql** -Datenbank verbunden ist. 

    ```sql
    USE irissql
    GO
    ```

2. Kopieren Sie den folgenden Code, um eine neue gespeicherte Prozedur zu erstellen. 

   Bei der Ausführung ruft diese Prozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) auf, um eine python-Sitzung zu starten. 
   
   Eingaben, die von Ihrem Python-Code benötigt werden, werden als Eingabeparameter für diese gespeicherte Prozedur weitergeleitet. Die Ausgabe ist ein trainiertes Modell, das auf der Python **scikit-Learn-** Bibliothek für den Machine Learning-Algorithmus basiert. 

   In diesem Code wird [**Pickle**](https://docs.python.org/2/library/pickle.html) verwendet, um das Modell zu serialisieren. Das Modell wird mithilfe von Daten aus den Spalten 0 bis 4 aus der **iris_data** -Tabelle trainiert. 
   
   Die Parameter, die im zweiten Teil der Prozedur angezeigt werden, formulieren Dateneingaben und Modell Ausgaben. So weit wie möglich soll der Python-Code, der in einer gespeicherten Prozedur ausgeführt wird, klar definierte Eingaben und Ausgaben aufweisen, die gespeicherten Prozedur Eingaben und Ausgaben zugeordnet sind, die zur Laufzeit übergebenen werden. 

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

3. Prüfen Sie, ob die gespeicherte Prozedur vorhanden ist. 

   Wenn das T-SQL-Skript aus dem vorherigen Schritt ohne Fehler ausgeführt wurde, wird eine neue gespeicherte Prozedur mit dem Namen **generate_iris_model** erstellt und der **irissql** -Datenbank hinzugefügt. Sie können gespeicherte Prozeduren in Management Studio **Objekt-Explorer**unter **Programmierbarkeit**suchen.

## <a name="execute-the-procedure-to-create-and-train-models"></a>Ausführen der Prozedur zum Erstellen und trainieren von Modellen

Führen Sie in diesem Schritt die Prozedur aus, um den eingebetteten Code auszuführen, und erstellen Sie ein trainiertes und serialisiertes Modell als Ausgabe. Modelle, die für die Wiederverwendung in SQL Server gespeichert werden, werden als Bytestream serialisiert und in einer varbinary (max)-Spalte in einer Datenbanktabelle gespeichert. Nachdem das Modell erstellt, trainiert, serialisiert und in einer Datenbank gespeichert wurde, kann es von anderen Prozeduren oder der [Vorhersage-T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) -Funktion bei der Bewertung von Arbeits Auslastungen aufgerufen werden.

1. Kopieren Sie den folgenden Code, um die Prozedur auszuführen. Die jeweilige Anweisung zum Ausführen einer gespeicherten Prozedur befindet `EXEC` sich in der fünften Zeile.

   Mit diesem Skript wird ein vorhandenes Modell mit dem gleichen Namen ("Naive Bayes") gelöscht, um Platz für neue Modelle zu schaffen, die durch erneutes Ausführen desselben Verfahrens erstellt werden. Ohne das Löschen von Modellen tritt ein Fehler auf, wenn das Objekt bereits vorhanden ist. Das Modell wird in einer Tabelle namens **iris_models**gespeichert, die beim Erstellen der **irissql** -Datenbank bereitgestellt wurde.

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes'
    EXEC generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

2. Überprüfen Sie, ob das Modell eine andere Möglichkeit zum Zurückgeben einer Liste von Modellen ist.

    ```sql
    SELECT * FROM dbo.iris_models
    ```

    **Ergebnisse**

    | model_name  | model |
    |---|-----------------|
    | Naive Bayes | 0x800363736b6c6561726e2e6e616976655l62617965730a... | 

## <a name="create-and-execute-a-stored-procedure-for-generating-predictions"></a>Erstellen und Ausführen einer gespeicherten Prozedur zum Generieren von Vorhersagen

Nachdem Sie ein Modell erstellt, trainiert und gespeichert haben, fahren Sie mit dem nächsten Schritt fort: Erstellen einer gespeicherten Prozedur, die Vorhersagen generiert. Dies erreichen Sie, indem Sie sp_execute_external_script aufrufen, um Python zu starten, und dann das Python-Skript übergeben, das ein serialisiertes Modell lädt, das Sie in der letzten Übung erstellt haben, und dann Dateneingaben an die Bewertung übergibt.

1. Führen Sie den folgenden Code aus, um die gespeicherte Prozedur zu erstellen, die die Bewertung ausführt. Zur Laufzeit lädt dieses Verfahren ein binäres Modell, verwendet Spalten `[1,2,3,4]` als Eingaben und gibt Spalten `[0,5,6]` als Ausgabe an.

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

2. Führen Sie die gespeicherte Prozedur aus, und geben Sie den Modellnamen "Naive Bayes" an, damit die Prozedur weiß, welches Modell verwendet werden soll. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    Wenn Sie die gespeicherte Prozedur ausführen, wird ein python Data. Frame zurückgegeben. Diese T-SQL-Zeile gibt das Schema für die zurückgegebenen Ergebnisse `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`an:. Sie können die Ergebnisse in eine neue Tabelle einfügen oder Sie an eine Anwendung zurückgeben.

    ![Resultset aus Ausführung gespeicherter Prozeduren](media/train-score-using-python-NB-model-results.png)

    Bei den Ergebnissen handelt es sich um 150 Vorhersagen über die Art und Verwendung von floralen Merkmalen Bei den meisten Beobachtungen stimmen die vorhergesagten Werte mit den tatsächlichen Werten überein.

    Dieses Beispiel wurde mithilfe des python IRIS-Datasets für Training und Bewertung vereinfacht. Ein typischer Ansatz wäre das Ausführen einer SQL-Abfrage, um die neuen Daten zu erhalten, und die Übergabe an `InputDataSet`python als. 

## <a name="conclusion"></a>Schlussbemerkung

In dieser Übung haben Sie erfahren, wie Sie gespeicherte Prozeduren erstellen, die für verschiedene Aufgaben vorgesehen sind, wobei jede gespeicherte Prozedur die gespeicherte System Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) verwendet, um einen python-Prozess zu starten. Eingaben in den python-Prozess werden als Parameter an das sp_execute_external-Skript übermittelt. Das Python-Skript selbst und Daten Variablen in einer SQL Server Datenbank werden als Eingaben übermittelt.

Im Allgemeinen sollten Sie nur die Verwendung von SSMS mit poliertem Python-Code oder einfachen Python-Code planen, der die zeilenbasierte Ausgabe zurückgibt. Als Tool unterstützt SSMS Abfrage Sprachen wie T-SQL und gibt vereinfachte Rowsets zurück. Wenn Ihr Code eine visuelle Ausgabe wie ein Punkt Diagramm oder ein Histogramm generiert, benötigen Sie ein Tool oder eine Endbenutzer Anwendung, die das Bild renderingweise rendieren kann.

Für einige Python-Entwickler, die zum Schreiben von vollständig inklusiven Skripts verwendet werden, die eine Reihe von Vorgängen verarbeiten, scheint das Organisieren von Aufgaben in separaten Prozeduren unnötig Training und Bewertung haben jedoch unterschiedliche Anwendungsfälle. Indem Sie Sie trennen, können Sie jede Aufgabe unterschiedlichen Zeit Plan-und Bereichs Berechtigungen für den Betrieb platzieren.

Ebenso können Sie auch die ausgewähltem Ressourcen-Features von SQL Server nutzen, z. b. parallele Verarbeitung, Ressourcenkontrolle oder das Skript schreiben, um Algorithmen in [revoscalepy](../python/ref-py-revoscalepy.md) oder [microsoftml](../python/ref-py-microsoftml.md) zu verwenden, die Streaming und parallele Ausführung unterstützen. Durch die Trennung von Training und Bewertung können Sie Optimierungen für bestimmte Workloads ausrichten.

Der endgültige Vorteil besteht darin, dass Prozesse mit Parametern geändert werden können. In dieser Übung wurde Python-Code, der das Modell (in diesem Beispiel mit dem Namen "Naive Bayes") erstellt hat, als Eingabe an eine zweite gespeicherte Prozedur, die das Modell in einem Bewertungsprozess aufgerufen hat, übermittelt. In dieser Übung wird nur ein Modell verwendet, aber Sie können sich vorstellen, wie das parametrisierungsmodell in einer Bewertungsaufgabe das Skript nützlicher machen würde.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie SQL-Entwickler neu in python sind, überprüfen Sie die Schritte und Tools für die lokale Verwendung von Python-Code mit der Möglichkeit, die Ausführung von lokalen Sitzungen auf eine Remote SQL Server-Instanz zu verlagern.

> [!div class="nextstepaction"]
> [Richten Sie eine Python-Client](../python/setup-python-client-tools-sql.md)Arbeitsstation ein.

