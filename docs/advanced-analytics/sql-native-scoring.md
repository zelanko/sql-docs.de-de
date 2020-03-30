---
title: Native Bewertung mit der T-SQL-Funktion PREDICT
description: Generieren Sie Vorhersagen mithilfe der PREDICT-T-SQL-Funktion, und bewerten Sie Dateneingaben anhand eines vorab trainierten Modells, das in R oder Python auf einer SQL Server-Instanz geschrieben wurde.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 766adecbc91f88ed0796e4214b7e4074fc564f01
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "73727288"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Native Bewertung mithilfe der PREDICT-T-SQL-Funktion
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Bei der nativen Bewertung werden die [PREDICT-T-SQL-Funktion](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) und die nativen C++-Erweiterungsfunktionen in SQL Server 2017 verwendet, um Vorhersagewerte oder *Bewertungen* für neue Dateneingaben in nahezu Echtzeit zu generieren. Dieses Verfahren bietet die schnellstmögliche Verarbeitungsgeschwindigkeit von Vorhersage- und Prognoseworkloads, ist aber mit Plattform- und Bibliotheksanforderungen verbunden: In C++ sind nur Funktionen von RevoScaleR und revoscalepy implementiert.

Für die native Bewertung ist ein bereits trainiertes Modell erforderlich. In SQL Server 2017 Windows oder Linux bzw. in Azure SQL-Datenbank können Sie die PREDICT-Funktion in Transact-SQL aufrufen, um eine native Bewertung für neue Daten zu erstellen, die Sie als Eingabeparameter angeben. Die PREDICT-Funktion gibt Bewertungen zu den von Ihnen bereitgestellten Dateneingaben zurück.

## <a name="how-native-scoring-works"></a>Funktionsweise der nativen Bewertung

Für die native Bewertung werden Bibliotheken von Microsoft verwendet, die ein bereits trainiertes Modell lesen können, das zuvor in einem speziellen Binärformat gespeichert oder als Rohdatenstrom auf der Festplatte gespeichert wurde. Zudem generiert sie die Ergebnisse für neue Dateneingaben, die Sie bereitstellen. Da das Modell trainiert, veröffentlicht und gespeichert wird, kann es für die Bewertung verwendet werden, ohne den R- oder Python-Interpreter aufrufen zu müssen. Dadurch wird der Aufwand für mehrere Prozessinteraktionen verringert, was wesentlich schnellere Vorhersagen in Unternehmensproduktionsszenarios ermöglicht.

Zur Verwendung der nativen Bewertung rufen Sie die Funktion PREDICT-T-SQL auf und übergeben Sie die folgenden erforderlichen Eingaben:

+ Ein kompatibles Modell, das auf einem unterstützten Algorithmus basiert.
+ Eingabedaten, die in der Regel als SQL-Abfrage definiert sind.

Die Funktion gibt Vorhersagen für die Eingabedaten zurück, zusammen mit allen Spalten der Quelldaten, die Sie durchlaufen möchten.

## <a name="prerequisites"></a>Voraussetzungen

PREDICT ist für alle Editionen der SQL Server 2017-Datenbank-Engine verfügbar und standardmäßig aktiviert, einschließlich SQL Server Machine Learning Services unter Windows, SQL Server 2017 (Windows), SQL Server 2017 (Linux) oder Azure SQL-Datenbank. Sie müssen R bzw. Python nicht installieren oder zusätzliche Funktionen aktivieren.

+ Das Modell muss vorab mit einem der unterstützten **rx**-Algorithmen trainiert werden, die unten aufgeführt sind.

+ Serialisieren Sie das Modell mithilfe von [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) für R und [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) für Python. Diese Serialisierungsfunktionen wurden zur Unterstützung einer schnellen Bewertung optimiert.

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>Unterstützte Algorithmen

+ revoscalepy-Modelle

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) 
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) 
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) 
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) 

+ RevoScaleR-Modelle

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Wenn Sie Modelle aus MicrosoftML oder microsoftml verwenden müssen, verwenden Sie [Echtzeitbewertung mit sp_rxPredict](real-time-scoring.md).

Die folgenden Modelltypen werden nicht unterstützt:

+ Modelle, die andere Transformationen enthalten
+ Modelle, die die `rxGlm`- oder `rxNaiveBayes`-Algorithmen in Entsprechungen von RevoScaleR oder revoscalepy verwenden
+ PMML-Modelle
+ Mit anderen Open-Source- oder Drittanbieterbibliotheken erstellte Modelle

## <a name="example-predict-t-sql"></a>Beispiel: PREDICT (T-SQL)

In diesem Beispiel erstellen Sie ein Modell und rufen dann die T-SQL-Funktion für Vorhersagen in Echtzeit auf.

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

Verwenden Sie die folgende Anweisung, um die Datentabelle mit Daten aus dem **Iris**-Dataset aufzufüllen.

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

Mit dem folgenden Code wird ein Modell erstellt, das auf dem **Iris**-Dataset basiert und in der Tabelle mit dem Namen **Modelle** gespeichert wird.

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
> Stellen Sie sicher, dass Sie die [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)-Funktion von RevoScaleR verwenden, um das Modell zu speichern. Die standardmäßige R-Funktion `serialize` kann das erforderliche Format nicht generieren.

Sie können eine Anweisung wie die folgende ausführen, um das gespeicherte Modell im Binärformat anzuzeigen:

```sql
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Schritt 2: Ausführen von PREDICT für das Modell

Die folgende einfache PREDICT-Anweisung ruft eine Klassifizierung aus dem Entscheidungsstrukturmodell mithilfe der Funktion für die **native Bewertung** ab. Die Irisarten werden anhand der von Ihnen angegebenen Attribute, der Länge und Breite der Blütenblätter, vorhergesagt.

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

Wenn ein Fehler wie „Fehler bei der Ausführung der Funktion PREDICT. Modell ist beschädigt oder ungültig.“ erhalten, bedeutet das normalerweise, dass die Abfrage kein Modell zurückgegeben hat. Überprüfen Sie, ob Sie den Modellnamen ordnungsgemäß eingegeben haben oder ob die Tabelle des Modells leer ist.

> [!NOTE]
> Da die von **PREDICT** zurückgegebenen Spalten und Werte je nach Modelltyp variieren können, müssen Sie das Schema der zurückgegebenen Daten mithilfe einer **WITH**-Klausel definieren.

## <a name="next-steps"></a>Nächste Schritte

Eine Komplettlösung mit nativer Bewertung finden Sie in diesen Beispielen des SQL Server-Entwicklungsteams:

+ Stellen Sie Ihr ML-Skript bereit: [Verwenden eines Python-Modells](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Stellen Sie Ihr ML-Skript bereit: [Verwenden eines R-Modells](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)