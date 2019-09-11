---
title: Erstellen von SSIS- und SSRS-Workflows mit R
description: Integrationsszenarien, in denen SQL Server Machine Learning Services und R Services, Reporting Services (SSRS) und SQL Server Integration Services (SSIS) kombiniert werden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2b8d55e95991437e4d76911fd26afb5b1bc9c550
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715171"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Erstellen von SSIS-und SSRS-Workflows mit R auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird erläutert, wie Sie eingebettete R-und python-Skripts mithilfe der Sprach-und Data Science Funktionen SQL Server Machine Learning Services mit zwei wichtigen SQL Server Features verwenden: SQL Server Integration Services (SSIS) und SQL Server Reporting Services SSRS. R-und python-Bibliotheken in SQL Server stellen statistische und Vorhersagefunktionen bereit. SSIS und SSRS bieten koordinierte ETL-Transformation und-Visualisierungen. In diesem Artikel wird erläutert, wie alle diese Features in diesem Workflow Muster eingefügt werden:

> [!div class="checklist"]
> * Erstellen einer gespeicherten Prozedur, die ausführbare R-oder python-Dateien enthält
> * Ausführen der gespeicherten Prozedur aus SSIS oder SSRS

In den Beispielen in diesem Artikel geht es hauptsächlich um R und SSIS, die Konzepte und Schritte gelten jedoch auch für python. Der zweite Abschnitt enthält Anleitungen und Links zu SSRS-Visualisierungen.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>Verwenden von SSIS für die Automatisierung

Data Science-Workflows sind hoch iterativ und umfassen eine Menge Transformation von Daten, einschließlich Skalierung, Aggregationen, die Berechnung der Wahrscheinlichkeiten, sowie das Umbenennen und Zusammenführen von Attributen. Obwohl Datenanalysten daran gewöhnt sind, viele dieser Aufgaben in R, Python oder einer anderen Sprache zu erledigen, erfordert das Ausführen solcher Workflows mit Unternehmensdaten nahtlose Integration mit ETL-Tools und -Prozessen.

