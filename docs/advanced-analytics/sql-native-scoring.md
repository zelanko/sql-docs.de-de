---
title: Native Bewertung mit VORHERSAGEN für T-SQL-Anweisung – SQL Server Machine Learning Services
description: Generieren von Vorhersagen mit der VORHERSAGE für T-SQL-Funktion, die Bewertung der Dta-Eingaben für ein vorab trainiertes Modell in R oder Python geschrieben sind, auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: bd0a79a3991c34ddbcf874aca80160299074919a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513217"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Native Bewertung mithilfe der VORHERSAGEN für T-SQL-Funktion
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Native Bewertung verwendet [VORHERSAGEN für T-SQL-Funktion](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) und die systemeigenen C++-Erweiterungsfunktionen in SQL Server 2017 um Vorhersagewerte zu generieren oder *Bewertungen* für neue Dateneingaben in nahezu in Echtzeit. Diese Methode bietet die schnellste möglich verarbeitungsgeschwindigkeit von Vorhersagen und Vorhersagen Workloads, aber im Lieferumfang von Plattform- und bibliotheksunterstützung Anforderungen: nur Funktionen aus Revoscaler- und Revoscalepy C++-Implementierungen verfügen.

Native Bewertung erfordert, dass Sie bereits ein trainingsmodell verfügen. In SQL Server 2017-Windows oder Linux oder in Azure SQL-Datenbank können Sie aufrufen die PREDICT-Funktion in Transact-SQL zum Aufrufen native Bewertung für neue Daten, die Sie als Eingabeparameter bereitstellen. Die PREDICT-Funktion gibt die Ergebnisse über Dateneingaben zurück.

## <a name="how-native-scoring-works"></a>Wie systemeigene Bewertung funktioniert

Native Bewertung verwendet systemeigene C++-Bibliotheken von Microsoft, die ein bereits trainiertes Modell lesen kann zuvor in einem speziellen Binärformat gespeichert oder auf dem Datenträger als raw Byte-Stream gespeichert und Generieren von Bewertungen für neue Dateneingaben, die Sie bereitstellen. Da das Modell trainiert ist, kann gespeichert und veröffentlicht, es verwendet werden für die Bewertung, ohne den R oder Python-Interpreter aufrufen zu müssen. Daher wird der Mehraufwand für mehrere Prozess-Interaktionen reduziert, viel schneller Vorhersage Leistung in Produktionsszenarien Enterprise.

Klicken Sie zum Verwenden der nativen Bewertung, rufen Sie die VORHERSAGEN für T-SQL-Funktion, und übergeben Sie die folgenden erforderlichen Eingaben:

+ Ein kompatibles Modell basierend auf einen unterstützten Algorithmus.
+ Eingabedaten als SQL-Abfrage in der Regel definiert.

Die Funktion gibt die Vorhersagen für die Eingabedaten, sowie alle Spalten der Quelldaten, denen Sie durchlaufen möchten.

## <a name="prerequisites"></a>Erforderliche Komponenten

VORHERSAGEN für alle Editionen von SQL Server 2017-Datenbank-Engine verfügbar und standardmäßig, einschließlich SQL Server 2017 Machine Learning Services auf Windows, SQL Server 2017 (Windows), SQL Server 2017 (Linux) oder Azure SQL-Datenbank aktiviert ist. Sie müssen sich nicht zum Installieren von R, Python, oder zusätzliche Funktionen aktivieren.

+ Das Modell muss mithilfe einer der unterstützten im Voraus trainiert werden **Rx** Algorithmen, die unten aufgeführten.

+ Serialisiert das Modell, indem [RxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) für R und [Rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) für Python. Diese Serialisierungsfunktionen wurden optimiert, um die schnelle Bewertung zu unterstützen.

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>Unterstützte Algorithmen

+ die Revoscalepy-Modelle

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

Wenn Sie Modelle aus MicrosoftML oder Microsoftml verwenden möchten, verwenden Sie [echtzeitbewertung mit Sp_rxPredict](real-time-scoring.md).

Nicht unterstützte Modelltypen umfassen die folgenden Typen:

+ Modelle, die andere Transformationen enthält.
+ Modelle mit den `rxGlm` oder `rxNaiveBayes` Algorithmen in Revoscaler- oder Revoscalepy-Entsprechungen
+ PMML-Modelle
+ Mit anderen Bibliotheken Open Source- oder von Drittanbietern erstellte Modelle

## <a name="example-predict-t-sql"></a>Beispiel: VORHERSAGEN SIE (T-SQL)

In diesem Beispiel stellen Sie ein Modell erstellen, und rufen dann die echtzeitvorhersage-Funktion von T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Schritt 1: Bereiten Sie vor und Speichern des Modells

Führen Sie den folgenden Code zum Erstellen der Beispieldatenbank und die erforderlichen Tabellen.

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

Verwenden Sie die folgende Anweisung zum Auffüllen der Datentabelle mit Daten aus der **Iris** Dataset.

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

Der folgende Code erstellt ein Modell basierend auf den **Iris** Dataset und speichert es in der Tabelle, die mit dem Namen **Modelle**.

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
> Verwenden Sie die [RxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) Funktion von RevoScaleR, um das Modell zu speichern. Die R-Standardfunktion `serialize` Funktion kann nicht das erforderliche Format generiert werden.

Sie können eine Anweisung ähnlich der folgenden im Binärformat an das gespeicherte Modell ausführen:

```sql
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Schritt 2: Führen Sie VORHERSAGEN für das Modell

Die folgende einfache PREDICT-Anweisung ruft eine Klassifizierung ab, von der Entscheidung Tree-Modell unter Verwendung der **nativen Bewertung** Funktion. Es sagt die Iris-Arten basierend auf Attribute, die Sie bereitstellen, des kelchblatts sowie Länge und Breite.

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

Wenn Sie eine Fehlermeldung erhalten, Fehler"bei der Ausführung der PREDICT-Funktion. Modell ist beschädigt oder ungültig.", es in der Regel bedeutet, dass die Abfrage ein Modell zurückgegeben wurden. Überprüfen Sie, ob Sie den Modellnamen richtig eingegeben, oder die Modelle Tabelle leer ist.

> [!NOTE]
> Da die Spalten und Werte von zurückgegeben **PREDICT** je nach Modelltyp variieren kann, definieren Sie das Schema der zurückgegebenen Daten mithilfe einer **WITH** Klausel.

## <a name="next-steps"></a>Nächste Schritte

Eine vollständige Lösung, die enthält nativen Bewertung, finden Sie in diesen Beispielen aus dem SQL Server-Entwicklungsteam:

+ Bereitstellen Sie Ihres ML-Skripts: [Verwenden ein Python-Modell](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Bereitstellen Sie Ihres ML-Skripts: [Mithilfe eines R-Modells](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)