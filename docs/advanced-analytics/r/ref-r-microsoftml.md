---
title: 'MicrosoftML R - Funktionsbibliothek: SQL Server Machine Learning Services'
description: Einführung in MicrosoftML Funktionsbibliothek in SQL Server 2016 R Services und SQL Server 2017 Machine Learning Services mit R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e3dc94026f90ef769abb3889a716b5dadb317c4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962503"
---
# <a name="microsoftml-r-library-in-sql-server"></a>MicrosoftML (R-Bibliothek in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**MicrosoftML** ist eine R-Funktion-Bibliothek von Microsoft High-Performance-Machine Learning-Algorithmen bereitstellt. Es enthält Funktionen für Training und Transformationen, Bewertung, Text- und Image-Analyse und featureextraktion für das Ableiten von Werten aus vorhandenen Daten.

Die Machine learning-APIs, die von Microsoft für interne Machine learning-Anwendungen entwickelt wurden, und wurden die optimierten im Laufe der Jahre zur Unterstützung von hoher Leistung für big Data mit multicore-Verarbeitung und schnelles streaming von Daten. MicrosoftML hinaus zahlreiche Transformationen für Text- und Image-Verarbeitung.

## <a name="full-reference-documentation"></a>Vollständige Referenz-Dokumentation

Die **MicrosoftML** Bibliothek wird in mehreren Microsoft-Produkte verteilt, aber wird, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die Funktionen identisch sind, [Dokumentation für die einzelnen RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) in nur einem Ort unter veröffentlicht wird die [R Verweis](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server. Sollten Sie jede Produkt-spezifische Verhalten vorhanden ist, wird Diskrepanzen auf der Hilfeseite für die Funktion angegeben.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Die **MicrosoftML** Bibliothek basierend auf R 3.4.3 und verfügbar ist, nur, wenn Sie eine der folgenden Microsoft-Produkten oder Downloads installieren:

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R client](set-up-a-data-science-client.md)

