---
title: IRIS-Demo Dataset für python-und R-Tutorials
Description: Erstellen Sie eine Datenbank, die das IRIS-DataSet und eine Tabelle zum Speichern von Modellen enthält. Dieses DataSet wird in Übungen verwendet, die zeigen, wie R-Sprache oder python-Code in einer SQL Server gespeicherten Prozedur eingebunden wird.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 78acdd0ef2eed808d8f974c38899282dc823436d
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715498"
---
#  <a name="iris-demo-data-for-python-and-r-tutorials-in-sql-server"></a>IRIS-Demodaten für python-und R-Tutorials in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Erstellen Sie in dieser Übung eine SQL Server Datenbank, um Daten aus dem [IRIS-Blumen](https://en.wikipedia.org/wiki/Iris_flower_data_set) DataSet und Modellen zu speichern, die auf denselben Daten basieren. IRIS-Daten sind sowohl in den von SQL Server installierten R-als auch in der Python-Distribution enthalten und werden in Machine Learning-Tutorials für SQL Server verwendet. 

Um diese Übung abzuschließen, sollten Sie über [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) oder ein anderes Tool verfügen, das T-SQL-Abfragen ausführen kann.

Zu den Tutorials und Schnellstarts, die dieses DataSet verwenden, gehören die folgenden:

+  [Schnellstart: Erstellen, trainieren und Verwenden eines python-Modells mit gespeicherten Prozeduren in SQL Server](quickstart-python-train-score-in-tsql.md)

## <a name="create-the-database"></a>Erstellen der Datenbank

1. Starten Sie SQL Server Management Studio, und öffnen Sie ein neues **Abfrage** Fenster.  

2. Erstellen Sie eine neue Datenbank für dieses Projekt, und ändern Sie den Kontext des **Abfrage** Fensters, um die neue Datenbank zu verwenden.

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

    > [!TIP] 
    > Wenn Sie noch nicht mit SQL Server vertraut sind oder an einem Server arbeiten, den Sie besitzen, ist es ein häufiger Fehler, sich anzumelden und mit der Arbeit zu beginnen, ohne zu bemerken, dass Sie sich in der **Master** -Datenbank befinden. Um sicherzustellen, dass Sie die richtige Datenbank verwenden, geben Sie den Kontext immer mithilfe `USE <database name>` der-Anweisung an ( `use irissql`z. b.).

3. Fügen Sie einige leere Tabellen hinzu: eine zum Speichern der Daten und eine zum Speichern der trainierten Modelle. Die **iris_models** -Tabelle wird zum Speichern von serialisierten Modellen verwendet, die in anderen Übungen generiert werden.

    Der folgende Code erstellt die Tabelle für die Trainingsdaten.

    ```sql
    DROP TABLE IF EXISTS iris_data;
    GO
    CREATE TABLE iris_data (
      id INT NOT NULL IDENTITY PRIMARY KEY
      , "Sepal.Length" FLOAT NOT NULL, "Sepal.Width" FLOAT NOT NULL
      , "Petal.Length" FLOAT NOT NULL, "Petal.Width" FLOAT NOT NULL
      , "Species" VARCHAR(100) NOT NULL, "SpeciesId" INT NOT NULL
    );
    ```

    > [!TIP] 
    > Wenn Sie noch nicht mit T-SQL vertraut sind, wird die Anweisung für `DROP...IF` die Erinnerung an die Anweisung bezahlt. Wenn Sie versuchen, eine Tabelle zu erstellen, und eine bereits vorhanden ist, gibt SQL Server einen Fehler zurück: "In der Datenbank ist bereits ein Objekt mit dem Namen ' iris_data ' vorhanden." Eine Möglichkeit, solche Fehler zu vermeiden, besteht darin, vorhandene Tabellen oder andere Objekte als Teil des Codes zu löschen.

4. Führen Sie den folgenden Code aus, um die zum Speichern des trainierten Modells verwendete Tabelle zu erstellen. Um python-(oder R-) Modelle in SQL Server zu speichern, müssen Sie serialisiert und in einer Spalte vom Typ **varbinary (max)** gespeichert werden. 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    Zusätzlich zum Modell Inhalt würden Sie in der Regel auch Spalten für weitere nützliche Metadaten hinzufügen, z. b. den Namen des Modells, das ertrainierte Datum, den Quell Algorithmus und die Parameter, die Quelldaten usw. Vorerst halten wir es einfach und verwenden nur den Modellnamen.

