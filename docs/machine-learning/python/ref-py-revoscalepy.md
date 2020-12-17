---
title: Python-Paket für revoscalepy
description: revoscalepy ist ein Python-Paket von Microsoft, das verteiltes Computing, Remotecomputekontexte und hochleistungsfähige Data-Science-Algorithmen unterstützt.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/14/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15'
ms.openlocfilehash: 1fcaa82829b35926e2707dda792ac2c376241650
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470931"
---
# <a name="revoscalepy-python-package-in-sql-server-machine-learning-services"></a>revoscalepy (Python-Paket in SQL Server Machine Learning Services)
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

**revoscalepy** ist ein Python-Paket von Microsoft, das verteiltes Computing, Remotecomputekontexte und hochleistungsfähige Data-Science-Algorithmen unterstützt. Es ist in [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) enthalten.

Dieses Paket bietet die folgenden Funktionen:

+ Lokale und Remotecomputekontexte auf Systemen mit derselben **revoscalepy**-Version
+ Funktionen für Datentransformation und -visualisierung
+ Data Science-Funktionen, skalierbar durch verteilte oder parallele Verarbeitung
+ Verbesserte Leistung, einschließlich der Verwendung der mathematischen Intel-Bibliotheken

Datenquellen und Computekontexte, die Sie in **revoscalepy** erstellen, können auch in Machine Learning-Algorithmen verwendet werden. Eine Einführung zu diesen Algorithmen finden Sie unter [microsoftml-Python-Modul in SQL Server](ref-py-microsoftml.md).

## <a name="full-reference-documentation"></a>Vollständige Referenzdokumentation

Das **revoscalepy**-Paket wird in mehreren Microsoft-Produkten bereitgestellt. Die Verwendung ist jedoch immer identisch, unabhängig davon, ob Sie das Paket in SQL Server oder einem anderen Produkt abrufen. Aus diesem Grund wird die [Dokumentation für einzelne revoscalepy-Funktionen](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) nur an einer Stelle in der [Python-Referenz](/machine-learning-server/python-reference/introducing-python-package-reference) für Microsoft Machine Learning Server veröffentlicht. Abweichungen durch produktspezifisches Verhalten finden Sie ggf. auf der Hilfeseite der Funktion.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Das **revoscalepy**-Modul basiert auf Python 3.5 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder Downloads installieren:

+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](/machine-learning-server/)
+ [Python-Client-Bibliotheken für einen Data Science-Client](setup-python-client-tools-sql.md)

> [!NOTE]
> Vollständige Produktversionen sind in SQL Server 2017 nur unter Windows verfügbar. In [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) und höher wird **revoscalepy** sowohl unter Windows als auch unter Linux unterstützt.

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorien aufgelistet, damit Sie einen Überblick über die Verwendung der einzelnen Funktionen erhalten. Im [Inhaltsverzeichnis](/machine-learning-server/python-reference/introducing-python-package-reference) können Sie in alphabetischer Reihenfolge nach den Funktionen suchen.

## <a name="1-data-source-and-compute"></a>1: Datenquelle und Compute

**revoscalepy** enthält Funktionen zum Erstellen von Datenquellen und zum Festlegen des Speicherorts bzw. *Computekontexts*, in dem Berechnungen durchgeführt werden. In der folgenden Tabelle sind die für SQL Server-Szenarios relevanten Funktionen aufgeführt.

SQL Server und Python verwenden in bestimmten Fällen unterschiedliche Datentypen. Eine Liste der Zuordnungen zwischen SQL Server- und Python-Datentypen finden Sie unter [Zuordnungen zwischen Python- und SQL Server-Datentypen](python-libraries-and-data-types.md).

