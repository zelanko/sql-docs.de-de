---
title: SQLServer R Services Performance Tuning - SQL Server Machine Learning-Dienste
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: bb3f48a9a25b12568497c3583536d8c650a6f702
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962434"
---
# <a name="performance-tuning-for-r-in-sql-server"></a>Leistungsoptimierung für R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist der erste in einer Reihe von vier Artikeln, die zur leistungsoptimierung für R-Dienste basierend auf zwei Fallstudien zu beschreiben:

- Durch das Produktentwicklungsteam auf die Leistung von R-Lösungen überprüft durchgeführten Leistungstests

- Optimierung der Leistung von Microsoft Data Science-Teams für ein bestimmtes Machine Learning-Szenario, das häufig von Kunden angeforderte.

Das Ziel dieser Reihe ist Anleitung zu den Arten von Techniken, die besonders hilfreich für die Ausführung von R-Aufträgen in SQL Server sind die Optimierung der Leistung zu bieten.

+ In diesem Thema (ersten) bietet eine Übersicht über die Architektur und einige der häufigsten Probleme beim Optimieren der für Data Science-Aufgaben.
+ Der zweite Artikel befasst sich bestimmte Hardware- und SQL Server-Optimierungen.
+ Der dritte Artikel behandelt die Optimierungen in R-Code und Ressourcen für die operationalisierung.
+ Die vierte Artikel wird beschrieben, Testmethoden in Details und Ergebnisse für Berichte und Ihre Absichten zu ziehen.

**Gilt für:** SQL Server 2016 R Services, SQL Server 2017-Machine Learning-Dienste

## <a name="performance-goals-and-targeted-scenarios"></a>Leistungsziele und Zielszenarien

Die R-Funktion wurde in SQL Server 2016, um die Ausführung von R-Skripts unterstützen von SQL Server eingeführt. Wenn Sie dieses Feature verwenden, wird die R-Laufzeit in einem separaten Prozess aus der Datenbank-Engine ausgeführt wird, aber tauscht Daten sicher mit der Datenbank-Engine, die mithilfe von Server-Ressourcen und Dienste, die Interaktion mit SQL Server, z. B. das Trusted Launchpad.

In SQL Server 2017 wurde Unterstützung für die Ausführung von Python-Skripts, die mit der Architektur, mit zusätzlichen Sprache in Zukunft folgen angekündigt.

Mit steigender Anzahl der unterstützten Versionen und die Sprache, ist es wichtig, dass der Datenbankadministrator und datenbankarchitekt kennen das Potenzial für Ressourcenkonflikte aufgrund von Machine Learning-Aufträge sind und sie den Server zur Unterstützung konfigurieren können die neue Workloads. Obwohl unsichere datenbewegungen unnötig datennahe Analysen beibehalten wird, wird es auch analytische Workloads aus der Laptop Data scientists und wieder auf dem Hostserver für die Daten verschoben.

Leistungsoptimierung für Machine Learning ist nicht eindeutig eine allgemeingültige-Option. Die folgenden allgemeinen Aufgaben möglicherweise sehr unterschiedliche Leistungsprofile:

- Trainieren von Aufgaben: Erstellen und Trainieren ein Regressionsmodell im Vergleich zu trainieren eines neuronalen Netzwerks
- Entwickeln Sie Features mithilfe von R im Vergleich zu featureextraktion mit T-SQL
- Bewerten von auf einzelne Zeilen oder kleine Batches im Vergleich zu Bulk Bewertung mit tabellarischen Eingaben
- Ausführen der Bewertung, die in R und Bereitstellen von Modellen in der produktionsumgebung auf SQL Server in gespeicherten Prozeduren
- Ändern die R-Code für die Datenübertragung minimieren, oder entfernen kostspielige Datentransformationen
- Aktivieren von automatisierten Tests und das erneute Trainieren von Modellen

Da die Auswahl von Optimierungstechniken, hängt davon ab, welche Aufgabe wichtig für Ihre Anwendung oder einen Anwendungsfall ist, werden Fallstudien sowohl allgemeinen Leistungstipps und Anleitungen, wie Sie für ein bestimmtes Szenario, Optimierung für die batchbewertung zu optimieren.

+ **Der einzelnen Optimierungsoptionen in SQL Server**

    In der ersten Fallstudie zur Leistung wurden mehrere Tests auf einem einzelnen Dataset mit einem einzelnen Modell ausführen. Der Algorithmus RxLinMod in RevoscaleR wurde verwendet, um ein Modell erstellen und zu Bewertungen daraus erstellen, aber der Code als auch die zugrunde liegenden Datentabellen wurden systematisch geändert, damit Sie um die Auswirkungen der einzelnen Änderungen zu testen.

    Beispielsweise wurde in einem Testlauf, der R-Code geändert, damit ein Vergleich zwischen der Featureentwicklung anhand einer Transformationsfunktion an, und die Funktionen im Voraus berechnet und das anschließende Laden von Funktionen aus einer Tabelle durchgeführt werden konnte. In einem anderen Test ausführen wurde die Leistung des Modells Training zwischen der Verwendung von einer standardmäßigen volltextindizierten Tabelle im Vergleich mit Daten in eine Tabelle mit verschiedenen Arten von Komprimierung oder neue Typen von Indizes verglichen.

