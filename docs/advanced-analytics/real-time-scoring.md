---
title: Echtzeitbewertung in SQL Server-Machine Learning | Microsoft-Dokumentation
description: Generieren von Vorhersagen mithilfe von Sp_rxPredict, Bewerten von Dta Eingaben für ein vorab trainiertes Modell in R auf SQL Server geschrieben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d5a3d0318f925918ef98ae18744e4287d6b81108
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2018
ms.locfileid: "40392121"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>Echtzeitbewertung mit Sp_rxPredict in SQL Server-Machine learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Bewertung in nahezu Echtzeit funktioniert für relationale SQL Server-Daten mithilfe von Machine Learning in r geschriebenen-Modellen 

> [!Note]
> Native Bewertung ist eine besondere Implementierung von echtzeitbewertung, die die systemeigene T-SQL PREDICT-Funktion für die sehr schnelle Bewertung verwendet. Weitere Informationen und Verfügbarkeit zu erzielen, finden Sie unter [nativen Bewertung](sql-native-scoring.md).

## <a name="how-real-time-scoring-works"></a>Wie echtzeitbewertung funktioniert

Echtzeitbewertung in SQL Server 2016 und SQL Server 2017 unterstützt wird, für bestimmte Modelltypen, z. B. anhand von RevoScaleR oder MicrosoftML Functions [RxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) oder [RxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Es verwendet die systemeigene C++-Bibliotheken zum Generieren von Bewertungen, die auf Grundlage der Benutzereingabe bereitgestellt, um ein Machine learning-Modell in einem speziellen binären Format gespeichert.

Da ein trainiertes Modell verwendet werden kann, für die Bewertung, ohne eine externe Sprachlaufzeit aufrufen zu müssen, wird der Aufwand von mehreren Prozessen reduziert. Dadurch wird eine schnellere vorhersageleistung für die Produktion, die Bewertung von Szenarien unterstützt. Da die Daten nicht SQL Server verlässt, können Ergebnisse generiert und in eine neue Tabelle ohne jegliche Übersetzung Daten zwischen R und SQL eingefügt werden.

Echtzeitbewertung ist ein mehrstufiger Prozess:

1. Die gespeicherte Prozedur, die Bewertung muss auf einer Basis pro Datenbank aktiviert sein.
2. Sie laden das vortrainierte Modell im Binärformat.
3. Sie geben neue Eingabedaten, tabellarische oder einzelne Zeilen als Eingabe für das Modell.
4. Generieren von Bewertungen, rufen Sie die Sp_rxPredict gespeicherte Prozedur.

## <a name="get-started"></a>Erste Schritte

Codebeispiele und Anleitungen finden Sie unter [wie nativen Bewertung oder echtzeitbewertung](r/how-to-do-realtime-scoring.md).

Ein Beispiel wie RxPredict für die Bewertung verwendet werden kann, finden Sie unter [End-to-End Loan Kreditabschreibungen Vorhersage erstellt mithilfe von Azure HDInsight Spark-Cluster und SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> Wenn Sie ausschließlich in R-Code arbeiten, können Sie auch die [RxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) Funktion für die schnelle Bewertung.

## <a name="requirements"></a>Anforderungen

Echtzeitbewertung wird auf diesen Plattformen unterstützt:

+ SQL Server 2017-Machine Learning-Dienste
+ SQL Server R Services 2016 mit einem Upgrade von R-Komponenten auf 9.1.0 oder höher

Auf SQL Server müssen Sie die Bewertung in Echtzeit-Funktion im Voraus zum Hinzufügen der CLR-basierten Bibliotheken zu SQL Server aktivieren.

Informationen zur echtzeitbewertung in einer verteilten Umgebung, die auf Basis von Microsoft R Server finden Sie in der [PublishService](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice) Funktion zur Verfügung steht, in der [MrsDeploy-Paket](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package), welche unterstützt Veröffentlichen von Modellen für die echtzeitbewertung als neuer eines Webdiensts, der auf R Server ausgeführt wird.

### <a name="restrictions"></a>Restrictions

+ Das Modell muss mithilfe einer der unterstützten im Voraus trainiert werden **Rx** Algorithmen. Weitere Informationen finden Sie unter [unterstützt Algorithmen](#bkmk_rt_supported_algos). Echtzeitbewertung mit `sp_rxPredict` unterstützt sowohl "RevoScaleR" und "MicrosoftML-Algorithmen.

+ Das Modell muss gespeichert werden, mit den neuen Serialisierungsfunktionen: [RxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) für R und [Rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) für Python. Diese Serialisierungsfunktionen wurden optimiert, um die schnelle Bewertung zu unterstützen.

+ Echtzeitbewertung wird einen Interpreter nicht verwendet werden. aus diesem Grund wird keine Funktionen, die möglicherweise einen Interpreter erfordern, während der Bewertung Schritt nicht unterstützt.  Diese können Folgendes umfassen:

  + Modelle mit den `rxGlm` oder `rxNaiveBayes` Algorithmen werden derzeit nicht unterstützt.

  + RevoScaleR-Modelle, verwenden eine R-Transformation-Funktion oder eine Formel, die eine Transformation, z. B. enthält <code>A ~ log(B)</code> werden in echtzeitbewertung nicht unterstützt. Um ein Modell dieses Typs verwenden zu können, empfehlen wir, dass Sie auf die Transformation für das Ausführen der Eingabe von Daten vor der Übergabe an die echtzeitbewertung.

+ Echtzeitbewertung ist derzeit für schnelle Vorhersagen für kleinere Datasets, die von ein paar Zeilen bis hin zu mehreren hunderttausend Zeilen optimiert. Für große Datasets, mit [RxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) möglicherweise schneller.

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-real-time-scoring"></a><a name="bkmk_rt_supported_algos">Algorithmen, die echtzeitbewertung unterstützen

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

Echtzeitbewertung wird für Transformationen von R als die aufgeführten explizit im vorherigen Abschnitt nicht unterstützt. 

Für Entwickler daran gewöhnt, mit der Arbeit mit RevoScaleR und anderen Bibliotheken von Microsoft R-spezifischen nicht unterstützte Funktionen enthalten `rxGlm` oder `rxNaiveBayes` Algorithmen in RevoScaleR PMML-Modelle und andere Modelle erstellt haben, verwenden von anderen R-Bibliotheken aus CRAN oder andere Repositorys aus.

### <a name="known-issues"></a>Bekannte Probleme

+ `sp_rxPredict` Gibt eine fehlerhafte Nachricht zurück, wenn ein NULL-Wert wie das Modell übergeben wird: "System.Data.SqlTypes.SqlNullValueException:Data in Null".

## <a name="next-steps"></a>Nächste Schritte

[Wie Sie echtzeitbewertung](r/how-to-do-realtime-scoring.md)
