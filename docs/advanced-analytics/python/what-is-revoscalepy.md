---
title: Einführung in die Revoscalepy-Python-Paket in SQL Server-Machine Learning | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f1d4d8bbb47c34fce61bdb95a3184a1d2b10f4d1
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889476"
---
# <a name="introducing-revoscalepy-in-sql-server-machine-learning"></a>Einführung in Revoscalepy in SQL Server-Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**die Revoscalepy** von Microsoft zur Unterstützung der verteilten Verarbeitung Remote compute-Kontexte und leistungsstarke Algorithmen für Python-Entwickler eine neue Python-Bibliothek dient.

Es basiert auf der **RevoScaleR** -Paket für R, die in Microsoft R Server und SQL Server R Services und zielt darauf ab, die dieselbe Funktionalität bieten bereitgestellt wurde:

+ Unterstützt mehrere computekontexte, lokalen und remote
+ Bietet Funktionen, die in RevoScaleR gleich für die Datentransformation und Visualisierung
+ Python-Versionen von RevoScaleR Machine Learning-Algorithmen bietet zur verteilten oder parallele Verarbeitung
+ Verbesserte Leistung, einschließlich der Verwendung der Intel Math-Bibliotheken

MicrosoftML-Pakete werden für R und Python ebenfalls bereitgestellt werden. Weitere Informationen finden Sie unter [mithilfe MicrosoftML in SQL Server](../using-the-microsoftml-package.md)

## <a name="versions-and-supported-platforms"></a>Versionen und unterstützte Plattformen

Die **Revoscalepy** -Modul ist verfügbar nur wenn Sie eine der folgenden Microsoft-Produkte installieren:

+ Machine Learning-Dienste, die in SQLServer 2017
+ Microsoft Machine Learning Server 9.2.0 oder höher

Um die neueste Version von Revoscalepy zu erhalten, installieren Sie kumulative Update 1 für SQL Server 2017 aus. Sie enthält viele Verbesserungen an, in Python, u.a.:

+ Eine neue Python-Funktion, `rx_create_col_info`, Schemainformationen aus einer SQL Server-Datenquelle, z. B. abruft [RxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) für 
+ Verbesserungen bei der [Rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) zur Unterstützung der paralleler Szenarien für die Verwendung der `RxLocalParallel` compute Context verwenden. 

## <a name="supported-functions-and-data-types"></a>Unterstützte Funktionen und Datentypen

Dieser Abschnitt enthält eine Übersicht über die Python-Datentypen und eine neue Python-Funktionen, die in unterstützt die **Revoscalepy** ab Version von SQL Server 2017 CTP 2.0-Modul. 

Die aktuelle Liste der Funktionen in der Python-Bibliotheken, die bisher veröffentlichten finden Sie unter folgenden Links:

