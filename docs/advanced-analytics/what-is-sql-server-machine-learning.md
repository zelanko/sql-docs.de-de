---
title: Sprache R und Python-Funktionsintegration – SQL Server Machine Learning Services
description: Sprache R und Python-Features in SQL Server, die Integration mit relationalen Daten für Data Science und statistische Modellierung, Machine Learning-Modellen, predictive Analytics, Visualisierung von Daten und mehr.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: fb98f2dad8f16ac7f9e06920d56bd225962dca7b
ms.sourcegitcommit: 11ab8a241a6d884b113b3cf475b2b9ed61ff00e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161847"
---
# <a name="machine-learning-services-r-python-in-sql-server-2017"></a>Machine Learning-Dienste (R, Python), in SQLServer 2017
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017-Machine Learning Services ist ein Add-on für eine Datenbank-Engine-Instanz, die zur Ausführung von R und Python-Code in SQL Server verwendet. Die Funktion enthält [Microsoft R und Python-Paketen](#components) für leistungsstarke predictive Analytics und Machine Learning. Code wird in einem Erweiterbarkeitsframework,, ausgeführt, von der Kern-Engine-Prozesse isoliert, jedoch vollständig auf relationale Daten als gespeicherte Prozeduren, wie T-SQL-Skript, R oder Python-Anweisungen enthält, oder wie R oder Python-Code mit T-SQL verfügbar. 

Wenn Sie zuvor [SQL Server 2016 R Services](r/sql-server-r-services.md), Machine Learning Services in SQL Server 2017 ist die nächste Generation von Unterstützung für R, mit aktualisierten Versionen von Basis-R "," RevoScaleR-MicrosoftML lautet und anderen Bibliotheken, die in 2016 eingeführt wurde. 

In Azure SQL-Datenbank [Machine Learning Services (mit R)](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview) befindet sich derzeit in der öffentlichen Vorschau.

## <a name="bring-compute-power-to-the-data"></a>Schalten Sie die computeleistung auf die Daten

Der entscheidenden Wertbeiträge von Machine Learning Services ist die Potenz Enterprise R und Python-Pakete, um erweiterte Analysen und Berechnungen und Verarbeitung an, in denen die Daten befinden, bieten die Möglichkeit zu übermitteln und Sie müssen Daten in das Netzwerk. Dies bietet mehrere Vorteile:

+ Datensicherheit. Bringen R- und Python werden Ausführung näher an der Quelle der Daten unnötiger oder unsicherer Datentransfer vermieden.
+ Geschwindigkeit. Datenbanken sind für setbasierte Vorgänge optimiert. Aktuelle Innovationen in Datenbanken, z.B. in-Memory-Tabellen stellen Zusammenfassungen und Aggregationen der Daten extrem, und es sind eine perfekte Ergänzung für die Data Science.
+ Einfache Bereitstellung und Integration. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist der zentrale Punkt von Vorgängen für viele Verwaltungsaufgaben von Daten und Anwendungen. Verwenden Sie die Daten, die in der Datenbank oder ein berichterstellungs-Warehouse befinden, stellen Sie sicher, dass die Daten, die von Machine learning-Lösungen verwendet konsistent und aktuell ist. 
+ Effizienz im gesamten Cloud und lokal. Anstatt Verarbeiten von Daten in R oder Python-Sitzungen können Sie eine verlassen auf Datenpipelines des Unternehmens einschließlich [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] und Azure Data Factory. Das Berichten von Ergebnissen oder Analysen ist über Power BI oder [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]einfach.

Durch die Verwendung der richtigen Kombination von SQL und R für verschiedene Datenverarbeitungstasks und analytische Tasks, können Datenanalysten und Entwickler produktiver sein.

<a name="components"></a>

## <a name="components"></a>Komponenten

SQL Server-2017 unterstützt R und Python. Die folgende Tabelle beschreibt die Komponenten an.

| Komponente | Description |
|-----------|-------------|
| SQL Server Launchpad-Dienst | Ein Dienst, der Kommunikation zwischen der externen R und Python-Laufzeiten und die Instanz der Datenbank-Engine verwaltet. |
| R-Pakete | [**RevoScaleR** ](r/ref-r-revoscaler.md) ist die primäre Bibliothek für skalierbare r-Funktionen in dieser Bibliothek auf die am häufigsten verwendeten sind. Datentransformationen und Manipulation, statistische Zusammenfassung, Visualisierung und viele Formen der Modellierung und Analysen werden in diesen Bibliotheken gefunden. Darüber hinaus verteilen Funktionen in diesen Bibliotheken automatisch Workloads auf verfügbaren Kerne für die parallele Verarbeitung, mit der Möglichkeit, die für Segmente der Daten zu arbeiten, die koordiniert und verwaltet werden, indem die berechnungs-Engine.  <br/>[**MicrosoftML (R)** ](r/ref-r-microsoftml.md) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen. <br/>[**SqlRUtils** ](r/ref-r-sqlrutils.md) Stellt Hilfsfunktionen für das Einfügen von R-Skripts in einer gespeicherten T-SQL-Prozedur, eine gespeicherte Prozedur mit einer Datenbank registrieren und Ausführen der gespeicherten Prozedur aus einer R-Entwicklungsumgebung.<br/>[**OlapR** ](r/ref-r-olapr.md) zum Erstellen oder eine MDX-Abfrage in R-Skript ausgeführt wird.|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open) ist die Open-Source-Distribution von R. Das Paket und ein Interpreter sind enthalten. Verwenden Sie immer die Version der MRO, die von Setup installiert. |
| R-tools | R-Konsole Windows und eingabeaufforderungen werden zu einer Verteilung von R-Standardtools.  |
| R-Beispiele und Skripts |  Open-Source-R und RevoScaleR-Pakete enthalten die integrierten Datasets, damit Sie erstellen und Ausführen von Skripts mit vorinstallierten Daten können. |
| Python-Pakete | [**die Revoscalepy** ](python/ref-py-revoscalepy.md) ist die primäre Bibliothek für skalierbare Python mit Funktionen zur datenbearbeitung, Transformation, Visualisierung und Analyse. <br/>[**Microsoftml (Python)** ](python/ref-py-microsoftml.md) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen.  |
| Python-tools | Das integrierte Tool der Python-Befehlszeile eignet sich für ad-hoc-Tests und Aufgaben.  |
| Anaconda | Anaconda ist ein Open-Source-Distribution von Python und essential-Pakete. |
| Python-Beispiele und Skripts | Enthält wie bei R, Python, integrierten Datasets und Skripts.  |
| Vortrainierte Modelle in R und Python | Vortrainierte Modelle sind für spezielle Anwendungsfälle von erstellt und verwaltet die Data Science engineering-Team bei Microsoft. Können Sie die vorab trainierte Modelle wie-besteht darin, eine Bewertung positiv Negative Stimmung im Text-Format oder Erkennen von Funktionen in Images können neue Dateneingaben, die Sie bereitstellen. Die Modelle in Machine Learning-Dienste ausgeführt, jedoch nicht über SQL Server-Setup installiert werden. Weitere Informationen finden Sie unter [installieren vorab trainierten Machine learning-Modelle in SQL Server](install/sql-pretrained-models-install.md). |