+ **Optimierung für ein bestimmtes Bewertung Szenario mit hohem Volumen**

    Der Machine Learning-Aufgaben in der zweiten Fallstudie umfasst viele setzt für mehrere Positionen übermittelt werden soll, und suchen die beste Wahl für jede Position Auftrag verarbeitet. Der Machine Learning-Modell selbst wird als ein binäres klassifizierungsproblem formuliert: er eine Beschreibung "Resume" und "Auftrag" als Eingabe akzeptiert und die Wahrscheinlichkeit für jedes Paar Resume-Job generiert. Da das Ziel ist die beste Übereinstimmung gefunden wird, wird ein benutzerdefinierte wahrscheinlichkeitsschwellenwert zum weiter zu filtern und nur die Übereinstimmungen zu erhalten.

    Für diese Lösung war das Hauptziel bei der Bewertung niedrige Latenz zu erreichen. Diese Aufgabe ist jedoch rechenintensiv ist auch bei der Bewertung, da es sich bei jeder neuer Auftrag mit Millionen von nimmt innerhalb eines angemessenen Zeitraums verglichen werden muss. Darüber hinaus die Feature-engineering-Schritt mehr als 2000 Features für die einzelnen fortsetzen oder Auftrag erzeugt, und einen erheblichen Leistungsengpass wird.

Es wird empfohlen, überprüfen Sie die erste Fallstudie, um zu bestimmen, welche Techniken für Ihre Lösung gelten alle Ergebnisse und ihren möglichen Auswirkungen abwägen.

Klicken Sie dann überprüfen Sie die Ergebnisse der Bewertung Optimierung Fallstudie zu sehen, wie der Autor verschiedene Techniken angewendet, und den Server zur Unterstützung einer bestimmten arbeitsauslastung optimiert.

## <a name="performance-optimization-process"></a>Leistung-Optimierungsprozess

Konfiguration und Optimierung von Leistung erfordert, erstellen eine solide Grundlage, auf dem Layer-Optimierungen, die für bestimmte Workloads konzipiert:

- Wählen Sie einen geeigneten Server zum Host Analytics. In der Regel wird eine sekundäre reporting, Datawarehouse oder einen anderen Server, die bereits für andere Berichte oder Analysen verwendet wird, bevorzugt. Allerdings können in einer hybridlösung für die transaktionale-analyseverarbeitung (HTAP), operative Daten als Eingabe für R für die schnelle Bewertung verwendet werden.

- Konfigurieren Sie die SQL Server-Instanz Guthaben-Datenbank-Engine-Operationen und R oder Python-Skript die Ausführung mit passender. Dazu zählen SQL Server-Standardeinstellungen für die Speicher- und CPU-Auslastung, NUMA und prozessoraffinitätsoptionen und Erstellung von Ressourcengruppen zu ändern.

- Optimieren Sie die Server-Computers für die effiziente Verwendung externer Skripts unterstützt. Erhöhen der Anzahl von Konten, die für die Ausführung des externen Skripts, aktivieren die paketverwaltung verwendet werden. dazu gehören, und Zuweisen von Benutzern zu zugehörigen Sicherheitsrollen aus.

- Anwenden von Optimierungen, die bestimmte für Datenspeicher und Übertragung in SQL Server, einschließlich der Indizierung und Statistiken Strategien, Abfrage-Designer und die abfrageoptimierung und des Entwurfs von Tabellen, die für Machine Learning verwendet werden. Sie können auch analysieren, Datenquellen und Daten transportieren von Methoden, oder Ändern von ETL-Prozesse, um die featureextraktion zu optimieren.

- Optimieren Sie das analytische Modell um Ineffizienz zu vermeiden. Der Bereich der Optimierungen, die möglich sind abhängig von der Komplexität der R-Code und die Pakete und die Daten, die Sie verwenden. Wichtige Aufgaben enthalten, entfernen Sie kostspielige Datentransformationen oder Auslagern der Daten zur Vorbereitung oder ein Feature engineering Aufgaben aus R oder Python auf ETL-Prozesse oder SQL. Sie können auch Umgestalten Skripte, beseitigen Inline-Paket installiert, unterteilen R-Code in separate Verfahren für Trainings-, bewertungs- und Auswertung oder vereinfachen Code effizienter als eine gespeicherte Prozedur funktioniert.

## <a name="articles-in-this-series"></a>Artikel in dieser Serie

+ [Leistungsoptimierung für R in SQL Server - hardware](../r/sql-server-configuration-r-services.md)

    Enthält Anleitungen zum Konfigurieren der Hardware, [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] installiert ist, auf, und klicken Sie zum Konfigurieren von SQL Server-Instanz, um externe Skripts besser zu unterstützen. Es ist besonders nützlich für **Datenbankadministratoren**.

+ [Leistungsoptimierung für R in SQL Server - Code und Daten Optimierung](../r/r-and-data-optimization-r-services.md)

    Enthält spezifische Tipps zur Optimierung von externen Skripts um bekannte Probleme zu vermeiden. Es ist besonders nützlich für **Datenanalysten**.

    > [!NOTE]
    > Während der Großteil der Informationen in diesem Abschnitt für R im Allgemeinen gilt, ist einige Informationen spezifisch für analytische RevoScaleR-Funktionen. Ausführliche Leistungsleitfaden ist nicht verfügbar für **Revoscalepy** und andere unterstützte Python-Bibliotheken.
    >

+ [Leistungsoptimierung für R in SQL Server - Methoden und Ergebnisse](../r/performance-case-study-r-services.md)

    Fasst Daten wurde zwei Fallstudien, wie die Leistung getestet wurde und wie wirkt sich die Optimierungen Ergebnisse verwendet.
