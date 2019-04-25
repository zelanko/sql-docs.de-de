---
title: 'die Revoscalepy-Python-Paket: SQL Server Machine Learning Services'
description: Einführung in die Revoscalepy-Modul in SQL Server 2017 Machine Learning-Diensten mit Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e0cded793f6017398641ffa055deec62010b2b3d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642461"
---
# <a name="revoscalepy-python-module-in-sql-server"></a>die Revoscalepy (Python-Modul in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**die Revoscalepy** ist ein Modul Python35 kompatible von Microsoft, die verteilte Verarbeitung unterstützt, remoterechenkontexte und leistungsfähige Data Science-Algorithmen. Es basiert auf der **RevoScaleR** -Paket für R (zusammen mit Microsoft R Server und SQL Server R Services), ähnliche Funktionen bietet:

+ Lokal und Remote computekontexte für Systeme mit derselben Version von **Revoscalepy**
+ Data Transformation und Visualisierung-Funktionen
+ Data Science-Funktionen, skalierbare, verteilte oder parallele Verarbeitung
+ Verbesserte Leistung, einschließlich der Verwendung der Intel Math-Bibliotheken

Datenquellen und computekontexten, die Sie, in erstellen **Revoscalepy** kann auch in Machine Learning-Algorithmen verwendet werden. Eine Einführung zu diesen Algorithmen finden Sie unter [Microsoftml-Python-Modul in SQL Server](ref-py-microsoftml.md).

## <a name="full-reference-documentation"></a>Vollständige Referenz-Dokumentation

Die **Revoscalepy** Bibliothek wird in mehreren Microsoft-Produkte verteilt, aber wird, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die Funktionen identisch sind, [Dokumentation für einzelne Revoscalepy Funktionen](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) in nur einem Ort unter veröffentlicht wird die [Python-Referenz](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) für Microsoft Machine Learning Server. Sollten Sie jede Produkt-spezifische Verhalten vorhanden ist, wird Diskrepanzen auf der Hilfeseite für die Funktion angegeben.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Die **Revoscalepy** Modul basierend auf Python 3.5 und verfügbar ist, nur, wenn Sie eine der folgenden Microsoft-Produkten oder Downloads installieren:

+ [SQL Server 2017-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Python-Clientbibliotheken für ein Data Science-client](setup-python-client-tools-sql.md)

