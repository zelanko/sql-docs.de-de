---
title: revoscalepy-Python-Paket
description: Einführung in das revoscalepy-Modul in SQL Server 2017 Machine Learning Services mit Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e38cac8969544a93d7487d83636c866ec7b09ce9
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344611"
---
# <a name="revoscalepy-python-module-in-sql-server"></a>revoscalepy (Python-Modul in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy** ist ein Python35 kompatibles Modul von Microsoft, das verteiltes Computing, remotecomputekontexte und Hochleistungs-Data Science Algorithmen unterstützt. Es basiert auf dem **revoscaler** -Paket für R (verteilt mit Microsoft R Server und SQL Server R Services) und bietet eine ähnliche Funktionalität:

+ Lokale und remotecomputekontexte auf Systemen mit derselben Version von **revoscalepy**
+ Funktionen für die Datentransformation und-Visualisierung
+ Data Science-Funktionen, skalierbar durch verteilte oder parallele Verarbeitung
+ Verbesserte Leistung, einschließlich der Verwendung der mathematischen Intel-Bibliotheken

Datenquellen und computekontexte, die Sie in **revoscalepy** erstellen, können auch in Algorithmen für Maschinelles Lernen verwendet werden. Eine Einführung zu diesen Algorithmen finden Sie unter [microsoftml Python-Modul in SQL Server](ref-py-microsoftml.md).

## <a name="full-reference-documentation"></a>Vollständige Referenz Dokumentation

Die **revoscalepy** -Bibliothek wird in mehreren Microsoft-Produkten verteilt, aber die Verwendung ist identisch, unabhängig davon, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die-Funktionen identisch sind, wird die [Dokumentation für einzelne revoscalepy-Funktionen](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) nur an einem Speicherort unter der [python-Referenz](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) für Microsoft Machine Learning Server veröffentlicht. Wenn produktspezifische Verhalten vorhanden sind, werden auf der Hilfeseite der Funktion Abweichungen festgestellt.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Das **revoscalepy** -Modul basiert auf Python 3,5 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder-Downloads installieren:

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Python-Client Bibliotheken für einen Data Science-Client](setup-python-client-tools-sql.md)