## <a name="populate-the-table"></a>Auffüllen der Tabelle

Sie können integrierte IRIS-Daten von R oder python abrufen. Sie können python oder R verwenden, um die Daten in einen Datenrahmen zu laden und Sie dann in eine Tabelle in der Datenbank einzufügen. Das Verschieben von Trainingsdaten aus einer externen Sitzung in eine SQL Server Tabelle ist ein mehrstufiger Prozess:

+ Entwerfen Sie eine gespeicherte Prozedur, die die gewünschten Daten abruft.
+ Führen Sie die gespeicherte Prozedur aus, um die Daten tatsächlich zu erhalten.
+ Erstellen Sie eine INSERT-Anweisung, um anzugeben, wo die abgerufenen Daten gespeichert werden sollen.

1. Erstellen Sie auf Systemen mit python-Integration die folgende gespeicherte Prozedur, die den Python-Code zum Laden der Daten verwendet.

    ```sql
    CREATE PROCEDURE get_iris_dataset
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    from sklearn import datasets
    iris = datasets.load_iris()
    iris_data = pandas.DataFrame(iris.data)
    iris_data["Species"] = pandas.Categorical.from_codes(iris.target, iris.target_names)
    iris_data["SpeciesId"] = iris.target
    ', 
    @input_data_1 = N'', 
    @output_data_1_name = N'iris_data'
    WITH RESULT SETS (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100) not null, "SpeciesId" int not null));
    END;
    GO
    ```

    Wenn Sie diesen Code ausführen, sollten Sie die Meldung "Befehle wurden erfolgreich abgeschlossen" erhalten. Dies bedeutet, dass die gespeicherte Prozedur gemäß ihren Spezifikationen erstellt wurde.

2. Alternativ dazu können Sie auf Systemen, die über r-Integration verfügen, eine Prozedur erstellen, die stattdessen r verwendet.

    ```sql
    CREATE PROCEDURE get_iris_dataset
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'R', 
    @script = N'
    library(RevoScaleR)
    data(iris)
    iris$SpeciesID <- c(unclass(iris$Species))
    iris_data <- iris
    ', 
    @input_data_1 = N'', 
    @output_data_1_name = N'iris_data'
    WITH RESULT SETS (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100) not null, "SpeciesId" int not null));
    END;
    GO
    ```

3. Um die Tabelle tatsächlich aufzufüllen, führen Sie die gespeicherte Prozedur aus, und geben Sie die Tabelle an, in die die Daten geschrieben werden sollen. Bei der Ausführung führt die gespeicherte Prozedur den Python-oder R-Code aus, der das integrierte IRIS-Dataset lädt und dann die Daten in die **iris_data** -Tabelle einfügt.

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Wenn Sie noch nicht mit T-SQL vertraut sind, beachten Sie, dass durch die INSERT-Anweisung nur neue Daten hinzugefügt werden. Er überprüft nicht, ob vorhandene Daten vorhanden sind, oder löscht und erstellt die Tabelle neu. Um zu vermeiden, dass Sie mehrere Kopien derselben Daten in einer Tabelle erhalten, können Sie diese Anweisung zuerst `TRUNCATE TABLE iris_data`ausführen:. Die T-SQL- [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) -Anweisung löscht vorhandene Daten, behält jedoch die Struktur der Tabelle bei.

    > [!TIP]
    > Um die gespeicherte Prozedur zu einem späteren Zeitpunkt zu ändern, müssen Sie Sie nicht löschen und neu erstellen. Verwenden Sie die [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql) -Anweisung. 


## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie als Überprüfungs Schritt eine Abfrage aus, um zu bestätigen, dass die Daten hochgeladen wurden.

1. Klicken Sie in Objekt-Explorer unter Datenbanken mit der rechten Maustaste auf die Datenbank **irissql** , und starten Sie eine neue Abfrage.

2. Führen Sie einige einfache Abfragen aus:

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>Nächste Schritte

Im folgenden Schnellstart erstellen Sie ein Machine Learning-Modell und speichern es in einer Tabelle. Anschließend generieren Sie mit dem Modell vorhergesagte Ergebnisse.

+ [Schnellstart: Erstellen, trainieren und Verwenden eines python-Modells mit gespeicherten Prozeduren in SQL Server](quickstart-python-train-score-in-tsql.md)
