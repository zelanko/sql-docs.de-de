---
title: Echtzeitbewertung in SQL Server-Machine Learning | Microsoft-Dokumentation
description: Generieren von Vorhersagen mithilfe von Sp_rxPredict, Bewerten von von Dateneingaben für ein vorab trainiertes Modell in R auf SQL Server geschrieben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dce0928c0675172c503e6783aa25d6cbcaec9b5f
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713513"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>Echtzeitbewertung mit Sp_rxPredict in SQL Server-Machine learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Echtzeitbewertung verwendet die [Sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) gespeicherte Prozedur und die Funktionen der CLR-Erweiterung in SQL Server für hohe Leistung vorhersagen oder Bewertungen in Prognosen der arbeitsauslastungen. Echtzeitbewertung sprachagnostisch ist und ausgeführt wird und ohne Abhängigkeiten R- oder Python-Mal ausgeführt. Wenn ein Modell erstellt und trainiert mit von Microsoft-Funktionen und dann serialisiert, binäres Format kann im SQL Server, können Sie echtzeitbewertung um vorhergesagten Ergebnisse in neue Dateneingaben in SQL Server-Instanzen zu generieren, denen keine das R- oder Python-Add-On installiert.

## <a name="how-real-time-scoring-works"></a>Wie echtzeitbewertung funktioniert

Echtzeitbewertung wird in SQL Server 2017 und SQL Server 2016 auf unterstützt [Modelltypen unterstützt](#bkmk_py_supported_algos) für lineare und logistische Regression und Decision Tree Modellierung. Es verwendet die systemeigene C++-Bibliotheken zum Generieren von Bewertungen, die auf Grundlage der Benutzereingabe bereitgestellt, um ein Machine learning-Modell in einem speziellen binären Format gespeichert.

Da ein trainiertes Modell verwendet werden kann, für die Bewertung, ohne eine externe Sprachlaufzeit aufrufen zu müssen, wird der Aufwand von mehreren Prozessen reduziert. Dadurch wird eine schnellere vorhersageleistung für die Produktion, die Bewertung von Szenarien unterstützt. Da die Daten nicht SQL Server verlässt, können Ergebnisse generiert und in eine neue Tabelle ohne jegliche Übersetzung Daten zwischen R und SQL eingefügt werden.

Echtzeitbewertung ist ein mehrstufiger Prozess:

1. Die gespeicherte Prozedur, die Bewertung muss auf einer Basis pro Datenbank aktiviert sein.
2. Sie laden das vortrainierte Modell im Binärformat.
3. Sie bieten die neue Eingabedaten werden bewertet, tabellarische oder einzelne Zeilen als Eingabe für das Modell.
4. Rufen Sie zum Generieren von Bewertungen der [Sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) gespeicherte Prozedur.

> [!TIP]
> Ein Beispiel für die echtzeitbewertung in Aktion, finden Sie unter [End-to-End Loan Kreditabschreibungen Vorhersage erstellt mithilfe von Azure HDInsight Spark-Cluster und SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="prerequisites"></a>Erforderliche Komponenten

+ [Aktivieren der SQL Server-CLR-Integration](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ [Aktivieren Sie die echtzeitbewertung](#bkmk_enableRtScoring).

+ Das Modell muss mithilfe einer der unterstützten im Voraus trainiert werden **Rx** Algorithmen. Für R, echtzeitbewertung mit `sp_rxPredict` arbeitet mit [RevoScaleR und MicrosoftML unterstützt Algorithmen](#bkmk_rt_supported_algos). Für Python finden Sie unter [Revoscalepy und Microsoftml unterstützt Algorithmen](#bkmk_py_supported_algos)

+ Serialisiert das Modell, indem [RxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) für R und [Rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) für Python. Diese Serialisierungsfunktionen wurden optimiert, um die schnelle Bewertung zu unterstützen.

+ Speichern Sie das Modell, in der Datenbank-Engine-Instanz, die von der Sie sie aufrufen möchten. Diese Instanz ist nicht erforderlich, um die R oder Python-Runtime-Erweiterung zu erhalten.

> [!Note]
> Echtzeitbewertung ist derzeit für schnelle Vorhersagen für kleinere Datasets, die von ein paar Zeilen bis hin zu mehreren hunderttausend Zeilen optimiert. Für große Datasets, mit [RxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) möglicherweise schneller.

<a name="bkmk_py_supported_algos"></a>

## <a name="supported-algorithms"></a>Unterstützte Algorithmen

### <a name="python-algorithms-using-real-time-scoring"></a>Python-Algorithmen, die mithilfe der echtzeitbewertung

+ die Revoscalepy-Modelle

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) \*
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) \*
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) \*
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) \*
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) \*
  
  Modelle mit markierten \* unterstützen auch die nativen Bewertung, mit der PREDICT-Funktion.

