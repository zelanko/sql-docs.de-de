---
title: Iris-Demodataset für Python und R-Tutorials in SQL Server | Microsoft-Dokumentation
Description: Create a database containing the Iris dataset and a table for storing models. This dataset is used in exercises showing how to wrap R language or Python code in a SQL Server stored procedure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2fbe5915f7b135882bbbefbb83b572d2cd640837
ms.sourcegitcommit: 12779bddd056a203d466d83c4a510a97348fe9d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216680"
---
#  <a name="iris-demo-data-for-python-and-r-tutorials-in-sql-server"></a>Iris-Demodaten für Python und R-Tutorials in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser Übung erstellen Sie eine SQL Server-Datenbank zum Speichern von Daten aus der [Iris Flower DataSet](https://en.wikipedia.org/wiki/Iris_flower_data_set) und Modelle, die auf denselben Daten basieren. Iris-Daten befindet sich auf die R und Python-Distributionen, die von SQL Server installiert und werden in Machine Learning-Tutorial für SQL Server verwendet. 

Um in dieser Übung abgeschlossen haben, müssen Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) oder ein anderes Tool, das T-SQL-Abfragen ausgeführt werden kann.

Lernprogramme und dieses DataSet mit Schnellstarts umfassen Folgendes:

+  [Verwenden Sie ein Python-Modell in SQL Server für das Trainieren und bewerten](train-score-using-python-in-tsql.md)

## <a name="create-the-database"></a>Erstellen der Datenbank

1. Starten Sie SQL Server Management Studio, und öffnen Sie ein neues **Abfrage** Fenster.  

2. Erstellen einer neuen Datenbank für dieses Projekt, und ändern Sie im Rahmen Ihrer **Abfrage** Fenster, das die neue Datenbank verwendet.

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

    > [!TIP] 
    > Wenn Sie noch nicht mit SQL Server oder auf einem Server, die Sie besitzen arbeiten, ein häufiger Fehler besteht darin, sich anmelden und loslegen bemerken, die Sie in der **master** Datenbank. Immer um sicherzustellen, dass Sie die richtige Datenbank verwenden, geben Sie den Kontext mithilfe der `USE <database name>` Anweisung (z. B. `use irissql`).

3. Fügen Sie einige leeren Tabellen: eine zum Speichern der Daten und eine zum Speichern der trainierten Modelle. Die **Iris_models** -Tabelle dient zum Speichern der serialisierten Modelle, die in anderen Übungen generiert.

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
    > Wenn Sie T-SQL vertraut sind, lohnt es sich merken der `DROP...IF` Anweisung. Wenn Sie versuchen, eine Tabelle zu erstellen und bereits eine vorhanden ist, gibt SQL Server einen Fehler zurück: "Es ist bereits ein Objekt mit dem Namen"Iris_data"in der Datenbank." Eine Möglichkeit zur Vermeidung derartiger Fehler werden alle bestehenden Tabellen oder andere Objekte als Teil des Codes zu löschen.

4. Führen Sie den folgenden Code zum Erstellen der Tabelle zum Speichern des trainierten Modells verwendet. Um Python (oder R)-Modelle in SQL Server zu speichern, sie müssen werden serialisiert und in einer Spalte vom Typ gespeicherte **'varbinary(max)'**. 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    Zusätzlich zum Standardinhalt der Modell in der Regel würden Sie auch Hinzufügen von Spalten für weitere nützliche Metadaten, wie z. B. dem Namen des Modells, das Datum an, das es trainiert wurde, das die Quelle Algorithmus und Parameter, die Quelldaten aus, und so weiter. Jetzt wird einfach und nur den Name des Modells verwenden.

## <a name="populate-the-table"></a>Füllen Sie die Tabelle

Sie erhalten die integrierten Iris-Daten aus R oder Python. Sie können Python oder R zum Laden der Daten in einen Datenrahmen verwenden, und fügen sie in einer Tabelle in der Datenbank. Verschieben von Daten aus einer externen Sitzung in eine SQL Server-Tabelle ist ein mehrstufiger Prozess:

+ Entwerfen Sie eine gespeicherte Prozedur, die die Daten abruft, die Sie möchten.
+ Führen Sie die gespeicherte Prozedur aus, um die Daten tatsächlich zu erhalten.
+ Erstellen Sie eine INSERT-Anweisung, um anzugeben, wo die abgerufenen Daten gespeichert werden soll.

1. Erstellen Sie auf Systemen mit Integration von Python die folgende gespeicherte Prozedur, die Python-Code zum Laden der Daten verwendet.

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

    Wenn Sie diesen Code ausführen, sollten Sie die Meldung erhalten "Befehle erfolgreich abgeschlossen." Dies bedeutet lediglich, dass die gespeicherte Prozedur entsprechend Ihren Spezifikationen erstellt wurde.

2. Alternativ für Systeme, die mit R-Integration werden, erstellen Sie eine Prozedur, die R verwendet.

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

3. Tatsächlich füllen Sie die Tabelle, die gespeicherte Prozedur auszuführen, und geben Sie die Tabelle, in denen die Daten geschrieben werden soll. Bei der Ausführung wird die gespeicherte Prozedur führt die Python- oder R-Code, der lädt des integrierte Iris-Datasets und fügt dann die Daten in die **Iris_data** Tabelle.

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Wenn Sie mit T-SQL vertraut sind, achten Sie darauf, dass die INSERT-Anweisung nur neue Daten hinzugefügt; Es wird nicht für vorhandene Daten überprüfen oder zu löschen und Neuerstellen die Tabelle. Um zu vermeiden, mehrere Kopien derselben Daten in einer Tabelle abrufen, können Sie zunächst diese Anweisung ausführen: `TRUNCATE TABLE iris_data`. Das T-SQL [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) Anweisung werden vorhandene Daten gelöscht, aber die Struktur der Tabelle intakt bleibt.

    > [!TIP]
    > Zum Ändern der gespeicherten Prozedur müssen nicht höher, Sie löschen und neu erstellen. Verwenden der [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql) Anweisung. 


## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie als Schritt zur Überprüfung eine Abfrage aus, um sicherzustellen, dass die Daten hochgeladen wurden.

1. Im Objekt-Explorer unter "Datenbanken", mit der Maustaste der **Irissql** Datenbank, und starten Sie eine neue Abfrage.

2. Führen Sie einige einfachen Abfragen:

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>Nächste Schritte

In der folgenden Lektion Sie Machine Learning-Modellen zu erstellen und speichern es in einer Tabelle, und klicken Sie dann das Modell verwenden, um die vorhergesagten Ergebnisse zu generieren.

+ [Verwenden Sie ein Python-Modell in SQL Server für das Trainieren und bewerten](train-score-using-python-in-tsql.md)
