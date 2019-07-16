---
title: Erstellen von SSIS und die SSRS-Workflows mit R – SQL Server Machine Learning Services
description: Kombination von SQL Server Machine Learning Services und R Services, Reporting Services (SSRS) und SQL Server Integration Services (SSIS) Integrationsszenarien.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: a9f3a76ac1829f529e0f3e5459ab842dcafa7c80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962699"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Erstellen von SSIS und die SSRS-Workflows mit R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie mit eingebetteten R und Python-Skripts verwenden die Sprache und Data Science-Funktionen von SQL Server-Machine Learning-Dienste mit zwei wichtige Funktionen von SQL Server: SQL Server Integration Services (SSIS) und SQL Server Reporting Services SSRS. R und Python-Bibliotheken in SQL Server bieten Statistik-und predictive. SSIS und SSRS enthalten koordinierte ETL-Transformation und Visualisierungen. In diesem Artikel wird erläutert, wie auf alle diese Features in diesem Muster Workflow zusammengestellt werden:

> [!div class="checklist"]
> * Erstellen einer gespeicherten Prozedur, die ausführbaren R oder Python enthält.
> * Führen Sie die gespeicherte Prozedur von SSIS oder SSRS

In die Beispielen in diesem Artikel werden hauptsächlich über R und SSIS, aber die Konzepte und Schritte gelten auch für Python. Der zweite Abschnitt enthält Anweisungen und Links für SSRS-Visualisierungen.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>Verwenden von SSIS für die Automatisierung

Data Science-Workflows sind hoch iterativ und umfassen eine Menge Transformation von Daten, einschließlich Skalierung, Aggregationen, die Berechnung der Wahrscheinlichkeiten, sowie das Umbenennen und Zusammenführen von Attributen. Obwohl Datenanalysten daran gewöhnt sind, viele dieser Aufgaben in R, Python oder einer anderen Sprache zu erledigen, erfordert das Ausführen solcher Workflows mit Unternehmensdaten nahtlose Integration mit ETL-Tools und -Prozessen.

Da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ermöglicht es Ihnen, komplexe Vorgänge in R über Transact-SQL und gespeicherte Prozeduren auszuführen. Sie können die Data Science-Aufgaben mit vorhandenen ETL-Prozesse integrieren. Stattdessen als eine Kette von arbeitsspeicherintensive Tasks auszuführen, die Vorbereitung der Daten kann optimiert werden mit den effizientesten Tools wie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Hier sind einige Ideen für, wie Sie die Verarbeitung Ihrer Daten automatisieren können, und Modellierung von pipelines mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Extrahieren von Daten aus lokalen oder cloud-Quellen aus, um die Trainingsdaten erstellen 
+ Erstellen und Ausführen von R- oder Python-Modelle im Rahmen eines Datenworkflows für die integration
+ Erneutes Trainieren von Modellen in regelmäßigen Abständen (geplant)
+ Laden Sie die Ergebnisse aus R oder Python-Skript an andere Ziele, z. B. Excel, Power BI, Oracle und Teradata, um nur einige zu nennen
+ Verwenden von SSIS-Tasks zum Erstellen von Data-Features in der SQL-Datenbank
+ Verwenden von bedingter Verzweigung um computekontext für R und Python-Aufträge zu wechseln.

## <a name="ssis-example"></a>SSIS-Beispiel

Das folgende Beispiel stammt aus einer inzwischen eingestellten MSDN-Blogbeitrag von Jimmy Wong unter dieser URL erstellt: `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

Dieses Beispiel zeigt, wie zum Automatisieren von Aufgaben, die mithilfe von SSIS. Sie erstellen Sie gespeicherte Prozeduren mit eingebetteten R mit SQL Server Management Studio, und führen Sie dann auf diese gespeicherten Prozeduren von [T-SQL ausführen-Tasks](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) in einem SSIS-Paket.

Um die Schritte in diesem Beispiel sollten Sie mit Management Studio, SSIS, SSIS-Designer, Paketentwurfs und T-SQL vertraut sein. Das SSIS-Paket verwendet drei [T-SQL ausführen-Tasks](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) , die Trainingsdaten in eine Tabelle einfügen, die Daten modellieren und bewerten Sie die Daten, um die vorhersageausgabe zu erhalten.

### <a name="load-training-data"></a>Laden der Trainingsdaten

Führen Sie das folgende Skript in SQL Server Management Studio zum Erstellen einer Tabelle zum Speichern der Daten. Sie sollten erstellen und verwenden für diese Übung eine Testdatenbank. 

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

Erstellen Sie eine gespeicherte Prozedur, die Trainingsdaten in Datenrahmen lädt. In diesem Beispiel wird das integrierte Iris-DataSet verwendet. 

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

Erstellen Sie im SSIS-Designer eine [Task SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) , das die gespeicherte Prozedur, die soeben definierten ausführt. Das Skript für **SQLStatement** entfernt die vorhandene Daten, gibt an, welche Daten einzufügen, und ruft dann die gespeicherte Prozedur, um die Daten bereitzustellen.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![Einfügen von Daten](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "Einfügen von Daten")

### <a name="generate-a-model"></a>Generieren eines Modells

Führen Sie das folgende Skript in SQL Server Management Studio zum Erstellen einer Tabelle, die ein Modell speichert. 

```T-SQL
Use test-db
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

Erstellen einer gespeicherten Prozedur, die ein Lineares Modell mit generiert [RxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Revoscaler- und Revoscalepy-Bibliotheken sind in R und Python-Sitzungen auf SQL Server automatisch verfügbar, daher keine Notwendigkeit besteht, um die Bibliothek importieren.

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

Erstellen Sie im SSIS-Designer eine [Task SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) zum Ausführen der **Generate_iris_rx_model** gespeicherte Prozedur. Das Modell wird serialisiert und in der Tabelle Ssis_iris_models gespeichert. Das Skript für **SQLStatement** lautet wie folgt:

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![Generiert ein Lineares Modell](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "generiert ein Lineares Modell")

Als Prüfpunkt nachdem diese Aufgabe abgeschlossen ist, können Sie Abfragen der Ssis_iris_models, um festzustellen, ob es sich um ein binäres Modell enthält.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Vorhersagen Sie (Bewertung)-Ergebnissen, die mit dem "trainingsmodell"

Nun, da Sie über Code verfügen, die Daten lädt und ein Modell generiert, verwendet der einzige Schritt links des Modells, um vorhersagen zu generieren. 

Zu diesem Zweck fügen Sie das R-Skript in die SQL-Abfrage zum Auslösen der [RxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) integrierte R-Funktion auf Ssis_iris_model. Eine gespeicherte Prozedur aufgerufen **Predict_species_length** führt diese Aufgabe aus.

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

Erstellen Sie im SSIS-Designer eine [Task SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) , ausgeführt wird die **Predict_species_length** gespeicherte Prozedur zum Generieren der vorhergesagten des kelchblatts sowie Länge.

```T-SQL
exec predict_species_length 'rxLinMod';
```

![Generieren von Vorhersagen](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "Generieren von Vorhersagen")

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