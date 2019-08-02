---
title: Python-Paket für microsoftml
description: Führt die Microsoft Machine Learning-Algorithmen und-Modelle für python ein, die mit SQL Server Machine Learning-Workloads verknüpft sind.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c7e7a25749484ff0db4d133f10862438ae5f8ea1
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715143"
---
# <a name="microsoftml-python-module-in-sql-server"></a>microsoftml (Python-Modul in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**microsoftml** ist ein Python35-kompatibles Modul von Microsoft, das hochleistungsfähige Machine Learning-Algorithmen bereitstellt. Sie enthält Funktionen für Trainings-und Transformationen, Bewertung, Text-und Bildanalyse und featureextraktion zum Ableiten von Werten aus vorhandenen Daten.

Die Machine Learning-APIs wurden von Microsoft für interne Machine Learning-Anwendungen entwickelt und wurden im Laufe der Jahre optimiert, um eine hohe Leistung bei Big Data zu unterstützen, indem die multikernverarbeitung und das schnelle Datenstreaming genutzt werden. Dieses Paket stammt als python-Entsprechung einer R-Version, [microsoftml](../r/ref-r-microsoftml.md), die ähnliche Funktionen aufweist. 

## <a name="full-reference-documentation"></a>Vollständige Referenz Dokumentation

Die **microsoftml** -Bibliothek ist in mehreren Microsoft-Produkten verteilt, aber die Verwendung ist identisch, unabhängig davon, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die Funktionen identisch sind, wird die [Dokumentation für einzelne microsoftml-Funktionen](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) nur an einem Speicherort unter der [python-Referenz](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) für Microsoft Machine Learning Server veröffentlicht. Wenn produktspezifische Verhalten vorhanden sind, werden auf der Hilfeseite der Funktion Abweichungen festgestellt.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Das **microsoftml** -Modul basiert auf Python 3,5 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder-Downloads installieren:

+ [SQL Server-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Python-Client Bibliotheken für einen Data Science-Client](setup-python-client-tools-sql.md)

> [!NOTE]
> Vollversion der Produktversion ist nur Windows, beginnend mit SQL Server 2017. Die Linux-Unterstützung für **microsoftml** ist neu in [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Paketabhängigkeiten

Algorithmen in **microsoftml** sind von [revoscalepy](ref-py-revoscalepy.md) abhängig für:

+ Datenquellen Objekte. Die von **microsoftml** -Funktionen genutzten Daten werden mithilfe von **revoscalepy** -Funktionen erstellt.
+ Remote Computing (Verschieben der Funktions Ausführung in eine Remote SQL Server-Instanz). Die **revoscalepy** -Bibliothek stellt Funktionen zum Erstellen und Aktivieren eines remotecomputekontexts für SQL Server bereit.

In den meisten Fällen laden Sie die Pakete immer dann, wenn Sie **microsoftml**verwenden.

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorie aufgelistet, um Ihnen einen Überblick darüber zu verschaffen, wie die einzelnen Funktionen verwendet werden. Sie können auch das Inhalts [Verzeichnis](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) verwenden, um Funktionen in alphabetischer Reihenfolge zu suchen.

## <a name="1-training-functions"></a>1-Schulungs Funktionen

| Funktion | Beschreibung |
|----------|-------------|
|[microsoftml. rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Trainieren eines Ensembles von Modellen. |
|[microsoftml.rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Zufällige Gesamtstruktur. |
|[microsoftml.rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Lineares Modell. mit Stochastic Dual Koordinate. |
|[microsoftml.rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Verstärkte Strukturen. |
|[microsoftml.rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Logistische Regression. |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Neuronale Netzwerke. |
|[microsoftml.rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Anomalieerkennung. |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2: Transformieren von Funktionen

### <a name="categorical-variable-handling"></a>Behandeln von kategorischen Variablen

| Funktion | Beschreibung |
|----------|-------------|
|[microsoftml.categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | Konvertiert eine Text Spalte in Kategorien. |
|[microsoftml.categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | Hashes und konvertiert eine Text Spalte in Kategorien. |

### <a name="schema-manipulation"></a>Schema Bearbeitung

| Funktion | Beschreibung |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | Verkettet mehrere Spalten zu einem einzelnen Vektor. |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | Löscht Spalten aus einem DataSet. |
|[microsoftml.select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | Behält Spalten eines Datasets bei. |


### <a name="variable-selection"></a>Variablenauswahl

| Funktion | Beschreibung |
|----------|-------------|
|[microsoftml.count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |Funktionsauswahl basierend auf Zählungen. |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Funktionsauswahl auf der Grundlage von gegenseitigen Informationen. |


### <a name="text-analytics"></a>Text Analyse

| Funktion | Beschreibung |
|----------|-------------|
|[microsoftml.featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | Konvertiert Textspalten in numerische Funktionen. |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | Stimmungs Analyse. |


### <a name="image-analytics"></a>Image Analyse 

| Funktion | Beschreibung |
|----------|-------------|
|[microsoftml.load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | Lädt ein Bild. |
|[microsoftml.resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | Ändert die Größe eines Bilds. |
|[microsoftml.extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | Extrahiert Pixel aus einem Bild. |
|[microsoftml.featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Konvertiert ein Bild in-Funktionen. |

### <a name="featurization-functions"></a>Featurefunktionen

| Funktion | Beschreibung |
|----------|-------------|
|[microsoftml.rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | Datentransformation für Datenquellen |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3-Bewertungs Funktionen

| Funktion | Beschreibung |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Bewertungen mit einem Microsoft Machine Learning-Modell |

## <a name="how-to-call-microsoftml"></a>Vorgehensweise beim Abrufen von microsoftml

Funktionen in **microsoftml** können in Python-Code in gespeicherten Prozeduren gekapselt werden. Die meisten Entwickler erstellen **microsoftml** -Lösungen lokal und Migrieren dann fertigen Python-Code zu gespeicherten Prozeduren als Bereitstellungs Übung.

Das **microsoftml** -Paket für python wird standardmäßig installiert, aber im Gegensatz zu **revoscalepy**wird es nicht standardmäßig geladen, wenn Sie eine python-Sitzung mithilfe der ausführbaren python-Dateien starten, die mit SQL Server installiert wurden.

Importieren Sie als ersten Schritt das **microsoftml** -Paket, und importieren Sie **revoscalepy** , wenn Sie remotecomputekontexte oder zugehörige Konnektivität oder Datenquellen Objekte verwenden müssen. Verweisen Sie dann auf die einzelnen benötigten Funktionen.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Siehe auch

+ [Python-Tutorials](../tutorials/sql-server-python-tutorials.md)
+ [Tutorial: Einbetten von Python-Code in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Python-Referenz (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