+ Microsoftml-Modelle

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_net](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

+ Transformationen vom microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)


<a name="bkmk_rt_supported_algos"></a>

### <a name="r-algorithms-using-real-time-scoring"></a>R-Algorithmen, die mithilfe von echtzeitbewertung

+ RevoScaleR-Modelle

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) \*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  Modelle mit markierten \* unterstützen auch die nativen Bewertung, mit der PREDICT-Funktion.

+ MicrosoftML-Modelle

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ Transformationen vom MicrosoftML

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Nicht unterstützte Modelltypen

Echtzeitbewertung wird einen Interpreter nicht verwendet werden. aus diesem Grund wird keine Funktionen, die möglicherweise einen Interpreter erfordern, während der Bewertung Schritt nicht unterstützt.  Diese können Folgendes umfassen:

  + Modelle mit den `rxGlm` oder `rxNaiveBayes` Algorithmen werden nicht unterstützt.

  + Modelle mit einer Transformationsfunktion oder eine Formel, die eine Transformation, z. B. enthält <code>A ~ log(B)</code> werden in echtzeitbewertung nicht unterstützt. Um ein Modell dieses Typs zu verwenden, empfehlen wir, dass Sie die Transformation für Eingabedaten vor der Übergabe an die echtzeitbewertung ausführen.


## <a name="example-sprxpredict"></a>Beispiel: Sp_rxPredict

In diesem Abschnitt wird beschrieben, die erforderlichen Schritte zum Einrichten von **in Echtzeit** Vorhersage und bietet ein Beispiel für das Aufrufen der Funktion von T-SQL in R.

<a name ="bkmk_enableRtScoring"></a> 

### <a name="step-1-enable-the-real-time-scoring-procedure"></a>Schritt 1: Aktivieren Sie das Real-Time scoring Verfahren

Sie müssen diese Funktion für jede Datenbank aktivieren, die Sie für die Bewertung verwenden möchten. Der Server-Administrator sollten die Befehlszeile-Hilfsprogramm RegisterRExt.exe, ausführen und die in das RevoScaleR-Paket enthalten ist.

> [!NOTE]
> In der Reihenfolge für die echtzeitbewertung funktioniert muss SQL CLR-Funktionalität in der Instanz aktiviert werden; Darüber hinaus muss die Datenbank als vertrauenswürdig gekennzeichnet werden. Wenn Sie das Skript ausführen, werden diese Aktionen für Sie durchgeführt. Jedoch sollten Sie Auswirkungen auf die zusätzliche Sicherheit ein, bevor Sie dies tun!

1. Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und navigieren Sie zu dem Ordner, in denen RegisterRExt.exe befindet. Der folgende Pfad kann in einer Standardinstallation verwendet werden:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Führen Sie den folgenden Befehl aus, und Ersetzen Sie dabei den Namen Ihrer Instanz und die Zieldatenbank, in dem Sie die erweiterten gespeicherten Prozeduren aktivieren möchten:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Geben Sie z. B. zum Hinzufügen der erweiterten gespeicherten Prozedur mit der Datenbank CLRPredict auf der Standardinstanz:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Der Instanzname ist optional, wenn die Datenbank für die Standardinstanz ist. Wenn Sie eine benannte Instanz verwenden, müssen Sie den Namen der Instanz angeben.

