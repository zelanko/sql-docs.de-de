---
title: 'Microsoftml-Python-Paket: SQL Server Machine Learning Services'
description: Stellt die Microsoft Machine learning-Algorithmen und -Modelle für Python, als im Zusammenhang mit SQL Server Machine Learning-Workloads.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 618c4b127c42aae6a5b8d7570f1962f8c8e38e9a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642361"
---
# <a name="microsoftml-python-module-in-sql-server"></a>Microsoftml (Python-Modul in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**Microsoftml** ist ein Modul Python35 kompatible von Microsoft High-Performance-Machine Learning-Algorithmen bereitstellt. Es enthält Funktionen für Training und Transformationen, Bewertung, Text- und Image-Analyse und featureextraktion für das Ableiten von Werten aus vorhandenen Daten.

Die Machine learning-APIs von Microsoft entwickelt wurden, die für interne Machine Learning-Anwendungen und wurden die optimierten im Laufe der Jahre zur Unterstützung von hoher Leistung für big Data mit multicore-Verarbeitung und schnelles streaming von Daten. Dieses Paket als ein Python-Entsprechung zu einem R-Version stammen [MicrosoftML](../r/ref-r-microsoftml.md), die verfügt über ähnliche Funktionen. 

## <a name="full-reference-documentation"></a>Vollständige Referenz-Dokumentation

Die **Microsoftml** Bibliothek wird in mehreren Microsoft-Produkte verteilt, aber wird, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die Funktionen identisch sind, [Dokumentation für einzelne Microsoftml Functions](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) in nur einem Ort unter veröffentlicht wird die [Referenz zum Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) für Microsoft Machine Learning Server. Sollten Sie jede Produkt-spezifische Verhalten vorhanden ist, wird Diskrepanzen auf der Hilfeseite für die Funktion angegeben.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Die **Microsoftml** Modul basierend auf Python 3.5 und verfügbar ist, nur, wenn Sie eine der folgenden Microsoft-Produkten oder Downloads installieren:

+ [SQL Server 2017-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Python-Clientbibliotheken für ein Data Science-client](setup-python-client-tools-sql.md)

> [!NOTE]
> Releaseversionen der Vollversion des Produkts sind Windows ausschließlich ab SQL Server 2017. Linux-Unterstützung für **Microsoftml** ist neu in [Vorschau von SQL Server-2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Paketabhängigkeiten

Algorithmen in **Microsoftml** hängen [Revoscalepy](ref-py-revoscalepy.md) für:

+ Datenquellenobjekte. Daten von genutzt **Microsoftml** Funktionen werden mit erstellt **Revoscalepy** Funktionen.
+ Remote computing (wechselnden funktionsausführung zu einer Remoteinstanz von SQL Server). Die **Revoscalepy** -Bibliothek bietet Funktionen für das Erstellen und aktivieren eine-Kontext für SQLServer Compute.

In den meisten Fällen werden Laden Sie die Pakete zusammen bei jeder Verwendung **Microsoftml**.

## <a name="functions-by-category"></a>Funktionen, die nach Kategorie

Dieser Abschnitt listet die Funktionen nach Kategorie, erhalten Sie einen Überblick darüber, wie jeweils verwendet wird. Sie können auch die [Inhaltsverzeichnis](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) Sie Funktionen in alphabetischer Reihenfolge suchen.

## <a name="1-training-functions"></a>1 – Training-Funktionen

| Funktion | Description |
|----------|-------------|
|[microsoftml.rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Eine Ensemble-Modelle zu trainieren. |
|[microsoftml.rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Random Forest. |
|[microsoftml.rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Lineares Modell. mit dem stochastischen Dual-Koordinate Versalhöhe. |
|[microsoftml.rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | -Boosted-Strukturen. |
|[microsoftml.rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Logistische Regression. |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Neural Network. |
|[microsoftml.rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Erkennung von Anomalien. |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2-Transform-Funktionen

### <a name="categorical-variable-handling"></a>Behandlung von kategorischen Variablen

| Funktion | Description |
|----------|-------------|
|[microsoftml.categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | Konvertiert eine Textspalte in Kategorien. |
|[microsoftml.categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | Erstellt einen Hashwert und konvertiert eine Textspalte in Kategorien. |

### <a name="schema-manipulation"></a>Schema bearbeiten

| Funktion | Description |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | Verkettet mehrere Zeichenfolgenspalten in einen einzelnen Vektor. |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | Löscht aus einem Dataset. |
|[microsoftml.select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | Behält die Spalten eines Datasets. |


### <a name="variable-selection"></a>Variablenauswahl

| Funktion | Description |
|----------|-------------|
|[microsoftml.count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |Die Funktionsauswahl basierend auf der Menge. |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Die Funktionsauswahl basierend auf transinformation. |


### <a name="text-analytics"></a>Textanalyse

| Funktion | Description |
|----------|-------------|
|[microsoftml.featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | In den Spalten der konvertiert in numerischen Features. |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | Standpunktanalyse. |


### <a name="image-analytics"></a>Bildanalyse 

| Funktion | Description |
|----------|-------------|
|[microsoftml.load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | Lädt ein Bild. |
|[microsoftml.resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | Ändert die Größe ein Bild. |
|[microsoftml.extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | Extrahiert Pixel aus einem Bild. |
|[microsoftml.featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Konvertiert ein Bild in Funktionen. |

### <a name="featurization-functions"></a>Featurebereitstellung-Funktionen

| Funktion | Description |
|----------|-------------|
|[microsoftml.rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | Datentransformation für Datenquellen |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3-Bewertung-Funktionen

| Funktion | Description |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Bewertungen mithilfe von Microsoft Machine Learning-Modellen |

## <a name="how-to-call-microsoftml"></a>Das Aufrufen von microsoftml

Funktionen in **Microsoftml** in Python-Code gekapselt, die in gespeicherten Prozeduren können aufgerufen werden. Die meisten Entwickler erstellen **Microsoftml** Lösungen lokal, und migrieren Sie dann die komplette Python-Code zu gespeicherten Prozeduren als eine Übung für die Bereitstellung.

Die **Microsoftml** -Paket für Python installiert ist, standardmäßig aber im Gegensatz zu **Revoscalepy**, es ist nicht standardmäßig geladen, wenn Sie eine Python-Sitzung, die mithilfe von Python ausführbaren Dateien installiert, die mit SQL Server starten.

Importieren Sie als ersten Schritt die **Microsoftml** -Paket, und importieren Sie **Revoscalepy** remotecomputekontexte oder verbundene Konnektivitäts- oder Data-Source-Objekte verwenden werden sollen. Klicken Sie dann, verweisen auf den einzelnen Funktionen, die Sie benötigen.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Siehe auch

+ [Python-Tutorials](../tutorials/sql-server-python-tutorials.md)
+ [Tutorial: Einbetten von Python-Code in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Python-Referenz (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

