---
title: Erstellen von SSIS und die SSRS-Workflows mit R – SQL Server Machine Learning Services
description: Kombination von SQL Server Machine Learning Services und R Services, Reporting Services (SSRS) und SQL Server Integration Services (SSIS) Integrationsszenarien.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 76ddf3e3fdb43fea6bb8fd224f8199cda4134b64
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57976300"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Erstellen von SSIS und die SSRS-Workflows mit R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie mit gespeicherten Prozeduren in zwei wichtige Funktionen von SQL Server, SQL Server Integration Services (SSIS) und SQL Server Reporting Services SSRS Weise, in der relationale Daten, Data Science-Funktionen von Microsoft R-Bibliotheken kombiniert werden, und BI-Funktionen für eine koordinierte Datentransformationen und Visualisierung. Erfahren Sie, welche Funktionen von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] eignen sich für ein Data Science-Lösung. In diesem Artikel auch erinnert Sie daran, dass Code und Daten in SQL Server, z. B. eingebetteten R-Code in gespeicherten Prozeduren verarbeitet problemlos in Visualisierungen, die im bereitgestellten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

## <a name="bring-compute-power-to-the-data"></a>Schalten Sie die computeleistung auf die Daten

Ein Design des Ziel der Integration von R und Python mit SQL Server wurde um Analysen in der Nähe der Daten zu bringen. Dies bietet mehrere Vorteile:

+ Datensicherheit. Bringen R näher an der Quelle der Daten vermeiden unnötiger oder unsicherer Datentransfer.
+ Geschwindigkeit. Datenbanken sind für setbasierte Vorgänge optimiert. Aktuelle Innovationen in Datenbanken, z.B. in-Memory-Tabellen stellen Zusammenfassungen und Aggregationen der Daten extrem, und es sind eine perfekte Ergänzung für die Data Science.
+ Einfache Bereitstellung und Integration. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist der zentrale Punkt von Vorgängen für viele Verwaltungsaufgaben von Daten und Anwendungen. Verwenden Sie die Daten, die in der Datenbank oder ein berichterstellungs-Warehouse befinden, stellen Sie sicher, dass die Daten, die von Machine learning-Lösungen verwendet konsistent und aktuell ist. 
+ Effizienz im gesamten Cloud und lokal. Anstatt die Daten in R zu verarbeiten, können Sie Datenpipelines des Unternehmens nutzen, darunter [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und Azure Data Factory. Das Berichten von Ergebnissen oder Analysen ist über Power BI oder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]einfach.

Durch die Verwendung der richtigen Kombination von SQL und R für verschiedene Datenverarbeitungstasks und analytische Tasks, können Datenanalysten und Entwickler produktiver sein.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-data-transformation-and-automation"></a>Verwenden von SSIS für die Datentransformation und -Automatisierung

Data Science-Workflows sind hoch iterativ und umfassen eine Menge Transformation von Daten, einschließlich Skalierung, Aggregationen, die Berechnung der Wahrscheinlichkeiten, sowie das Umbenennen und Zusammenführen von Attributen. Obwohl Datenanalysten daran gewöhnt sind, viele dieser Aufgaben in R, Python oder einer anderen Sprache zu erledigen, erfordert das Ausführen solcher Workflows mit Unternehmensdaten nahtlose Integration mit ETL-Tools und -Prozessen.

Da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] es Ihnen ermöglicht, komplexe Vorgänge in R über Transact-SQL und gespeicherte Prozeduren auszuführen, können Sie R-spezifische Aufgaben mit vorhandenen ETL-Prozessen ohne erneute Entwicklung integrieren. Stattdessen als eine Kette von Aufgaben für arbeitsspeicherintensive in R auszuführen, die Vorbereitung der Daten kann optimiert werden mit den effizientesten Tools wie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Hier sind einige Ideen für, wie Sie die Verarbeitung Ihrer Daten automatisieren können, und Modellierung von pipelines mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Verwendung [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Tasks zum Erstellen von Features der erforderlichen Daten in der SQL-Datenbank
+ Verwenden von bedingter Verzweigung, um Computekontext für R-Aufträge zu wechseln
+ Führen Sie R-Aufträge, die ihre eigenen Daten in der Datenbank zu generieren, und Freigeben von Daten für Anwendungen
+ Bei Verwendung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], laden Sie R-Skript in einer Textvariablen gespeichert, und führen Sie es in SQL Server

