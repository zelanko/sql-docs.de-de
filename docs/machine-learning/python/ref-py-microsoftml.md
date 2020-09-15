---
title: Python-Paket für microsoftml
description: microsoftml ist ein Python-Paket von Microsoft, das leistungsstarke Machine-Learning-Algorithmen bereitstellt. Sie enthält Funktionen für Training, Transformationen, Bewertung, Text- und Bildanalyse sowie Featureextraktion zum Ableiten von Werten aus vorhandenen Daten. Es ist in SQL Server Machine Learning Services enthalten.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/14/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c638b3c32af037b8c597c840d4bdf388aad56efc
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88178587"
---
# <a name="microsoftml-python-package-in-sql-server-machine-learning-services"></a>microsoftml (Python-Paket in SQL Server Machine Learning Services)
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

**microsoftml** ist ein Python-Paket von Microsoft, das leistungsstarke Machine-Learning-Algorithmen bereitstellt. Sie enthält Funktionen für Training, Transformationen, Bewertung, Text- und Bildanalyse sowie Featureextraktion zum Ableiten von Werten aus vorhandenen Daten. Das Paket ist in [Machine Learning Services in SQL Server](../sql-server-machine-learning-services.md) enthalten und unterstützt Hochleistung für Big Data. Dafür wird Verarbeitung mit mehreren Kernen und schnelles Datenstreaming verwendet.

## <a name="full-reference-documentation"></a>Vollständige Referenzdokumentation

Das **microsoftml**-Paket wird in mehreren Microsoft-Produkten bereitgestellt. Die Verwendung ist jedoch immer identisch, unabhängig davon, ob Sie das Paket in SQL Server oder einem anderen Produkt abrufen. Aus diesem Grund wird die [Dokumentation für einzelne microsoftml-Funktionen](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) nur an einer Stelle in der [Python-Referenz](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) für Microsoft Machine Learning Server veröffentlicht. Abweichungen durch produktspezifisches Verhalten finden Sie ggf. auf der Hilfeseite der Funktion.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Das **microsoftml**-Modul basiert auf Python 3.5 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder Downloads installieren:

+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Python-Client-Bibliotheken für einen Data Science-Client](setup-python-client-tools-sql.md)

> [!NOTE]
> Vollständige Produktversionen sind in SQL Server 2017 nur unter Windows verfügbar. In [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) wird **microsoftml** sowohl unter Windows als auch unter Linux unterstützt.

## <a name="package-dependencies"></a>Paketabhängigkeiten

Die Algorithmen folgender Elemente hängen in **microsoftml** von [revoscalepy](ref-py-revoscalepy.md) ab:

+ Datenquellenobjekte: Die von **microsoftml**-Funktionen genutzten Daten werden mithilfe von **revoscalepy**-Funktionen erstellt.
+ Remotecomputing (das Verschieben der Funktionsausführung in eine SQL Server-Remoteinstanz): Das **revoscalepy**-Paket stellt Funktionen zum Erstellen und Aktivieren eines Remotecomputekontexts für SQL Server bereit.

In den meisten Fällen werden die Pakete bei der Verwendung von **microsoftml** zusammen geladen.

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorien aufgelistet, damit Sie einen Überblick über die Verwendung der einzelnen Funktionen erhalten. Im [Inhaltsverzeichnis](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) können Sie in alphabetischer Reihenfolge nach den Funktionen suchen.

## <a name="1-training-functions"></a>1: Trainingsfunktionen

| Funktion | BESCHREIBUNG |
|----------|-------------|
|[microsoftml.rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Trainiert ein Modellensemble |
|[microsoftml.rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Zufällige Gesamtstruktur |
|[microsoftml.rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Lineares Modell mit doppeltem stochastischen Koordinatenanstieg |
|[microsoftml.rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Verstärkte Entscheidungsbäume |
|[microsoftml.rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Logistische Regression |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Neuronales Netzwerk |
|[microsoftml.rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Erkennt Anomalien |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2: Transformationsfunktionen

### <a name="categorical-variable-handling"></a>Behandeln von kategorischen Variablen

| Funktion | BESCHREIBUNG |
|----------|-------------|
|[microsoftml.categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | Konvertiert Textspalten in Kategorien |
|[microsoftml.categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | Erstellt einen Hash für eine Textspalte und konvertiert diese in Kategorien |

### <a name="schema-manipulation"></a>Schemabearbeitung

| Funktion | BESCHREIBUNG |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | Verkettet mehrere Spalten zu einem einzelnen Vektor |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | Löscht Spalten aus einem Dataset |
|[microsoftml.select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | Behält Spalten eines Datasets bei |


### <a name="variable-selection"></a>Variablenauswahl

| Funktion | BESCHREIBUNG |
|----------|-------------|
|[microsoftml.count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |Wählt Funktionen basierend auf Anzahlen aus |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Wählt Funktionen auf der Grundlage von gegenseitigen Informationen aus |


### <a name="text-analytics"></a>Textanalyse

| Funktion | BESCHREIBUNG |
|----------|-------------|
|[microsoftml.featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | Konvertiert Textspalten in numerische Funktionen |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | Stimmungsanalyse |


### <a name="image-analytics"></a>Bildanalyse 

| Funktion | BESCHREIBUNG |
|----------|-------------|
|[microsoftml.load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | Lädt ein Bild |
|[microsoftml.resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | Ändert die Größe eines Bilds |
|[microsoftml.extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | Extrahiert Pixel aus einem Bild |
|[microsoftml.featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Konvertiert ein Bild in Features |

### <a name="featurization-functions"></a>Featurefunktionen

| Funktion | BESCHREIBUNG |
|----------|-------------|
|[microsoftml.rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | Datentransformation für Datenquellen |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3: Bewertungsfunktionen

| Funktion | BESCHREIBUNG |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Nimmt Bewertungen unter Verwendung eines Microsoft Machine Learning-Modells vor |

## <a name="how-to-call-microsoftml"></a>Vorgehensweise beim Abrufen von microsoftml

Funktionen in **microsoftml** können in Python-Code aufgerufen werden, der in gespeicherten Prozeduren gekapselt ist. Die meisten Entwickler erstellen **microsoftml**-Lösungen lokal, und migrieren den fertigen Python-Code anschließend als Bereitstellungsübung in gespeicherte Prozeduren.

Das **microsoftml**-Paket für Python ist standardmäßig installiert, im Gegensatz zu **revoscalepy** wird es jedoch nicht standardmäßig geladen, wenn Sie eine Python-Sitzung mit den mit SQL Server installierten Python-Dateien starten.

Importieren Sie zunächst das **microsoftml**-Paket, und importieren Sie anschließend **revoscalepy**, wenn Sie Remotecomputekontexte oder zugehörige Verbindungs- oder Datenquellenobjekte verwenden müssen. Verweisen Sie dann auf die einzelnen Funktionen, die Sie benötigen.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Weitere Informationen

+ [Python-Tutorials](../tutorials/sql-server-python-tutorials.md)
+ [Python-Referenz (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