| Funktion| BESCHREIBUNG|
| ------- | ---------- |
| [RxInSqlServer](/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  Erstellt ein SQL Server-Computekontextobjekt, um Berechnungen in eine Remoteinstanz zu überführen. Mehrere **revoscalepy**-Funktionen verwenden den Computekontext als Argument. Ein Beispiel für einen Kontextwechsel finden Sie unter [Erstellen eines Modells mithilfe von revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md).|
| [RxSqlServerData](/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | Erstellt ein Datenobjekt basierend auf einer SQL Server-Abfrage oder -Tabelle |
| [RxOdbcData](/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| Erstellt eine Datenquelle basierend auf einer ODBC-Verbindung |
| [RxXdfData](/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | Erstellt eine Datenquelle basierend auf einer lokalen XDF-Datei. XDF-Dateien werden häufig verwendet, um In-Memory-Daten auf einen Datenträger auszulagern. Eine XDF-Datei kann nützlich sein, wenn Sie mit mehr Daten arbeiten als in einem Batch aus der Datenbank übertragen werden können oder als in den Arbeitsspeicher passen. Wenn Sie beispielsweise regelmäßig große Mengen von Daten aus einer Datenbank zu einer lokalen Arbeitsstation verschieben, anstatt die Datenbank wiederholt für jeden R-Vorgang abzufragen, können Sie die XDF-Datei als Cache verwenden, um die Daten lokal zu speichern und anschließend mit ihnen im R-Arbeitsbereich zu arbeiten. |

> [!TIP]
> Wenn Sie mit dem Konzept von Datenquellen oder Computekontexten noch nicht vertraut sind, empfiehlt es sich, zunächst den Artikel über [verteiltes Computing](/machine-learning-server/r/how-to-revoscaler-distributed-computing) in der Microsoft Machine Learning Server-Dokumentation zu lesen.

## <a name="2-data-manipulation-etl"></a>2: Datenbearbeitung (ETL)

| Funktion | BESCHREIBUNG |
|----------|-------------|
|[rx_import](/machine-learning-server/python-reference/revoscalepy/rx-import) | Importiert Daten in eine XDF-Datei oder einen Datenrahmen|
|[rx_data_step](/machine-learning-server/python-reference/revoscalepy/rx-data-step) | Wandelt Daten von einem Eingabedataset in ein Ausgabedataset um|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3: Schulung und Zusammenfassung

| Funktion| BESCHREIBUNG|
| ------- | ---------- |
|[rx_btrees](/machine-learning-server/python-reference/revoscalepy/rx-btrees) | Passt stochastische farbverlaufverstärkte Entscheidungsstrukturen an|
|[rx_dforest](/machine-learning-server/python-reference/revoscalepy/rx-dforest) | Passt Klassifizierungs- und Regressionsentscheidungswälder an|
|[rx_dtree](/machine-learning-server/python-reference/revoscalepy/rx-dtree) | Passt Klassifizierungs- und Regressionsbäume an |
|[rx_lin_mod](/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | Erstellen eines linearen Regressionsmodells|
|[rx_logit](/machine-learning-server/python-reference/revoscalepy/rx-logit) | Erstellen eines logistischen Regressionsmodells|
|[rx_summary](/machine-learning-server/python-reference/revoscalepy/rx-summary) | Erstellt univariate Zusammenfassungen von Objekten in revoscalepy.|

Sie sollten auch die Funktionen in [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) auf weitere Ansätze überprüfen.

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>4: Bewertungsfunktionen

| Funktion| BESCHREIBUNG|
| ------- | ---------- |
| [rx_predict](/machine-learning-server/python-reference/revoscalepy/rx-predict) | Generiert Vorhersagen aus einem trainierten Modell|) | Generiert Vorhersagen aus einem trainierten Modell und kann für die Echtzeitbewertung verwendet werden. |
|[rx_predict_default](/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | Berechnet vorhergesagte Werte und Restwerte mithilfe von rx_lin_mod- und rx_logit-Objekten |
|[rx_predict_rx_dforest](/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Berechnet vorhergesagte oder angepasste Werte für ein Dataset aus einem rx_dforest- oder rx_btrees-Objekt |
|[rx_predict_rx_dtree](/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Berechnet vorhergesagte oder angepasste Werte für ein Dataset aus einem rx_dtree-Objekt |

## <a name="how-to-work-with-revoscalepy"></a>Arbeiten mit revoscalepy

Funktionen in **revoscalepy** können in Python-Code aufgerufen werden, der in gespeicherten Prozeduren gekapselt ist. Die meisten Entwickler erstellen **revoscalepy**-Lösungen lokal, und migrieren den fertigen Python-Code anschließend als Bereitstellungsübung in gespeicherte Prozeduren.

Für eine lokale Ausführung führen Sie in der Regel ein Python-Skript über die Befehlszeile oder eine Python-Entwicklungsumgebung aus, und geben einen SQL Server-Computekontext an, indem Sie eine der **revoscalepy**-Funktionen verwenden. Sie können den Remotecomputekontext für den gesamten Code oder für einzelne Funktionen verwenden. Sie können beispielsweise das Modelltraining auf den Server auslagern, um die neuesten Daten zu verwenden und Datenverschiebung zu vermeiden.

Wenn Sie bereit sind, ein Python-Skript in einer gespeicherten Prozedur, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), zu kapseln, empfiehlt es sich, den Code als eine einzelne Funktion mit klar definierte Eingaben und Ausgaben neu zu schreiben. 

Eingaben und Ausgaben müssen **Pandas**-Datenrahmen sein. Wenn dies der Fall ist, können Sie die gespeicherte Prozedur von jedem Client aus abrufen, der T-SQL unterstützt, SQL-Abfragen problemlos als Eingaben übergeben und die Ergebnisse in SQL-Tabellen speichern. Ein Beispiel finden Sie unter [Informationen zur datenbankinternen Python-Analyse für SQL-Entwickler](../tutorials/python-taxi-classification-introduction.md).

### <a name="using-revoscalepy-with-microsoftml"></a>Verwenden von revoscalepy mit microsoftml

Die Python-Funktionen für [microsoftml](ref-py-microsoftml.md) sind in die Computekontexte und Datenquellen integriert, die in revoscalepy bereitgestellt werden. Wenn Sie in microsoftml Funktionen aufrufen, z. B. zum Definieren und Trainieren eines Modells, verwenden Sie die revoscalepy-Funktionen, um den Python-Code entweder lokal oder in einem SQL Server-Remotecomputekontext auszuführen.

Das folgende Beispiel zeigt die Syntax zum Importieren von Modulen im Python-Code. Sie können dann auf die einzelnen Funktionen, die Sie benötigen, verweisen.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Weitere Informationen

+ [Python-Tutorials](../tutorials/python-tutorials.md)
+ [Python-Referenz (Microsoft Machine Learning Server)](/machine-learning-server/python-reference/introducing-python-package-reference)