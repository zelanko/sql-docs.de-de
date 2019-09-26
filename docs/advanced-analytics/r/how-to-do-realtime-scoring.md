---
title: Generieren von Vorhersagen und Vorhersagen mit Machine Learning-Modellen
description: Verwenden Sie rxvorhersage oder sp_rxPredict für die Echtzeitbewertung, oder prognostizieren Sie T-SQL für die native Bewertung für Vorhersagen und Vorhersagen in R und python in SQL Server Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 14ccd4beb2186213cb3d94b10031ac732224f4d9
ms.sourcegitcommit: 2f56848ec422845ee81fb84ed321a716c677aa0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71271902"
---
# <a name="how-to-generate-forecasts-and-predictions-using-machine-learning-models-in-sql-server"></a>Generieren von Vorhersagen und Vorhersagen mithilfe von Machine Learning-Modellen in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die Verwendung eines vorhandenen Modells zum Vorhersagen oder Vorhersagen der Ergebnisse für neue Dateneingaben ist eine zentrale Aufgabe beim maschinellen lernen. In diesem Artikel werden die Ansätze zum Generieren von Vorhersagen in SQL Server aufgelistet. Zu den Ansätzen zählen interne Verarbeitungsmethoden für hoch Geschwindigkeits Vorhersagen, bei denen die Geschwindigkeit auf inkrementellen Reduzierungen von Laufzeitabhängigkeiten basiert. Weniger Abhängigkeiten bedeuten schnellere Vorhersagen.

Die Verwendung der internen Verarbeitungs Infrastruktur (Echt Zeit-oder Native Bewertung) ist mit den Bibliotheks Anforderungen ausgestattet. Funktionen müssen aus den Microsoft-Bibliotheken bestehen. R-oder python-Code, der Open Source-Funktionen oder Funktionen von Drittanbietern aufrufen, wird C++ in CLR oder Erweiterungen nicht unterstützt.

In der folgenden Tabelle werden die Bewertungs Frameworks für Vorhersagen und Vorhersagen zusammengefasst. 

