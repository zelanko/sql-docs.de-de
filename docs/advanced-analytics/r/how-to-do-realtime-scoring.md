---
title: Generieren von Vorhersagen und Vorhersagen mithilfe von Machine Learning-Modelle – SQL Server Machine Learning Services
description: Verwenden Sie RxPredict oder Sp_rxPredict für echtzeitbewertung oder VORHERSAGEN für T-SQL für native Bewertung für Vorhersagen und Vorhersagen in R und Pythin in SQL Server-Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 001b90eafd26c90f730e5647f0dc62d756ca9d1b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62503768"
---
# <a name="how-to-generate-forecasts-and-predictions-using-machine-learning-models-in-sql-server"></a>Gewusst wie: Generieren von Vorhersagen und Vorhersagen mithilfe von Machine Learning-Modelle in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Mithilfe eines vorhandenen Modells vorhersagen oder das Vorhersagen von Ergebnissen für die neue Dateneingaben ist eine wesentliche Aufgabe in Machine Learning. Dieser Artikel listet die Methoden zum Generieren von Vorhersagen in SQL Server. Zwischen den Ansätzen werden die interne Verarbeitung von Methoden für schnelle Vorhersagen in dem die Geschwindigkeit auf inkrementelle Reduzierung der basiert zeitliche Abhängigkeiten ausgeführt. Das bedeutet weniger Abhängigkeiten schnellerer Prognosen.

Mithilfe der internen Verarbeitung-Infrastruktur (Echtzeit- oder nativen Bewertungen) im Lieferumfang von bibliotheksanforderungen. Funktionen müssen aus den Bibliotheken von Microsoft sein. R oder Python-Code Aufrufen von Open Source- oder Drittanbieter-Funktionen wird nicht in CLR oder C++-Erweiterungen unterstützt.

Die folgende Tabelle enthält die bewertungs-Frameworks für Vorhersagen und Vorhersagen. 

