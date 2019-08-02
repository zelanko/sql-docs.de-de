---
title: Microsoftml-R-Funktionsbibliothek
description: Einführung in die microsoftml-Funktionsbibliothek in SQL Server 2016 R Services und SQL Server Machine Learning Services mit R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: af9e85586a2aad69a87072caa820fff4026d1feb
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715665"
---
# <a name="microsoftml-r-library-in-sql-server"></a>Microsoftml (R-Bibliothek in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**Microsoftml** ist eine R-Funktionsbibliothek von Microsoft, die hochleistungsfähige Machine Learning-Algorithmen bereitstellt. Sie enthält Funktionen für Trainings-und Transformationen, Bewertung, Text-und Bildanalyse und featureextraktion zum Ableiten von Werten aus vorhandenen Daten.

Die Machine Learning-APIs wurden von Microsoft für interne Machine Learning-Anwendungen entwickelt und im Laufe der Jahre optimiert, um eine hohe Leistung bei der Big Data zu unterstützen, indem die multikernverarbeitung und das schnelle Datenstreaming genutzt werden. Microsoftml umfasst auch zahlreiche Transformationen für die Text-und Bildverarbeitung.

## <a name="full-reference-documentation"></a>Vollständige Referenz Dokumentation

Die **microsoftml** -Bibliothek ist in mehreren Microsoft-Produkten verteilt, aber die Verwendung ist identisch, unabhängig davon, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die-Funktionen identisch sind, wird die [Dokumentation für einzelne revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) nur an einem Speicherort unter der [R-Referenz](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server veröffentlicht. Wenn produktspezifische Verhalten vorhanden sind, werden auf der Hilfeseite der Funktion Abweichungen festgestellt.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Die **microsoftml** -Bibliothek basiert auf R 3.4.3 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder-Downloads installieren:

+ [SQL Server 2016 R-Dienste](../install/sql-r-services-windows-install.md)
+ [SQL Server-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R-Client](set-up-a-data-science-client.md)

> [!NOTE]
> Vollversion der Produktversion ist nur Windows, beginnend mit SQL Server 2017. Die Linux-Unterstützung für **microsoftml** ist neu in [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Paketabhängigkeiten

Algorithmen in **microsoftml** sind von [revoscaler](ref-r-revoscaler.md) für Folgendes abhängig:

+ Datenquellen Objekte. Die von **microsoftml** -Funktionen genutzten Daten werden mithilfe von **revoscaler** -Funktionen erstellt.
+ Remote Computing (Verschieben der Funktions Ausführung in eine Remote SQL Server-Instanz). Die **revoscaler** -Bibliothek stellt Funktionen zum Erstellen und Aktivieren eines remotecomputekontexts für SQL Server bereit.

In den meisten Fällen laden Sie die Pakete immer dann, wenn Sie **microsoftml**verwenden.

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorie aufgelistet, um Ihnen einen Überblick darüber zu verschaffen, wie die einzelnen Funktionen verwendet werden. Sie können auch das Inhalts [Verzeichnis](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) verwenden, um Funktionen in alphabetischer Reihenfolge zu suchen.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>1: Machine Learning-Algorithmen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Eine Implementierung von "fastrank", eine effiziente Implementierung des Mart-Algorithmus zum Erhöhen des Farbverlaufs.  |
|[rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Eine zufällige Gesamtstruktur-und quantilregression-Gesamtstruktur Implementierung mithilfe von [rxfasttrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Logistische Regression mit L-BFGS.  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Eine Klasse unterstützt Vector Machines.  
|[rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Binäres (Binary), MultiClass-und Regression Neural net.  |
|[rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Stochastic Dual Koordinate-Aufstiegs Optimierung für lineare binäre Klassifizierung und Regression. |
|[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | Trainiert eine Reihe von Modellen verschiedener Arten, um eine bessere Vorhersage Leistung zu erzielen, als aus einem einzelnen Modell abgerufen werden kann.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2-Transformations Funktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | Transformation zum Erstellen einer einzelnen Vektor Wert Spalte aus mehreren Spalten.  |
|[categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | Erstellen Sie einen Indikator Vektor mithilfe der kategorischen Transformation mit dem Wörterbuch.  |
|[categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | Konvertiert den kategorischen Wert durch Hashwert in ein Indikator Array. |
|[featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | Erzeugt einen Behälter mit einer Anzahl von Sequenzen von aufeinander folgenden Wörtern (n-grams) aus einem gegebenen Textkorpus. Es bietet die Spracherkennung, Tokenisierung, das Entfernen von Stopp Wörtern, die Text Normalisierung und die Generierung von Features.  |
|[getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | Bewertet Text in natürlicher Sprache und erstellt eine Spalte, die Wahrscheinlichkeiten enthält, dass die Stimmungen im Text positiv sind.|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | ermöglicht das Definieren von Argumenten für die Anzahl-und Hash basierte featureextraktion.|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | Wählt eine Reihe von Spalten zum erneuten trainieren aus, wobei alle anderen gelöscht werden. |
|[selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | Wählt Features aus den angegebenen Variablen unter Verwendung eines angegebenen Modus aus.|
|[loadImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | Lädt Bilddaten.|
|[resizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | Ändert die Größe eines Bilds mithilfe einer angegebenen Methode zum Ändern der Größe an eine angegebene Dimension.|
|[extractpixels](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | Extrahiert die Pixelwerte aus einem Bild.|
|[featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | Macht ein Image mit einem vorab trainierten Deep Neural Network-Modell aus.|


## <a name="3-scoring-and-training-functions"></a>3-Bewertungs-und Trainingsfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | Führt die Bewertungs Bibliothek aus SQL Server mithilfe der gespeicherten Prozedur oder aus R-Code aus, der die Echtzeitbewertung ermöglicht, um eine wesentlich schnellere Vorhersage Leistung zu erzielen.|
|[rxFeaturize](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Wandelt Daten aus einem Eingabedaten Satz in ein Ausgabe DataSet um.|
|[mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Bietet eine Zusammenfassung eines Microsoft R Machine Learning-Modells.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4-Verluste-Funktionen für Klassifizierung und Regression

| Funktionsname | Beschreibung |
|---------------|-------------|
|[expLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für die Funktion zum Verlust von exponentiellen Klassifizierungen. | 
|[logLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für die Funktion zum Verlust der Protokoll Klassifizierung.  |
|[hingeloss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für die Funktion zum Verlust der Scharnier Klassifizierung. | 
|[smoothHingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für die Funktion zum Verlust der Smooth-Scharnier Klassifizierung.  |
| [poissonLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für die Poisson-Regressions Verlust Funktion. | 
|[squaredLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Spezifikationen für die Funktion der quadratischen Regressions Verluste.   |   

## <a name="5-feature-selection-functions"></a>5-Funktionsauswahl Funktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[minCount](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | Spezifikation für die Funktionsauswahl im Anzahl Modus. |
|[mutualInformation](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | Spezifikation für die Featureauswahl im Modus für die gegenseitige Information. |

## <a name="6-ensemble-modeling-functions"></a>6-Ensemble-Modellierungsfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[fasttrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | Erstellt eine Liste, die den Funktionsnamen und die Argumente enthält, mit denen ein schnelles Strukturmodell mit [rxensemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)trainiert wird.|
|[fastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Erstellt eine Liste, die den Funktionsnamen und die Argumente enthält, mit denen ein schnelles Gesamtstruktur Modell mit [rxensemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)trainiert wird.|
|[fastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | Erstellt eine Liste, die den Funktionsnamen und die Argumente enthält, mit denen ein schnelles lineares Modell mit [rxensemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)trainiert wird.|
|[logisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Erstellt eine Liste, die den Funktionsnamen und die Argumente für das Trainieren eines logistischen Regressionsmodells mit [rxensemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)enthält.|
|[oneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Erstellt eine Liste, die den Funktionsnamen und die Argumente für das Trainieren eines oneclasssvm-Modells mit [rxensemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)enthält.|

## <a name="7-neural-networking-functions"></a>7-neuronale Netzwerkfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[Optimierer](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | Gibt Optimierungsalgorithmen für den [rxneural net](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) -Machine Learning-Algorithmus an.|


## <a name="8-package-state-functions"></a>8-Package-Status Funktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxHashEnv](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Ein Umgebungs Objekt, das zum Speichern des Paket weiten Zustands verwendet wird. |


## <a name="how-to-use-microsoftml"></a>Verwenden von microsoftml

Funktionen in **microsoftml** können in R-Code in gespeicherten Prozeduren als gekapselt aufgerufen werden. Die meisten Entwickler erstellen **microsoftml** -Lösungen lokal und Migrieren den fertiggestellten R-Code als Bereitstellungs Übung zu gespeicherten Prozeduren.

Das **microsoftml** -Paket für R wird standardmäßig in SQL Server 2017 installiert. Es ist auch für die Verwendung mit SQL Server 2016 verfügbar, wenn Sie die R-Komponenten für die Instanz aktualisieren: [Aktualisieren einer Instanz von SQL Server mithilfe von Bindung](../install/upgrade-r-and-python.md)

Das Paket wird nicht standardmäßig geladen. Laden Sie als ersten Schritt das **microsoftml** -Paket, und laden Sie dann **revoscaler** , wenn Sie remotecomputekontexte oder zugehörige Konnektivität oder Datenquellen Objekte verwenden müssen. Verweisen Sie dann auf die einzelnen benötigten Funktionen.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>Siehe auch

+ [R-Tutorials](../tutorials/sql-server-r-tutorials.md)
+ [Weitere Informationen zur Verwendung von computekontexten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R für SQL-Entwickler: Trainieren und operationalisieren eines Modells](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Microsoft-Produktbeispiele auf GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [R-Verweis (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 