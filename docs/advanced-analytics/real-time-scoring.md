---
title: Echtzeitbewertung mithilfe der gespeicherten Prozedur sp_rxPredict
description: Generieren von Vorhersagen mithilfe von sp_rxPredict, bewerten von Dateneingaben anhand eines vorab trainierten Modells, das in R auf SQL Server geschrieben ist.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/26/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 26701ac6e538d195a5a85ad66af9578848889d23
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715647"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>Echtzeitbewertung mit sp_rxPredict in SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Bei der Echtzeitbewertung werden die gespeicherten System Prozeduren [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) und die CLR-Erweiterungsfunktionen in SQL Server für leistungsstarke Vorhersagen oder Ergebnisse bei der Vorhersage von Arbeits Auslastungen verwendet. Die Echtzeitbewertung ist sprach agnostisch und wird ohne Abhängigkeiten von R-oder python-Laufzeiten ausgeführt. Wenn Sie ein Modell verwenden, das mit Microsoft Functions erstellt und trainiert wurde, und anschließend in SQL Server in ein binäres Format serialisiert wurden, können Sie die Echtzeitbewertung verwenden, um vorhergesagte Ergebnisse für neue Dateneingaben auf SQL Server Instanzen zu generieren, die das R-oder python-Add-on nicht haben. lierter.

## <a name="how-real-time-scoring-works"></a>Funktionsweise der Echtzeitbewertung

Die Echtzeitbewertung wird für bestimmte Modelltypen unterstützt, die auf revoscaler-oder microsoftml-Funktionen, wie [rxlinmod (revoscaler)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)[rxneural net (microsoftml)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet), basieren. Native C++ Bibliotheken werden verwendet, um Bewertungen basierend auf Benutzereingaben zu generieren, die für ein in einem speziellen Binärformat gespeichertes Machine Learning-Modell bereitgestellt werden.

Da ein trainiertes Modell zur Bewertung verwendet werden kann, ohne eine externe Sprachlaufzeit aufrufen zu müssen, verringert sich der Aufwand mehrerer Prozesse. Dies unterstützt eine wesentlich schnellere Vorhersage Leistung für Produktions Bewertungs Szenarien. Da die Daten niemals SQL Server bleiben, können Ergebnisse generiert und in eine neue Tabelle eingefügt werden, ohne dass eine Daten Übersetzung zwischen R und SQL durchgeführt werden muss.

Die Echtzeitbewertung ist ein mehrstufiger Prozess:

1. Die gespeicherte Prozedur, die die Bewertung durchführt, muss auf Daten Bank Basis aktiviert werden.
2. Das Vortrainierte Modell wird im Binärformat geladen.
3. Sie stellen neue Eingabedaten, die bewertet werden sollen, entweder tabellarische oder einzelne Zeilen, als Eingabe für das Modell bereit.
4. Um Ergebnisse zu generieren, rufen Sie die gespeicherte Prozedur [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) auf.

## <a name="prerequisites"></a>Vorraussetzungen

+ [Aktivieren Sie die SQL Server CLR-Integration](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ [Aktivieren Sie die Echtzeitbewertung](#bkmk_enableRtScoring).

+ Das Modell muss im Voraus mit einem der unterstützten **RX** -Algorithmen trainiert werden. Für R funktioniert die Echtzeitbewertung mit `sp_rxPredict` mit [revoscaler-und microsoftml-Algorithmen](#bkmk_rt_supported_algos). Informationen zu python finden Sie [unter Unterstützte Algorithmen (revoscalepy und microsoftml](#bkmk_py_supported_algos) ).

+ Serialisieren Sie das Modell mithilfe von [rxserialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) für R und [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) für python. Diese Serialisierungsfunktionen wurden optimiert, um eine schnelle Bewertung zu unterstützen.

+ Speichern Sie das Modell in der Datenbank-Engine-Instanz, von der es aufgerufen werden soll. Diese Instanz ist nicht erforderlich, um die R-oder python-Lauf Zeit Erweiterung zu haben.

> [!Note]
> Die Echtzeitbewertung ist zurzeit für schnelle Vorhersagen für kleinere Datasets optimiert und reicht von einigen wenigen Zeilen bis hin zu Hunderttausenden von Zeilen. Bei großen Datasets kann die Verwendung von [rxvorhersage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) beschleunigt werden.

<a name="bkmk_py_supported_algos"></a>

## <a name="supported-algorithms"></a>Unterstützte Algorithmen

### <a name="python-algorithms-using-real-time-scoring"></a>Python-Algorithmen mit Echtzeitbewertung

+ revoscalepy-Modelle

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) \*
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) \*
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)\*
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) \*
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)\*
  
  Mit \* markierte Modelle unterstützen auch die native Bewertung mit der Vorhersagefunktion.

+ microsoftml-Modelle

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_net](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

+ Von microsoftml bereitgestellte Transformationen

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)


<a name="bkmk_rt_supported_algos"></a>

### <a name="r-algorithms-using-real-time-scoring"></a>R-Algorithmen mit Echtzeitbewertung

+ Revoscaler-Modelle

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxbtrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)\*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdforest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)\*
  
  Mit \* markierte Modelle unterstützen auch die native Bewertung mit der Vorhersagefunktion.

+ Microsoftml-Modelle

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ Von microsoftml bereitgestellte Transformationen

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Nicht unterstützte Modelltypen

