---
title: Bereitstellen von R-Code in gespeicherten Prozeduren
description: Betten Sie R-Sprachcode in eine gespeicherte Prozedur von SQL Server ein, um ihn für alle Clientanwendungen mit Zugriff auf eine SQL Server-Datenbank verfügbar zu machen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ebca30560a437cc8c95b9604cc24fbd7542c9d85
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117583"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>Operationalisieren von R-Code mithilfe von gespeicherten Prozeduren in SQL Server-Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Bei der Verwendung von R- und Python-Funktionen in SQL Server-Machine Learning Services ist die häufigste Methode zum Verschieben von Lösungen in eine Produktionsumgebung das Einbetten von Code in gespeicherten Prozeduren. In diesem Artikel werden die wichtigsten Punkte zusammengefasst, die SQL-Entwickler beim Operationalisieren von R-Code mithilfe von SQL Server beachten müssen.

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>Bereitstellen eines produktionsbereiten Skripts mithilfe von T-SQL und gespeicherten Prozeduren

In der Regel erfordert die Integration von Data Science-Lösungen eine umfangreiche Neuprogrammierung zur Unterstützung von Leistung und Integration. Diese Aufgabe wird mit SQL Server-Machine Learning Services vereinfacht, da R- und Python-Code in SQL Server ausgeführt und mithilfe von gespeicherten Prozeduren aufgerufen werden können. Weitere Informationen zur Einbettung von Code in gespeicherten Prozeduren finden Sie unter:

+ [Erstellen und Ausführen einfacher R-Skripts in SQL Server](../tutorials/quickstart-r-create-script.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

Ein umfangreicheres Beispiel für die Bereitstellung von R-Code in der Produktion mithilfe von gespeicherten Prozeduren finden Sie unter [Tutorial: R-Datenanalysen für SQL-Entwickler](../../machine-learning/tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>Richtlinien zur Optimierung von R-Code für SQL

Die Konvertierung von R-Code in SQL gestaltet sich einfacher, wenn der R- oder Python-Code zuvor optimiert wird. Dazu gehört das Vermeiden von Datentypen, die Probleme verursachen, das Vermeiden von unnötigen Datenkonvertierungen sowie das Umschreiben des R-Codes in einen einzelnen Funktionsaufruf, der leicht parametrisiert werden kann. Weitere Informationen finden Sie unter

+ [R-Bibliotheken und -Datentypen](r-libraries-and-data-types.md)
+ [Konvertieren von R-Code für die Verwendung in R Services](converting-r-code-for-use-in-sql-server.md)
+ [Verwenden von sqlrutils-Hilfsfunktionen](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Integrieren von R und Python in Anwendungen

Da R oder Python aus einer gespeicherten Prozedur ausgeführt werden kann, können Sie Skripts aus jeder beliebigen Anwendung ausführen, die eine T-SQL-Anweisung senden und die Ergebnisse verarbeiten kann. Beispielsweise können Sie ein Modell nach einem Zeitplan erneut trainieren, indem Sie die Aufgabe [T-SQL-Anweisung ausführen](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) in Integration Services oder einen anderen Auftragsplaner verwenden, der eine gespeicherte Prozedur ausführen kann.

Die Bewertung ist eine wichtige Aufgabe, die auf einfache Weise automatisiert oder aus externen Anwendungen gestartet werden kann. Das Modell wird im Voraus mit R, Python oder einer gespeicherten Prozedur trainiert und in einer Tabelle [im Binärformat gespeichert](../tutorials/walkthrough-build-and-save-the-model.md). Anschließend kann das Modell als Teil des Aufrufs einer gespeicherten Prozedur in eine Variable geladen werden, wobei eine der folgenden T-SQL-Optionen für die Bewertung verwendet wird:

+ Echtzeitbewertung (für kleine Batches optimiert)
+ Bewertung einer einzelnen Zeile (für Aufrufe aus einer Anwendung)
+ [Native Bewertung](../sql-native-scoring.md) (für eine schnelle Batchvorhersage in SQL Server ohne Aufruf von R)

Die folgende exemplarische Vorgehensweise enthält Beispiele für die Bewertung mithilfe einer gespeicherten Prozedur sowohl im Batchmodus als auch für eine einzelne Zeile:

+ [Exemplarische End-to-End-Vorgehensweise zu Data Science für R in SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Beispiele für die Integration der Bewertung in eine Anwendung finden Sie in den folgenden Lösungsvorlagen:

+ [Einzelhandelsprognosen](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Betrugserkennung](https://github.com/Microsoft/r-server-fraud-detection)
+ [Kundenclustering](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Steigern von Leistung und Skalierung

Obwohl die Open-Source-Sprache R bekannte Einschränkungen in Bezug auf große Datasets aufweist, können die in SQL Server-Machine Learning Services enthaltenen [RevoScaleR-Paket-APIs](ref-r-revoscaler.md) mit großen Datasets ausgeführt werden und von datenbankinternen Berechnungen mithilfe mehrerer Threads, Kerne und Prozesse profitieren.

Wenn Ihre R-Lösung komplexe Aggregationen verwendet oder große Datasets enthält, können Sie die hocheffizienten In-Memory-Aggregationen und die Columnstore-Indizes von SQL Server nutzen und die statistischen Berechnungen und Bewertungen mit R-Code verarbeiten.

Weitere Informationen zur Steigerung der Leistung in SQL Server-Machine Learning Services finden Sie unter:

+ [Leistungsoptimierung für SQL Server R Services](../../machine-learning/r/sql-server-r-services-performance-tuning.md)
+ [Tipps und Tricks für die Leistungsoptimierung](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Anpassen von R-Code für andere Plattformen oder Computekontexte

Den R-Code, den Sie für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Daten ausführen, können Sie auch für andere Datenquellen verwenden, wie z. B. Spark mit HDFS, wenn Sie beim SQL Server-Setup die Option [Eigenständiger Server](../install/sql-machine-learning-standalone-windows-install.md) aktivieren oder das Nicht-SQL-Markenprodukt Microsoft Machine Learning Server (früher **Microsoft R Server**) verwenden:

+ [Dokumentation zu Machine Learning Server](https://docs.microsoft.com/r-server/)

+ [Erkunden von R für RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [Schreiben von Segmentierungsalgorithmen](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Computing mit Big Data in R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Entwickeln eines parallelen Algorithmus](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

