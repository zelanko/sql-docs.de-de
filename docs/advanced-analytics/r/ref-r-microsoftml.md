---
title: MicrosoftML-Funktionsbibliothek für R
description: Einführung in die MicrosoftML-Funktionsbibliothek in SQL Server 2016 R Services und SQL Server-Machine Learning Services mit R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 450091bba39cf10e551b8da5e62993ca676c64af
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "73707916"
---
# <a name="microsoftml-r-library-in-sql-server"></a>MicrosoftML (R-Bibliothek in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**MicrosoftML** ist eine R-Funktionsbibliothek von Microsoft, die leistungsstarke Machine Learning-Algorithmen bereitstellt. Sie enthält Funktionen für Training, Transformationen, Bewertung, Text- und Bildanalyse sowie Featureextraktion zum Ableiten von Werten aus vorhandenen Daten.

Die Machine Learning-APIs wurden von Microsoft für interne Machine Learning-Anwendungen entwickelt und im Laufe der Jahre so optimiert, dass sie bei Big Data eine hohe Leistung durch Verarbeitung auf Mehrkernprozessoren und schnelles Datenstreaming unterstützen. MicrosoftML enthält auch zahlreiche Transformationen für die Text- und Bildverarbeitung.

## <a name="full-reference-documentation"></a>Vollständige Referenzdokumentation

Die **MicrosoftML**-Bibliothek wird in mehreren Microsoft-Produkten bereitgestellt. Die Verwendung ist jedoch immer identisch, unabhängig davon, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt abrufen. Aus diesem Grund wird die [Dokumentation für einzelne RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) nur an einer Stelle in der [R-Referenz](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server veröffentlicht. Abweichungen durch produktspezifisches Verhalten finden Sie ggf. auf der Hilfeseite der Funktion.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Die **MicrosoftML**-Bibliothek basiert auf R 3.4.3 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder Downloads installieren:

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R Client](set-up-a-data-science-client.md)

> [!NOTE]
> Vollständige Produktversionen sind in SQL Server 2017 nur unter Windows verfügbar. In [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) wird **MicrosoftML** sowohl unter Windows als auch unter Linux unterstützt.

## <a name="package-dependencies"></a>Paketabhängigkeiten

Die Algorithmen folgender Elemente hängen in **MicrosoftML** von [RevoScaleR](ref-r-revoscaler.md) ab:

+ Datenquellenobjekte: Die von **MicrosoftML**-Funktionen genutzten Daten werden mithilfe von **RevoScaleR**-Funktionen erstellt.
+ Remotecomputing (das Verschieben der Funktionsausführung in eine SQL Server-Remoteinstanz): Die **RevoScaleR**-Bibliothek stellt Funktionen zum Erstellen und Aktivieren eines Remotecomputekontexts für SQL Server bereit.

