---
title: Erstellen und bewerten eines Vorhersagemodells in python
titleSuffix: SQL Server Machine Learning Services
description: Erstellen Sie ein einfaches Vorhersagemodell in python mithilfe SQL Server Machine Learning Services, und prognostizieren Sie dann mithilfe neuer Daten ein Ergebnis.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ad067e81bdb132d7958451d711e49ca57e308bac
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71204287"
---
# <a name="quickstart-create-and-score-a-predictive-model-in-python-with-sql-server-machine-learning-services"></a>Schnellstart: Erstellen und bewerten eines Vorhersagemodells in Python mit SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Schnellstartanleitung erstellen und trainieren Sie ein Vorhersagemodell mithilfe von Python. speichern Sie das Modell in einer Tabelle in Ihrer SQL Server Instanz, und verwenden Sie dann das Modell, um Werte aus neuen Daten mithilfe [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)vorherzusagen.

Sie erstellen und führen zwei gespeicherte Prozeduren aus, die in SQL ausgeführt werden. Der erste verwendet das klassische IRIS-Blumen DataSet und generiert ein Naive Bayes-Modell, um auf der Grundlage der Blumen Merkmale eine IRIS-Art vorherzusagen. Das zweite Verfahren dient der Bewertung: Es wird das im ersten Verfahren generierte Modell aufgerufen, um einen Satz von Vorhersagen basierend auf neuen Daten auszugeben. Wenn Sie Code in einer gespeicherten Prozedur platzieren, sind Vorgänge enthalten, können wiederverwendbar und von anderen gespeicherten Prozeduren und Client Anwendungen aufgerufen werden.

Durch die Durchführung dieses Schnellstarts lernen Sie Folgendes:

> [!div class="checklist"]
> * Einbetten von Python-Code in eine gespeicherte Prozedur
> * Übergeben von Eingaben an Ihren Code mithilfe von Eingaben für die gespeicherte Prozedur
> * Verwenden gespeicherter Prozeduren zum operationalisieren von Modellen

## <a name="prerequisites"></a>Erforderliche Komponenten

- Diese Schnellstartanleitung erfordert Zugriff auf eine Instanz von SQL Server mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) , auf der die Python-Sprache installiert ist.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die python-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Daten Bank Verwaltungs-oder Abfrage Tool ausführen, solange eine Verbindung mit einer SQL Server Instanz hergestellt und eine T-SQL-Abfrage oder eine gespeicherte Prozedur ausgeführt werden kann. In diesem Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)verwendet.

- Die in dieser Übung verwendeten Beispiel Daten sind die Iris-Beispiel Daten. Befolgen Sie die Anweisungen in [IRIS DemoData](demo-data-iris-in-sql.md) , um die Beispieldatenbank " **irissql**" zu erstellen.

## <a name="create-a-stored-procedure-that-generates-models"></a>Erstellen einer gespeicherten Prozedur, die Modelle generiert

In diesem Schritt erstellen Sie eine gespeicherte Prozedur, die ein Modell zur Vorhersage von Ergebnissen generiert.

1. Öffnen Sie in SSMS ein neues Abfragefenster, das mit der **irissql** -Datenbank verbunden ist. 

    ```sql
    USE irissql
    GO
    ```

1. Kopieren Sie den folgenden Code, um eine neue gespeicherte Prozedur zu erstellen.

   Bei der Ausführung ruft diese Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) auf, um eine python-Sitzung zu starten. 
   
   Eingaben, die von Ihrem Python-Code benötigt werden, werden als Eingabeparameter für diese gespeicherte Prozedur weitergeleitet. Die Ausgabe ist ein trainiertes Modell, das auf der Python **scikit-Learn-** Bibliothek für den Machine Learning-Algorithmus basiert. 

   In diesem Code wird [**Pickle**](https://docs.python.org/2/library/pickle.html) verwendet, um das Modell zu serialisieren. Das Modell wird mithilfe von Daten aus den Spalten 0 bis 4 aus der **iris_data** -Tabelle trainiert. 
   
   Die Parameter, die im zweiten Teil der Prozedur angezeigt werden, formulieren Dateneingaben und Modell Ausgaben. So weit wie möglich soll der Python-Code, der in einer gespeicherten Prozedur ausgeführt wird, klar definierte Eingaben und Ausgaben aufweisen, die gespeicherten Prozedur Eingaben und Ausgaben zugeordnet sind, die zur Laufzeit übergebenen werden.

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model VARBINARY(max) OUTPUT)
    AS
    BEGIN
        EXECUTE sp_execute_external_script @language = N'Python'
            , @script = N'
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