Da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] es Ihnen ermöglicht, komplexe Vorgänge in R über Transact-SQL und gespeicherte Prozeduren auszuführen, können Sie Data Science Tasks mit vorhandenen ETL-Prozessen integrieren. Anstatt eine Kette Speicher intensiver Aufgaben auszuführen, kann die Daten Vorbereitung mithilfe der effizientesten Tools, einschließlich [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und [!INCLUDE[tsql](../../includes/tsql-md.md)], optimiert werden. 

Im folgenden finden Sie einige Ideen dazu, wie Sie Ihre Datenverarbeitungs-und Modellierungs [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]Pipelines mithilfe von automatisieren können:

+ Extrahieren von Daten aus lokalen oder cloudquellen zum Erstellen von Trainingsdaten 
+ Erstellen und Ausführen von R-oder python-Modellen als Teil eines Daten Integrations Workflows
+ Erneutes trainieren von Modellen in regelmäßigen Abständen (geplant)
+ Laden Sie Ergebnisse aus R-oder python-Skripts in andere Ziele, wie z. b. Excel, Power BI, Oracle und Teradata, um nur einige zu nennen.
+ Verwenden von SSIS-Tasks zum Erstellen von Datenfunktionen in der SQL-Datenbank
+ Verwenden der bedingten Verzweigung zum Wechseln des computekontexts für R-und python-Aufträge

## <a name="ssis-example"></a>SSIS-Beispiel

Das folgende Beispiel stammt aus einem jetzt zurückgezogenen MSDN-Blogbeitrag, der von Jimmy Wong unter dieser URL verfasst wurde:`https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

In diesem Beispiel wird gezeigt, wie Sie Aufgaben mithilfe von SSIS automatisieren. Sie erstellen gespeicherte Prozeduren mit eingebetteter R mithilfe von SQL Server Management Studio und führen diese gespeicherten Prozeduren dann aus [Execute T-SQL Tasks](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) in einem SSIS-Paket aus.

Wenn Sie dieses Beispiel schrittweise durchlaufen möchten, sollten Sie mit Management Studio, SSIS, SSIS-Designer, Package Design und T-SQL vertraut sein. Das SSIS-Paket verwendet drei [Execute T-SQL-Tasks](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) , die Trainingsdaten in eine Tabelle einfügen, die Daten modellieren und die Daten bewerten, um die Vorhersage Ausgabe zu erhalten.

### <a name="load-training-data"></a>Trainingsdaten laden

Führen Sie das folgende Skript in SQL Server Management Studio aus, um eine Tabelle zum Speichern der Daten zu erstellen. Für diese Übung sollten Sie eine Testdatenbank erstellen und verwenden. 

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

Erstellen Sie eine gespeicherte Prozedur, die Trainingsdaten in einen Datenrahmen lädt. In diesem Beispiel wird das integrierte IRIS-DataSet verwendet. 

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

Erstellen Sie im SSIS-Designer einen [Task "SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) ", mit dem die soeben definierte gespeicherte Prozedur ausgeführt wird. Das Skript für **SQLStatement** entfernt vorhandene Daten, gibt an, welche Daten eingefügt werden sollen, und ruft dann die gespeicherte Prozedur auf, um die Daten bereitzustellen.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![Einfügen von Daten](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "Einfügen von Daten")

### <a name="generate-a-model"></a>Generieren eines Modells

Führen Sie das folgende Skript in SQL Server Management Studio aus, um eine Tabelle zu erstellen, in der ein Modell gespeichert wird. 

```T-SQL
Use test-db
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

Erstellen Sie eine gespeicherte Prozedur, die mithilfe von [rxlinmod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)ein lineares Modell generiert. Revoscaler-und revoscalepy-Bibliotheken sind in R-und python-Sitzungen auf SQL Server automatisch verfügbar, sodass die Bibliothek nicht importiert werden muss.

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

Erstellen Sie im SSIS-Designer einen [Task "SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) ", um die gespeicherte Prozedur " **generate_iris_rx_model** " auszuführen. Das Modell wird serialisiert und in der ssis_iris_models-Tabelle gespeichert. Das Skript für **SQLStatement** lautet wie folgt:

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![Generiert ein lineares Modell](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "Generiert ein lineares Modell")

Nachdem diese Aufgabe abgeschlossen ist, können Sie als Prüfpunkt die ssis_iris_models Abfragen, um zu sehen, dass Sie ein binäres Modell enthält.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Vorhersagen (bewerten) von Ergebnissen mit dem "trainierten" Modell

Nun, da Sie über Code verfügen, der Trainingsdaten lädt und ein Modell generiert, besteht der einzige Schritt darin, das Modell zum Generieren von Vorhersagen zu verwenden. 

Fügen Sie zu diesem Zweck das R-Skript in der SQL-Abfrage ein, um die integrierte [rxvorhersage](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) -R-Funktion auf ssis_iris_model zu initiieren. Eine gespeicherte Prozedur mit dem Namen **predict_species_length** führt diese Aufgabe aus.

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

Erstellen Sie im SSIS-Designer einen [Task "SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) ", mit dem die gespeicherte Prozedur " **predict_species_length** " ausgeführt wird, um die vorhergesagte Länge des

```T-SQL
exec predict_species_length 'rxLinMod';
```

![Generieren von Vorhersagen](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "Generieren von Vorhersagen")

### <a name="run-the-solution"></a>Ausführen der Lösung

Drücken Sie im SSIS-Designer F5, um das Paket auszuführen. Es sollte ein Ergebnis ähnlich dem folgenden Screenshot angezeigt werden.

![F5 zum Ausführen im Debugmodus](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5 zum Ausführen im Debugmodus")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Verwenden von SSRS für Visualisierungen

Obwohl R Diagramme und interessante Visualisierungen erstellen kann, ist es nicht gut in externe Datenquellen integriert, was bedeutet, dass jedes Diagramm oder jedes Diagramm einzeln erstellt werden muss. Gemeinsame Nutzung kann auch schwierig sein.

Mithilfe von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]können Sie komplexe Vorgänge in R über [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren ausführen, die problemlos von einer Vielzahl von Tools für Unternehmensberichte, einschließlich [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und Power BI, genutzt werden können.

### <a name="ssrs-example"></a>SSRS-Beispiel

[R Graphics Device for Microsoft Reporting Services (SSRS) (R-Grafikgerät für Microsoft Reporting Services (SSRS))](https://rgraphicsdevice.codeplex.com/)

Dieses CodePlex-Projekt stellt den Code bereit, mit dem Sie ein benutzerdefiniertes Berichts Element erstellen können, das die Grafikausgabe von R als Bild [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] rendert, das in Berichten verwendet werden kann.  Mit dem benutzerdefinierten Berichtselement können Sie folgende Aktionen ausführen:

+ Veröffentlichen von Diagrammen und mit dem R-Grafikgerät erstellten Plots an [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dashboards

+ Übergeben von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Parametern an R-Plots

> [!NOTE]
> In diesem Beispiel muss der Code, der das R-Grafikgerät für Reporting Services unterstützt, sowohl auf dem Reporting Services Server als auch in Visual Studio installiert werden. Manuelle Kompilierung und Konfiguration sind ebenfalls erforderlich.

## <a name="next-steps"></a>Nächste Schritte

Die SSIS-und SSRS-Beispiele in diesem Artikel veranschaulichen zwei Fälle der Ausführung gespeicherter Prozeduren, die eingebettetes R-oder Python-Skript enthalten. Ein wichtiger Punkt ist, dass Sie R-oder python-Skripts für jede Anwendung oder jedes Tool verfügbar machen können, die eine Ausführungs Anforderung für eine gespeicherte Prozedur senden kann. Ein zusätzlicher Zeitraum für SSIS besteht darin, dass Sie Pakete erstellen können, mit denen Sie eine Vielzahl von Vorgängen automatisieren und planen können, wie z. b. Datenbeschaffung, Bereinigung, Manipulation usw. mit R-oder python-Data Science Funktionen, die in der Kette der Vorgänge enthalten sind. Weitere Informationen und Ideen finden Sie unter [operationalisieren von R-Code mithilfe gespeicherter Prozeduren in SQL Server Machine Learning Services](operationalizing-your-r-code.md).