## <a name="ssis-example"></a>SSIS-Beispiel

Das folgende Beispiel stammt aus einer inzwischen eingestellten MSDN-Blogbeitrag von Jimmy Wong unter dieser URL erstellt: `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`.

Dieses Beispiel zeigt, wie zum Automatisieren von Aufgaben, die mithilfe von SSIS. Sie erstellen Sie gespeicherte Prozeduren mit eingebetteten R mit SQL Server Management Studio, und führen Sie dann auf diese gespeicherten Prozeduren von [T-SQL ausführen-Tasks](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) in einem SSIS-Paket.

Um die Schritte in diesem Beispiel sollten Sie mit Management Studio, SSIS, SSIS-Designer, Paketentwurfs und T-SQL vertraut sein. Das SSIS-Paket verwendet drei [T-SQL ausführen-Tasks](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) , die Trainingsdaten in eine Tabelle einfügen, die Daten modellieren und bewerten Sie die Daten, um die vorhersageausgabe zu erhalten.

### <a name="create-tables"></a>Erstellen von Tabellen

Führen das folgende Skript in SQL Server Management Studio zum Erstellen von ein paar Tabellen: eine zum Speichern der Daten und eine andere, um ein Modell zu speichern. Die Rolle der Ssis_iris Tabelle ist, als Trainingsdaten in einem operationalisierungsszenario zu fungieren. 