1. Prüfen Sie, ob die gespeicherte Prozedur vorhanden ist. 

   Wenn das T-SQL-Skript aus dem vorherigen Schritt ohne Fehler ausgeführt wurde, wird eine neue gespeicherte Prozedur mit dem Namen **generate_iris_model** erstellt und der **irissql** -Datenbank hinzugefügt. Gespeicherte Prozeduren finden Sie im SSMS- **Objekt-Explorer**unter **Programmierbarkeit**.

## <a name="execute-the-procedure-to-create-and-train-models"></a>Ausführen der Prozedur zum Erstellen und trainieren von Modellen

In diesem Schritt führen Sie die Prozedur aus, um den eingebetteten Code auszuführen, und erstellen ein trainiertes und serialisiertes Modell als Ausgabe. 

Modelle, die für die Wiederverwendung in SQL Server gespeichert werden, werden als Bytestream serialisiert und in einer varbinary (max)-Spalte in einer Datenbanktabelle gespeichert. Nachdem das Modell erstellt, trainiert, serialisiert und in einer Datenbank gespeichert wurde, kann es von anderen Prozeduren oder der [Vorhersage-T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) -Funktion bei der Bewertung von Arbeits Auslastungen aufgerufen werden.

1. Führen Sie das folgende Skript aus, um die Prozedur auszuführen. Die jeweilige Anweisung zum Ausführen einer gespeicherten Prozedur befindet `EXECUTE` sich in der vierten Zeile.

   Mit diesem Skript wird ein vorhandenes Modell mit dem gleichen Namen ("Naive Bayes") gelöscht, um Platz für neue Modelle zu schaffen, die durch erneutes Ausführen desselben Verfahrens erstellt werden. Ohne das Löschen von Modellen tritt ein Fehler auf, wenn das Objekt bereits vorhanden ist. Das Modell wird in einer Tabelle namens **iris_models**gespeichert, die beim Erstellen der **irissql** -Datenbank bereitgestellt wurde.

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes'
    EXECUTE generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

1. Vergewissern Sie sich, dass das Modell eingefügt wurde.

    ```sql
    SELECT * FROM dbo.iris_models
    ```

    **Ergebnisse**

    | model_name  | model |
    |---|-----------------|
    | Naive Bayes | 0x800363736b6c6561726e2e6e616976655l62617965730a... | 

## <a name="create-and-execute-a-stored-procedure-for-generating-predictions"></a>Erstellen und Ausführen einer gespeicherten Prozedur zum Generieren von Vorhersagen

Nachdem Sie ein Modell erstellt, trainiert und gespeichert haben, fahren Sie mit dem nächsten Schritt fort: Erstellen einer gespeicherten Prozedur, die Vorhersagen generiert. Dazu rufen `sp_execute_external_script` Sie auf, um ein Python-Skript auszuführen, das das serialisierte Modell lädt, und gibt neue Dateneingaben für die Bewertung aus.

1. Führen Sie den folgenden Code aus, um die gespeicherte Prozedur zu erstellen, die die Bewertung ausführt. Zur Laufzeit lädt dieses Verfahren ein binäres Modell, verwendet Spalten `[1,2,3,4]` als Eingaben und gibt Spalten `[0,5,6]` als Ausgabe an.

   ```sql
   CREATE PROCEDURE predict_species (@model VARCHAR(100))
   AS
   BEGIN
       DECLARE @nb_model VARBINARY(max) = (
               SELECT model
               FROM iris_models
               WHERE model_name = @model
               );
   
       EXECUTE sp_execute_external_script @language = N'Python'
           , @script = N'
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
       WITH RESULT SETS((
                   "id" INT
                 , "SpeciesId" INT
                 , "SpeciesId.Predicted" INT
                   ));
   END;
   GO
   ```