| Methodik           | Interface         | Bibliotheks Anforderungen | Verarbeitungsgeschwindigkeiten |
|-----------------------|-------------------|----------------------|----------------------|
| Erweiterbarkeitsframework | [rxPredict (R)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) <br/>[rx_predict (python)](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Keine. Modelle können auf jeder R-oder python-Funktion basieren. | Hunderte Millisekunden. <br/>Das Laden einer Laufzeitumgebung hat einen Fixwert von drei bis 600 Millisekunden, bevor neue Daten bewertet werden. |
| [Echtzeitbewertung der CLR-Erweiterung](../real-time-scoring.md) | [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) bei einem serialisierten Modell | R RevoScaleR, MicrosoftML <br/>Python: revoscalepy, microsoftml | Durchschnittlich zehn Millisekunden. |
| [Native Bewertungs C++ Erweiterung](../sql-native-scoring.md) | [Vorhersagen der T-SQL-Funktion](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) für ein serialisiertes Modell | R RevoScaleR <br/>Python: revoscalepy | Im Durchschnitt weniger als 20 Millisekunden. | 

Die Verarbeitungsgeschwindigkeit und nicht der Inhalt der Ausgabe ist das differenzierende Feature. Wenn die gleichen Funktionen und Eingaben angenommen werden, sollte die bewertete Ausgabe nicht je nach verwendeter Herangehensweise variieren.

Das Modell muss mit einer unterstützten Funktion erstellt und dann in einen unformatierten Bytestream serialisiert werden, der auf einem Datenträger gespeichert oder im Binärformat in einer Datenbank gespeichert wird. Mithilfe einer gespeicherten Prozedur oder T-SQL können Sie ein binäres Modell ohne den Aufwand einer R-oder python-Sprachlaufzeit laden und verwenden, was zu einer schnelleren Zeit bis zum Abschluss der Erstellung von Vorhersage Bewertungen für neue Eingaben führt.

Die Bedeutung von CLR und C++ Erweiterungen liegt in der Nähe der Datenbank-Engine selbst. Die systemeigene Sprache der Datenbank-Engine C++ist. Dies bedeutet, dass C++ in erstellte Erweiterungen mit weniger Abhängigkeiten ausgeführt werden. Im Gegensatz dazu sind CLR-Erweiterungen von .net Core abhängig. 

Wie Sie vielleicht erwarten, ist die Platt Form Unterstützung von diesen Laufzeitumgebungen betroffen. Native Datenbankmodul Erweiterungen werden überall dort ausgeführt, wo die relationale Datenbank unterstützt wird Windows, Linux, Azure. CLR-Erweiterungen mit der .net Core-Anforderung sind derzeit nur Windows.

## <a name="scoring-overview"></a>Bewertungs Übersicht

Die _Bewertung_ ist ein zweistufiger Prozess. Zunächst geben Sie ein bereits trainiertes Modell an, das aus einer Tabelle geladen werden soll. Übergeben Sie Zweitens neue Eingabedaten an die Funktion, um Vorhersagewerte (oder _Bewertungen_) zu generieren. Die Eingabe ist häufig eine T-SQL-Abfrage, die entweder tabellarische oder einzelne Zeilen zurückgibt. Sie können auswählen, ob ein einzelner Spaltenwert, der eine Wahrscheinlichkeit darstellt, ausgegeben werden soll, oder Sie können mehrere Werte ausgeben, z. b. ein Vertrauensintervall, einen Fehler oder eine andere hilfreiche Ergänzung der Vorhersage.

Wenn Sie einen Schritt zurücknehmen, kann der Gesamtprozess der Vorbereitung des Modells und das anschließende Erstellen von Bewertungen auf diese Weise zusammengefasst werden:

1. Erstellen Sie ein Modell mit einem unterstützten Algorithmus. Die Unterstützung variiert je nach der gewählten Bewertungsmethodik.
2. Trainieren Sie das Modell.
3. Serialisieren Sie das Modell mithilfe eines speziellen Binär Formats.
3. Speichern Sie das Modell in SQL Server. Dies bedeutet in der Regel, dass das serialisierte Modell in einer SQL Server Tabelle gespeichert wird.
4. Nennen Sie die Funktion oder die gespeicherte Prozedur, und geben Sie das Modell und die Dateneingaben als Parameter an.

Wenn die Eingabe viele Daten Zeilen enthält, ist es in der Regel schneller, die Vorhersagewerte als Teil des Bewertungsprozesses in eine Tabelle einzufügen. Das Erstellen einer einzelnen Bewertung ist typischer in einem Szenario, in dem Sie Eingabewerte aus einer Formular-oder Benutzer Anforderung erhalten und das Ergebnis an eine Client Anwendung zurückgeben. Um die Leistung beim erzeugen aufeinander folgender Ergebnisse zu verbessern, können SQL Server das Modell Zwischenspeichern, sodass es in den Arbeitsspeicher geladen werden kann.

## <a name="compare-methods"></a>Methoden vergleichen

Um die Integrität der zentralen Datenbank-Engine-Prozesse beizubehalten, wird die Unterstützung für R und python in einer dualen Architektur aktiviert, die die Sprachverarbeitung von der RDBMS-Verarbeitung isoliert. Ab SQL Server 2016 wurde von Microsoft ein Erweiterbarkeits Framework hinzugefügt, das das Ausführen von R-Skripts aus T-SQL ermöglicht. In SQL Server 2017 wurde die python-Integration hinzugefügt. 

Das Erweiterbarkeit Framework unterstützt jeden Vorgang, den Sie in R oder python ausführen können, und reicht von einfachen Funktionen bis hin zum trainieren komplexer Machine Learning-Modelle. Allerdings erfordert die Dual-Process-Architektur, dass unabhängig von der Komplexität des Vorgangs ein externer R-oder python-Prozess für jeden Aufruf aufgerufen wird. Wenn die Arbeitsauslastung das Laden eines vorab trainierten Modells aus einer Tabelle und die Bewertung auf der Grundlage der bereits in SQL Server vorhandenen Daten umfasst, fügt der Aufwand des Aufrufs externer Prozesse Latenzzeit ein, die unter bestimmten Umständen nicht akzeptabel sein kann. Beispielsweise erfordert die Betrugserkennung, dass eine schnelle Bewertung relevant ist.

Um Bewertungs Geschwindigkeiten für Szenarien wie die Betrugserkennung zu erhöhen, SQL Server integrierte Bewertungs Bibliotheken als C++ und CLR-Erweiterungen hinzugefügt, die den mehr Aufwand von R-und python-Start Prozessen vermeiden.

Die [**Echtzeitbewertung**](../real-time-scoring.md) war die erste Lösung für die Bewertung mit hoher Leistung. In frühen Versionen von SQL Server 2017 und neueren Updates SQL Server 2016 basiert die Echtzeitbewertung auf CLR-Bibliotheken, die für die R-und python-Verarbeitung über von Microsoft gesteuerte Funktionen in revoscaler, microsoftml (R), revoscalepy und microsoftml (python). CLR-Bibliotheken werden mithilfe der gespeicherten Prozedur **sp_rxPredict** aufgerufen, um Ergebnisse aus einem beliebigen unterstützten Modelltyp zu generieren, ohne die R-oder python-Laufzeit aufzurufen.

Die [**native Bewertung**](../sql-native-scoring.md) ist eine SQL Server 2017-Funktion, die als C++ native Bibliothek implementiert ist, jedoch nur für revoscaler-und revoscalepy-Modelle. Dies ist der schnellste und sicherere Ansatz, unterstützt jedoch einen kleineren Satz von Funktionen relativ zu anderen Methoden.

## <a name="choose-a-scoring-method"></a>Auswählen einer Bewertungsmethode

Platt Form Anforderungen legen oft fest, welche Bewertungsmethodik verwendet werden soll.

| Produktversion und Plattform | Methodik |
|------------------------------|-------------|
| SQL Server 2017 unter Windows, SQL Server 2017 Linux und Azure SQL-Datenbank | **Native Bewertung** mit T-SQL-Vorhersage |
| SQL Server 2017 (nur Windows), SQL Server 2016 R Services bei SP1 oder höher | **Echtzeitbewertung** mit der in\_SP rxvorhersage gespeicherten Prozedur |

Wir empfehlen die native Bewertung mit der Vorhersagefunktion. Die Verwendung\_von SP rxprognostizieren erfordert, dass Sie die SQLCLR-Integration aktivieren. Berücksichtigen Sie die Sicherheitsrisiken, bevor Sie diese Option aktivieren.

## <a name="serialization-and-storage"></a>Serialisierung und Speicherung

Wenn Sie ein Modell mit einer der Optionen für die schnelle Bewertung verwenden möchten, speichern Sie das Modell unter Verwendung eines speziellen serialisierten Formats, das für die Größen-und Bewertungs Effizienz optimiert wurde.

+ Aufrufen von [rxserializemodel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) zum Schreiben eines unterstützten Modells in das **RAW** -Format.
+ Aufrufen von [rxunserializemodel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)' zum erneuten darstellen des Modells für die Verwendung in anderem R-Code oder zum Anzeigen des Modells.

**Verwenden von SQL**

Aus SQL-Code können Sie das Modell mithilfe von [sp_execute_external_script](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)trainieren und die trainierten Modelle direkt in eine Tabelle einfügen, in einer Spalte vom Typ **varbinary (max)** . Ein einfaches Beispiel finden Sie unter [Erstellen eines prätiven Modells in R](../tutorials/quickstart-r-train-score-model.md) .

**Verwenden von R**

Rufen Sie aus R-Code die Funktion [rxschreiteobject](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxwriteobject) aus dem revoscaler-Paket auf, um das Modell direkt in die Datenbank zu schreiben. Die Funktion **rxschreiteobject ()** kann R-Objekte aus einer ODBC-Datenquelle wie SQL Server abrufen oder Objekte in SQL Server schreiben. Die API wird nach einem einfachen Schlüssel-Wert-Speicher modelliert.
  
Wenn Sie diese Funktion verwenden, stellen Sie sicher, dass Sie das Modell zuerst mithilfe von [rxserializemodel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) serialisieren. Legen Sie dann das *serialisieren* -Argument in **rxschreiteobject** auf false fest, um zu vermeiden, dass der serialisierungsschritt wiederholt wird.

Die Serialisierung eines Modells in ein Binärformat ist hilfreich, aber nicht erforderlich, wenn Sie Vorhersagen mithilfe der R-und python-Laufzeitumgebung im Erweiterbarkeits Framework bewerten. Sie können ein Modell im Raw Byte-Format in einer Datei speichern und dann aus der Datei in SQL Server lesen. Diese Option kann nützlich sein, wenn Sie Modelle zwischen Umgebungen verschieben oder kopieren.

## <a name="scoring-in-related-products"></a>Bewertung in verwandten Produkten

Wenn Sie den [eigenständigen Server](r-server-standalone.md) oder einen [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)verwenden, haben Sie neben gespeicherten Prozeduren auch weitere Optionen und T-SQL-Funktionen zum schnellen Generieren von Vorhersagen. Sowohl der eigenständige Server als auch der Machine Learning Server unterstützen das Konzept eines *Webdiensts* für die Code Bereitstellung. Sie können ein vorab trainiertes R-oder python-Modell als Webdienst bündeln, der zur Laufzeit aufgerufen wird, um neue Dateneingaben auszuwerten. Weitere Informationen dazu finden Sie in diesen Artikeln:

+ [Was sind Webdienste in Machine Learning Server?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Was ist operationalization?](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)
+ [Bereitstellen eines python-Modells als Webdienst mit azureml-Model-Management-SDK](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [Veröffentlichen eines R-Code Blocks oder eines echt zeitmodells als neuen Webdienst](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [mrsbereitstellungs-Paket für R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)


## <a name="see-also"></a>Siehe auch

+ [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)  
+ [rxRealTimeScoring](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxrealtimescoring)
+ [sp-rxPredict](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)
+ [VORHERSAGEN VON T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)