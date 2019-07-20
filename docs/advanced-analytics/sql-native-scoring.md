---
title: Native Bewertung mithilfe der Vorhersage-T-SQL-Anweisung
description: Generieren Sie Vorhersagen mithilfe der Funktion zum Vorhersagen von T-SQL, und bewerten Sie dta-Eingaben anhand eines vorab trainierten Modells, das in R oder python auf SQL Server geschrieben ist
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: b148bd1ca51a7121ae043e2b616100e295c008aa
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344758"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Native Bewertung mithilfe der Vorhersage T-SQL-Funktion
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Bei der nativen Bewertung werden die [T-SQL-Funktion Vorhersagen](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) und die systemeigenen C++ Erweiterungsfunktionen in SQL Server 2017 verwendet, um Vorhersagewerte oder *Ergebnisse* für neue Dateneingaben nahezu in Echtzeit zu generieren. Diese Methodik bietet die schnellste Verarbeitungsgeschwindigkeit von Vorhersage-und Vorhersage Arbeits Auslastungen, ist jedoch mit den Anforderungen an die Plattform und Bibliothek ausgestattet: nur Funktionen von revoscaler und revoscalepy haben C++ Implementierungen.

Die native Bewertung erfordert, dass Sie bereits über ein trainiertes Modell verfügen. In SQL Server 2017 Windows oder Linux oder in Azure SQL-Datenbank können Sie die Vorhersagefunktion in Transact-SQL aufrufen, um die native Bewertung für neue Daten aufzurufen, die Sie als Eingabeparameter bereitstellen. Die Vorhersagefunktion gibt Bewertungen über Dateneingaben zurück, die Sie bereitstellen.

## <a name="how-native-scoring-works"></a>Funktionsweise der systemeigenen Bewertung

Native Bewertung verwendet Native C++ Bibliotheken von Microsoft, die ein bereits trainiertes Modell lesen können, das zuvor in einem speziellen Binärformat gespeichert oder auf einem Datenträger als Rohdaten Strom gespeichert wurde, und Ergebnisse für neue Dateneingaben generieren, die Sie bereitstellen. Da das Modell trainiert, veröffentlicht und gespeichert wird, kann es für die Bewertung verwendet werden, ohne den R-oder Python-Interpreter aufrufen zu müssen. Daher wird der Aufwand mehrerer Prozess Interaktionen reduziert, was zu einer deutlich schnelleren Vorhersage Leistung in Produktionsszenarien in Unternehmen führt.

Um die native Bewertung zu verwenden, müssen Sie die Funktion "Vorhersagen T-SQL" aufzurufen und die folgenden erforderlichen Eingaben übergeben:

+ Ein kompatibles Modell, das auf einem unterstützten Algorithmus basiert.
+ Eingabedaten, die in der Regel als SQL-Abfrage definiert sind.

Die-Funktion gibt die Vorhersagen für die Eingabedaten sowie alle Spalten der Quelldaten zurück, die Sie durchlaufen möchten.

## <a name="prerequisites"></a>Vorraussetzungen

Die Vorhersage ist in allen Editionen von SQL Server 2017-Datenbank-Engine verfügbar und standardmäßig aktiviert, einschließlich SQL Server 2017 Machine Learning Services unter Windows, SQL Server 2017 (Windows), SQL Server 2017 (Linux) oder Azure SQL-Datenbank. Sie müssen R, python nicht installieren oder zusätzliche Funktionen aktivieren.

+ Das Modell muss im Voraus mithilfe eines der unten aufgeführten unterstützten **RX** -Algorithmen trainiert werden.

+ Serialisieren Sie das Modell mithilfe von [rxserialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) für R und [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) für python. Diese Serialisierungsfunktionen wurden optimiert, um eine schnelle Bewertung zu unterstützen.

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>Unterstützte Algorithmen

+ revoscalepy-Modelle

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) 
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) 
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) 
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) 

+ Revoscaler-Modelle

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxbtrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Wenn Sie Modelle von microsoftml oder microsoftml verwenden müssen, verwenden Sie die [Echtzeitbewertung mit sp_rxPredict](real-time-scoring.md).

Nicht unterstützte Modelltypen umfassen die folgenden Typen:

