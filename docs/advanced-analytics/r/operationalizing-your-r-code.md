---
title: Operationalisieren von R-Code mit gespeicherten Prozeduren – SQL Server Machine Learning Services
description: Einbetten von R-Sprache-Code in einer gespeicherten SQL Server-Prozedur, um es für jede Clientanwendung, die Zugriff auf SQL Server-Datenbank verfügbar zu machen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6e882243f73588cbe3f9bf301dd3fa5a99cef03e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962596"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>Operationalisieren von R-Code mithilfe von gespeicherten Prozeduren in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Wenn Sie die R- und Python-Funktionen in SQL Server Machine Learning Services verwenden zu können, ist die am häufigsten verwendete Ansatz für das Verschieben von Lösungen in einer produktionsumgebung bereit, durch Einbetten von Code in gespeicherten Prozeduren. Dieser Artikel beschreibt die wichtigsten Punkte für SQL-Entwickler bei der operationalisierung von R-Code mithilfe von SQL Server zu berücksichtigen.

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>Stellen Sie bereit für die Produktion-Skript mithilfe von T-SQL und gespeicherte Prozeduren

In der Vergangenheit hat die Integration von Data Science-Lösungen bedeutet umfangreiche neuprogrammierung, um Leistung und Integration zu unterstützen. SQL Server-Machine Learning-Dienste vereinfacht diese Aufgabe, da die R- und Python-Code in SQL Server ausgeführt werden kann und mit gespeicherten Prozeduren aufgerufen. Weitere Informationen über die Funktionsweise der Einbettung von Code in gespeicherten Prozeduren finden Sie unter:

+ [Schnellstart: "Hello World"-R-Skript in SQL Server](../../advanced-analytics/tutorials//quickstart-r-run-using-tsql.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

Ein Beispiel für eine umfassendes Bereitstellung von R-Code in der produktionsumgebung mit gespeicherten Prozeduren finden Sie unter [Lernprogramm: R-Data-Analysen für SQL-Entwickler](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>Richtlinien zum Optimieren von R-Code für SQl

Konvertieren von R-Code in SQL ist einfacher, wenn einige Optimierungen im Voraus in den R oder Python-Code fertig sind. Dazu gehören das Vermeiden von Datentypen, die Probleme verursachen, vermeiden Eliminierung unnötiger datenkonvertierungen und umschreiben des R-Codes als einen einzigen Funktionsaufruf, der einfach parametrisiert werden kann. Weitere Informationen finden Sie in den folgenden Themen:

+ [R-Bibliotheken und -Datentypen](r-libraries-and-data-types.md)
+ [Konvertieren von R-Code für die Verwendung in R Services](converting-r-code-for-use-in-sql-server.md)
+ [Arbeiten mit Hilfsfunktionen sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Integrieren von R und Python in Anwendungen

Da Sie von einer gespeicherten Prozedur R- oder Python ausführen können, können Sie Skripts aus einer beliebigen Anwendung ausführen, die eine T-SQL-Anweisung zu senden und Verarbeiten der Ergebnisse können. Angenommen, Sie können erneutes Trainieren eines Modells nach einem Zeitplan mit der [Task T-SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) in Integration Services oder mit einem anderen Auftragsplaner, die eine gespeicherte Prozedur ausführen können.

Bewerten ist eine wichtige Aufgabe, die kann leicht automatisiert oder aus externen Anwendungen gestartet werden. Sie trainieren das Modell im Vorfeld mithilfe von R oder Python oder einer gespeicherten Prozedur und [speichern Sie das Modell im Binärformat](../tutorials/walkthrough-build-and-save-the-model.md) in einer Tabelle. Das Modell kann dann in eine Variable als Teil des Aufrufs einer gespeicherten Prozedur, eine der folgenden Optionen für die Bewertung von T-SQL mit geladen werden:

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

Obwohl die Open-Source-Sprache R verfügt über Einschränkungen im Hinblick auf die große Datasets bekannt sind die [RevoScaleR-Paket-APIs](ref-r-revoscaler.md) Lieferumfang von SQL Server Machine Learning-Dienst großen Datasets ausgeführt werden können, und profitieren Sie mit mehreren Threads , mit mehreren Kernen und Prozessen in der Datenbank-Berechnungen.

Wenn Ihre R-Lösung komplexe Aggregationen verwendet oder große Datasets, können Sie SQL Server hocheffizientes in-Memory Aggregationen und columnstore-Indizes nutzen, und können Sie den R-Code verarbeiten die statistischen Berechnungen und Bewertungen.

Weitere Informationen zur Verbesserung der Leistung in SQL Server-Machine Learning finden Sie unter:

+ [Leistungsoptimierung für SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Performance Optimization Tipps und tricks](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Anpassen von R-Code für andere Plattformen oder compute-Kontexten

Derselbe R-Code, die Sie vor Ausführen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten können für andere Datenquellen, z.B. Spark über HDFS, verwendet werden, bei der Verwendung der [eigenständige Serveroption](../install/sql-machine-learning-standalone-windows-install.md) in SQL Server-Setup oder bei der Installation von nicht-SQL mit Branding Produkts, Microsoft Machine Learning Server (ehemals **Microsoft R Server**):

+ [Machine Learning Server-Dokumentation](https://docs.microsoft.com/r-server/)

+ [Erkunden von R von RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [Bestimmen von Blöcken Algorithmen schreiben](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Computing mit big Data in R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Entwickeln Sie Ihrer eigenen parallelen Algorithmus](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

