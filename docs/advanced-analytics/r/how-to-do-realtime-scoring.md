---
title: Generieren von Prognosen und Vorhersagen
description: Verwenden Sie rxPredict oder sp_rxPredict für die Echtzeitbewertung, bzw. PREDICT T-SQL zur nativen Bewertung für Vorhersagen und Prognosen in R und Python in SQL Server Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7822cd56a52e47493fe175c293dbfe491a9524af
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727434"
---
# <a name="how-to-generate-forecasts-and-predictions-using-machine-learning-models-in-sql-server"></a>Vorgehensweise: Generieren von Prognosen und Vorhersagen mit Modellen für maschinelles Lernen in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die Verwendung eines vorhandenen Modells zum Prognostizieren oder Vorhersagen von Ergebnissen für neue Dateneingaben ist eine zentrale Aufgabe des maschinellen Lernens. In diesem Artikel werden die Ansätze zum Generieren von Vorhersagen in SQL Server aufgelistet. Zu den Ansätzen zählen interne Verarbeitungsmethodiken für Hochgeschwindigkeits-Vorhersagen, bei denen die Geschwindigkeit auf inkrementellen Reduzierungen von Runtimeabhängigkeiten basiert. Weniger Abhängigkeiten bedeuten schnellere Vorhersagen.

Die Verwendung der internen Verarbeitungsinfrastruktur (Echtzeit- oder native Bewertung) ist mit Bibliotheksanforderungen verbunden. Funktionen müssen aus den Microsoft-Bibliotheken stammen. R- oder Python-Code, der Open-Source-Funktionen oder Funktionen von Drittanbietern aufruft, wird in CLR- oder C++-Erweiterungen nicht unterstützt.

In der folgenden Tabelle werden die Bewertungsframeworks für Prognosen und Vorhersagen zusammengefasst. 