```T-SQL
Use irissql
GO

Create table ssis_iris (
    id int not null identity primary key
    , "Sepal.Length" float not null, "Sepal.Width" float not null
    , "Petal.Length" float not null, "Petal.Width" float not null
    , "Species" varchar(100) null
);
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

### <a name="create-a-stored-procedure-that-loads-training-data"></a>Erstellen einer gespeicherten Prozedur, die Daten lädt.

Dieses Skript erstellt eine gespeicherte Prozedur, die Iris in einen Datenrahmen, die die integrierte R DataSet lädt.

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

### <a name="define-an-execute-sql-task-that-refreshes-the-model"></a>Definieren Sie einen Task SQL ausführen, der das Modell aktualisieren

Erstellen Sie im SSIS-Designer eine [Task SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task).

![Einfügen von Daten](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "Einfügen von Daten")

Das Skript für die SQL-Anweisung lautet wie folgt aus. Das Skript entfernt die vorhandene Daten und lädt dann erneut, neue Daten mithilfe der **Load_iris** gespeicherte Prozedur, die Sie im vorherigen Schritt erstellt haben.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

### <a name="create-a-stored-procedure-that-generates-a-model"></a>Erstellen einer gespeicherten Prozedur, die ein Modell generiert.

Diese gespeicherte Prozedur ist Code, der erstellt ein Lineares Modell mit [RxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Revoscaler- und Revoscalepy-Bibliotheken werden in R und Python-Sitzungen auf SQL Server automatisch geladen.

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

### <a name="define-an-execute-sql-task-that-runs-the-model-generation-stored-procedure"></a>Definieren Sie einen Task SQL ausführen, der die modellgenerierung gespeicherte Prozedur ausgeführt wird.

In diesem Schritt [Task SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) führt die **Generate_iris_rx_model** gespeicherte Prozedur erstellen des Modells und in der Tabelle Ssis_iris_models einfügen.

![Generiert ein Lineares Modell](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "generiert ein Lineares Modell")

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

Nach Abschluss dieser Aufgabe können Sie durch Abfragen der Ssis_iris_models, um festzustellen, ob es sich um ein binäres Modell enthält.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Vorhersagen Sie (Bewertung)-Ergebnissen, die mit dem "trainingsmodell"

In diesem Beispiel einfach ist die Annahme dieses Ssis_iris_model ein trainiertes Modell. Da der Zweck eines trainierten Modells ist, um vorhersagen zu generieren, können wir nun zum Ausführen einer Vorhersage verwenden. 

Zu diesem Zweck fügen Sie das R-Skript in die SQL-Abfrage zum Auslösen der [RxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) integrierte R-Funktion auf Ssis_iris_model. Wird aufgerufen, eine gespeicherte Prozedur in SQL Server **Predict_species_length** führt diese Aufgabe aus.

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

### <a name="define-an-execute-sql-task-that-predicts-outcomes"></a>Definieren Sie einen Task SQL ausführen, der vorhersagt, Ergebnisse

Mithilfe von [Task SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task), führen Sie die **Predict_species_length** Verfahren zum Generieren der vorhergesagten des kelchblatts sowie Länge gespeichert.

![Generieren von Vorhersagen](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "Generieren von Vorhersagen")

```T-SQL
exec predict_species_length 'rxLinMod';
```

### <a name="run-the-solution"></a>Führen Sie die Projektmappe

Drücken Sie F5, um das Paket ausgeführt werden, im SSIS-Designer. Daraufhin sollte ein Ergebnis ähnlich wie im folgenden Screenshot.

![F5, um im Debugmodus auszuführen](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5, um im Debugmodus auszuführen.")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Verwenden von SSRS für Visualisierungen

Obwohl R Diagramme und interessante Visualisierungen erstellen kann, ist es nicht gut integrierten mit externen Datenquellen, was bedeutet, dass jedes Diagramm oder jeder Graph einzeln erstellt werden muss. Gemeinsame Nutzung kann auch schwierig sein.

Mithilfe von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], können Sie komplexe Vorgänge in R über ausführen [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren, die durch eine Vielzahl von Tools bereit, z. B. für Unternehmensberichte problemlos genutzt werden können [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und Power BI.

### <a name="ssrs-example"></a>SSRS-Beispiel

[R Graphics Device for Microsoft Reporting Services (SSRS) (R-Grafikgerät für Microsoft Reporting Services (SSRS))](https://rgraphicsdevice.codeplex.com/)

Dieses CodePlex-Projekt enthält der Code können Sie ein benutzerdefiniertes Berichtselement erstellen, stellt die Grafikausgabe von R als Bild, die verwendet werden kann [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichte.  Mit dem benutzerdefinierten Berichtselement können Sie folgende Aktionen ausführen:

+ Veröffentlichen von Diagrammen und mit dem R-Grafikgerät erstellten Plots an [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dashboards

+ Übergeben von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Parametern an R-Plots

> [!NOTE]
> In diesem Beispiel muss der Code, der das R-Grafikgerät für Reporting Services unterstützt sowohl auf dem Reporting Services-Server als auch in Visual Studio installiert werden. Manuelle Kompilierung und Konfiguration sind ebenfalls erforderlich.

## <a name="next-steps"></a>Nächste Schritte

Die SSIS und die SSRS-Beispiele in diesem Artikel veranschaulichen zwei Fälle, für die Ausführung von gespeicherter Prozeduren, die eingebettete R oder Python-Skript enthalten. Ein wesentlicher Punkt ist, dass Sie verfügbar machen, können R oder Python-Skript zu einer Anwendung oder ein Tool, das eine ausführungsanforderung für eine gespeicherte Prozedur senden kann. Eine weitere Punkt für SSIS ist, Sie Pakete, die automatisieren und Planen der Vielzahl von Vorgängen, z. B. der Datenerfassung erstellen können, Bereinigung, Bearbeitung und So weiter mit R oder Python Data Science-Funktionalität in der Kette der Vorgänge enthalten. Weitere Informationen und Ideen, finden Sie unter [Operationalisieren von R-Code mithilfe von gespeicherten Prozeduren in SQL Server Machine Learning Services](operationalizing-your-r-code.md).