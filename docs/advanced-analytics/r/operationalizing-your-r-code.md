---
title: Operationalisieren von R-Code mit gespeicherten Prozeduren – SQL Server Machine Learning Services
description: Einbetten von R-Sprache-Code in einer gespeicherten SQL Server-Prozedur, um es für jede Clientanwendung, die Zugriff auf SQL Server-Datenbank verfügbar zu machen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3fc96e57fffb3e000a7e1a19887ed27651df9009
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432183"
---
# <a name="operationalize-r-code-machine-learning-services"></a>Operationalisieren von R-Code (Machine Learning-Dienste)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Datenbankentwickler stehen vor der Aufgabe, zahlreiche Technologien integrieren und die Ergebnisse zusammenführen zu müssen, sodass diese im gesamten Unternehmen gemeinsam genutzt werden können. Der Datenbankentwickler arbeitet zusammen mit Anwendungsentwicklern, SQL-Entwickler und Data scientists bis zum Entwerfen und Bereitstellen von Lösungen.

Dieser Artikel beschreibt die wichtigsten Punkte für Datenbankentwickler beim operationalisieren von R-Code mithilfe von SQL Server zu berücksichtigen.

## <a name="get-started-with-r-code-in-sql-server"></a>Erste Schritte mit R-Code in SQL Server

In der Vergangenheit hat die Integration von Machine Learning-Lösungen bedeutet umfangreiche neuprogrammierung, um Leistung und Integration zu unterstützen. Verschieben von R und Python-Code in einer produktionsumgebung ist viel einfacher, in SQL Server Machine Learning-Diensten, da der Code in SQL Server ausgeführt werden kann und mit aufgerufen werden jedoch Prozeduren gespeichert. Sie können weiterhin vertraute Tools nutzen und müssen keine R-Entwicklungsumgebung installieren. 

Weitere Informationen zur grundlegenden Syntax finden Sie unter:

+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
+ [Verwenden von R-Code in SQL](../../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

Ein Beispiel dafür, wie Sie R-Code in der Produktion mithilfe von gespeicherten Prozeduren bereitstellen können finden Sie unter:

+ [Datenbankinterne Analysen für SQL-Entwickler](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="optimize-your-r-code"></a>Optimieren Sie Ihren R-code

Konvertieren von R-Code in SQL ist natürlich einfacher, wenn einige Optimierungen im Voraus in den R oder Python-Code fertig sind. Dazu gehören das Vermeiden von Datentypen, die Probleme verursachen, vermeiden Eliminierung unnötiger datenkonvertierungen und umschreiben des R-Codes als einen einzigen Funktionsaufruf, der einfach parametrisiert werden kann. Weitere Informationen finden Sie in den folgenden Themen:

+ [R-Bibliotheken und -Datentypen](r-libraries-and-data-types.md)

+ [Konvertieren von R-Code für die Verwendung in R Services](converting-r-code-for-use-in-sql-server.md)

+ [Arbeiten mit Hilfsfunktionen sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Integrieren von R und Python in Anwendungen

Da Sie Machine Learning-Dienste aus einer gespeicherten Prozedur beginnen können, können Sie R- oder Python-Skripts aus einer beliebigen Anwendung ausführen, die eine T-SQL-Anweisung zu senden und Verarbeiten der Ergebnisse können.

Beispielsweise können Sie erneutes Trainieren eines Modells nach einem Zeitplan mit dem Task T-SQL-Task in Integration Services oder mithilfe einer anderen Auftragsplaner, die eine gespeicherte Prozedur ausführen können.

Bewerten ist eine wichtige Aufgabe, die kann leicht automatisiert oder aus externen Anwendungen gestartet werden. Sie im Vorfeld Trainieren des Modells mithilfe von R oder Python oder eine gespeicherte Prozedur, und speichern Sie das Modell im binären Format in eine Tabelle. Das Modell kann dann in eine Variable als Teil des Aufrufs einer gespeicherten Prozedur, eine der folgenden Optionen für die Bewertung von T-SQL mit geladen werden:

+ [In Echtzeit](../real-time-scoring.md) Bewertungen, optimiert für kleine Batches
+ Einzeiliges Bewertungen, für den Aufruf aus einer Anwendung
+ [Native Bewertung](../sql-native-scoring.md), für die schnelle batchvorhersage von SQL Server ohne Aufruf von R

Diese exemplarische Vorgehensweise enthält Beispiele für die Bewertung mithilfe einer gespeicherten Prozedur im Batch und einzeiligen Modus:

+ [End-to-end von Exemplarische Data Science-Vorgehensweise für die R in SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Finden Sie diese Vorlagen für die Beispiele für die Bewertung in einer Anwendung zu integrieren:

+ [Prognosenerstellung](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Betrugserkennung](https://github.com/Microsoft/r-server-fraud-detection)
+ [Kunden, die clustering](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Leistung und Skalierung

Obwohl die open Source-R-Sprache bekannte Einschränkungen aufweist, das RevoScaleR-Paket APIs können großen Datasets ausgeführt werden und in der Datenbank-Berechnungen mit mehreren Threads, Kernen und Prozessen profitieren.

Wenn Ihre R-Lösung komplexe Aggregationen verwendet oder große Datasets, können Sie SQL Server hocheffizientes in-Memory Aggregationen und columnstore-Indizes nutzen, und können Sie den R-Code verarbeiten die statistischen Berechnungen und Bewertungen.

Weitere Informationen zur Verbesserung der Leistung in SQL Server-Machine Learning finden Sie unter:

+ [Leistungsoptimierung für SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Performance Optimization Tipps und tricks](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Anpassen von R-Code für andere Plattformen oder compute-Kontexten

Derselbe R-Code, die Sie vor Ausführen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten für andere Datenquellen wie Hadoop verwendet werden können und in anderen Kontexten zu berechnen.

Weitere Informationen zu den von Microsoft R unterstützten Plattformen finden Sie unter:

+ [Einführung in Microsoft R](https://docs.microsoft.com/r-server/)

+ [Untersuchen von RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

Weitere Informationen dazu, wie Sie Ihre Microsoft R-Lösungen auf große Datenmengen oder mehreren Plattformen ausgeführt optimieren können finden Sie unter:

+ [Bestimmen von Blöcken Algorithmen schreiben](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Computing mit big Data in R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Entwickeln Sie Ihrer eigenen parallelen Algorithmus](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