## <a name="using-sql-mls"></a>Verwenden von SQL-MLS

Entwickler und Wirtschaftsanalytiker verfügen häufig über Code, die auf einer lokalen SQL Server-Instanz ausgeführt wird. Hinzufügen von Machine Learning-Dienste aus, und Aktivieren der externen skriptausführung, erhalten Sie die Möglichkeit zum Ausführen von R und Python-Code in SQL Server-Modalitäten: Umschließen von Skripts in gespeicherten Prozeduren, Speichern von Modellen in einer SQL Server-Tabelle oder Kombinieren von T-SQL und R oder Python-Funktionen in Abfragen.

Ausführung des Skripts wird innerhalb der Grenzen des Sicherheitsmodells Daten: Berechtigungen für die relationale Datenbank bilden die Grundlage des Datenzugriffs in Ihrem Skript. Ein Benutzer, die R- oder Python-Skript ausführen sollte nicht zu verwenden, alle Daten, die von diesem Benutzer in einer SQL-Abfrage konnte nicht zugegriffen werden. Sie benötigen die standard-Datenbank Lese- und Schreibberechtigungen sowie eine zusätzliche Berechtigung zum Ausführen externen Skripts. Modellen und Code, den Sie für relationale Daten zu schreiben sind innerhalb von gespeicherten Prozeduren werden in einem binären Format serialisiert und in einer Tabelle gespeichert oder vom Datenträger geladen wird, wenn Sie den raw Bytestream in eine Datei serialisiert.

Die am häufigsten verwendete Ansatz für in-Database-Analyse ist die Verwendung [Sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), R oder Python-Skript als Eingabeparameter übergeben.

Klassischen Client / Server-Interaktionen sind ein weiterer Ansatz. Von einer beliebigen Clientarbeitsstation, die über eine IDE verfügt, können Sie installieren [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) oder [Python-Bibliotheken](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter), und klicken Sie dann Code schreiben, der Ausführung überträgt (genannt eine *remote-Compute Kontext*) auf Daten und Vorgänge mit einem SQL-Remoteserver. 

Schließlich bei Verwendung einer [eigenständiger Server](r/r-server-standalone.md) und Developer Edition können Sie Lösungen auf einer Clientarbeitsstation, die mit demselben Interpreter und Bibliotheken erstellen und anschließend bereitstellen Produktionscode in SQL Server Machine Learning Dienste (Datenbankintern). 