Die Echtzeitbewertung verwendet keinen Interpreter. Daher wird jede Funktionalität, die möglicherweise einen Interpreter erfordert, während des Bewertungs Schritts nicht unterstützt.  Diese können Folgendes umfassen:

  + Modelle, die `rxGlm` die `rxNaiveBayes` Algorithmen oder verwenden, werden nicht unterstützt.

  + Modelle, <code>A ~ log(B)</code> die eine Transformations Funktion oder-Formel mit einer Transformation enthalten, wie z. b., werden bei der Echtzeitbewertung nicht unterstützt. Wenn Sie ein Modell dieses Typs verwenden möchten, empfiehlt es sich, die Transformation für Eingabedaten durchzuführen, bevor die Daten an die Echtzeitbewertung übergeben werden.


## <a name="example-sprxpredict"></a>Beispiel: sp_rxPredict

In diesem Abschnitt werden die Schritte beschrieben, die zum Einrichten der **Echt Zeit** Vorhersage erforderlich sind, und es wird ein Beispiel für R zum Aufruf der-Funktion von T-SQL bereitstellt.

<a name ="bkmk_enableRtScoring"></a> 

### <a name="step-1-enable-the-real-time-scoring-procedure"></a>Schritt 1: Aktivieren der Echt Zeit Bewertungs Prozedur

Sie müssen diese Funktion für jede Datenbank aktivieren, die Sie für die Bewertung verwenden möchten. Der Server Administrator sollte das Befehlszeilen-Hilfsprogramm registerrext. exe ausführen, das im revoscaler-Paket enthalten ist.

> [!NOTE]
> Damit die Echtzeitbewertung funktioniert, muss die SQL CLR-Funktionalität in der Instanz aktiviert werden. Außerdem muss die Datenbank als vertrauenswürdig gekennzeichnet sein. Wenn Sie das Skript ausführen, werden diese Aktionen für Sie ausgeführt. Berücksichtigen Sie jedoch die zusätzlichen Sicherheitsrisiken, bevor Sie dies tun!

1. Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und navigieren Sie zu dem Ordner, in dem sich die Datei registerrext. exe befindet. Der folgende Pfad kann in einer Standardinstallation verwendet werden:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Führen Sie den folgenden Befehl aus, und ersetzen Sie dabei den Namen der-Instanz und der Zieldatenbank, in der Sie die erweiterten gespeicherten Prozeduren aktivieren möchten:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Geben Sie beispielsweise Folgendes ein, um die erweiterte gespeicherte Prozedur der clrvorhersage-Datenbank auf der Standard Instanz hinzuzufügen:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Der Instanzname ist optional, wenn sich die Datenbank auf der Standard Instanz befindet. Wenn Sie eine benannte Instanz verwenden, müssen Sie den Instanznamen angeben.

3. Registerrext. exe erstellt die folgenden Objekte:

    + Vertrauenswürdige Assembly
    + Die gespeicherte Prozedur`sp_rxPredict`
    + Eine neue Daten Bank Rolle `rxpredict_users`,. Der Datenbankadministrator kann diese Rolle zum Erteilen von Berechtigungen für Benutzer verwenden, die die Echt Zeit Bewertungsfunktion verwenden.

4. Fügen Sie alle Benutzer hinzu, die `sp_rxPredict` die neue Rolle ausführen müssen.

> [!NOTE]
> 
> In SQL Server 2017 sind zusätzliche Sicherheitsmaßnahmen vorhanden, um Probleme bei der CLR-Integration zu vermeiden. Diese Measures erzwingen auch zusätzliche Einschränkungen bei der Verwendung dieser gespeicherten Prozedur. 

### <a name="step-2-prepare-and-save-the-model"></a>Schritt 2: Vorbereiten und Speichern des Modells

Das für SP\_rxvorhersage erforderliche Binärformat ist identisch mit dem Format, das für die Verwendung der Vorhersagefunktion erforderlich ist. Fügen Sie daher in Ihrem R-Code einen [rxserializemodel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)-Befehl ein, und stellen Sie sicher `realtimeScoringOnly = TRUE`, wie in diesem Beispiel:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Schritt 3: Sp_rxPredict anrufen

Sie nennen SP\_rxvorhersage wie jede andere gespeicherte Prozedur. In der aktuellen Version benötigt die gespeicherte Prozedur nur zwei Parameter:  _\@Model_ für das Modell im Binärformat und  _\@inputData_ für die Daten, die in der Bewertung verwendet werden sollen, die als gültige SQL-Abfrage definiert sind.

Da das binäre Format das gleiche ist, das von der Vorhersagefunktion verwendet wird, können Sie die Modelle und die Datentabelle aus dem vorherigen Beispiel verwenden.

```sql
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
> Der Aufrufe von SP\_rxvorhersage schlägt fehl, wenn die Eingabedaten für die Bewertung keine Spalten enthalten, die den Anforderungen des Modells entsprechen. Derzeit werden nur die folgenden .NET-Datentypen unterstützt: Double, float, Short, ushort, Long, ULONG und String.
> 
> Daher müssen Sie möglicherweise nicht unterstützte Typen in ihren Eingabedaten herausfiltern, bevor Sie Sie für die Echtzeitbewertung verwenden.
> 
> Weitere Informationen zu entsprechenden SQL-Typen finden Sie unter [SQL-CLR-Typzuordnung](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) oder [Mapping von CLR-Parameter Daten](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Echtzeitbewertung deaktivieren

Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und führen Sie den folgenden Befehl aus, um Echt Zeit Bewertungs Funktionen zu deaktivieren:`RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="next-steps"></a>Nächste Schritte

Weitere Hintergrundinformationen zur Bewertung in SQL Server finden [Sie unter Generieren von Vorhersagen in SQL Server Machine Learning](r/how-to-do-realtime-scoring.md).