3. RegisterRExt.exe erstellt die folgenden Objekte:

    + Vertrauenswürdige Assemblys
    + Die gespeicherte Prozedur `sp_rxPredict`
    + Eine neue Datenbankrolle `rxpredict_users`. Der Datenbankadministrator kann diese Rolle verwenden, Benutzern Berechtigungen gewähren, die die Funktionalität des Real-Time scoring verwenden.

4. Fügen Sie alle Benutzer, die auszuführenden `sp_rxPredict` der neuen Rolle.

> [!NOTE]
> 
> Sind in SQL Server 2017 zusätzliche Sicherheitsmaßnahmen, um Probleme mit der CLR-Integration zu verhindern. Diese Measures geben zusätzliche Einschränkungen für die Verwendung dieser gespeicherten Prozedur ebenfalls. 

### <a name="step-2-prepare-and-save-the-model"></a>Schritt 2: Bereiten Sie vor und Speichern des Modells

Das Binärformat sp erforderlichen\_RxPredict ist, entspricht das Datendateiformat dem Format erforderlich, um der PREDICT-Funktion verwenden. Fügen Sie daher in Ihrem R-Code einen Aufruf [RxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), und geben Sie unbedingt `realtimeScoringOnly = TRUE`, wie in diesem Beispiel:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Schritt 3: Rufen Sie sp_rxPredict

Rufen Sie sp\_RxPredict wie würde alle anderen gespeicherten Prozedur. In der aktuellen Version, die gespeicherte Prozedur akzeptiert nur zwei Parameter:  _\@Modell_ für das Modell im binären Format und  _\@InputData_ als für die Daten in die Bewertung mit definiert eine gültige SQL-Abfrage.

Da das binäre Format, die von der PREDICT-Funktion verwendet wird übereinstimmt, können Sie in der Tabelle Modelle und Daten aus dem vorherigen Beispiel.

```SQL
DECLARE @irismodel varbinary(max)
SELECT @irismodel = [native_model_object] from [ml_models]
WHERE model_name = 'iris.dtree' 
AND model_version = 'v1''

EXEC sp_rxPredict
@model = @irismodel,
@inputData = N'SELECT * FROM iris_rx_data'
```

> [!NOTE]
> 
> Der Aufruf von sp\_RxPredict schlägt fehl, wenn die Eingabedaten für die Bewertung keine Spalten enthalten sind, die die Anforderungen des Modells entsprechen. Derzeit werden nur die folgenden .NET Datentypen unterstützt: double, Float, Short, Ushort, long, Ulong und Zeichenfolge.
> 
> Aus diesem Grund müssen Sie nicht unterstützte Typen in Ihre Daten herausfiltern, bevor Sie ihn für die echtzeitbewertung verwenden.
> 
> Weitere Informationen zu den entsprechenden SQL-Datentypen, finden Sie unter [SQL-CLR-Typzuordnung](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) oder [Zuordnen von CLR-Parameterdaten](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Deaktivieren Sie die echtzeitbewertung

Um in Echtzeit Bewertung Funktionalität deaktivieren, öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und führen Sie den folgenden Befehl: `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="next-steps"></a>Nächste Schritte

Ein Beispiel wie RxPredict für die Bewertung verwendet werden kann, finden Sie unter [End-to-End Loan Kreditabschreibungen Vorhersage erstellt mithilfe von Azure HDInsight Spark-Cluster und SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/).

Weitere Hintergrundinformationen zur Bewertung in SQL Server zu erhalten, finden Sie unter [Gewusst wie: Generieren von Vorhersagen in SQL Server-Machine Learning](r/how-to-do-realtime-scoring.md).