2. Führen Sie die gespeicherte Prozedur aus, und geben Sie den Modellnamen "Naive Bayes" an, damit die Prozedur weiß, welches Modell verwendet werden soll.

   ```sql
   EXECUTE predict_species 'Naive Bayes';
   GO
   ```

   Wenn Sie die gespeicherte Prozedur ausführen, wird ein python Data. Frame zurückgegeben. Diese T-SQL-Zeile gibt das Schema für die zurückgegebenen Ergebnisse `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`an:. Sie können die Ergebnisse in eine neue Tabelle einfügen oder Sie an eine Anwendung zurückgeben.

   ![Resultset aus Ausführung gespeicherter Prozeduren](media/train-score-using-python-NB-model-results.png)

   Bei den Ergebnissen handelt es sich um 150 Vorhersagen über die Art und Verwendung von floralen Merkmalen Bei den meisten Beobachtungen stimmen die vorhergesagten Werte mit den tatsächlichen Werten überein.

   Dieses Beispiel wurde mithilfe des python IRIS-Datasets für Training und Bewertung vereinfacht. Ein typischer Ansatz wäre das Ausführen einer SQL-Abfrage, um die neuen Daten zu erhalten, und die Übergabe an `InputDataSet`python als.

## <a name="conclusion"></a>Schlussbemerkung

In dieser Übung haben Sie erfahren, wie Sie gespeicherte Prozeduren erstellen, die für verschiedene Aufgaben vorgesehen sind, wobei jede gespeicherte `sp_execute_external_script` Prozedur die gespeicherte System Prozedur verwendet, um einen python-Prozess zu starten. Eingaben in den python-Prozess werden als `sp_execute_external` Parameter an das-Verfahren übermittelt. Das Python-Skript selbst und Daten Variablen in einer SQL Server Datenbank werden als Eingaben übermittelt.

Im Allgemeinen sollten Sie nur die Verwendung von SSMS mit poliertem Python-Code oder einfachen Python-Code planen, der die zeilenbasierte Ausgabe zurückgibt. Als Tool unterstützt SSMS Abfrage Sprachen wie T-SQL und gibt vereinfachte Rowsets zurück. Wenn Ihr Code eine visuelle Ausgabe wie ein Punkt Diagramm oder ein Histogramm generiert, benötigen Sie ein Tool oder eine Endbenutzer Anwendung, die das Bild renderingweise rendieren kann.

Für einige Python-Entwickler, die zum Schreiben von vollständig inklusiven Skripts verwendet werden, die eine Reihe von Vorgängen verarbeiten, scheint das Organisieren von Aufgaben in separaten Prozeduren unnötig Training und Bewertung haben jedoch unterschiedliche Anwendungsfälle. Indem Sie Sie trennen, können Sie jede Aufgabe in einem anderen Zeitplan und in Bereichs Berechtigungen für jeden Vorgang platzieren.

Ebenso können Sie auch die ausgewähltem Ressourcen-Features von SQL Server nutzen, z. b. parallele Verarbeitung, Ressourcenkontrolle oder das Skript schreiben, um Algorithmen in [microsoftml](../python/ref-py-microsoftml.md) zu verwenden, die Streaming und parallele Ausführung unterstützen. Durch die Trennung von Training und Bewertung können Sie Optimierungen für bestimmte Workloads ausrichten.

Der letzte Vorteil besteht darin, dass die Prozesse mithilfe von Parametern geändert werden können. In dieser Übung wurde Python-Code, der das Modell (in diesem Beispiel mit dem Namen "Naive Bayes") erstellt hat, als Eingabe an eine zweite gespeicherte Prozedur, die das Modell in einem Bewertungsprozess aufgerufen hat, übermittelt. In dieser Übung wird nur ein Modell verwendet, aber Sie können sich vorstellen, wie das parametrisierungsmodell in einer Bewertungsaufgabe das Skript nützlicher machen würde.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Behandlung von python-Datentypen in SQL Server finden Sie in diesem Schnellstart:

> [!div class="nextstepaction"]
> [Verarbeiten von Datentypen und Objekten mithilfe von python in SQL Server Machine Learning Services](quickstart-python-data-structures.md)

Weitere Informationen zum SQL Server Machine Learning Services finden Sie unter:

- [Was ist SQL Server Machine Learning Services (python und R)?](../what-is-sql-server-machine-learning.md)
