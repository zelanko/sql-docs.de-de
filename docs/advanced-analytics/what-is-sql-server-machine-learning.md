---
title: Übersicht über SQL Server Machine Learning Services (R, python)
description: Übersicht über das Machine Learning Services Feature in SQL Server, in dem Sie python und R mit relationalen Daten für Data Science und statistische Modellierung, Machine Learning-Modelle, Predictive Analytics, Datenvisualisierung und vieles mehr integrieren können.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: ead0dd3d9ba69a4bf0079fe8065a2d5aa7a11d3e
ms.sourcegitcommit: 63c6f3758aaacb8b72462c2002282d3582460e0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68495397"
---
# <a name="sql-server-machine-learning-services-r-python"></a>SQL Server Machine Learning Services (R, python)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Machine Learning Services ist eine Funktion von SQL Server, die zum Ausführen von R-und python-Skripts in der Datenbank verwendet wird. Das Feature umfasst [Microsoft R-und Python-Pakete](#components) für Hochleistungs Predictive Analytics und Maschinelles Lernen. Die relationalen Daten können in r-und python-Skripts durch gespeicherte Prozeduren, T-SQL-Skripts mit r-und python-Anweisungen oder r-und Python-Code mit T-SQL verwendet werden.

Wenn Sie zuvor [SQL Server 2016 R-Dienste](r/sql-server-r-services.md)verwendet haben, ist Machine Learning Services in SQL Server 2017 und höher die nächste Generation von r-Unterstützung mit aktualisierten Versionen von Base r, revoscaler, microsoftml und anderen Bibliotheken, die in 2016 eingeführt wurden.

In Azure SQL-Datenbank befindet sich [Machine Learning Services (mit R)](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview) zurzeit in der öffentlichen Vorschau Phase.

## <a name="bring-compute-power-to-the-data"></a>Rechenleistung für die Daten

Der wichtigste Wert von Machine Learning Services ist die Leistungsfähigkeit der R-und Python-Pakete von Unternehmen, um erweiterte Analysefunktionen bereitzustellen, sowie die Möglichkeit, Berechnungen und Verarbeitungsvorgänge in den Speicherort der Daten zu übertragen, sodass keine Daten mehr übertragen werden müssen. das Netzwerk. Dies bietet mehrere Vorteile:

+ Datensicherheit. Wenn Sie die R-und python-Ausführung näher an der Datenquelle machen, vermeiden Sie verschwenderisch oder unsichere Daten Verschiebungen.
+ Geschwindigkeit. Datenbanken sind für setbasierte Vorgänge optimiert. Aktuelle Innovationen in Datenbanken, wie z. b. in-Memory-Tabellen, machen Zusammenfassungen und Aggregationen blitzartig und sind eine perfekte Ergänzung der Data Science.
+ Einfache Bereitstellung und Integration. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ist der zentrale Punkt von Vorgängen für viele andere Daten Verwaltungsaufgaben und-Anwendungen. Mithilfe von Daten, die sich in der Datenbank oder im Berichterstattungs-Warehouse befinden, stellen Sie sicher, dass die von Machine Learning-Lösungen verwendeten Daten konsistent und aktuell sind. 
+ Effizienz in der Cloud und lokal. Anstatt Daten in R-oder python-Sitzungen zu verarbeiten, können Sie auf Unternehmensdaten Pipelines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] wie und Azure Data Factory basieren. Das Berichten von Ergebnissen oder Analysen ist über Power BI oder [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]einfach.

Durch die Verwendung der richtigen Kombination von SQL und R für verschiedene Datenverarbeitungstasks und analytische Tasks, können Datenanalysten und Entwickler produktiver sein.

<a name="components"></a>

## <a name="components"></a>Komponenten

SQL Server-2017 unterstützt R und Python. In der folgenden Tabelle werden die-Komponenten beschrieben.

