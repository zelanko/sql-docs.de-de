---
title: MicrosoftML-R-Paket
description: MicrosoftML ist ein R-Paket von Microsoft, das leistungsstarke Machine-Learning-Algorithmen bereitstellt. Sie enthält Funktionen für Training, Transformationen, Bewertung, Text- und Bildanalyse sowie Featureextraktion zum Ableiten von Werten aus vorhandenen Daten. Das Paket ist in Machine Learning Services in SQL Server und in SQL Server 2016 R Services enthalten und unterstützt Hochleistung für Big Data. Dafür wird Verarbeitung mit mehreren Kernen und schnelles Datenstreaming verwendet. MicrosoftML enthält auch zahlreiche Transformationen für die Text- und Bildverarbeitung.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/06/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6295756f727dacffbfa54c1dccaf223cfac58351
ms.sourcegitcommit: afb02c275b7c79fbd90fac4bfcfd92b00a399019
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91956888"
---
# <a name="microsoftml-r-package-in-sql-server-machine-learning-services"></a>MicrosoftML (R-Paket in Machine Learning Services in SQL Server)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

**MicrosoftML** ist ein R-Paket von Microsoft, das leistungsstarke Machine-Learning-Algorithmen bereitstellt. Sie enthält Funktionen für Training, Transformationen, Bewertung, Text- und Bildanalyse sowie Featureextraktion zum Ableiten von Werten aus vorhandenen Daten. Das Paket ist in [Machine Learning Services in SQL Server](../sql-server-machine-learning-services.md) und in [SQL Server 2016 R Services](sql-server-r-services.md) enthalten und unterstützt Hochleistung für Big Data. Dafür wird Verarbeitung mit mehreren Kernen und schnelles Datenstreaming verwendet. MicrosoftML enthält auch zahlreiche Transformationen für die Text- und Bildverarbeitung.

## <a name="full-reference-documentation"></a>Vollständige Referenzdokumentation

Das **MicrosoftML**-Paket wird in mehreren Microsoft-Produkten bereitgestellt. Die Verwendung ist jedoch immer identisch, unabhängig davon, ob Sie das Paket in SQL Server oder einem anderen Produkt abrufen. Aus diesem Grund wird die [Dokumentation für einzelne RevoScaleR-Funktionen](/machine-learning-server/r-reference/revoscaler/revoscaler) nur an einer Stelle in der [R-Referenz](/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server veröffentlicht. Abweichungen durch produktspezifisches Verhalten finden Sie ggf. auf der Hilfeseite der Funktion.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Das **MicrosoftML**-Paket basiert auf R 3.4.3 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder einen der Downloads installieren:

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](/machine-learning-server/)
+ [Microsoft R Client](set-up-a-data-science-client.md)

> [!NOTE]
> Vollständige Produktversionen sind in SQL Server 2017 nur unter Windows verfügbar. In [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) wird **MicrosoftML** sowohl unter Windows als auch unter Linux unterstützt.

## <a name="package-dependencies"></a>Paketabhängigkeiten

Die Algorithmen folgender Elemente hängen in **MicrosoftML** von [RevoScaleR](ref-r-revoscaler.md) ab:

+ Datenquellenobjekte: Die von **MicrosoftML**-Funktionen genutzten Daten werden mithilfe von **RevoScaleR**-Funktionen erstellt.
+ Remotecomputing (das Verschieben der Funktionsausführung in eine SQL Server-Remoteinstanz): Das **RevoScaleR**-Paket stellt Funktionen zum Erstellen und Aktivieren eines Remotecomputekontexts für SQL Server bereit.