In den meisten Fällen werden die Pakete bei der Verwendung von **MicrosoftML** zusammen geladen.

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorien aufgelistet, damit Sie einen Überblick über die Verwendung der einzelnen Funktionen erhalten. Im [Inhaltsverzeichnis](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) können Sie in alphabetischer Reihenfolge nach den Funktionen suchen.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>1: Machine Learning-Algorithmen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Implementierung von FastRank, effiziente Implementierung des Gradient Boosting-MART-Algorithmus.  |
|[rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Implementierung der zufälligen Gesamtstruktur und der Gesamtstruktur nach Quantilregression mit [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Logistische Regression mit L-BFGS.  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Einklassige Support Vector Machine.  
|[rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Binäres, mehrklassiges und neuronales Regressionsnetzwerk.  |
|[rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Optimierung des doppelten stochastischen Koordinatenanstiegs für die lineare binäre Klassifizierung und Regression. |
|[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | Trainiert eine Reihe von verschiedenen Modellen zur Steigerung der Vorhersageleistung im Vergleich zu einem einzelnen Modell.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2: Transformationsfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | Erstellt eine Spalte mit einem einzelnen Vektorwert aus mehreren Spalten.  |
|[categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | Erstellt einen Indikatorvektor durch Kategorietransformation mit einem Wörterbuch.  |
|[categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | Konvertiert den Kategoriewert durch einen Hashvorgang in ein Indikatorarray. |
|[featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | Erstellt aus einem angegebenen Textkorpus einen Behälter mit der Anzahl von Sequenzen aus aufeinander folgenden Wörtern (sogenannten N-Grammen). Enthält Spracherkennung, Tokenisierung, das Entfernen von Stoppwörtern, Textnormalisierung und Featuregenerierung.  |
|[getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | Bewertet Text in natürlicher Sprache und erstellt eine Spalte mit Wahrscheinlichkeiten, dass die Stimmung im Text positiv ist.|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | Ermöglicht das Definieren von Argumenten für die anzahl- und hashbasierte Featureextraktion.|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | Wählt mehrere Spalten aus, die erneut trainiert werden sollen, und löscht alle anderen Spalten. |
|[selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | Wählt unter Verwendung eines angegebenen Modus Funktionen aus den angegebenen Variablen aus.|
|[loadImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | Lädt Bilddaten.|
|[resizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | Ändert die Größe eines Bilds in eine angegebene Größe unter Verwendung einer angegebenen Methode zur Größenänderung.|
|[extractPixels](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | Extrahiert die Pixelwerte aus einem Bild.|
|[featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | Erstellt mithilfe eines vortrainierten tiefen neuronalen Netzwerkmodells Merkmale für ein Bild.|


## <a name="3-scoring-and-training-functions"></a>3: Bewertungs- und Trainingsfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | Führt die Bewertungsbibliothek entweder in SQL Server mithilfe der gespeicherten Prozedur oder über R-Code aus, um eine Echtzeitbewertung und dadurch eine wesentlich schnellere Vorhersageleistung zu erzielen.|
|[rxFeaturize](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Wandelt Daten von einem Eingabedataset in ein Ausgabedataset um.|
|[mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Stellt die Zusammenfassung eines Microsoft Machine Learning-Modells für R bereit.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4: Verlustfunktionen zur Klassifizierung und Regression

| Funktionsname | Beschreibung |
|---------------|-------------|
|[expLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für exponentielle Klassifizierungen. | 
|[logLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für Protokollklassifizierungen.  |
|[hingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für Scharnierklassifizierungen. | 
|[smoothHingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für geglättete Scharnierklassifizierungen.  |
| [poissonLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für Poisson-Regressionen. | 
|[squaredLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für quadratische Regressionen.   |   

## <a name="5-feature-selection-functions"></a>5: Funktionsauswahlfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[minCount](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | Spezifikation für die Funktionsauswahl im Anzahlmodus. |
|[mutualInformation](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | Spezifikation für die Funktionsauswahl im Transinformationsmodus. |

## <a name="6-ensemble-modeling-functions"></a>6: Ensemble-Modellierungsfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[fastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines schnellen Strukturmodells mit [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines schnellen Gesamtstrukturmodells mit [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines schnellen linearen Modells mit [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[logisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines logistischen Regressionsmodells mit [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[oneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines OneClassSvm-Modells mit [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>7: Neuronale Netzwerkfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[optimizer](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | Gibt Optimierungsalgorithmen für den Machine Learning-Algorithmus [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) an.|


## <a name="8-package-state-functions"></a>8: Paketstatusfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxHashEnv](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Umgebungsobjekt zum Speichern des paketweiten Status. |


## <a name="how-to-use-microsoftml"></a>Verwendung von MicrosoftML

Funktionen in **MicrosoftML** können in R-Code aufgerufen werden, der in gespeicherten Prozeduren gekapselt ist. Die meisten Entwickler erstellen **MicrosoftML**-Lösungen lokal, und migrieren den fertigen R-Code anschließend als Bereitstellungsübung in gespeicherte Prozeduren.

Das **MicrosoftML**-Paket für R ist in SQL Server 2017 bereits installiert. Es ist auch für SQL Server 2016 verfügbar, wenn Sie die R-Komponenten für die Instanz aktualisieren: [Aktualisieren einer Instanz von SQL Server mithilfe von Bindung](../install/upgrade-r-and-python.md).

Das Paket wird nicht standardmäßig geladen. Laden Sie zunächst das **MicrosoftML**-Paket und anschließend **RevoScaleR**, wenn Sie Remotecomputekontexte oder verbundene Verbindungs- oder Datenquellenobjekte verwenden müssen. Verweisen Sie dann auf die einzelnen Funktionen, die Sie benötigen.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>Weitere Informationen

+ [R-Tutorials](../tutorials/sql-server-r-tutorials.md)
+ [Informationen zur Verwendung von Computekontexten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R für SQL-Entwickler: Trainieren und Operationalisieren eines Modells](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Microsoft-Produktbeispiele auf GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [R-Referenz (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 