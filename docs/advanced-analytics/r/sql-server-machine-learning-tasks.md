---
title: Machine learning-Lebenszyklus und die Team-Prozess – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2218034dd6ac4cc3e7926b214c5c021815e57ed3
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432203"
---
# <a name="machine-learning-lifecycle-and-personas"></a>Machine Learning-Lebenszyklus und personas
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Machine Learning-Projekten können komplex sein, da sie die Fähigkeiten und Zusammenarbeit einem unterschiedlichen Satz von IT-Experten benötigen. Dieser Artikel beschreibt die grundlegenden Aufgaben im Lebenszyklus Machine Learning, der den Typ des Daten-Experten, die in Machine Learning und wie die Anforderungen von SQL Server unterstützt involviert sind.

> [!TIP]
> 
> Bevor Sie mit einem Machine Learning-Projekt beginnen, es wird empfohlen, dass Sie die Tools und bewährten Methoden, die bereitgestellt werden, indem Sie überprüfen die [Microsoft Data Science-Prozesses](https://blogs.technet.microsoft.com/machinelearning/2017/10/09/the-microsoft-team-data-science-process-tdsp-recent-updates/), oder TDSP. Dieser Prozess wurde von Machine learning-Berater bei Microsoft, konsolidieren bewährte Verfahren für die Planung und Durchlaufen von Machine learning-Projekte erstellt. Der TDSP hat seine Wurzeln in Industriestandards wie CRISP-DM, enthält jedoch aktuelle Methoden wie z. B. DevOps und Visualisierung.

## <a name="machine-learning-life-cycle"></a>Machine Learning-Lebenszyklus

Machine Learning ist ein komplexer Prozess, der betrifft alle Aspekte der Daten im Unternehmen sowie viele Machine Learning-Projekten am Ende dauert länger und komplexer als erwartet wird. Hier sind einige der Methoden, Machine Learning die Unterstützung von Data-Experten im Unternehmen erfordert:

+ Machine Learning beginnt mit der ID der Ziele und Geschäftsregeln.
+ Machine Learning-Experten müssen von Richtlinien für das Speichern, extrahieren und Überwachungsdaten bewusst sein.
+ Sammlung von potenziell anwendbar Daten geht es weiter.  Datenquellen müssen identifiziert werden, und die entsprechenden Daten von Sensoren und Geschäftsanwendungen extrahiert. 
+ Die Qualität der Machine Learning-bemühungen ist stark abhängig von der nicht nur den Typ der Daten, die verfügbar ist, aber die Prozesse zum Extrahieren, verarbeiten und Speichern von Daten verwendet. 
+ Keine Machine Learning-Projekt wäre vollständig ohne eine Strategie für die berichterstellung und Analyse und möglicherweise die kundenbindung und Feedback.

SQL Server können viele der Lücken zwischen Enterprise-Daten-Experten und Machine Learning-Experten zu überbrücken:

+ Daten können lokal gespeichert werden oder in der Cloud
+ SQL Server ist in jeder Phase des Enterprise-Datenverarbeitung, einschließlich reporting und ETL-integriert.
+ SQL Server unterstützt, die datensicherheit, die Datenredundanz und Überwachung
+ Stellt die Ressourcenkontrolle

## <a name="data-scientists"></a>Data scientists

Datenanalysten verwenden verschiedene Tools für die Analyse und Machine learning, die von Excel oder kostenlose Open-Source-Plattformen bis hin zu kostspieligen statistischen Programmsuites, die fundierte technische Kenntnisse erfordern. Verwenden von R oder Python mit SQL Server bietet jedoch einige besondere Vorteile im Vergleich zu herkömmlichen sagte:

+ Sie können entwickeln eine Lösung testen, indem Sie mithilfe der Entwicklungsumgebung Ihrer Wahl, und stellen Sie Ihren R oder Python-Code als Teil des T-SQL-Code.
+ Verschieben Sie komplexe Berechnungen aus dem Datenanalysten Laptop und an den Server, Verschieben von Daten zur Einhaltung von Sicherheitsrichtlinien für Unternehmen zu vermeiden.
+ Leistung und Skalierung werden über spezielle R-Pakete und APIs verbessert. Sie sind nicht mehr von der Singlethread-speichergebunden Architektur von R beschränkt und können mit größeren Datasets und Berechnungen für mit mehreren Threads, Kernen und Prozessen arbeiten.
+ Codeportabilität: Lösungen können in SQL Server oder in Hadoop oder Linux ausführen mit [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Einmal Code, überall bereitstellen.

## <a name="application-and-database-developers"></a>Anwendungs- und Datenbankentwickler

Datenbankentwickler stehen vor der Aufgabe, zahlreiche Technologien integrieren und die Ergebnisse zusammenführen zu müssen, sodass diese im gesamten Unternehmen gemeinsam genutzt werden können. Der Datenbankentwickler arbeitet zusammen mit Anwendungsentwicklern, SQL-Entwickler und Datenanalysten Lösungen entwerfen, wird empfohlen, Verwaltungsmethoden für Daten, und entwickeln oder Bereitstellen von Lösungen.

Integration in SQL Server bietet viele Vorteile für datenentwickler.

+ Data scientists kann in RStudio arbeiten, während die Lösung mithilfe von SQL Server Management Studio die Daten bereitstellen. Keine weiteren neuprogrammierung von Lösungen für R oder Python.
+ Optimieren Sie Ihre Lösungen, indem Sie das beste von T-SQL, R und Python. Komplexe Vorgänge in großen Datasets können wesentlich effizienter mithilfe von SQL Server als in r nutzen die Kenntnis Ihrer Datenbankexperten zur leistungsverbesserung von Machine Learning-Lösungen mithilfe von in-Memory-Columnstore-Indizes ausgeführt werden und Aggregationen, die mithilfe von SQL-basierten Vorgängen. 
+ Einfaches Automatisieren von Aufgaben, die für große Mengen an Daten, z. B. Generieren von vorhersagebewertungen für Produktionsdaten wiederholt ausgeführt werden müssen. 
+ Zugriff parametrisiert, R oder Python-Skript aus einer beliebigen Anwendung, die verwendet [!INCLUDE[tsql](../../includes/tsql-md.md)]. Rufen Sie einfach eine gespeicherte Prozedur zum Trainieren eines Modells, einer Zeichnung zu generieren oder Vorhersagen ausgeben.
+ APIs können Streamen von großen Datasets und in der Datenbank-Berechnungen mit mehreren Threads, Kernen und Prozessen profitieren.

Informationen zu Aufgaben finden Sie unter:
+ [Operationalisieren Ihres R-Codes](../../advanced-analytics/r/operationalizing-your-r-code.md)

### <a name="database-administrators"></a>Datenbank-Administratoren

Datenbankadministratoren müssen konkurrierende Projekte und Prioritäten in einen zentralen Kontaktpunkt integrieren: den Datenbankserver. Sie müssen jedoch nicht nur Datenanalysten den Zugriff auf die Daten ermöglichen, sondern einer Vielzahl von Berichtsentwicklern, Business Analysts und Business-Daten-Consumern. Gleichzeitig müssen sie die Integrität der Betriebs- und Berichtsdatenspeicher aufrecht erhalten. Im Unternehmen spielt der Datenbankadministrator eine wichtige Rolle bei der Erstellung und Bereitstellung einer effektiven Data Science-Infrastruktur. 

SQL Server bietet einzigartige Funktionen für den Datenbankadministrator, der der Data Science-Rolle unterstützen muss:

+ Sicherheit von SQLServer: Die Architektur des [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] gewährleistet die Sicherheit Ihrer Datenbanken und isoliert die Ausführung von externen Skript-Sitzungen vom Betrieb der Datenbankinstanz. Sie können angeben, wer hat die Berechtigung zum Ausführen von Machine Learning-Skripts und Datenbankrollen verwenden, um Pakete zu verwalten.

+ R und Python-Sitzungen werden ausgeführt, in einem separaten Prozess aus, um sicherzustellen, dass der Server wie gewohnt ausgeführt wird weiterhin, auch wenn die externen Skripts Probleme auftreten.

+ Ressourcenkontrolle, die mithilfe von SQL Server können Sie den Speicher und Prozesse, die externen Runtimes zugeordnet werden, um zu verhindern, dass umfangreiche Berechnungen die gesamtleistung des Servers gefährden zu steuern.

Informationen zu Aufgaben finden Sie unter:
+ [Verwalten und Überwachen von Machine Learning-Lösungen](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)

## <a name="architects-and-data-engineers"></a>Architekten und Data engineers

Architekten entwerfen Sie Dank integrierter Workflows, die alle Aspekte des Machine Learning-Lebenszyklus erstrecken. Data Engineers entwerfen und Erstellen von ETL-Lösungen und bestimmen, wie featureengineeringaufgaben für Machine Learning zu optimieren. Die gesamte Datenplattform muss entworfen werden, um konkurrierende unternehmensanforderungen auszugleichen.

Da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] eng in andere Microsoft-Tools integriert ist, z.B. in den Business Intelligence- und Data Warehouse-Stapel, die Enterprise Cloud- und Mobilitätstools sowie Hadoop, gibt es zahlreiche Vorteile für Datentechniker und Systemarchitekten, die erweiterte Analysen ausführen möchten.

+ Rufen Sie alle Python- oder R-Skript mithilfe von gespeicherten Systemprozeduren zum Auffüllen von Datasets, Grafiken zu generieren oder Abrufen von Vorhersagen. Keine weitere Entwurf von parallelen Workflows in Data Science und ETL-Tools. Unterstützung für Azure Data Factory und Azure SQL-Datenbank erleichtert es, Cloud-Datenquellen in Machine learning-Workflows verwenden.

+ Verwenden Sie für die Planung und Verwaltung von Machine learning-Aufgaben Automation standard-Workflows in SQL Server, basierend auf den Integration Services, SQL-Agent oder Azure Data Factory. Oder verwenden Sie die [operationalisierung Features](https://docs.microsoft.com/machine-learning-server/operationalize/how-to-deploy-web-service-publish-manage-in-r) in Machine Learning-Server.

Informationen zu Aufgaben finden Sie unter:

+ [Erstellen von Workflows für Machine Learning in SQL Server](../../advanced-analytics/r/creating-workflows-that-use-r-in-sql-server.md)