## <a name="how-to-get-started"></a>Erste Schritte

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der software

+ [SQL Server Machine Learning-Dienste (Datenbankintern)](install/sql-machine-learning-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren Sie ein Entwicklungstool

Datenanalysten verwenden R oder Python in der Regel auf ihre eigenen Arbeitsstation Laptop oder Entwicklungscomputer zum Durchsuchen von Daten, und erstellen und optimieren prädiktive Modelle aus, bis ein geeignetes Vorhersagemodell erreicht ist. Mit in-Database-Analyse in SQL Server ist es nicht erforderlich, diesen Prozess zu ändern. Nachdem die Installation abgeschlossen ist, können Sie R oder Python-Code in SQL Server lokal und Remote ausführen.

![rsql_keyscenario2](r/media/rsql-keyscenario2.png) 

+ **Verwenden Sie die IDE, die Sie bevorzugen**. Sie können die R- und Python-Bibliotheken zu Ihrem Entwicklungstool Ihrer Wahl verknüpfen. Weitere Informationen finden Sie unter [Einrichten von R-Tools](r/set-up-a-data-science-client.md) und [Python-Tools einrichten](python/setup-python-client-tools-sql.md).  

+ **Arbeiten Sie Remote oder lokal**. Datenanalysten können eine Verbindung mit SQL Server herstellen und bringen die Daten an dem Client zur lokalen Analyse wie gewohnt. Jedoch eine bessere Lösung ist die Verwendung der **RevoScaleR** oder **Revoscalepy** APIs Push Berechnungen auf dem SQL Server-Computer, um kostenintensive und unsichere datenbewegungen zu vermeiden.

+ **Einbetten von R oder Python-Skripts in SQL Server gespeicherte Prozeduren**. Wenn Ihr Code vollständig optimiert ist, binden Sie diese in einer gespeicherten Prozedur zum vermeiden unnötige datenbewegungen und Aufgaben der Datenverarbeitung zu optimieren.

### <a name="step-3-write-your-first-script"></a>Schritt 3: Das erste Skript schreiben

Rufen Sie R- oder Python-Funktionen in T-SQL-Skript:

+ [R: Erfahren Sie mehr in-Database-Analyse, die mithilfe von R](tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [R: End-to-End Walkthrough mit R](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
+ [Python: Führen Sie Python mit T-SQL](tutorials/run-python-using-t-sql.md)
+ [Python: Erfahren Sie mehr in-Database Analytics mithilfe von Python](tutorials/sqldev-in-database-python-for-sql-developers.md)

Wählen Sie die beste Sprache für den Task. R ist am besten für statistische Berechnungen, die mit SQL schwierig sind. Nutzen Sie für setbasierte Vorgänge für Daten die Leistungsfähigkeit von SQL Server, um maximale Leistung zu erzielen. Verwenden Sie die in-Memory-Datenbank-Engine für sehr schnelle Berechnungen über Spalten hinweg.

### <a name="step-4-optimize-your-solution"></a>Schritt 4: Optimieren Sie Ihre Lösung

Wenn das Modell für die Skalierung auf Enterprise-Daten ist, funktioniert der Data Scientist häufig mit dem Datenbankadministrator oder SQL-Entwickler, um Prozesse zu optimieren, wie z. B.:

+ Featureentwicklung
+ Datenerfassung und Transformation von Daten
+ Bewertung

In der Vergangenheit mussten Datenanalysten, die mithilfe von R Probleme mit der Leistung und Skalierung, insbesondere bei Verwendung von großen Datasets. Der Grund ist die Implementierung des allgemeinen Laufzeitmoduls einen einzelnen Thread und nur die Datasets, die in den verfügbaren Arbeitsspeicher auf dem lokalen Computer entsprechen aufnehmen kann. Integration in SQL Server Machine Learning Services bietet mehrere Features zur Verbesserung der Leistung mit größeren Datenmengen:

+ **RevoScaleR**: Dieses R-Paket enthält die Implementierung einiger der beliebtesten R-Funktionen, die neu gestaltet, um die Parallelität und Skalierung bereitzustellen. Das Paket enthält auch Funktionen, die weiter erhöhen, Leistung und Skalierbarkeit durch pushen von Berechnungen auf dem SQL Server-Computer, der in der Regel wesentlich mehr Arbeitsspeicher und rechenleistung verfügt.

+ **revoscalepy**. Diese Python-Bibliothek implementiert der beliebtesten Funktionen in RevoScaleR, z. B. remotecomputekontexte und viele Algorithmen, die Unterstützung verteilter Verarbeitung.

Weitere Informationen zur Leistung finden Sie in diesem [Fallstudie zur Leistung](r/performance-case-study-r-services.md) und [R und Data-Optimierung](r/r-and-data-optimization-r-services.md).

### <a name="step-5-deploy-and-consume"></a>Schritt 5: Bereitstellen und nutzen

Wenn das Skript oder das Modell für die Produktion bereit ist, kann ein Datenbankentwickler den Code oder das Modell in einer gespeicherten Prozedur einbetten, damit diese der gespeicherte R oder Python-Code aus einer Anwendung aufgerufen werden kann. Speichern und Ausführen von R-Code in SQL Server hat viele Vorteile: Sie können die geeignete SQL Server-Benutzeroberfläche verwenden, und alle Berechnungen erfolgen in der Datenbank, wodurch unnötige datenbewegungen vermieden.

![rsql_keyscenario1](r/media/rsql-keyscenario1.png)

+ **Sicheres und erweiterbares**. SQL Server verwendet eine neue erweiterbarkeitsarchitektur, die gewährleistet die Sicherheit Ihrer Datenbank-Engine und R und Python-Sitzungen isoliert. Sie haben auch die Kontrolle über die Benutzer, die Skripts ausgeführt werden kann, und Sie können angeben, welche Datenbanken, die vom Code zugegriffen werden können. Sie können die Menge an Ressourcen, die die Runtime zugeordnet werden, um zu verhindern, dass umfangreiche Berechnungen die gesamtleistung des Servers gefährden steuern.

+ **Planung und Überwachung**. Wenn externe Skripts für Aufträge in SQL Server ausgeführt werden, können Sie steuern und überwachen die von Datenanalysten verwendeten Daten. Sie können auch planen, Aufträge und Workflows erstellen, die externe R oder Python-Skripts, wie Sie jede andere T-SQL-Auftrag oder die gespeicherte Prozedur planen, würde.

Um die ressourcenverwaltung und Sicherheitsfunktionen in SQL Server nutzen, kann während des Bereitstellungsvorgangs diesen Aufgaben gehören:

+ Konvertieren von Code an eine Funktion, die optimal in einer gespeicherten Prozedur ausgeführt werden können
+ Einrichten der Sicherheit und Sperren Pakete, die von einer bestimmten Aufgabe verwendet werden.
+ Aktivieren der Ressourcenkontrolle (erfordert die Enterprise Edition)

Weitere Informationen finden Sie unter [Ressourcenkontrolle für R](r/resource-governance-for-r-services.md) und [R-Paketverwaltung für SQL Server](r/install-additional-r-packages-on-sql-server.md).

## <a name="version-history"></a>Versionsverlauf

SQL Server 2017-Machine Learning Services ist die nächste Generation von SQL Server 2016 R Services, erweitert und Python. In der folgende Tabelle ist eine vollständige Liste aller Produkt-Versionen, von Anfang an auf die aktuelle Version. 

| Produktname | Engine-version | Veröffentlichungsdatum |
|--------------|---------|--------------|
| SQL Server 2017-Machine-Learning-Services (Datenbankintern) | R Server 9.2.1 <br/> Python-Server 9.2 | Oktober 2017 |
| SQL Server 2017-Machine-Learning-Server (eigenständig) | R Server 9.2.1 <br/> Python-Server 9.2 | Oktober 2017 |
| SQL Server 2016 R Services (Datenbankintern) | R Server 9.1  | Juli 2017  |
| SQL Server 2016 R Server (eigenständig)  |  R Server 9.1 | Juli 2017 |

Versionen des Pakets von Version, finden Sie unter der Version in Zuordnung [ein Upgrade von R und Python-Komponenten](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md#version-map).

## <a name="portability-and-related-products"></a>Portabilität und verwandte Produkte

Portabilität von Ihrem benutzerdefinierten R- und Python-Code wird behoben, durch Package-Distribution und Interpreter, die in mehrere Produkte integriert sind. Die gleichen Pakete der SQL Server sind auch verfügbar in verschiedene andere Microsoft-Produkte und Dienste, einschließlich einer nicht-SQL-Version wird aufgerufen, [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/). 

Kostenlose Clients, die unsere R- und Python-Interpretern sind [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) und [Python-Bibliotheken](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter).

In Azure, Microsoft R und Python-Paketen und -Interpretern sind auch verfügbar in Azure Machine Learning und Azure-Dienste wie [HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview), und [virtuellen Azure-Computern](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-azure-vm-on-linux). Die [Data Science Virtual Machine](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) enthält eine vollständig ausgestatteten Entwicklungsarbeitsstation mit Tools von mehreren Anbietern als auch die Bibliotheken und Interpreter von Microsoft.

## <a name="see-also"></a>Siehe auch

[Installieren von SQL Server Machine Learning-Dienste](install/sql-machine-learning-services-windows-install.md)
