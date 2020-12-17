---
title: Erstellen von SSIS- und SSRS-Workflows mit R
description: Integrationsszenarios, in denen SQL Server Machine Learning Services und R Services, Reporting Services (SSRS) und SQL Server Integration Services (SSIS) kombiniert werden.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 08/28/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 12088a5d5a8413f76176da09e2f8aa94e72e63f0
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470911"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Erstellen von SSIS- und SSRS-Workflows mit R unter SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

In diesem Artikel wird erläutert, wie Sie eingebettete R- und Python-Skripts mithilfe der Sprach-und Data Science Funktionen von SQL Server Machine Learning Services mit zwei wichtigen SQL Server-Features verwenden: SQL Server Integration Services (SSIS) und SQL Server Reporting Services (SSRS). R- und Python-Bibliotheken in SQL Server stellen statistische Funktionen und Vorhersagefunktionen bereit. SSIS und SSRS bieten koordinierte ETL-Transformationen bzw. ETL-Visualisierungen. In diesem Artikel wird erläutert, wie in diesem Workflowmuster alle diese Features zusammen verwendet werden:

> [!div class="checklist"]
> * Erstellen einer gespeicherten Prozedur, die ausführbare R- oder Python-Dateien enthält
> * Ausführen der gespeicherten Prozedur über SSIS oder SSRS

In den Beispielen in diesem Artikel geht es hauptsächlich um R und SSIS, die Konzepte und Schritte gelten jedoch auch für Python. Der zweite Abschnitt enthält Anleitungen und Links zu SSRS-Visualisierungen.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>Verwenden von SSIS für die Automatisierung

Data Science-Workflows sind hoch iterativ und umfassen eine Menge Transformation von Daten, einschließlich Skalierung, Aggregationen, die Berechnung der Wahrscheinlichkeiten, sowie das Umbenennen und Zusammenführen von Attributen. Obwohl Datenanalysten daran gewöhnt sind, viele dieser Aufgaben in R, Python oder einer anderen Sprache zu erledigen, erfordert das Ausführen solcher Workflows mit Unternehmensdaten nahtlose Integration mit ETL-Tools und -Prozessen.

Da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] es Ihnen ermöglicht, komplexe Vorgänge in R über Transact-SQL und gespeicherte Prozeduren auszuführen, können Sie Data Science-Aufgaben in vorhandene ETL-Prozessen integrieren. Anstatt eine Kette von speicherintensiven Aufgaben auszuführen, kann die Vorbereitung der Daten mit effizienten Tools wie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und [!INCLUDE[tsql](../../includes/tsql-md.md)] optimiert werden. 

Im Folgenden finden Sie einige Anregungen zum Automatisieren von Datenverarbeitungs- und Modellierungspipelines mithilfe von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Extrahieren von Daten aus lokalen Quellen oder Quellen in der Cloud zum Erstellen von Trainingsdaten 
+ Erstellen und Ausführen von R- oder Python-Modellen im Rahmen eines Datenintegrationsworkflows
+ Erneutes Trainieren von Modellen in regelmäßigen (geplanten) Abständen
+ Laden von Ergebnissen aus R- oder Python-Skripts in andere Ziele, wie Excel, Power BI, Oracle, Teradata u. a.
+ Verwenden von SSIS-Aufgaben zum Erstellen von Datenfunktionen in der SQL-Datenbank
+ Verwenden von bedingter Verzweigung, um Computekontext für R- und Python-Aufträge zu wechseln

## <a name="ssis-example"></a>SSIS-Beispiel

