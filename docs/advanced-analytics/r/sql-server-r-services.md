---
title: SQLServer Machine Learning und R-Services (Datenbankintern) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 05a2a17988912d7066b0d9f6bf398b889a3cd882
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174777"
---
# <a name="sql-server-machine-learning-and-r-services-in-database"></a>SQLServer Machine Learning und R-Services (Datenbankintern)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Eine Installation in der Datenbank des maschinellen Lernens operiert innerhalb des Kontexts einer SQL Server-Datenbank-Engine-Instanz, R und Python externes Skript-Unterstützung für Residente Daten in Ihrer SQL Server-Instanz bereitzustellen. In Machine Learning integriert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], können Sie Analysen in der Nähe der Daten und zu beseitigen, die Kosten und Sicherheitsrisiken bei der datenverschiebung.

Da die Datenbank-Engine mit mehreren Instanzen ist, können Sie mehrere Instanzen von in-Database-Analyse, oder auch ältere und neuere Versionen Seite-an-Seite installieren. Optionen sind entweder [SQL Server 2017-Machine Learning Services (Datenbankintern)](../install/sql-machine-learning-standalone-windows-install.md) mit R und Python oder [SQL Server 2016 R Services (Datenbankintern)](../install/sql-r-standalone-windows-install.md) mit nur R. 

Machine Learning-Komponenten können auch als Unabhängigkeit von der Instanz installiert [eigenständigen Servern](r-server-standalone.md). Im Allgemeinen empfohlen, Sie behandeln (eigenständig) und (In-Database) Installationen als sich gegenseitig exklusiv zur Vermeidung von Ressourcenkonflikten, aber wenn Sie über genügend Ressourcen stehen keine verboten für beide auf demselben physischen Computer installieren.

## <a name="choosing-between-in-database-and-standalone-analytics"></a>Auswählen zwischen Analysen in der Datenbank und eigenständige

Grundlegendes zu den entwicklungsanforderungen Ihrer können Sie entscheiden (In-Database) und (eigenständig) erreicht. Ein eigenständigen Server ist einfacher zu konfigurieren und verwalten Sie maximale Flexibilität wie diese verwendet werden soll, oder wenn Sie auch eine Verbindung mit einer Vielzahl von Datenquellen außerhalb von SQL Server herstellen möchten. 

In-Database-Analyse dienen für die enge Integration mit Daten in SQL Server. Sie können die T-SQL-Abfragen schreiben, die R- oder Python-Funktionen aufrufen, und führen Sie das Skript in SQL Server Management Studio oder beliebige Tools oder die app, die für externe oder eingebettete T-SQL verwendet. Bei Bedarf zum Ausführen von R oder Python-Code in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], entweder mithilfe von gespeicherten Prozeduren oder mithilfe von SQL Server-Instanz als die [compute Context verwenden](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context), müssen Sie in-Database-Analyse installieren. Diese Option bietet maximale Sicherheit und Integration in SQL Server-Tools.

Sowohl in der Datenbank und die Arbeitsspeicher und verarbeitungsleistung Einschränkungen von Open-Source-R und Python können ein eigenständiger Server verringern. Beide Optionen werden die gleichen Pakete und Tools, mit der Möglichkeit zum Laden und verarbeiten große Mengen von Daten auf mehreren Kernen und Aggregieren der Ergebnisse in eine einzelne, konsolidierte Ausgabe enthalten. Die Funktionen und Algorithmen werden für sowohl Skalierung als auch Hilfsprogramm entwickelt: Bereitstellung von predictive Analytics, statistische Modellierung, datenvisualisierungen und fortschrittliche-Machine learning-Algorithmen in einer kommerziellen Serverprodukt konzipiert und unterstützt von Von Microsoft. 

## <a name="components-of-an-in-database-installation"></a>Komponenten einer in-Database-installation

R wird nur von SQL Server 2016 ist. SQL Server-2017 unterstützt R und Python. Die folgende Tabelle beschreibt die Funktionen in der jeweiligen Version. Mit Ausnahme von den SQL Server Launchpad-Dienst in dieser Tabelle ist identisch mit dem Umwandlungsoperator den [eigenständige Server-Artikel](r-server-standalone.md).