| Methodik           | Schnittstelle         | Anforderungen an | Mindestgeschwindigkeiten für die Verarbeitung |
|-----------------------|-------------------|----------------------|----------------------|
| Erweiterbarkeitsframework | [rxPredict (R)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) <br/>[Rx_predict (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Keine. Modelle können auf eine beliebige R oder Python-Funktion basieren | Hunderte von Millisekunden. <br/>Laden eine Laufzeitumgebung hat eine feste Kosten, dreihundert auf sechs Millisekunden, Durchschnitt, bevor neuen Daten bewertet werden. |
| [Real-Time scoring CLR-Erweiterung](../real-time-scoring.md) | [Sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) für ein serialisiertes Modell | R: RevoScaleR, MicrosoftML <br/>Python: revoscalepy, microsoftml | Um Dutzende Millisekunden verlängert, durchschnittlich. |
| [Native Bewertung C++-Erweiterung](../sql-native-scoring.md) | [VORHERSAGEN für T-SQL-Funktion](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) für ein serialisiertes Modell | R: RevoScaleR <br/>Python: Revoscalepy | Weniger als 20 Millisekunden im Durchschnitt. | 

Hohe Geschwindigkeit und nicht die Substanz der Ausgabe ist die unterscheidenden-Funktion. Wenn die gleichen Funktionen und die Eingaben, sollte der erzielten Ausgabe nicht basierend auf den Ansatz abhängt.

Das Modell muss mit der eine unterstützte Funktion erstellt und dann serialisiert, raw Byte-Stream auf dem Datenträger gespeichert oder in einem Binärformat in einer Datenbank gespeichert. Verwenden eine gespeicherte Prozedur oder T-SQL, können Sie laden und verwenden ein binäres Modell ohne den Aufwand für eine Zeit des R- oder Python-Sprache, die ausgeführt, wodurch kürzere Zeit bis zum Abschluss beim Generieren von vorhersagebewertungen für neue Eingaben.

Die Bedeutung der CLR und C++-Erweiterungen ist die Nähe zu den Datenbank-Engine. Die systemeigene Sprache von der Datenbank-Engine ist C++, das bedeutet, Erweiterungen geschrieben in C++ mit weniger Abhängigkeiten führen dass. Im Gegensatz dazu Sie .NET Core CLR-Erweiterungen abhängig. 

Wie zu erwarten, wird die Unterstützung für durch diese Umgebungen zur Laufzeit beeinträchtigt. Führen Sie systemeigenen Datenbank-Engine-Erweiterungen an jeder Stelle, die relationale Datenbank unterstützt wird: Windows, Linux, Azure. CLR-Erweiterungen mit der .NET Core-Anforderung ist derzeit nur Windows.

## <a name="scoring-overview"></a>Übersicht über die Bewertung

_Bewertung_ ist ein zweistufiger Prozess. Zuerst legen Sie eine bereits trainierten Modells aus einer Tabelle zu laden. Zweitens übergeben, die neuen Eingabedaten an die Funktion zum Generieren von Werten der Vorhersage (oder _Bewertungen_). Die Eingabe ist häufig eine T-SQL-Abfrage, die tabellarische oder einzelne Zeilen zurückgegeben werden. Sie können auch Ausgabe einen einzelne Spalte-Wert, die Wahrscheinlichkeit darstellt, oder Sie möglicherweise mehrere Werte, z. B. eines Konfidenzintervalls, Fehler oder andere nützliche Ergänzung der Vorhersage ausgegeben.

Einen Schritt zu sichern, den gesamten Vorgang der Vorbereitung des Modells, und klicken Sie dann Generieren von Bewertungen kann auf diese Weise zusammengefasst werden:

1. Erstellen Sie ein Modell mit einem unterstützten Algorithmus an. Unterstützung variiert je nach der Bewertung Methodik, die Sie auswählen.
2. Das Modell zu trainieren.
3. Das Modell mit einem speziellen Binärformat zu serialisieren.
3. Speichern Sie das Modell in SQL Server. In der Regel bedeutet dies das serialisierte Modell in einer SQL Server-Tabelle gespeichert werden sollen.
4. Rufen Sie die Funktion oder gespeicherte Prozedur, die Eingaben Modell und die Daten als Parameter angeben.

Wenn die Eingabe viele Zeilen mit Daten enthält, ist es in der Regel schneller, die Vorhersagewerte im Rahmen der Bewertung in eine Tabelle einzufügen. Generieren ein einzelnes Ergebnis ist ein üblicher in einem Szenario, in dem Sie Eingabewerte aus einem Formular oder einer benutzeranforderung, und das Ergebnis an eine Clientanwendung zurück. Zur Verbesserung der Leistung beim aufeinander folgenden Bewertungen zu generieren, kann SQL Server das Modell zwischenspeichern, damit sie in den Arbeitsspeicher neu geladen werden kann.

## <a name="compare-methods"></a>Vergleichen von Methoden

Um die Integrität der Datenbank-Engine die Kernprozesse beizubehalten, ist die Unterstützung für R und Python in einer Architektur mit doppeltem aktiviert, die Verarbeitung der Sprache von RDBMS-Verarbeitung isoliert. Ab SQL Server 2016 hat Microsoft ein Extensibility Framework für die R-Skripts, die von T-SQL ausgeführt werden kann. hinzugefügt. In SQL Server 2017 wurde die Integration von Python hinzugefügt. 

Das Extensibility Framework unterstützt bei Vorgängen, die Sie in R oder Python, von einfachen Funktionen bis hin zu Schulungen komplexen Machine learning-Modelle ausführen können. Die Dual-Process-Architektur erfordert jedoch einen externen R oder Python-Prozess für jeden Aufruf, unabhängig von der Komplexität des Vorgangs aufgerufen. Wenn die Workload umfasst, laden ein vorab trainiertes Modell aus einer Tabelle und die Bewertung für diese Daten bereits in SQL Server, fügt der Aufwand für das Aufrufen von externen Prozessen Latenz, die unter bestimmten Umständen nicht akzeptabel sein können. Beispielsweise erfordert die betrugserkennung, schnelle Bewertung, um relevant sein.

Um mindestgeschwindigkeiten für die Bewertung für Szenarien wie z.B. betrugserkennung zu erhöhen, hinzugefügt SQL Server integrierten bewertungsbibliotheken als C++- und CLR-Erweiterungen, die den Aufwand für R und Python-Start-Prozesse zu vermeiden.

[**Echtzeitbewertung** ](../real-time-scoring.md) war die erste Lösung für hohe Leistung zu bewerten. In frühen Versionen von SQL Server 2017 und späteren Updates eingeführt, um SQL Server 2016, CLR-Bibliotheken, die für R und Python-Verarbeitung über Funktionen im RevoScaleR, MicrosoftML (R), Revoscalepy, Kontrolle von Microsoft stehen abhängig echtzeitbewertung und Microsoftml (Python). CLR-Bibliotheken werden aufgerufen, mit der **Sp_rxPredict** gespeicherte Prozedur generiert Ergebnisse aus jedem unterstützten Modelltyp an, ohne die R- oder Python-Laufzeit aufrufen.

[**Native Bewertung** ](../sql-native-scoring.md) ist eine SQL Server 2017-Funktion, die implementiert werden, wie eine systemeigene C++-Bibliothek, jedoch nur für Revoscaler- und Revoscalepy-Modelle. Ist der schnellste und sicherer Ansatz, sondern eine kleinere Gruppe von Funktionen, die relativ zu anderen Methoden unterstützt.

## <a name="choose-a-scoring-method"></a>Wählen Sie eine Bewertungsmethode

Plattformanforderungen geben häufig die bewertungs-Methodik zur verwenden.

| Produktversion und Plattform | Methodik |
|------------------------------|-------------|
| SQLServer 2017 unter Windows, Linux für SQL Server 2017 und Azure SQL-Datenbank | **Native Bewertung** mit T-SQL-VORHERSAGEN |
| SQL Server 2017 (nur Windows), SQL Server 2016 R Services SP1 oder höher | **Echtzeitbewertung** mit sp\_RxPredict gespeicherten Prozedur |

Es wird empfohlen, nativen Bewertung, mit der PREDICT-Funktion. Mithilfe von sp\_RxPredict erfordert, dass Sie SQLCLR-Integration aktivieren. Beachten Sie die Sicherheitsrisiken, bevor Sie diese Option aktivieren.

## <a name="serialization-and-storage"></a>Serialisierung und Speicherung

Um ein Modell mit der schnellen Bewertung Optionen zu verwenden, speichern Sie das Modell mithilfe von einem speziellen serialisierte Format für Größe optimiert wurde und die Bewertung der Effizienz.

+ Rufen Sie [RxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) ein unterstütztes Modell zum Schreiben der **unformatierten** Format.
+ Rufen Sie [RxUnserializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)' wiederherstellen, kann das Modell für die Verwendung in anderen R-Code oder das Modell anzuzeigen.

**Mithilfe von SQL**

Von SQL-Code können Sie trainieren das Modell, indem [Sp_execute_external_script](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), und fügen Sie direkt die trainierten Modelle in einer Tabelle in einer Spalte vom Typ **'varbinary(max)'** . Ein einfaches Beispiel finden Sie unter [preditive Modell in R erstellen](../tutorials/rtsql-create-a-predictive-model-r.md)

**Mithilfe von R**

Aufrufen von R-Code, der [RxWriteObject](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxwriteobject) Funktion von RevoScaleR-Paket, das Modell direkt an die Datenbank zu schreiben. Die **rxWriteObject()** Funktion R-Objekte aus einer ODBC-Datenquelle wie SQL Server, oder Schreiben von Objekten in SQL Server. Die API wird nach einem einfachen Schlüssel-Wert-Speicher modelliert.
  
Wenn Sie diese Funktion verwenden, werden Sie sicher, dass das Modell, indem Serialisieren [RxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) erste. Legen Sie dann die *Serialisieren* -Argument in **RxWriteObject** auf "false", um zu vermeiden, wiederholen den Schritt für die Serialisierung.

Serialisieren ein Modell auf ein binäres Format ist nützlich, aber nicht erforderlich, wenn sind Sie Bewertungen, Vorhersagen mithilfe von R und Python Laufzeitumgebung, in dem Extensibility Framework ausführen. Sie können Speichern eines Modells im raw Byte-Format in eine Datei, und klicken Sie dann in SQL Server aus der Datei gelesen. Diese Option kann nützlich sein, wenn Sie verschieben oder kopieren die Modelle zwischen Umgebungen.

## <a name="scoring-in-related-products"></a>Bewertung in verwandte Produkte

Bei Verwendung der [eigenständiger Server](r-server-standalone.md) oder [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), Sie haben andere Optionen als gespeicherte Prozeduren und T-SQL-Funktionen zum schnellen Generieren von Vorhersagen. Dem eigenständigen Server und dem Machine Learning Server unterstützen das Konzept einer *Webdienst* für die codebereitstellung. Können Sie eine R bündeln oder Python von vortrainierten Modell als Webdienst, zur Laufzeit zum Auswerten von neuen Dateneingaben aufgerufen wird. Weitere Informationen dazu finden Sie in diesen Artikeln:

+ [Was sind Webdienste im Machine Learning Server?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Was ist die operationalisierung?](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)
+ [Bereitstellen eines Python-Modells als Webdienst mit Azure ml-Modell-Management-sdk](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [Veröffentlichen Sie ein R-Code-Block oder ein Modell in Echtzeit als neuen Webdienst](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [Mrsdeploy-Paket für R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)


## <a name="see-also"></a>Siehe auch

+ [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)  
+ [rxRealTimeScoring](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxrealtimescoring)
+ [sp-rxPredict](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)
+ [VORHERSAGEN VON T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)