+ Modelle mit anderen Transformationen
+ Modelle, die `rxGlm` die `rxNaiveBayes` -oder-Algorithmen in revoscaler-oder revoscalepy-Entsprechungen verwenden
+ PMML-Modelle
+ Modelle, die mit anderen Open-Source-oder Drittanbieterbibliotheken erstellt wurden

## <a name="example-predict-t-sql"></a>Beispiel: VORHERSAGEN (T-SQL)

In diesem Beispiel erstellen Sie ein Modell und rufen dann die Echt Zeit Vorhersagefunktion von T-SQL auf.

### <a name="step-1-prepare-and-save-the-model"></a>Schritt 1: Vorbereiten und Speichern des Modells

Führen Sie den folgenden Code aus, um die Beispieldatenbank und die erforderlichen Tabellen zu erstellen.

```sql
CREATE DATABASE NativeScoringTest;
GO
USE NativeScoringTest;
GO
DROP TABLE IF EXISTS iris_rx_data;
GO
CREATE TABLE iris_rx_data (
  "Sepal.Length" float not null, "Sepal.Width" float not null
  , "Petal.Length" float not null, "Petal.Width" float not null
  , "Species" varchar(100) null
);
GO
```

Verwenden Sie die folgende Anweisung, um die Datentabelle mit Daten aus dem **IRIS** -DataSet aufzufüllen.

```sql
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

Erstellen Sie nun eine Tabelle zum Speichern von Modellen.

```sql
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Der folgende Code erstellt ein Modell auf der Grundlage des **IRIS** -Datasets und speichert es in der Tabelle " **Models**".

```sql
DECLARE @model varbinary(max);
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'
    iris.sub <- c(sample(1:50, 25), sample(51:100, 25), sample(101:150, 25))
    iris.dtree <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris[iris.sub, ])
    model <- rxSerializeModel(iris.dtree, realtimeScoringOnly = TRUE)
    '
  , @params = N'@model varbinary(max) OUTPUT'
  , @model = @model OUTPUT
  INSERT [dbo].[ml_models]([model_name], [model_version], [native_model_object])
  VALUES('iris.dtree','v1', @model) ;
```

> [!NOTE] 
> Verwenden Sie die Funktion [rxserializemodel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) aus revoscaler, um das Modell zu speichern. Die Standard- `serialize` R-Funktion kann das erforderliche Format nicht generieren.

Sie können eine Anweisung wie die folgende ausführen, um das gespeicherte Modell im Binärformat anzuzeigen:

```sql
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Schritt 2: Vorhersage für das Modell ausführen

Die folgende einfache Vorhersage Anweisung ruft eine Klassifizierung aus dem Entscheidungsstruktur Modell mithilfe der **nativen** Bewertungsfunktion ab. Die Iris-Art wird anhand der von Ihnen bereitgestellten Attribute, der Länge und der Breite des Blatts vorhergesagt.

```sql
DECLARE @model varbinary(max) = (
  SELECT native_model_object
  FROM ml_models
  WHERE model_name = 'iris.dtree'
  AND model_version = 'v1');
SELECT d.*, p.*
  FROM PREDICT(MODEL = @model, DATA = dbo.iris_rx_data as d)
  WITH(setosa_Pred float, versicolor_Pred float, virginica_Pred float) as p;
go
```

Wenn die Fehlermeldung angezeigt wird, "Fehler beim Ausführen der Vorhersage der Funktion. Das Modell ist beschädigt oder ungültig ". Dies bedeutet in der Regel, dass die Abfrage kein Modell zurückgegeben hat. Überprüfen Sie, ob Sie den Modellnamen ordnungsgemäß eingegeben haben oder ob die Tabelle Models leer ist.

> [!NOTE]
> Da die von der **Vorhersage** zurückgegebenen Spalten und Werte je nach Modelltyp variieren können, müssen Sie das Schema der zurückgegebenen Daten mit einer **with** -Klausel definieren.

## <a name="next-steps"></a>Nächste Schritte

Eine umfassende Lösung, die native Bewertung umfasst, finden Sie in den folgenden Beispielen des SQL Server Entwicklungsteams:

+ Stellen Sie Ihr ml-Skript bereit: [Verwenden eines python-Modells](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Stellen Sie Ihr ml-Skript bereit: [Verwenden eines R-Modells](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)