| Komponente | Beschreibung |
|-----------|-------------|
| SQL Server-Launchpad-Dienst | Ein Dienst, der die Kommunikation zwischen der externen R-und der python-Laufzeiten und der Datenbank-Engine-Instanz verwaltet. |
| R-Pakete | [**Revoscaler**](r/ref-r-revoscaler.md) ist die primäre Bibliothek für skalierbare R. Funktionen in dieser Bibliothek gehören zu den am häufigsten verwendeten Funktionen. In diesen Bibliotheken finden Sie Daten Transformationen und-Manipulation, statistische Zusammenfassung, Visualisierung und viele Formen der Modellierung und Analyse. Außerdem verteilen Funktionen in diesen Bibliotheken Workloads automatisch auf verfügbare Kerne für die parallele Verarbeitung, mit der Möglichkeit, an Datenblöcken zu arbeiten, die von der Berechnungs-Engine koordiniert und verwaltet werden.  <br/>[**Microsoftml (R)** ](r/ref-r-microsoftml.md) fügt Machine Learning-Algorithmen hinzu, um benutzerdefinierte Modelle für die Textanalyse, die Bildanalyse und die Stimmungs Analyse zu erstellen. <br/>[**sqlrutils**](r/ref-r-sqlrutils.md) stellt Hilfsfunktionen für das Einfügen von R-Skripts in eine gespeicherte T-SQL-Prozedur, das Registrieren einer gespeicherten Prozedur in einer Datenbank und das Ausführen der gespeicherten Prozedur aus einer R-Entwicklungsumgebung bereit.<br/>[**olapr**](r/ref-r-olapr.md) dient zum Erstellen oder Ausführen einer MDX-Abfrage im R-Skript.|
| Microsoft R Open (MRO) | [**MRO**](https://mran.microsoft.com/open) ist die Open Source-Verteilung von R von Microsoft. Das Paket und der Interpreter sind eingeschlossen. Verwenden Sie immer die von Setup installierte MRO-Version. |
| R-Tools | R-Konsolenfenster und Eingabe Aufforderungen sind Standard Tools in einer R-Distribution.  |
| R-Beispiele und-Skripts |  Open-Source-R-und revoscaler-Pakete enthalten integrierte Datasets, mit denen Sie Skripts mit vorinstallierten Daten erstellen und ausführen können. |
| Python-Pakete | [**revoscalepy**](python/ref-py-revoscalepy.md) ist die primäre Bibliothek für skalierbare python mit Funktionen für die Datenbearbeitung, Transformation, Visualisierung und Analyse. <br/>[**microsoftml (python)** ](python/ref-py-microsoftml.md) fügt Machine Learning-Algorithmen hinzu, um benutzerdefinierte Modelle für die Textanalyse, die Bildanalyse und die Stimmungs Analyse zu erstellen.  |
| Python-Tools | Das integrierte python-Befehlszeilen Tool eignet sich für Ad-hoc-Tests und-Aufgaben.  |
| Anaconda | Anaconda ist eine Open Source-Verteilung von Python-und Essentials-Paketen. |
| Python-Beispiele und-Skripts | Wie bei R umfasst python auch integrierte Datasets und Skripts.  |
| Vortrainierte Modelle in R und python | Vorab trainierte Modelle werden für bestimmte Anwendungsfälle erstellt und vom Data Science Engineering-Team bei Microsoft verwaltet. Mit den von Ihnen bereitgestellten neuen Dateneingaben können Sie die vorab trainierten Modelle unverändert verwenden, um positive negative Stimmungen in Text zu bewerten oder Features in Bildern zu erkennen. Die Modelle werden in Machine Learning Services ausgeführt, können jedoch nicht über SQL Server Setup installiert werden. Weitere Informationen finden Sie unter [Installieren von vorab trainierten Machine Learning-Modellen auf SQL Server](install/sql-pretrained-models-install.md). |

## <a name="using-sql-mls"></a>Verwenden von SQL-MLS

Entwickler und Analysten verfügen häufig über Code, der auf einer lokalen SQL Server-Instanz ausgeführt wird. Wenn Sie Machine Learning Services hinzufügen und die Ausführung externer Skripts aktivieren, erhalten Sie die Möglichkeit, R-und Python-Code in SQL Server Modalitäten auszuführen: das Packen von Skripts in gespeicherten Prozeduren, das Speichern von Modellen in einer SQL Server Tabelle oder das Kombinieren von T-SQL-und R in Abfragen.

Die Skriptausführung liegt innerhalb der Grenzen des Daten Sicherheitsmodells: Berechtigungen für die relationale Datenbank sind die Grundlage für den Datenzugriff in Ihrem Skript. Ein Benutzer, der ein R-oder Python-Skript verwendet, sollte keine Daten verwenden können, auf die dieser Benutzer in einer SQL-Abfrage nicht zugreifen konnte. Sie benötigen die Lese-und Schreibberechtigungen der Standarddatenbank sowie eine zusätzliche Berechtigung zum Ausführen externer Skripts. Modelle und Code, die Sie für relationale Daten schreiben, werden in gespeicherte Prozeduren umgeschrieben oder in ein Binärformat serialisiert und in einer Tabelle gespeichert oder vom Datenträger geladen, wenn Sie den unformatierten Bytestream in eine Datei serialisieren.

Der häufigste Ansatz für Daten bankübergreifende Analysen ist die Verwendung von [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), indem R-oder python-Skripts als Eingabeparameter übergeben werden.

Klassische Client-Server-Interaktionen sind ein weiterer Ansatz. Auf jeder Client Arbeitsstation mit einer IDE können Sie [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) oder die python- [Bibliotheken](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)installieren und dann Code schreiben, der die Ausführung (als remotecomputekontext bezeichnet) auf Daten und Vorgänge an eine Remote SQL Server überträgt. 

Wenn Sie einen [eigenständigen Server](r/r-server-standalone.md) und die Developer Edition verwenden, können Sie mit denselben Bibliotheken und Interpretern Lösungen auf einer Client Arbeitsstation erstellen und dann Produktionscode auf SQL Server Machine Learning Services (Daten bankeigen) bereitstellen. 

## <a name="how-to-get-started"></a>Vorgehensweise beim Einstieg

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der Software

+ [SQL Server Machine Learning Services (in-Database)](install/sql-machine-learning-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren eines Entwicklungs Tools

Datenanalysten verwenden R oder python in der Regel auf Ihrem eigenen Laptop oder Ihrer Entwicklungs Arbeitsstation, um Daten zu durchsuchen und Vorhersagemodelle zu erstellen und zu optimieren, bis ein gutes Vorhersagemodell erreicht wird. Bei Daten bankinternen Analysen in SQL Server muss dieser Prozess nicht geändert werden. Nach Abschluss der Installation können Sie R-oder python-Code auf SQL Server lokal und Remote ausführen.

![rsql_keyscenario2](r/media/rsql-keyscenario2.png) 

+ **Verwenden Sie die von Ihnen bevorzugte IDE**. Sie können die R-und python-Bibliotheken mit dem Entwicklungs Tool Ihrer Wahl verknüpfen. Weitere Informationen finden Sie unter [Einrichten von R-Tools](r/set-up-a-data-science-client.md) und [Einrichten von python-Tools](python/setup-python-client-tools-sql.md).  

+ **Arbeiten Sie Remote oder lokal**. Datenanalysten können eine Verbindung mit SQL Server herstellen und die Daten für die lokale Analyse wie gewohnt auf den Client übertragen. Eine bessere Lösung ist jedoch die Verwendung der **revoscaler** -oder **revoscalepy** -APIs, um Berechnungen an den SQL Server Computer zu übermitteln und so eine kostspielige und unsichere Daten Verschiebung zu vermeiden.

+ **Integrieren Sie R-oder python-Skripts in SQL Server gespeicherte Prozeduren** Wenn Ihr Code vollständig optimiert ist, wrappen Sie ihn in einer gespeicherten Prozedur, um unnötige Daten Verschiebungen zu vermeiden und Datenverarbeitungs Aufgaben zu optimieren.

### <a name="step-3-write-your-first-script"></a>Schritt 3: Schreiben Ihres ersten Skripts

R-oder python-Funktionen innerhalb des T-SQL-Skripts aufzurufen:

+ [R Erlernen von Daten bankbasierten Analysen mit R](tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [R Exemplarische End-to-End-Exemplarische Vorgehensweise mit R](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
+ [Python: Ausführen von Python mit T-SQL](tutorials/run-python-using-t-sql.md)
+ [Python: Informationen in Daten Bank Analysen mithilfe von python](tutorials/sqldev-in-database-python-for-sql-developers.md)

Wählen Sie die beste Sprache für den Task aus. R eignet sich am besten für statistische Berechnungen, die mit SQL schwierig zu implementieren sind. Nutzen Sie die Leistungsfähigkeit von SQL Server, um eine maximale Leistung zu erzielen. Verwenden Sie die in-Memory-Datenbank-Engine für sehr schnelle Berechnungen über Spalten.

### <a name="step-4-optimize-your-solution"></a>Schritt 4: Optimieren der Lösung

Wenn das Modell für die Skalierung von Unternehmensdaten bereit ist, arbeitet der Daten Analyst häufig mit dem DBA-oder SQL-Entwickler zusammen, um Prozesse wie die folgenden zu optimieren:

+ Featureentwicklung
+ Datenerfassung und Datentransformation
+ Hnen

Normalerweise haben Datenanalysten mit R Probleme mit Leistung und Skalierbarkeit verursacht, insbesondere bei der Verwendung großer Datasets. Dies liegt daran, dass die allgemeine Lauf Zeit Implementierung Single Thread ist und nur die Datasets unterstützen kann, die in den verfügbaren Arbeitsspeicher auf dem lokalen Computer passen. Die Integration in SQL Server Machine Learning Services bietet mehrere Features, um die Leistung zu verbessern, mit mehr Daten:

+ **Revoscaler**: Dieses R-Paket enthält Implementierungen einiger der beliebtesten R-Funktionen, die neu gestaltet wurden, um Parallelität und Skalierbarkeit bereitzustellen. Das Paket enthält auch Funktionen, die die Leistung und Skalierbarkeit verbessern, indem Berechnungen auf den SQL Server Computer übertragen werden, der in der Regel viel mehr Arbeitsspeicher und Rechenleistung aufweist.

+ **revoscalepy**. Diese Python-Bibliothek implementiert die beliebtesten Funktionen in revoscaler, z. b. remotecomputekontexte und viele Algorithmen, die die verteilte Verarbeitung unterstützen.

Weitere Informationen zur Leistung finden Sie in dieser [Leistungs Fallstudie](r/performance-case-study-r-services.md) und in der [R-und Daten Optimierung](r/r-and-data-optimization-r-services.md).

### <a name="step-5-deploy-and-consume"></a>Schritt 5: Bereitstellen und nutzen

Nachdem das Skript oder das Modell für die Verwendung in der Produktion bereit ist, kann ein Datenbankentwickler den Code oder das Modell in eine gespeicherte Prozedur einbetten, sodass der gespeicherte R-oder python-Code von einer Anwendung aufgerufen werden kann. Das Speichern und Ausführen von R-Code aus SQL Server hat viele Vorteile: Sie können die praktische SQL Server Schnittstelle verwenden, und alle Berechnungen erfolgen in der Datenbank, wodurch unnötige Daten Verschiebungen vermieden werden.

![rsql_keyscenario1](r/media/rsql-keyscenario1.png)

+ **Sicher und erweiterbar**. SQL Server verwendet eine neue Erweiterbarkeits Architektur, die die Datenbank-Engine schützt und R-und python-Sitzungen isoliert. Außerdem haben Sie die Kontrolle über die Benutzer, die Skripts ausführen können, und Sie können angeben, auf welche Datenbanken durch Code zugegriffen werden kann. Sie können die Menge der Ressourcen steuern, die der Laufzeit zugeordnet sind, um zu verhindern, dass umfangreiche Berechnungen die Gesamtleistung des Servers gefährden.

+ **Planung und**Überwachung. Wenn externe Skript Aufträge in SQL Server ausgeführt werden, können Sie die von Datenanalysten verwendeten Daten steuern und überwachen. Sie können auch Aufträge planen und Workflows erstellen, die externe R-oder python-Skripts enthalten, genauso wie Sie einen anderen T-SQL-Auftrag oder eine gespeicherte Prozedur planen.

Um die Features für die Ressourcenverwaltung und die Sicherheit in SQL Server nutzen zu können, kann der Bereitstellungs Prozess folgende Aufgaben umfassen:

+ Wandeln Sie Ihren Code in eine Funktion um, die in einer gespeicherten Prozedur optimal ausgeführt werden kann.
+ Einrichten der Sicherheit und Sperren von Paketen, die von einer bestimmten Aufgabe verwendet werden
+ Aktivieren der Ressourcenkontrolle (erfordert die Enterprise Edition)

Weitere Informationen finden Sie unter [Ressourcenkontrolle für r](r/resource-governance-for-r-services.md) und [r-Paketverwaltung für SQL Server](r/install-additional-r-packages-on-sql-server.md).

## <a name="version-history"></a>Versionsverlauf

SQL Server 2017 Machine Learning Services ist die nächste Generation von SQL Server 2016 R Services, erweitert um Python. Die folgende Tabelle stellt eine vollständige Liste aller Produktversionen dar, von Anfang bis zur aktuellen Version. 

| Produktname | Engine-Version | Veröffentlichungsdatum |
|--------------|---------|--------------|
| SQL Server 2017 Machine Learning Services (in-Database) | R Server 9.2.1 <br/> Python-Server 9,2 | Oktober 2017 |
| SQL Server 2017 Machine Learning Server (eigenständig) | R Server 9.2.1 <br/> Python-Server 9,2 | Oktober 2017 |
| SQL Server 2016 R Services (in-Database) | R Server 9,1  | 2017. Juli  |
| SQL Server 2016 R Server (eigenständig)  |  R Server 9,1 | 2017. Juli |

Informationen zu Paketversionen nach Release finden Sie in der Versions Zuordnung unter Upgraden von [R-und python-Komponenten](install/upgrade-r-and-python.md#version-map).

## <a name="portability-and-related-products"></a>Portabilität und Verwandte Produkte

Die Portabilität Ihres benutzerdefinierten R-und python-Codes wird mithilfe von Paketverteilung und Interpretern adressiert, die in mehrere Produkte integriert sind. Die Pakete, die in SQL Server ausgeliefert werden, sind auch in mehreren anderen Microsoft-Produkten und-Diensten verfügbar, einschließlich einer nicht-SQL-Version mit dem Namen [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/). 

Kostenlose Clients, die unsere R-und Python-Interpreter enthalten, sind [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) und die [python-Bibliotheken](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter).

In Azure sind die R-und Python-Pakete und-Interpreter von Microsoft auch auf Azure Machine Learning und Azure-Diensten wie [hdinsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview)und [Azure Virtual Machines](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-azure-vm-on-linux)verfügbar. Die [Data Science Virtual Machine](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) umfasst eine vollständig ausgestattete Entwicklungs Arbeitsstation mit Tools von mehreren Anbietern sowie den Bibliotheken und Interpretern von Microsoft.

## <a name="see-also"></a>Siehe auch

[Installieren Sie SQL Server Machine Learning Services](install/sql-machine-learning-services-windows-install.md)