> [!NOTE]
> Releaseversionen der Vollversion des Produkts sind Windows ausschließlich ab SQL Server 2017. Linux-Unterstützung für **Revoscalepy** ist neu in [Vorschau von SQL Server-2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Funktionen, die nach Kategorie

Dieser Abschnitt listet die Funktionen nach Kategorie, erhalten Sie einen Überblick darüber, wie jeweils verwendet wird. Sie können auch die [Inhaltsverzeichnis](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) Sie Funktionen in alphabetischer Reihenfolge suchen.

## <a name="1-data-source-and-compute"></a>1-Datenquelle und compute

**die Revoscalepy** enthält Funktionen zum Erstellen von Datenquellen und Festlegen des Speicherorts, oder *computekontext*, der, in dem Berechnungen ausgeführt werden. Funktionen, die relevant für SQL Server-Szenarien werden in der folgenden Tabelle aufgeführt.

Verwenden unterschiedliche Datentypen in einigen Fällen, SQL Server und Python. Eine Liste der Zuordnungen zwischen SQL und Python-Datentypen, finden Sie unter [Python-an-SQL-Datentypen](python-libraries-and-data-types.md).

| Funktion| Description|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  Erstellen Sie eine SQL Server Compute Context-Objekt, Push-Berechnungen auf einer remote-Instanz. Mehrere **Revoscalepy** Funktionen nehmen computekontext als Argument. Ein Wechsel des Ausführungskontexts Beispiel finden Sie unter [Erstellen eines Modells mithilfe von Revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md).|
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | Erstellen Sie ein Datenobjekt, das basierend auf einer SQL Server-Abfrage oder Tabelle. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| Erstellen Sie eine Datenquelle basierend auf einer ODBC-Verbindung. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | Erstellen Sie eine Datenquelle basierend auf eine lokale XDF-Datei. XDF-Dateien werden häufig verwendet, um in-Memory-Daten auf den Datenträger auszulagern. Eine XDF-Datei kann nützlich sein, bei der Verwendung von mehr Daten als aus der Datenbank in einem einzigen Batch übertragen werden kann, oder mehr Daten als in den Speicher passen. Z. B. Wenn Sie regelmäßig große Mengen von Daten aus einer Datenbank zu einer lokalen Arbeitsstation verschieben, anstatt die Abfrage der Datenbank wiederholt für jede R-Vorgang können Sie die XDF-Datei als eine Art von Cache die Daten lokal speichern, und klicken Sie dann mit Ihren R-Arbeitsbereich bearbeiten. |

> [!TIP]
> Wenn Sie noch nicht mit der Vorstellung von Datenquellen oder computekontexte, es wird empfohlen, zunächst [verteilte Verarbeitung](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) in der Microsoft Machine Learning Server-Dokumentation.

## <a name="2-data-manipulation-etl"></a>2 – datenbearbeitung (ETL)

| Funktion | Description |
|----------|-------------|
|[rx_import](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-import) | Importieren von Daten in einer xdf-Datei oder einem Datenrahmen.|
|[rx_data_step](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-data-step) | Transformieren von Daten aus einem Eingabedataset auf einen Ausgabe-DataSet.|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3-Training und Zusammenfassung

| Funktion| Description|
| ------- | ---------- |
|[rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) | Mit ähnlichen Zeichen stochastic Gradient-boosted-Decision-Strukturen|
|[rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) | Passen Sie die Klassifizierung und Regression entscheidungswälder|
|[rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) | Mit ähnlichen Strukturen für Klassifizierung und regression |
|[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | Erstellen eines linearen Regressionsmodells|
|[rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) | Erstellen eines logistischen Regressionsmodells|
|[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) | Erzeugen von Univariate Zusammenfassungen von Objekten in Revoscalepy.|

Überprüfen Sie auch die Funktionen in [Microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) für weitere Ansätze.

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>4-Bewertung-Funktionen

| Funktion| Description|
| ------- | ---------- |
| [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Generieren von Vorhersagen aus einem trainierten Modell|) | Vorhersagen von einem trainierten Modell generiert und kann verwendet werden, für die Bewertung in Echtzeit. |
|[rx_predict_default](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | Berechnen Sie vorhergesagten Werte und Residuen Rx_lin_mod und Rx_logit-Objekte verwenden. |
|[rx_predict_rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Für ein Dataset aus einem Objekt Rx_dforest oder Rx_btrees vorhergesagten oder eingepasste Werte zu berechnen. |
|[rx_predict_rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Für ein Dataset aus einem Objekt Rx_dtree vorhergesagten oder eingepasste Werte zu berechnen. |

## <a name="how-to-work-with-revoscalepy"></a>Arbeiten mit revoscalepy

Funktionen in **Revoscalepy** in Python-Code gekapselt, die in gespeicherten Prozeduren können aufgerufen werden. Die meisten Entwickler erstellen **Revoscalepy** Lösungen lokal, und migrieren Sie dann die komplette Python-Code zu gespeicherten Prozeduren als eine Übung für die Bereitstellung.

Bei lokaler Ausführung Sie in der Regel ein Python-Skript über die Befehlszeile oder über eine Python-Entwicklungsumgebung ausgeführt, und geben Sie einen SQL Server-computekontext mithilfe eines der **Revoscalepy** Funktionen. Sie können den entfernten computekontext für den gesamten Code oder für einzelne Funktionen verwenden. Beispielsweise empfiehlt es sich zum Trainieren des Modells mit dem Server verwenden die neuesten Daten und vermeiden datenverschiebungen auslagern.

Wenn Sie bereit sind, kapseln Python-Skript innerhalb einer gespeicherten Prozedur, [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), es wird empfohlen, den Code umzuschreiben, als einzelne Funktion, die eindeutig die Eingaben und Ausgaben definiert wurde. 

Eingaben und Ausgaben muss **Pandas** Datenrahmen. Wenn dies abgeschlossen ist, können Sie rufen die gespeicherte Prozedur von jedem Client, der T-SQL unterstützt, einfach SQL-Abfragen als Eingabe übergeben und die Ergebnisse in SQL-Tabellen speichern. Ein Beispiel finden Sie unter [erfahren Sie mehr in-Database Python Analytics für SQL-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-revoscalepy-with-microsoftml"></a>Mithilfe von Revoscalepy mit microsoftml

Die Python-Funktionen für [Microsoftml](ref-py-microsoftml.md) sind integriert, mit der Compute-Kontexte und Datenquellen, die in Revoscalepy bereitgestellt werden. Beim Aufruf von Funktionen aus Microsoftml, z. B. beim Definieren und das training eines Modells verwenden Sie die Revoscalepy Funktionen zum Ausführen von Python code entweder lokal oder in einer SQl Server-remote-computekontext.

Das folgende Beispiel zeigt die Syntax zum Importieren von Modulen in Ihren Python-Code. Sie können dann die einzelnen Funktionen verweisen, die Sie benötigen.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Siehe auch

+ [Python-Tutorials](../tutorials/sql-server-python-tutorials.md)
+ [Tutorial: Einbetten von Python-Code in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Python-Referenz (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)
