---
title: Iris-Demodataset für Tutorials
Description: Erstellen Sie eine Datenbank, die das IRIS-Dataset und eine Tabelle zum Speichern von Modellen enthält. Dieses Dataset wird in Übungen verwendet, die zeigen, wie die Sprache R oder Python-Code in einer gespeicherten SQL Server-Prozedur umschlossen wird.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e580a4d3b8d0e294573cf19c0194cc9b8a103518
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727093"
---
#  <a name="iris-demo-data-for-python-and-r-tutorials-in-sql-server"></a>Iris-Demodaten für Python- und R-Tutorials in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Übung erstellen Sie eine SQL Server-Datenbank zum Speichern von Daten aus dem [Iris flower-Datensatz](https://en.wikipedia.org/wiki/Iris_flower_data_set) sowie zum Speichern von Modellen, die auf diesen Daten basieren. Iris-Daten sind den durch SQL Server installierten Verteilungen von R und Python enthalten und werden in Tutorials zum maschinellen Lernen für SQL Server verwendet. 

Für diese Übung benötigen Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) oder ein anderes Tool zum Ausführen von T-SQL-Abfragen.

Dieses Dataset wird in folgenden Tutorials und Schnellstarts verwendet:

+  [Schnellstart: Erstellen, Trainieren und Verwenden eines Python-Modells mit gespeicherten Prozeduren in SQL Server](quickstart-python-train-score-in-tsql.md)

## <a name="create-the-database"></a>Erstellen der Datenbank

1. Starten Sie SQL Server Management Studio, und öffnen Sie ein neues **Abfragefenster**.  

2. Erstellen Sie für dieses Projekt eine neue Datenbank, und ändern Sie den Kontext für Ihr **Abfragefenster** so, dass die neue Datenbank verwendet wird.

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

    > [!TIP] 
    > Wenn Benutzer mit SQL Server noch nicht vertraut sind oder an einem eigenen Server arbeiten, machen sie häufig den Fehler, sich anzumelden und mit der Arbeit zu beginnen, ohne zu bemerken, dass sie sich in der **Masterdatenbank** befinden. Daher sollten Sie immer mithilfe der `USE <database name>`-Anweisung den Kontext angeben (z. B. `use irissql`), um sicherzustellen, dass Sie die richtige Datenbank verwenden.

3. Fügen Sie leere Tabellen hinzu: eine zum Speichern der Daten und eine zum Speichern der trainierten Modelle. Die Tabelle **iris_models** wird zum Speichern von serialisierten Modellen verwendet, die in anderen Übungen generiert werden.

    Mit dem folgenden Code wird die Tabelle für die Trainingsdaten erstellt.

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
    > Falls Sie mit T-SQL noch nicht vertraut sind: Es lohnt sich, sich die `DROP...IF`-Anweisung zu merken. Wenn Sie eine Tabelle erstellen und bereits eine vorhanden ist, gibt SQL Server folgende Fehlermeldung zurück: „In der Datenbank ist bereits ein Objekt mit dem Namen 'iris_data' vorhanden.“ Fehler dieser Art können Sie vermeiden, indem Sie vorhandene Tabellen oder andere Objekte mit Ihrem Code löschen.

4. Führen Sie den folgenden Code aus, um die zum Speichern des trainierten Modells verwendete Tabelle zu erstellen. Python- oder R-Modelle können erst in SQL Server gespeichert werden, nachdem sie serialisiert und dann in einer Spalte vom Typ **varbinary(max)** gespeichert wurden. 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    Neben dem Modellinhalt sollten Sie auch Spalten für andere nützliche Metadaten wie für den Namen des Modells, das Trainingsdatum, den Quellalgorithmus, die Quellparameter, Quelldaten usw. hinzufügen. Vorerst halten wir es einfach und verwenden nur den Modellnamen.

## <a name="populate-the-table"></a>Auffüllen der Tabelle

Rufen Sie integrierte Iris-Daten von R oder Python ab. Laden Sie die Daten mit Python oder R in einen Datenrahmen, und fügen Sie diesen in eine Tabelle in der Datenbank ein. Um Trainingsdaten aus einer externen Sitzung in eine SQL Server-Tabelle zu verschieben, müssen Sie mehrere Schritte durchführen:

+ Entwerfen Sie eine gespeicherte Prozedur, mit der die gewünschten Daten abgerufen werden.
+ Führen Sie die gespeicherte Prozedur aus, um die Daten letztlich abzurufen.
+ Erstellen Sie eine INSERT-Anweisung, um anzugeben, in welchem Verzeichnis die abgerufenen Daten gespeichert werden sollen.

1. Erstellen Sie bei Systemen mit Python-Integration die folgende gespeicherte Prozedur, mit deren Hilfe die Daten mittels Python-Code geladen werden.

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

    Beim Ausführen dieses Codes wird die Meldung angezeigt, dass die Befehle erfolgreich ausgeführt wurden. Das bedeutet, dass die gespeicherte Prozedur gemäß Ihren Angaben erstellt wurde.

2. Bei Systemen mit R-Integration erstellen Sie eine Prozedur, die anstelle von Python-Code R-Code verwendet.

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

3. Um die Tabelle letztlich aufzufüllen, führen Sie die gespeicherte Prozedur aus und geben Sie die Tabelle an, in der die Daten gespeichert werden sollen. Beim Ausführen der gespeicherten Prozedur wird der Python-Code bzw. der R-Code ausgeführt, mit dem das integrierte Iris-Dataset geladen wird und die Daten in die Tabelle **iris_data** einfügt werden.

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Wenn Sie mit T-SQL nicht vertraut sind, sei Ihnen gesagt, dass mit der INSERT-Anweisung nur neue Daten hinzugefügt werden. Es wird nicht geprüft, ob Daten vorhanden sind, und die Tabelle wird weder gelöscht noch neu erstellt. Um zu vermeiden, dass sich in der Tabelle mehrere Kopien derselben Daten befinden, können Sie zuerst die folgende Anweisung ausführen: `TRUNCATE TABLE iris_data`. Mit der T-SQL-Anweisung [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) werden vorhandene Daten gelöscht, die Struktur der Tabelle bleibt jedoch erhalten.

    > [!TIP]
    > Wenn Sie die gespeicherte Prozedur später ändern möchten, müssen Sie sie nicht erst löschen und dann neu erstellen. Verwenden Sie die [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql)-Anweisung. 


## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie eine Abfrage aus, um zu prüfen, ob die Daten hochgeladen wurden.

1. Klicken Sie in Objekt-Explorer unter „Datenbanken“ mit der rechten Maustaste auf die Datenbank **irissql**, und starten Sie eine neue Abfrage.

2. Führen Sie einige einfache Abfragen aus:

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>Nächste Schritte

Im Rahmen des folgenden Schnellstarts erstellen Sie ein Machine Learning-Modell und speichern es in einer Tabelle. Anschließend generieren Sie mithilfe des Modells vorhergesagte Ergebnisse.

+ [Schnellstart: Erstellen, Trainieren und Verwenden eines Python-Modells mit gespeicherten Prozeduren in SQL Server](quickstart-python-train-score-in-tsql.md)