| Komponente | Description |
|-----------|-------------|
| SQL Server Launchpad-Dienst | Ein Dienst, der Kommunikation zwischen der externen R und Python-Laufzeiten verwaltet und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz. |
| R-Pakete | [RevoScaleR](revoscaler-overview.md) ist die primäre Bibliothek für skalierbare R mit Funktionen zur datenbearbeitung, Transformation, Visualzation und Analyse.  <br/>[MicrosoftML (R)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen. <br/>[Mrsdeploy](operationalization-with-mrsdeploy.md) bietet web-Service-Bereitstellung (in nur SQL Server 2017). <br/>[OlapR](how-to-create-mdx-queries-using-olapr.md) dient zum Angeben von MDX-Abfragen in r|
| Microsoft R Open (MRO) | [MRO](https://mran.microsoft.com/open) ist die Open-Source-Distribution von R. Das Paket und ein Interpreter sind enthalten. Verwenden Sie immer die Version der MRO Setup gebündelt. |
| R-tools | R-Konsole Windows und eingabeaufforderungen werden zu einer Verteilung von R-Standardtools. Finden sie unter \Programme\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| R-Beispiele und Skripts |  Open-Source-R und RevoScaleR-Pakete enthalten die integrierten Datasets, damit Sie erstellen und Ausführen von Skripts mit vorinstallierten Daten können. Suchen Sie unter \Programme\Microsoft SQL Server\140\R_SERVER\library\datasets und \library\RevoScaleR. |
| Python-Pakete | [die Revoscalepy](../python/what-is-revoscalepy.md) ist die primäre Bibliothek für skalierbare Python mit Funktionen zur datenbearbeitung, Transformation, Visualzation und Analyse. <br/>[Microsoftml (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen.  |
| Python-tools | Das integrierte Tool der Python-Befehlszeile eignet sich für ad-hoc-Tests und Aufgaben. Suchen Sie das Tool im Verzeichnis \Programme\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda ist ein Open-Source-Distribution von Python und essential-Pakete. |
| Python-Beispiele und Skripts | Enthält wie bei R, Python, integrierten Datasets und Skripts. Suchen Sie die Revoscalepy-Daten unter \Programme\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-Packages\revoscalepy\data\sample-Daten. |
| Vortrainierte Modelle in R und Python | Vortrainierte Modelle werden unterstützt und auf einem eigenständigen Server verwendet werden, aber sie kann nicht über SQL Server-Setup installiert werden. Das Setupprogramm für die Microsoft Machine Learning Server stellt die Modellen, die Sie installieren können kostenlos. Weitere Informationen finden Sie unter [Installation vorab Machine Learning-Modelle in SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="get-started-step-by-step"></a>Beginnen Sie Schritt für Schritt

Mit dem Setup starten Sie, fügen Sie die Binärdateien an Ihrem bevorzugten Entwicklungstool und Schreiben Sie das erste Skript.

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der Softwareupdates

Installieren Sie entweder eine dieser Versionen:

+ [SQL Server 2017-Machine-Learning-Services (Datenbankintern)](../install/sql-machine-learning-services-windows-install.md)

+ [SQL Server 2016 R Services (Datenbankintern) – nur R](../install/sql-r-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren Sie ein Entwicklungstool

Konfigurieren Sie Ihre Entwicklungstools, um die Machine Learning Server-Binärdateien zu verwenden. Weitere Informationen zu Python finden Sie unter [Link-Python-Binärdateien](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Anweisungen zur Verwendung in R Studio eine Verbindung herstellen, finden Sie unter [mit verschiedenen Versionen von R](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) , und zeigen Sie das Tool zu C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64. Sie können auch ausprobieren [R-Tools für Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation). 

Datenanalysten verwenden R oder Python in der Regel auf ihre eigenen Arbeitsstation Laptop oder Entwicklungscomputer zum Durchsuchen von Daten, und erstellen und optimieren prädiktive Modelle aus, bis ein geeignetes Vorhersagemodell erreicht ist. 

Mit in-Database-Analyse in SQL Server ist es nicht erforderlich, diesen Prozess zu ändern. Nach Abschluss der Installation können Sie R oder Python-Code ausführen, auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entweder lokal oder Remote:

![rsql_keyscenario2](media/rsql-keyscenario2.png) 

+ **Verwenden Sie die IDE, die Sie bevorzugen**. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] -Clientkomponenten stellen für Datenanalysten sämtliche Tools bereit, die zum Experimentieren und Entwickeln erforderlich sind. Zu diesen Tools zählen die R-Laufzeitversion, die mathematische Kernelbibliothek von Intel zur Leistungssteigerung von R-Standardfunktionen sowie eine Reihe von erweiterten R-Paketen, die das Ausführen von R-Code in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützen.  

+ **Arbeiten Sie Remote oder lokal**. Datenanalysten können eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und dem Client die Daten wie gewohnt zur lokalen Analyse vorlegen. Jedoch eine bessere Lösung ist die Verwendung der **RevoScaleR** oder **Revoscalepy** APIs, um die Push-Berechnungen, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer, um kostenintensive und unsichere datenbewegungen zu vermeiden.

+ **Einbetten von R oder Python-Skripts in [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren**. Wenn Ihr Code vollständig optimiert ist, binden Sie diese in einer gespeicherten Prozedur zum vermeiden unnötige datenbewegungen und Aufgaben der Datenverarbeitung zu optimieren.

### <a name="step-3-write-your-first-script"></a>Schritt 3: Schreiben Sie das erste Skript.

Rufen Sie R- oder Python-Funktionen in T-SQL-Skript:
  
  + [R: Verwenden des R-Codes in Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md) 
  + [R: Datenbankinterne Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)
  + [Python: Ausführen von Python mit T-SQL](../tutorials/run-python-using-t-sql.md)
  + [Python: Datenbankinterne Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Wählen Sie die beste Sprache für den Task. R ist am besten für statistische Berechnungen, die mit SQL schwierig sind. Nutzen Sie für setbasierte Vorgänge für Daten, die die Leistungsfähigkeit des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um maximale Leistung zu erzielen. Verwenden Sie die in-Memory-Datenbank-Engine für sehr schnelle Berechnungen über Spalten hinweg.

### <a name="step-4-optimize-your-solution"></a>Schritt 4: Optimieren Sie Ihre Lösung

Wenn das Modell für die Skalierung auf Enterprise-Daten ist, funktioniert der Data Scientist häufig mit dem Datenbankadministrator oder SQL-Entwickler, um Prozesse zu optimieren, wie z. B.:

+ Featureentwicklung
+ Datenerfassung und Transformation von Daten
+ Bewertung

Bisher mussten Datenanalysten, die mithilfe von R Probleme mit der Leistung und Skalierung, vor allem bei Verwendung von großen Datasets. Der Grund ist die Implementierung des allgemeinen Laufzeitmoduls einen einzelnen Thread und nur die Datasets, die in den verfügbaren Arbeitsspeicher auf dem lokalen Computer entsprechen aufnehmen kann. Integration in SQl Server Machine Learning Services bietet mehrere Features zur Verbesserung der Leistung mit größeren Datenmengen:

+ **RevoScaleR**: Diese R-Paket enthält die Implementierung einiger der beliebtesten R-Funktionen, die neu gestaltet, um die Parallelität und Skalierung bereitzustellen. Das Paket enthält auch Funktionen, die die Leistung und Skalierung weiter erhöhen, indem Berechnungen mittels Push auf den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computer übertragen werden, der in der Regel über wesentlich mehr Arbeitsspeicher und Rechenleistung verfügt.

+ **die Revoscalepy**. Dieser Python-Bibliotheken, die in SQL Server 2017 verfügbar implementiert der beliebtesten Funktionen in RevoScaleR, z. B. remotecomputekontexte und viele Algorithmen, die Unterstützung verteilter Verarbeitung.

**Ressourcen**

+ [Fallstudie zur Leistung](../../advanced-analytics/r/performance-case-study-r-services.md)
+ [R- und Datenoptimierung](../../advanced-analytics/r/r-and-data-optimization-r-services.md)

### <a name="step-5-deploy-and-consume"></a>Schritt 5: Bereitstellen und nutzen

Nachdem das Skript oder das Modell für die Produktion bereit ist, kann ein Datenbankentwickler den Code oder das Modell in einer gespeicherten Prozedur einbetten, sodass der gespeicherte R oder Python-Code aus einer Anwendung aufgerufen werden kann. Das Speichern und Ausführen von R über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet viele Vorteile: Sie können die komfortable [!INCLUDE[tsql](../../includes/tsql-md.md)] -Benutzeroberfläche verwenden. Außerdem erfolgen sämtliche Berechnungen in der Datenbank, wodurch unnötige Datenbewegungen vermieden werden.

![rsql_keyscenario1](media/rsql-keyscenario1.png)

+ **Sicheres und erweiterbares**. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] verwendet eine neue erweiterbarkeitsarchitektur, die gewährleistet die Sicherheit Ihrer Datenbank-Engine und R und Python-Sitzungen isoliert. Sie haben auch die Kontrolle über die Benutzer, die Skripts ausgeführt werden kann, und Sie können angeben, welche Datenbanken, die vom Code zugegriffen werden können. Sie können die Menge an Ressourcen, die die Runtime zugeordnet werden, um zu verhindern, dass umfangreiche Berechnungen die gesamtleistung des Servers gefährden steuern.

+ **Planung und Überwachung**. Wenn externe Skripts für Aufträge ausgeführt werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], können Sie steuern und überwachen Sie die Daten von datenspezialisten verwendet. Sie können auch planen, Aufträge und Workflows erstellen, die externe R oder Python-Skripts, wie Sie jede andere T-SQL-Auftrag oder die gespeicherte Prozedur planen, würde.

Um die Vorteile der Verwaltung und Sicherheit Funktionen in SQL Server nutzen zu können, kann der Bereitstellungsprozess diesen Aufgaben gehören:

+ Konvertieren von Yourcode an eine Funktion, die optimal in einer gespeicherten Prozedur ausgeführt werden können
+ Einrichten der Sicherheit und Sperren Pakete, die von einer bestimmten Aufgabe verwendet werden.
+ Aktivieren der Ressourcenkontrolle (erfordert die Enterprise Edition)

**Ressourcen**

+ [Ressourcenkontrolle für R](resource-governance-for-r-services.md)
+ [R-Paketverwaltung für SQLServer](install-additional-r-packages-on-sql-server.md)

## <a name="see-also"></a>Siehe auch

 [SQLServer Machine Learning und R Server (eigenständig)](sql-server-r-services.md)