Das folgende Beispiel stammt aus einem inzwischen eingestellten MSDN-Blogbeitrag, der von Jimmy Wong unter dieser URL verfasst wurde: `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

In diesem Beispiel wird gezeigt, wie Aufgaben mithilfe von SSIS automatisiert werden. Gespeicherte Prozeduren mit eingebettetem R-Skript werden mithilfe von SQL Server Management Studio erstellt und dann über den Task [T-SQL-Anweisung ausführen](../../integration-services/control-flow/execute-t-sql-statement-task.md) in einem SSIS-Paket ausgeführt.

Wenn Sie die einzelnen Schritte dieses Beispiels ausführen möchten, müssen Sie mit Management Studio, SSIS, SSIS Designer, Package Design und T-SQL vertraut sein. Vom SSIS-Paket werden drei Tasks vom Typ [T-SQL-Anweisungen ausführen](../../integration-services/control-flow/execute-t-sql-statement-task.md) verwendet, mit denen Trainingsdaten in eine Tabelle eingefügt, die Daten modelliert und die Daten bewertet werden, um ein Vorhersageergebnis zu erhalten.

### <a name="load-training-data"></a>Laden von Trainingsdaten

Führen Sie das folgende Skript in SQL Server Management Studio aus, um eine Tabelle zum Speichern der Daten zu erstellen. Für diese Übung erstellen und verwenden Sie eine Testdatenbank. 

```T-SQL
Use test-db
GO

Create table ssis_iris (
    id int not null identity primary key
    , "Sepal.Length" float not null, "Sepal.Width" float not null
    , "Petal.Length" float not null, "Petal.Width" float not null
    , "Species" varchar(100) null
);
GO
```

Erstellen Sie eine gespeicherte Prozedur, mit der die Trainingsdaten in einen Datenrahmen geladen werden. In diesem Beispiel wird das integrierte IRIS-Dataset verwendet. 

```T-SQL
Create procedure load_iris
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'iris_df <- iris;'
        , @input_data_1 = N''
        , @output_data_1_name = N'iris_df'
    with result sets (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100)));
end;
```

Erstellen Sie in SSIS Designer den Task [SQL ausführen](../../integration-services/control-flow/execute-sql-task.md), mit dem die gespeicherte Prozedur ausgeführt wird, die Sie eben definiert haben. Mit dem Skript für **SQLStatement** werden vorhandene Daten entfernt, angegeben, welche Daten eingefügt werden sollen, und anschließend die gespeicherte Prozedur zum Bereitstellen der Daten aufgerufen.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![Einfügen von Daten](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "Einfügen von Daten")

### <a name="generate-a-model"></a>Generieren eines Modells

Führen Sie das folgende Skript in SQL Server Management Studio aus, um eine Tabelle zum Speichern eines Modells zu erstellen. 

```T-SQL
Use test-db
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

Erstellen Sie eine gespeicherte Prozedur zum Generieren eines linearen Modells mithilfe von [rxLinMod](/machine-learning-server/r-reference/revoscaler/rxlinmod). Die Bibliotheken RevoScaleR und RevoScalePy sind in R und Python-Sitzungen unter SQL Server automatisch verfügbar und müssen daher nicht importiert werden.

```T-SQL
Create procedure generate_iris_rx_model
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'
          irisLinMod <- rxLinMod(Sepal.Length ~ Sepal.Width + Petal.Length + Petal.Width + Species, data = ssis_iris);
          trained_model <- data.frame(payload = as.raw(serialize(irisLinMod, connection=NULL)));'
        , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris'
        , @input_data_1_name = N'ssis_iris'
        , @output_data_1_name = N'trained_model'
    with result sets ((model varbinary(max)));
end;
GO
```

Erstellen Sie in SSIS Designer den Task [SQL ausführen](../../integration-services/control-flow/execute-sql-task.md), um die gespeicherte Prozedur **generate_iris_rx_model** auszuführen. Das Modell wird serialisiert und in der Tabelle „ssis_iris_models“ gespeichert. Das Skript für **SQLStatement** sieht wie folgt aus:

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![Generiert ein lineares Modell](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "Generiert ein lineares Modell")

Nach Abschluss dieser Aufgabe können Sie als Prüfpunkt die Tabelle „ssis_iris_models“ abfragen, um zu prüfen, ob sie ein binäres Modell enthält.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Vorhersagen (Bewerten) von Ergebnissen mit dem „trainierten“ Modell