In den meisten Fällen werden die Pakete bei der Verwendung von **MicrosoftML** zusammen geladen.

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorien aufgelistet, damit Sie einen Überblick über die Verwendung der einzelnen Funktionen erhalten. Im [Inhaltsverzeichnis](/machine-learning-server/r-reference/introducing-r-server-r-package-reference) können Sie in alphabetischer Reihenfolge nach den Funktionen suchen.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>1: Machine Learning-Algorithmen

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[rxFastTrees](/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Implementierung von FastRank, effiziente Implementierung des Gradient Boosting-MART-Algorithmus.  |
|[rxFastForest](/machine-learning-server/r-reference/microsoftml/rxfastforest) | Implementierung der zufälligen Gesamtstruktur und der Gesamtstruktur nach Quantilregression mit [rxFastTrees](/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](/machine-learning-server/r-reference/microsoftml/logisticregression) | Logistische Regression mit L-BFGS.  |
|[rxOneClassSvm](/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Einklassige Support Vector Machine.  
|[rxNeuralNet](/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Binäres, mehrklassiges und neuronales Regressionsnetzwerk.  |
|[rxFastLinear](/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Optimierung des doppelten stochastischen Koordinatenanstiegs für die lineare binäre Klassifizierung und Regression. |
|[rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble) | Trainiert eine Reihe von verschiedenen Modellen zur Steigerung der Vorhersageleistung im Vergleich zu einem einzelnen Modell.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2: Transformationsfunktionen

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[concat](/machine-learning-server/r-reference/microsoftml/concat) | Erstellt eine Spalte mit einem einzelnen Vektorwert aus mehreren Spalten.  |
|[categorical](/machine-learning-server/r-reference/microsoftml/categorical) | Erstellt einen Indikatorvektor durch Kategorietransformation mit einem Wörterbuch.  |
|[categoricalHash](/machine-learning-server/r-reference/microsoftml/categoricalhash) | Konvertiert den Kategoriewert durch einen Hashvorgang in ein Indikatorarray. |
|[featurizeText](/machine-learning-server/r-reference/microsoftml/featurizetext) | Erstellt aus einem angegebenen Textkorpus einen Behälter mit der Anzahl von Sequenzen aus aufeinander folgenden Wörtern (sogenannten N-Grammen). Enthält Spracherkennung, Tokenisierung, das Entfernen von Stoppwörtern, Textnormalisierung und Featuregenerierung.  |
|[getSentiment](/machine-learning-server/r-reference/microsoftml/getsentiment) | Bewertet Text in natürlicher Sprache und erstellt eine Spalte mit Wahrscheinlichkeiten, dass die Stimmung im Text positiv ist.|
|[ngram](/machine-learning-server/r-reference/microsoftml/ngram) | Ermöglicht das Definieren von Argumenten für die anzahl- und hashbasierte Featureextraktion.|
|[selectColumns](/machine-learning-server/r-reference/microsoftml/selectcolumns) | Wählt mehrere Spalten aus, die erneut trainiert werden sollen, und löscht alle anderen Spalten. |
|[selectFeatures](/machine-learning-server/r-reference/microsoftml/selectfeatures) | Wählt unter Verwendung eines angegebenen Modus Funktionen aus den angegebenen Variablen aus.|
|[loadImage](/machine-learning-server/r-reference/microsoftml/loadimage) | Lädt Bilddaten.|
|[resizeImage](/machine-learning-server/r-reference/microsoftml/resizeimage) | Ändert die Größe eines Bilds in eine angegebene Größe unter Verwendung einer angegebenen Methode zur Größenänderung.|
|[extractPixels](/machine-learning-server/r-reference/microsoftml/extractpixels) | Extrahiert die Pixelwerte aus einem Bild.|
|[featurizeImage](/machine-learning-server/r-reference/microsoftml/featurizeimage) | Erstellt mithilfe eines vortrainierten tiefen neuronalen Netzwerkmodells Merkmale für ein Bild.|


## <a name="3-scoring-and-training-functions"></a>3: Bewertungs- und Trainingsfunktionen

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[rxPredict.mlModel](/machine-learning-server/r-reference/microsoftml/rxpredict) | Führt die Bewertungsbibliothek entweder in SQL Server mithilfe der gespeicherten Prozedur oder über R-Code aus, um eine Echtzeitbewertung und dadurch eine wesentlich schnellere Vorhersageleistung zu erzielen.|
|[rxFeaturize](/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Wandelt Daten von einem Eingabedataset in ein Ausgabedataset um.|
|[mlModel](/machine-learning-server/r-reference/microsoftml/mlmodel) | Stellt die Zusammenfassung eines Microsoft Machine Learning-Modells für R bereit.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4: Verlustfunktionen zur Klassifizierung und Regression

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[expLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für exponentielle Klassifizierungen. | 
|[logLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für Protokollklassifizierungen.  |
|[hingeLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für Scharnierklassifizierungen. | 
|[smoothHingeLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für geglättete Scharnierklassifizierungen.  |
| [poissonLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für Poisson-Regressionen. | 
|[squaredLoss](/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für eine Verlustfunktion für quadratische Regressionen.   |   

## <a name="5-feature-selection-functions"></a>5: Funktionsauswahlfunktionen

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[minCount](/machine-learning-server/r-reference/microsoftml/mincount) | Spezifikation für die Funktionsauswahl im Anzahlmodus. |
|[mutualInformation](/machine-learning-server/r-reference/microsoftml/mutualinformation) | Spezifikation für die Funktionsauswahl im Transinformationsmodus. |

## <a name="6-ensemble-modeling-functions"></a>6: Ensemble-Modellierungsfunktionen

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[fastTrees](/machine-learning-server/r-reference/microsoftml/fasttrees) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines schnellen Strukturmodells mit [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastForest](/machine-learning-server/r-reference/microsoftml/rxfastforest) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines schnellen Gesamtstrukturmodells mit [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastLinear](/machine-learning-server/r-reference/microsoftml/fastlinear) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines schnellen linearen Modells mit [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[logisticRegression](/machine-learning-server/r-reference/microsoftml/logisticregression) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines logistischen Regressionsmodells mit [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[oneClassSvm](/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Erstellt eine Liste mit dem Funktionsnamen und den Argumenten zum Trainieren eines OneClassSvm-Modells mit [rxEnsemble](/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>7: Neuronale Netzwerkfunktionen

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[optimizer](/machine-learning-server/r-reference/microsoftml/optimizer) | Gibt Optimierungsalgorithmen für den Machine Learning-Algorithmus [rxNeuralNet](/machine-learning-server/r-reference/microsoftml/rxneuralnet) an.|


## <a name="8-package-state-functions"></a>8: Paketstatusfunktionen

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[rxHashEnv](/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Umgebungsobjekt zum Speichern des paketweiten Status. |


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

+ [R-Tutorials](../tutorials/r-tutorials.md)
+ [Informationen zur Verwendung von Computekontexten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R für SQL-Entwickler: Trainieren und Operationalisieren eines Modells](../tutorials/r-taxi-classification-introduction.md)
+ [Microsoft-Produktbeispiele auf GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [R-Referenz (Microsoft Machine Learning Server)](/machine-learning-server/r-reference/introducing-r-server-r-package-reference)