| Methodik           | Schnittstelle         | Anforderungen an Bibliotheken | Verarbeitungsgeschwindigkeiten |
|-----------------------|-------------------|----------------------|----------------------|
| Erweiterbarkeitsframework | [rxPredict (R)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) <br/>[rx_predict (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Keine. Modelle können auf jeder R- oder Python-Funktion basieren. | Hunderte von Millisekunden. <br/>Das Laden einer Runtimeumgebung hat Fixkosten von durchschnittlich 300 bis 600 Millisekunden, bevor neue Daten bewertet werden. |
| [Echtzeitbewertung mit CLR-Erweiterung](../real-time-scoring.md) | [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) auf einem serialisierten Modell | R: RevoScaleR, MicrosoftML <br/>Python: revoscalepy, microsoftml | Durchschnittlich ein Mehrfaches von zehn Millisekunden. |
| [Native Bewertung mit C++-Erweiterung](../sql-native-scoring.md) | [PREDICT T-SQL-Funktion](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) auf einem serialisierten Modell | R: RevoScaleR <br/>Python: revoscalepy | Durchschnittlich weniger als 20 Millisekunden. | 

Die Verarbeitungsgeschwindigkeit und nicht der Inhalt der Ausgabe ist das differenzierende Feature. Bei identischen Funktionen und Eingaben sollte die bewertete Ausgabe nicht vom Ansatz Ihrer Wahl abhängig variieren.

Das Modell muss mit einer unterstützten Funktion erstellt und dann in einen unformatierten Bytedatenstrom serialisiert auf einem Datenträger oder im Binärformat in einer Datenbank gespeichert werden. Mithilfe einer gespeicherten Prozedur oder T-SQL können Sie ein binäres Modell ohne den Aufwand einer R- oder Python-Sprachruntime laden und verwenden, was beim Generieren von Vorhersagebewertungen aufgrund neuer Eingaben schneller zum Abschluss führt.

Die Bedeutung von CLR- und C++-Erweiterungen liegt in der Nähe zur Datenbank-Engine selbst. Die native Sprache der Datenbank-Engine ist C++. Dies bedeutet, dass in C++ erstellte Erweiterungen mit weniger Abhängigkeiten ausgeführt werden. Im Gegensatz dazu sind CLR-Erweiterungen von .NET Core abhängig. 

Wie Sie vielleicht erwarten, ist die Plattformunterstützung von diesen Runtimeumgebungen betroffen. Native Datenbank-Engine-Erweiterungen werden überall dort ausgeführt, wo die relationale Datenbank unterstützt wird: Windows, Linux, Azure. CLR-Erweiterungen mit der .NET Core-Anforderung werden derzeit nur von Windows unterstützt.

## <a name="scoring-overview"></a>Bewertungsübersicht

Die _Bewertung_ umfasst zwei Schritte. Geben Sie zunächst ein bereits trainiertes Modell an, das aus einer Tabelle geladen werden soll. Übergeben Sie zweitens neue Eingabedaten an die Funktion, um Vorhersagewerte (oder _Bewertungen_) zu generieren. Die Eingabe ist häufig eine T-SQL-Abfrage, die entweder tabellarische oder einzelne Zeilen zurückgibt. Sie können auswählen, ob ein einzelner Spaltenwert ausgegeben werden soll, der eine Wahrscheinlichkeit darstellt, oder Sie könnten mehrere Werte ausgeben, z. B. ein Vertrauensintervall, einen Fehler oder eine andere hilfreiche Ergänzung der Vorhersage.

Der Gesamtprozess der Vorbereitung des Modells und das anschließende Generieren von Bewertungen kann auf diese Weise zusammengefasst werden:

1. Erstellen eines Modells mit einem unterstützten Algorithmus. Die Unterstützung variiert je nach der gewählten Bewertungsmethodik.
2. Trainieren des Modells.
3. Serialisieren des Modells mithilfe eines speziellen Binärformats.
3. Speichern des Modells in SQL Server. Dies bedeutet in der Regel, dass das serialisierte Modell in einer SQL Server-Tabelle gespeichert wird.
4. Aufruf der Funktion oder gespeicherten Prozedur, Angabe von Modell und Dateneingaben als Parameter.

Wenn die Eingabe viele Datenzeilen enthält, ist es in der Regel schneller, die Vorhersagewerte als Teil des Bewertungsprozesses in eine Tabelle einzufügen. Das Generieren einer einzelnen Bewertung ist typischer in einem Szenario, in dem Sie Eingabewerte aus einer Formular- oder Benutzeranforderung erhalten und die Bewertung an eine Clientanwendung zurückgeben. Um die Leistung beim Generieren aufeinander folgender Bewertungen zu verbessern, könnte SQL Server das Modell zwischenspeichern, sodass es erneut in den Arbeitsspeicher geladen werden kann.

## <a name="compare-methods"></a>Vergleich der Methoden

Um die Integrität der zentralen Datenbank-Engine-Prozesse beizubehalten, wird die Unterstützung für R und Python in einer dualen Architektur aktiviert, die die Sprachverarbeitung von der RDBMS-Verarbeitung isoliert. Ab SQL Server 2016 wurde von Microsoft ein Erweiterbarkeitsframework hinzugefügt, das die Ausführung von R-Skripts aus T-SQL ermöglicht. In SQL Server 2017 wurde die Python-Integration hinzugefügt. 

Das Erweiterbarkeitsframework unterstützt jeden Vorgang, den Sie in R oder Python ausführen könnten, und reicht von einfachen Funktionen bis hin zum Trainieren komplexer Modelle für maschinelles Lernen. Allerdings erfordert die Dualverarbeitungsarchitektur, dass unabhängig von der Komplexität des Vorgangs ein externer R- oder Python-Prozess für jeden Aufruf aufgerufen wird. Wenn die Workload mit dem Laden eines vorab trainierten Modells aus einer Tabelle und dessen Bewertung auf der Grundlage der bereits in SQL Server vorhandenen Daten verbunden ist, führt der Aufwand des Aufrufs externer Prozesse zu einer unter bestimmten Umständen unakzeptablen Latenz. Beispielsweise erfordert die Betrugserkennung eine schnelle Bewertung, damit sie relevant sein kann.

Um Bewertungsgeschwindigkeiten für Szenarien wie die Betrugserkennung zu erhöhen, hat SQL Server integrierte Bewertungsbibliotheken als C++- und CLR-Erweiterungen hinzugefügt, die den Aufwand von R- und Python-Startprozessen vermeiden.

Die [**Echtzeitbewertung**](../real-time-scoring.md) war die erste Lösung für die Bewertung mit hoher Leistung. Die in frühen Versionen von SQL Server 2017 und neueren Updates von SQL Server 2016 eingeführte Echtzeitbewertung basiert auf CLR-Bibliotheken, die die R- und Python-Verarbeitung über von Microsoft gesteuerte Funktionen in RevoScaleR, MicrosoftML (R), revoscalepy und microsoftml (Python) vertreten. CLR-Bibliotheken werden mithilfe der gespeicherten Prozedur **sp_rxPredict** aufgerufen, um Ergebnisse aus einem beliebigen unterstützten Modelltyp zu generieren, ohne die R- oder Python-Runtime aufzurufen.

Die [**native Bewertung**](../sql-native-scoring.md) ist eine als native C++-Bibliothek implementierte SQL Server 2017-Funktion, jedoch nur für RevoScaleR- und revoscalepy-Modelle. Dies ist der schnellste und sicherere Ansatz, unterstützt jedoch relativ zu anderen Methodiken einen kleineren Satz von Funktionen.

## <a name="choose-a-scoring-method"></a>Auswählen einer Bewertungsmethode

Plattformanforderungen schreiben oft die zu verwendende Bewertungsmethodik vor.

| Produktversion und Plattform | Methodik |
|------------------------------|-------------|
| SQL Server 2017 unter Windows, SQL Server 2017 Linux und Azure SQL-Datenbank | **Native Bewertung** mit PREDICT T-SQL |
| SQL Server 2017 (nur Windows), SQL Server 2016 R Services mit SP1 oder höher | **Echtzeitbewertung** mit der gespeicherten Prozedur sp\_rxPredict |

Wir empfehlen die native Bewertung mit der PREDICT-Funktion. Die Verwendung von sp\_rxPredict erfordert, dass Sie die SQLCLR-Integration aktivieren. Berücksichtigen Sie die Sicherheitsrisiken, bevor Sie diese Option aktivieren.

## <a name="serialization-and-storage"></a>Serialisierung und Speicherung

Wenn Sie ein Modell mit einer der Optionen für die schnelle Bewertung verwenden möchten, speichern Sie das Modell unter Verwendung eines für Größen- und Bewertungseffizienz optimierten speziellen serialisierten Formats.

+ Rufen Sie [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) auf, um ein unterstütztes Modell in das **RAW**-Format zu schreiben.
+ Rufen Sie [rxUnserializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) auf, um das Modell für die Verwendung in anderem R-Code wiederherzustellen, oder um das Modell anzuzeigen.

**Verwenden von SQL**

Aus SQL-Code können Sie das Modell mit [sp_execute_external_script](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) trainieren und die trainierten Modelle direkt in eine Tabelle einfügen, in eine Spalte vom Typ **varbinary(max)** . Ein einfaches Beispiel finden Sie unter [Schnellstart: Erstellen und Bewerten eines Vorhersagemodells in R mit SQL Server Machine Learning Services](../tutorials/quickstart-r-train-score-model.md)

**Verwenden von R**

Rufen Sie aus R-Code die Funktion [rxWriteObject](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxwriteobject) aus dem RevoScaleR-Paket auf, um das Modell direkt in die Datenbank zu schreiben. Die Funktion **rxWriteObject()** kann R-Objekte aus einer ODBC-Datenquelle wie SQL Server abrufen oder Objekte in SQL Server schreiben. Die API ist nach einem einfachen Schlüsselwertspeicher modelliert.
  
Wenn Sie diese Funktion verwenden, stellen Sie sicher, dass Sie das Modell zunächst mit [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) serialisieren. Legen Sie dann das *serialize*-Argument in **rxWriteObject** auf FALSE fest, um zu vermeiden, dass der Serialisierungsschritt wiederholt wird.

Die Serialisierung eines Modells in ein Binärformat ist hilfreich, aber nicht erforderlich, wenn Sie Vorhersagen mithilfe der R- und Python-Runtimeumgebung im Erweiterbarkeitsframework bewerten. Sie können ein Modell im RAW-Byteformat in einer Datei speichern und dann aus der Datei in SQL Server lesen. Diese Option kann nützlich sein, wenn Sie Modelle zwischen Umgebungen verschieben oder kopieren.

## <a name="scoring-in-related-products"></a>Bewertung in verwandten Produkten

Wenn Sie den [eigenständigen Server](r-server-standalone.md) oder einen [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server) verwenden, stehen Ihnen neben gespeicherten Prozeduren und T-SQL-Funktionen andere Optionen zum schnellen Generieren von Vorhersagen zur Verfügung. Sowohl der eigenständige Server als auch der Machine Learning Server unterstützt das Konzept eines *Webdiensts* für die Codebereitstellung. Sie können ein mit R oder Python vorab trainiertes Modell als Webdienst bündeln, der zur Runtime aufgerufen wird, um neue Dateneingaben auszuwerten. Weitere Informationen dazu finden Sie in diesen Artikeln:

+ [Was sind Webdienste in Machine Learning Server?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Operationalisieren der Analyse mit Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)
+ [Schnellstart: Bereitstellen eines Python-Modells als Webdienst mit azureml-model-management-sdk](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [publishService: Veröffentlichen eines R-Codeblocks oder eines Echtzeitmodells als neuer Webdienst](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [mrsdeploy-Paket für R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)


## <a name="see-also"></a>Siehe auch

+ [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)  
+ [rxRealTimeScoring](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxrealtimescoring)
+ [sp-rxPredict](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)
+ [PREDICT T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)