Nachdem Sie nun über Code verfügen, mit dem Sie Trainingsdaten laden und ein Modell generieren können, müssen Sie jetzt nur noch mit dem Modell Vorhersagen generieren. 

Fügen Sie hierzu das R-Skript in die SQL-Abfrage ein, um die in die R-Funktion in ssis_iris_model integrierte Funktion [rxPredict](/machine-learning-server/r-reference/revoscaler/rxpredict) auszulösen. Dieser Task wird von der gespeicherten Prozedur **predict_species_length** ausgeführt.

```T-SQL
Create procedure predict_species_length (@model varchar(100))
as
begin
    declare @rx_model varbinary(max) = (select model from ssis_iris_models where model_name = @model);
    -- Predict based on the specified model:
    exec sp_execute_external_script
        @language = N'R'
        , @script = N'
irismodel <-unserialize(rx_model);
irispred <- rxPredict(irismodel, ssis_iris[,2:6]);
OutputDataSet <- cbind(ssis_iris[1], irispred$Sepal.Length_Pred, ssis_iris[2]);
colnames(OutputDataSet) <- c("id", "Sepal.Length.Actual", "Sepal.Length.Expected");
#OutputDataSet <- subset(OutputDataSet, Species.Length.Actual != Species.Expected);
'
    , @input_data_1 = N'
    select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris
    '
    , @input_data_1_name = N'ssis_iris'
    , @params = N'@rx_model varbinary(max)'
    , @rx_model = @rx_model
    with result sets ( ("id" int, "Species.Length.Actual" float, "Species.Length.Expected" float)
        );
end;
```

Erstellen Sie in SSIS Designer den Task [SQL ausführen](../../integration-services/control-flow/execute-sql-task.md), mit dem die gespeicherte Prozedur **predict_species_length** ausgeführt wird, um die vorhergesagte Länge des Datenblatts zu generieren.

```T-SQL
exec predict_species_length 'rxLinMod';
```

![Generieren von Vorhersagen](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "Generieren von Vorhersagen")

### <a name="run-the-solution"></a>Ausführen der Lösung

Drücken Sie in SSIS Designer die Taste F5, um das Paket auszuführen. Das Ergebnis sollte ähnlich wie in diesem Screenshot aussehen.

![F5 zum Ausführen im Debugmodus](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5 zum Ausführen im Debugmodus")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Verwenden von SSRS für Visualisierungen

Mit R lassen sich zwar Diagramme und interessante Visualisierungen erstellen, aber R ist dennoch nicht gut in externe Datenquellen integriert. Das bedeutet, dass jedes Diagramm oder jeder Graph einzeln erstellt werden muss. Gemeinsame Nutzung kann auch schwierig sein.

Mithilfe von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] können Sie komplexe Vorgänge in R über gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren ausführen, die problemlos von einer Vielzahl von Tools für Unternehmensberichte, einschließlich [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und Power BI, genutzt werden können.

## <a name="next-steps"></a>Nächste Schritte

Anhand der Beispiele für SSIS und SSRS in diesem Artikel werden zwei Fälle veranschaulicht, in denen gespeicherte Prozeduren ausgeführt werden, die eingebettetes R- oder Python-Skript enthalten. Wichtig ist, dass Sie R- oder Python-Skripts für alle Anwendungen oder Tools verfügbar machen können, die eine Ausführungsanforderung für eine gespeicherte Prozedur senden können. Außerdem ist im Zusammenhang mit SSIS wichtig, dass Sie mit der R oder Python Data Science-Funktion in der Kette von Vorgängen Pakete erstellen und planen können, mit denen eine Vielzahl von Vorgängen wie Datenbeschaffung, Datenbereinigung, Datenbearbeitung usw. automatisiert werden können. Weitere Informationen und Anregungen finden Sie unter [Operationalisieren von R-Code mithilfe von gespeicherten Prozeduren in SQL Server Machine Learning Services](operationalizing-your-r-code.md).