---
title: Operationalisieren von R-Code mithilfe gespeicherter Prozeduren
description: Betten Sie R-Sprachcode in eine gespeicherte Prozedur SQL Server ein, um Sie für jede Client Anwendung verfügbar zu machen, die Zugriff auf eine SQL Server Datenbank hat.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: adcac48bc7d90aae5f05a9b671f05e34cc8cf554
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715687"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>Operationalisieren von R-Code mithilfe gespeicherter Prozeduren in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Wenn Sie die R-und Python-Funktionen in SQL Server Machine Learning Services verwenden, ist der häufigste Ansatz zum Verschieben von Lösungen in eine Produktionsumgebung das Einbetten von Code in gespeicherten Prozeduren. In diesem Artikel werden die wichtigsten Punkte zusammengefasst, die der SQL-Entwickler beim operationalisieren von R-Code mithilfe von SQL Server beachten muss.

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>Bereitstellen eines Produktions bereiten Skripts mit T-SQL und gespeicherten Prozeduren

Die Integration von Data Science Lösungen hat traditionell eine umfassende Zusammenführung zur Unterstützung von Leistung und Integration bedeuten. SQL Server Machine Learning Services vereinfacht diese Aufgabe, da R-und Python-Code in SQL Server ausgeführt und mithilfe gespeicherter Prozeduren aufgerufen werden können. Weitere Informationen zur Vorgehensweise beim Einbetten von Code in gespeicherten Prozeduren finden Sie unter:

+ [Schnellstart: "Hello World" R-Skript in SQL Server](../../advanced-analytics/tutorials//quickstart-r-run-using-tsql.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

Ein umfassenderes Beispiel für die Bereitstellung von R-Code in der Produktionsumgebung mithilfe von [gespeicherten Prozeduren finden Sie unter Tutorial: R-Datenanalysen für SQL-Entwickler](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>Richtlinien zum Optimieren von R-Code für SQL

Die Umstellung des r-Codes in SQL ist einfacher, wenn einige Optimierungen im Code von R oder python ausgeführt werden. Dazu gehört das Vermeiden von Datentypen, die Probleme verursachen, unnötige Datenkonvertierungen vermieden werden, und das Umschreiben des R-Codes als einzelner Funktions aufzurufen, der leicht parametrisiert werden kann. Weitere Informationen finden Sie in den folgenden Themen:

+ [R-Bibliotheken und -Datentypen](r-libraries-and-data-types.md)
+ [Umrechnen von r-Code für die Verwendung in R Services](converting-r-code-for-use-in-sql-server.md)
+ [Verwenden von sqlrutils-Hilfsfunktionen](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Integrieren von R und python in Anwendungen

Da R oder python über eine gespeicherte Prozedur ausgeführt werden kann, können Sie Skripts aus jeder beliebigen Anwendung ausführen, die eine T-SQL-Anweisung senden und die Ergebnisse verarbeiten kann. Beispielsweise können Sie ein Modell nach einem Zeitplan erneut trainieren, indem Sie den [Task T-SQL ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) in Integration Services oder einen anderen Auftrags Planer verwenden, der eine gespeicherte Prozedur ausführen kann.

Die Bewertung ist eine wichtige Aufgabe, die auf einfache Weise automatisiert oder von externen Anwendungen gestartet werden kann. Sie können das Modell im Voraus mit R oder python oder einer gespeicherten Prozedur trainieren und [das Modell im Binärformat in](../tutorials/walkthrough-build-and-save-the-model.md) einer Tabelle speichern. Anschließend kann das Modell als Teil eines gespeicherten Prozedur Aufrufes in eine Variable geladen werden, wobei eine dieser Optionen für die Bewertung von T-SQL verwendet wird:

+ [Echtzeitbewertung, optimiert für kleine Batches
+ Einzeilige Bewertung zum Aufrufen aus einer Anwendung
+ [Native Bewertung](../sql-native-scoring.md)für schnelle Batch Vorhersage von SQL Server ohne Aufrufen von R

Diese exemplarische Vorgehensweise enthält Beispiele für die Bewertung mithilfe einer gespeicherten Prozedur in Batch-und Einzel Zeilen Modi:

+ [End-to-End-Data Science Exemplarische Vorgehensweise für R in SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

In diesen Lösungs Vorlagen finden Sie Beispiele für die Integration der Bewertung in eine Anwendung:

+ [Verkaufsprognosen](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Betrugserkennung](https://github.com/Microsoft/r-server-fraud-detection)
+ [Customer-Clustering](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Steigern der Leistung und Skalierbarkeit

Obwohl die Open Source-Sprache "R" bekannte Einschränkungen in Bezug auf große Datasets aufweist, können die in SQL Server Machine Learning Dienst enthaltenen [revoscaler-Paket-APIs](ref-r-revoscaler.md) auf großen Datasets ausgeführt werden und von Multithread-, Multi-Core-, in-Database-Berechnungen mit mehreren Prozessen.

Wenn Ihre R-Lösung komplexe Aggregationen verwendet oder große Datasets umfasst, können Sie die hocheffizienten in-Memory-Aggregationen und columnstore--Indizes SQL Server nutzen und den R-Code die statistischen Berechnungen und Bewertungen verarbeiten lassen.

Weitere Informationen zum Verbessern der Leistung in SQL Server Machine Learning finden Sie unter:

+ [Leistungsoptimierung für SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Tipps und Tricks zur Leistungsoptimierung](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Anpassen von R-Code für andere Plattformen oder computekontexte

Derselbe R-Code, den Sie für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten ausführen, kann für andere Datenquellen wie Spark über HDFS verwendet werden, wenn Sie die [Option "eigenständiger Server](../install/sql-machine-learning-standalone-windows-install.md) " in SQL Server-Setup verwenden oder wenn Sie das nicht-SQL-Produkt installieren, Microsoft Machine Learning Server (früher als " **Microsoft R Server**" bezeichnet):

+ [Dokumentation zu Machine Learning Server](https://docs.microsoft.com/r-server/)

+ [Erkunden von R bis revoscaler](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [Schreiben von Segmentierungsalgorithmen](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Computing mit Big Data in R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Entwickeln Sie Ihren eigenen parallelen Algorithmus](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