> [!NOTE]
> Vollversion der Produktversion ist nur Windows, beginnend mit SQL Server 2017. Die Linux-Unterstützung für **revoscalepy** ist neu in [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorie aufgelistet, um Ihnen einen Überblick darüber zu verschaffen, wie die einzelnen Funktionen verwendet werden. Sie können auch das Inhalts [Verzeichnis](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) verwenden, um Funktionen in alphabetischer Reihenfolge zu suchen.

## <a name="1-data-source-and-compute"></a>1: Datenquelle und Compute

**revoscalepy** enthält Funktionen zum Erstellen von Datenquellen und zum Festlegen des Speicher Orts bzw. des computekontexts, in dem Berechnungen durchgeführt werden. In der folgenden Tabelle sind die für SQL Server Szenarien relevanten Funktionen aufgeführt.

SQL Server und Python verwenden in einigen Fällen unterschiedliche Datentypen. Eine Liste der Zuordnungen zwischen SQL-und python-Datentypen finden [Sie unter Python-zu-SQL-Datentypen](python-libraries-and-data-types.md).

| Funktion| Beschreibung|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  Erstellen Sie ein SQL Server computekontext-Objekt, um Berechnungen in eine Remote Instanz zu überführen. Mehrere **revoscalepy** -Funktionen nehmen den computekontext als Argument an. Ein Beispiel für einen Kontextwechsel finden [Sie unter Erstellen eines Modells mithilfe von revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md).|
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | Erstellen Sie ein Datenobjekt, das auf einer SQL Server Abfrage oder Tabelle basiert. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| Erstellen Sie eine Datenquelle basierend auf einer ODBC-Verbindung. |
| [Rxxdfdata](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | Erstellen Sie eine Datenquelle basierend auf einer lokalen Xdf-Datei. Xdf-Dateien werden häufig verwendet, um in-Memory-Daten auf den Datenträger zu laden. Eine Xdf-Datei kann nützlich sein, wenn Sie mit mehr Daten arbeiten, als aus der Datenbank in einem Batch übertragen werden können, oder mehr Daten als in den Arbeitsspeicher passen. Wenn Sie z. b. regelmäßig große Datenmengen aus einer Datenbank auf eine lokale Arbeitsstation verschieben, anstatt die Datenbank für jeden R-Vorgang wiederholt abzufragen, können Sie die Xdf-Datei als eine Art Cache verwenden, um die Daten lokal zu speichern und dann in Ihrem R-Arbeitsbereich zu arbeiten. |

> [!TIP]
> Wenn Sie mit der Idee von Datenquellen oder computekontexten noch nicht vertraut sind, empfehlen wir Ihnen, mit der [verteilten Verarbeitung](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) in der Microsoft Machine Learning Server-Dokumentation zu beginnen.

## <a name="2-data-manipulation-etl"></a>2-Datenbearbeitung (ETL)

| Funktion | Beschreibung |
|----------|-------------|
|[rx_import](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-import) | Importieren Sie Daten in eine Xdf-Datei oder einen Datenrahmen.|
|[rx_data_step](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-data-step) | Transformieren von Daten aus einem Eingabe DataSet in ein Ausgabe DataSet.|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3\. Schulung und Zusammenfassung

| Funktion| Beschreibung|
| ------- | ---------- |
|[rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) | Stochastischen Gradient-verstärkte Entscheidungsbäume anpassen|
|[rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) | Anpassen von Klassifizierungs-und Regressions Entscheidungs Gesamtstrukturen|
|[rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) | Anpassen von Klassifizierungs-und Regressions Strukturen |
|[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | Erstellen eines linearen Regressionsmodells|
|[rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) | Erstellen eines logistischen Regressionsmodells|
|[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) | Erstellt Univariate-Zusammenfassungen von Objekten in revoscalepy.|

Sie sollten auch die Funktionen in [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) überprüfen, um weitere Ansätze zu finden.

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>4-Bewertungs Funktionen

| Funktion| Beschreibung|
| ------- | ---------- |
| [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Generieren von Vorhersagen aus einem trainierten Modell|) | Generiert Vorhersagen aus einem trainierten Modell und kann für die Echtzeitbewertung verwendet werden. |
|[rx_predict_default](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | Berechnen Sie vorhergesagte Werte und residuale mithilfe von rx_lin_mod-und rx_logit-Objekten. |
|[rx_predict_rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Berechnen Sie vorhergesagte oder eingelegte Werte für ein DataSet aus einem rx_dforest-oder rx_btrees-Objekt. |
|[rx_predict_rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Berechnen Sie vorhergesagte oder eingelegte Werte für ein DataSet aus einem rx_dtree-Objekt. |

## <a name="how-to-work-with-revoscalepy"></a>Arbeiten mit revoscalepy

Funktionen in **revoscalepy** können in Python-Code in gespeicherten Prozeduren gekapselt werden. Die meisten Entwickler erstellen **revoscalepy** -Lösungen lokal und Migrieren dann fertigen Python-Code zu gespeicherten Prozeduren als Bereitstellungs Übung.

Wenn Sie lokal ausgeführt werden, führen Sie in der Regel ein Python-Skript über die Befehlszeile oder eine python-Entwicklungsumgebung aus, und geben Sie einen SQL Server computekontext mit einer der **revoscalepy** -Funktionen an. Sie können den remotecomputekontext für den gesamten Code oder für einzelne Funktionen verwenden. Beispielsweise können Sie die Modell Schulung auf den Server auslagern, um die neuesten Daten zu verwenden und die Daten Verschiebung zu vermeiden.

Wenn Sie bereit sind, ein Python-Skript in einer gespeicherten Prozedur, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), zu kapseln, empfiehlt es sich, den Code als einzelne Funktion zu umschreiben, die klar definierte Eingaben und Ausgaben aufweist. 

Eingaben und Ausgaben müssen **Pandas** -Datenrahmen sein. Wenn dies der Fall ist, können Sie die gespeicherte Prozedur von jedem Client aus abrufen, der T-SQL unterstützt, SQL-Abfragen problemlos als Eingaben übergeben und die Ergebnisse in SQL-Tabellen speichern. Ein Beispiel finden Sie unter [Erlernen von Daten bankinterner python-Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-revoscalepy-with-microsoftml"></a>Verwenden von revoscalepy mit microsoftml

Die python-Funktionen für [microsoftml](ref-py-microsoftml.md) sind in die computekontexte und Datenquellen integriert, die in revoscalepy bereitgestellt werden. Wenn Sie Funktionen von microsoftml aufrufen, z. b. Wenn Sie ein Modell definieren und trainieren, verwenden Sie die revoscalepy-Funktionen, um den Python-Code entweder lokal oder in einem SQL Server-remotecomputekontext auszuführen.

Das folgende Beispiel zeigt die Syntax zum Importieren von Modulen in ihren Python-Code. Sie können dann auf die einzelnen Funktionen verweisen, die Sie benötigen.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Siehe auch

+ [Python-Tutorials](../tutorials/sql-server-python-tutorials.md)
+ [Tutorial: Einbetten von Python-Code in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Python-Referenz (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)