+ [die Revoscalepy für Python](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

+ [Microsoftml für Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

### <a name="data-types-data-sources-and-compute-contexts"></a>Datentypen, Datenquellen und computekontexten

Verwenden unterschiedliche Datentypen in einigen Fällen, SQL Server und Python. Eine Liste der Zuordnungen zwischen SQL und Python-Datentypen, finden Sie unter [Python-Erweiterung](../concepts/extension-python.md).

Für Machine Learning mit Python in SQL Server unterstützte Datenquellen enthält ODBC-Datenquellen, SQL Server-Datenbank und lokale Dateien, einschließlich der XDF-Dateien.

Sie erstellen das neue Datenquellenobjekt mithilfe der Funktionen in der folgenden Tabelle aufgeführt sind. Nach dem Definieren der Datenquelle an, Sie laden oder Transformieren der Daten mit einer entsprechenden [ETL-Funktion](#bkmk_etl).

> [!IMPORTANT]
> Viele Funktionsnamen wurden seit der ersten Version von Python in CTP 2.0 geändert.

**SQL Server-Daten**

+ Verwendung [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) zum Definieren einer Datenquelle aus einer Abfrage oder eine Tabelle
+ Verwendung [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserver) zum Erstellen einer SQL Server-computekontexts
+ Verwendung [RxOdbcData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxodbcdata) So erstellen eine Datenquelle aus einer ODBC-Verbindung

**die Revoscalepy** unterstützt auch die [XDF-Datenquelle](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxxdfdata), die für das Verschieben von Daten zwischen Arbeitsspeicher und anderen Datenquellen verwendet.

> [!TIP]
> Wenn Sie noch nicht mit der Vorstellung von Datenquellen oder computekontexte, es wird empfohlen, die Sie starten, indem Themen zu verteilten computing – Funktionsweise für Machine Learning in [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-introduction).


### <a name="bkmk_algorithms"></a>Machine Learning und Zusammenfassungsfunktionen

Die folgenden Machine Learning-Algorithmen und die Zusammenfassung von RevoScaleR-Funktionen sind in SQL Server 2017 ab CTP 2.0 enthalten.

| Funktion| Description|Hinweise|
| ------ | ------ |------ |
|`rx_btrees` | Mit ähnlichen Zeichen stochastic Gradient-boosted-Decision-Strukturen|`rx_btrees_ex` in CTP 2.0|
|`rx_dforest` | Passen Sie die Klassifizierung und Regression entscheidungswälder|`rx_dforest_ex` in CTP 2.0|
|`rx_dtree` | Mit ähnlichen Strukturen für Klassifizierung und regression |`rx_dtree_ex` in CTP 2.0|
|`rx_lin_mod` | Erstellen Sie ein Lineares Modell|`rx_lin_mod_ex` in CTP 2.0|
|`rx_logit` | Erstellen eines logistischen Regressionsmodells|`rx_logit_ex` in CTP 2.0|
|`rx_predict` | Generieren von Vorhersagen aus einem trainierten Modell|`rx_predict_ex` in CTP 2.0|
|`rx_summary` | Generieren Sie eine Zusammenfassung des Modells||

Neue Machine Learning-Algorithmen werden ebenfalls bereitgestellt, von der Python-Version von [MicrosoftML](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package):

| Funktion| Description|
| ------ | ------ |
|`rx_fast_forest` |Erstellen Sie ein Decision Forest-Modell|
|`rx_fast_linear` | Lineare Regression mit stochastischen dual-Koordinate Versalhöhe|
|`rx_fast_trees` | Erstellen eines verstärkten Entscheidungsbaummodells |
|`rx_logistic_regression` | Erstellen eines logistischen Regressionsmodells|
|`rx_neural_network` | Erstellen eines anpassbaren neuronalen Netzwerkmodells |
|`rx_oneclass_svm` | Erstellt ein SVM-Modell für ein Dataset unausgeglichenen für die Verwendung in der Erkennung von Anomalien|

> [!TIP]
> Viele der folgenden Algorithmen werden bereits als Module in Azure Machine Learning bereitgestellt.

MicrosoftML für Python umfasst auch eine Reihe von Transformationen und Hilfsfunktionen, z. B.:

+ `rx_predict` Vorhersagen von einem trainierten Modell generiert und kann verwendet werden, für die Bewertung in Echtzeit
+ Image-featurebereitstellung-Funktionen
+ Funktionen für die Verarbeitung und der Stimmung Ausdrucksextrahierung

Weitere Informationen finden Sie unter [Einführung in MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> Die Python-Community verwendet Programmierung Konventionen, die möglicherweise unterscheiden, was Sie mit, einschließlich aller Kleinbuchstaben und Unterstriche statt Kamel-Schreibweise für Parameternamen sind. Darüber hinaus möglicherweise haben Sie bemerkt, die die **Revoscalepy** Bibliothek ist immer in Kleinbuchstaben. Das stimmt! Eine weitere Python-Konvention.
> 
> Sehen Sie sich die Tipps in der Python-Referenzdokumentation für die Microsoft R: [Python-Funktion Help][Python Funktionen](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="examples"></a>Beispiele

Sie können den Code, der enthält ausführen **Revoscalepy** Funktionen entweder lokal oder in einem remotecomputekontext. Sie können auch Python in SQL Server ausführen, durch das Einbetten von Python-Code in einer gespeicherten Prozedur.

Bei lokaler Ausführung Sie in der Regel ein Python-Skript über die Befehlszeile oder über eine Python-Entwicklungsumgebung ausgeführt, und geben Sie einen SQL Server-computekontext mithilfe eines der **Revoscalepy** Funktionen. Sie können den entfernten computekontext für den gesamten Code oder für einzelne Funktionen verwenden. Beispielsweise empfiehlt es sich zum Trainieren des Modells mit dem Server verwenden die neuesten Daten und vermeiden datenverschiebungen auslagern.

Wenn Sie ein vollständiges Python-Skript in der gespeicherten Prozedur, platzieren möchten [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), es wird empfohlen, dass Sie den Code als eine einzelne Funktion schreiben, die eindeutig die Eingaben und Ausgaben definiert wurde. Eingaben und Ausgaben muss **Pandas** Datenrahmen. Wenn dies abgeschlossen ist, können Sie rufen die gespeicherte Prozedur von jedem Client, der T-SQL unterstützt, einfach SQL-Abfragen als Eingabe übergeben und die Ergebnisse in SQL-Tabellen speichern. Ein Beispiel finden Sie unter [In-Database Python Analytics for SQL-Developers](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-remote-compute-contexts"></a>Verwenden von remotecomputekontexten

+ [Erstellen eines Modells mithilfe von revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md)

  Dieses Beispiel zeigt, wie Sie Python mit einer Instanz von SQL Server als Compute Context ausführen.

### <a name="using-a-stored-procedure"></a>Verwenden von gespeicherten Prozeduren

+ [Ausführen von Python mit T-SQL](../tutorials/run-python-using-t-sql.md)

  In diesem Beispiel wird veranschaulicht, den grundlegenden Mechanismus von Aufrufen von Python-Skript, das in einer gespeicherten Prozedur eingebettet ist.

### <a name="using-revoscalepy-with-microsoftml"></a>Mithilfe von Revoscalepy mit MicrosoftML

Die Python-Funktionen für MicrosoftML sind integriert, mit dem berechneten Kontexten und Datenquellen, die in Revoscalepy bereitgestellt werden. Aus diesem Grund können Sie mithilfe ein Algorithmus MicrosoftML definieren und Trainieren eines Modells in Python und die Revoscalepy-Funktionen zum Ausführen des Python-Codes, entweder lokal oder in einem SQl Server-computekontext verwenden.

Importieren Sie die Module in Ihrem Python-Code, und verweisen Sie dann die einzelnen Funktionen, die Sie benötigen.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

### <a name="requirements"></a>Anforderungen

Führen Sie Python-Code in SQL Server muss installiert sein SQL Server 2017 zusammen mit der Funktion **Machine Learning Services**, und aktiviert die Python-Sprache. Frühere Versionen von SQL Server unterstützen keine Integration von Python.

> [!NOTE]
> SQL Server-rechenkontext unterstützt Open-Source-Verteilungen von Python nicht. Allerdings können Sie bei Bedarf zum Veröffentlichen und nutzen Python-Anwendungen von Windows, Microsoft Machine Learning Server installieren, ohne die Installation von SQL Server. Weitere Informationen finden Sie unter [Installieren von SQL Server 2017 Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md).

## <a name="get-more-help"></a>Weitere Hilfe

Vollständige Dokumentation für diese APIs sind verfügbar, wenn das Produkt veröffentlicht wird. In der Zwischenzeit wird empfohlen, dass Sie die entsprechende Funktion in die Revoscaler- oder MicrosoftML-Bibliotheken verweisen.

+ [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler).
+ [MicrosoftML](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)

Sie können Hilfe für jede Python-Funktion durch Importieren des Moduls, und dem anschließenden Aufrufen `help()`. Z. B. Ausführung `help(revoscalepy)` über Ihre IDE Python gibt Sie eine Liste aller Funktionen in die Revoscalepy-Modul, mit deren Signaturen.

Wenn Sie Python-Tools für Visual Studio verwenden, können Sie IntelliSense verwenden, um Syntax und Argument-Hilfe zu erhalten. Weitere Informationen finden Sie unter [Python-Unterstützung in Visual Studio](http://docs.microsoft.com/visualstudio/python/installation), und Laden Sie die Erweiterung, die Ihrer Version von Visual Studio entspricht. Sie können Python mit Visual Studio 2015 und 2017 und früheren Versionen verwenden.

## <a name="see-also"></a>Siehe auch

[Python-Tutorials](../tutorials/sql-server-python-tutorials.md)