> [!NOTE]
> Releaseversionen der Vollversion des Produkts sind Windows ausschließlich ab SQL Server 2017. Linux-Unterstützung für **MicrosoftML** ist neu in [Vorschau von SQL Server-2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Paketabhängigkeiten

Algorithmen in **MicrosoftML** hängen [RevoScaleR](ref-r-revoscaler.md) für:

+ Datenquellenobjekte. Daten von genutzt **MicrosoftML** Funktionen werden mit erstellt **RevoScaleR** Funktionen.
+ Remote computing (wechselnden funktionsausführung zu einer Remoteinstanz von SQL Server). Die **RevoScaleR** -Bibliothek bietet Funktionen für das Erstellen und aktivieren eine-Kontext für SQLServer Compute.

In den meisten Fällen werden Laden Sie die Pakete zusammen bei jeder Verwendung **MicrosoftML**.

## <a name="functions-by-category"></a>Funktionen, die nach Kategorie

Dieser Abschnitt listet die Funktionen nach Kategorie, erhalten Sie einen Überblick darüber, wie jeweils verwendet wird. Sie können auch die [Inhaltsverzeichnis](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) Sie Funktionen in alphabetischer Reihenfolge suchen.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>1 – Machine Learning-Algorithmen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Eine Implementierung von FastRank, eine effiziente Implementierung des MART-Gradient-boosting-Algorithmus.  |
|[rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Ein zufälliger Gesamtstruktur und die Quantile Regression Gesamtstruktur Implementierung mit [RxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Logistische Regression über L-BFGS.  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Einklassiges Support Vector Computer.  
|[rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Binärdatei, mit mehreren Klassen und Regression neurales Netz.  |
|[rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Stochastischen dual-Koordinate Versalhöhe Optimierung für lineare binäre Klassifizierung und Regression. |
|[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | Trainiert eine Anzahl von Modellen, die von verschiedenen Arten, um besser vorhersagbare Leistung zu erhalten, als aus einem einzelnen Modell abgerufen werden konnte.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2-Transformationsfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | Transformation, die eine einzelne Spalte mit Vektor-Wert aus mehreren Spalten zu erstellen.  |
|[categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | Indikator Vektor Wörterbuch mit kategorischen Transformation zu erstellen.  |
|[categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | Konvertiert die kategorischen Wert in ein indikatorarray durch Ausführen einer Hashfunktion. |
|[featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | Erstellt eine Sammlung der Anzahl der Sequenzen von aufeinander folgenden Wörtern, die n-gramme, aus einem angegebenen Textkorpus aufgerufen. Es bietet sprachenerkennung, Tokenisierung, Stoppwörter entfernen, Text-Normalisierung und Generieren von Funktionen.  |
|[getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | Natürlicher Sprachtext bewertet, und erstellt eine Spalte, die Wahrscheinlichkeiten enthält die stimmungen in den Text nicht sicher sind.|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | ermöglicht das Festlegen von Argumenten für die merkmalsextraktion Count based und Hash-basierte.|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | Wählt einen Satz von Spalten erneut trainieren möchten, löschen alle anderen aus. |
|[selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | Wählt Features aus der angegebenen Variablen mithilfe eines angegebenen Modus.|
|[loadImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | Lädt Daten von Bildern.|
|[resizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | Ändert die Größe ein Bild, das einer angegebenen Dimension, die mit einer angegebenen Methode für die Größenänderung von Fenstern annimmt.|
|[extractPixels](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | Extrahiert die Pixelwerten aus einem Bild.|
|[featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | Featurizes eines Abbilds mithilfe von ein vorab trainiertes deep neural Networks-Modell.|


## <a name="3-scoring-and-training-functions"></a>3-Bewertung und Training-Funktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | Führt die bewertungs-Bibliothek an, entweder über SQL Server, mit der gespeicherten Prozedur, oder über R-Code aktivieren die echtzeitbewertung und ermöglicht damit deutlich schneller vorhersageleistung.|
|[rxFeaturize](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Transformiert die Daten aus einem Eingabedataset auf einen Ausgabe-DataSet.|
|[mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Enthält eine Zusammenfassung der Microsoft R Machine Learning-Modell.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4-Loss-Funktionen für Klassifizierung und regression

| Funktionsname | Beschreibung |
|---------------|-------------|
|[expLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für verlustfunktion exponentiellen Klassifizierung. | 
|[logLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für die Log-Verlust Klassifizierungsfunktion.  |
|[hingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für Hinge-Klassifizierungsfunktion verloren gehen. | 
|[smoothHingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für smooth Hinge-Klassifizierungsfunktion verloren gehen.  |
| [poissonLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für Poisson Regression verlustfunktion. | 
|[squaredLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für den quadrierten Verlust regressionsfunktion.   |   

## <a name="5-feature-selection-functions"></a>5-Feature-Selection-Funktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[minCount](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | Spezifikation für die Funktionsauswahl in seitenanzahlmodus, den. |
|[mutualInformation](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | Spezifikation für die Funktionsauswahl im Modus für gegenseitige Information. |

## <a name="6-ensemble-modeling-functions"></a>6-Ensemble-Modellierungsfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[fastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | Erstellt eine Liste mit den Funktionsnamen und Argumenten zum Trainieren eines Modells schnell Struktur mit [RxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Erstellt eine Liste mit den Funktionsnamen und Argumenten zum Trainieren eines Modells schneller Forest mit [RxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | Erstellt eine Liste mit den Funktionsnamen und Argumenten zum Trainieren eines Modells schnell Linear, mit [RxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[logisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Erstellt eine Liste mit den Funktionsnamen und Argumenten zum Trainieren eines logistischen Regressionsmodells mit [RxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[oneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Erstellt eine Liste mit den Funktionsnamen und Argumenten zum Trainieren eines Modells OneClassSvm mit [RxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>7-neuronalen Netzwerke-Funktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[Abfrageoptimierer](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | Gibt die Algorithmen für die [RxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) Machine Learning-Algorithmus.|


## <a name="8-package-state-functions"></a>Status des 8 Funktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxHashEnv](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Eine Umgebungsobjekt, das zum Speichern von Paket Zustand verwendet. |


## <a name="how-to-use-microsoftml"></a>Gewusst wie: Verwenden des MicrosoftML

Funktionen in **MicrosoftML** in R-Code gekapselt, die in gespeicherten Prozeduren können aufgerufen werden. Die meisten Entwickler erstellen **MicrosoftML** Lösungen lokal, und migrieren Sie dann die fertig gestellten R-Code zu gespeicherten Prozeduren als eine Übung für die Bereitstellung.

Die **MicrosoftML** -Paket für R installierten "Out-of-the-Box" in SQL Server 2017 ist. Es ist auch für die Verwendung mit SQL Server 2016 verfügbar, wenn Sie die R-Komponenten für die Instanz aktualisieren: [Aktualisieren einer Instanz von SQL Server mithilfe der Bindung](../install/upgrade-r-and-python.md)

Das Paket ist nicht standardmäßig geladen. Als erstes laden die **MicrosoftML** -Paket, und Laden Sie **RevoScaleR** remotecomputekontexte oder verbundene Konnektivitäts- oder Data-Source-Objekte verwenden werden sollen. Klicken Sie dann, verweisen auf den einzelnen Funktionen, die Sie benötigen.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>Siehe auch

+ [R-tutorials](../tutorials/sql-server-r-tutorials.md)
+ [Informationen Sie zur Verwendung von berechneten Kontexten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R für SQL-Entwickler: Trainieren und zu operationalisieren eines Modells](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Microsoft-Produkt-Beispielen auf GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [R-Verweis (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 