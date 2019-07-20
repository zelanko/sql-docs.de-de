---
title: Lernprogramme zu SQL Server R und python
description: Beispiele und Tutorials für die Skripterstellung für R und python in SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 9a212160c17e4cc3c8322af6026c9e2e4df97254
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343614"
---
# <a name="sql-server-machine-learning-tutorials-in-r-and-python"></a>SQL Server Machine Learning Tutorials in R und python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel enthält eine umfassende Liste von Tutorials und Codebeispielen, die die Machine Learning-Features von [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) oder [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)veranschaulichen. 

+ Schnellstarts verwenden integrierte Daten oder keine Daten für die schnelle Untersuchung mit geringstmöglichen Anstrengungen.
+ In den Tutorials werden weitere Aufgaben, größere Datasets und längere Erläuterungen näher behandelt.
+ Beispiele und Lösungen sind für Entwickler gedacht, die lieber mit dem Code beginnen möchten, und sich an die Konzepte und Lektionen zurück arbeiten, um die Wissenslücken zu füllen.

Sie erfahren, wie Sie r-und python-Bibliotheken mit residenten relationalen Daten im gleichen Betriebs Kontext verwenden, wie Sie SQL Server gespeicherten Prozeduren zum Ausführen und Bereitstellen von benutzerdefiniertem Code verwenden und wie Sie die Microsoft R-und python-Bibliotheken für Hochleistungs Daten aufzurufen. Aufgaben für Wissenschaft und Maschinelles Lernen.

Lesen Sie als ersten Schritt grundlegende Konzepte, die die R-und python-Integration von Microsoft in SQL Server unterstützen.

## <a name="concepts"></a>Konzepte

In-Database-Analysen bezieht sich auf die systemeigene Unterstützung für R und python auf SQL Server, wenn Sie SQL Server Machine Learning Services oder SQL Server 2016 r Services (nur R) als Add-on für die Datenbank-Engine installieren. Die Integration von R und python umfasst Basis-Open-Source-Distributionen sowie Microsoft-spezifische Bibliotheken für Hochleistungsanalysen.

Der Code wird von einem Architektur-Standpunkt aus als externer Prozess ausgeführt, um die Integrität der Datenbank-Engine beizubehalten. Allerdings erfolgt der gesamte Datenzugriff und die Sicherheit über SQL Server Daten bankrollen und-Berechtigungen. Dies bedeutet, dass jede Anwendung mit Zugriff auf SQL Server auf das R-und Python-Skript zugreifen kann, wenn Sie Sie als gespeicherte Prozedur bereitstellen oder ein trainiertes Modell in einem SQL- Server Datenbank.

Wichtige Unterschiede zwischen der R-und der Python-Unterstützung auf SQL Server im Vergleich zur entsprechenden Sprachunterstützung anderer Microsoft-Produkte und-Dienste:

+ Die Möglichkeit, Code in gespeicherten Prozeduren oder Binär Modellen zu verpacken.
+ Schreiben Sie Code, der die lokal installierten Microsoft R-und python-Bibliotheken mit den SQL Server-Programmdateien aufruft.
+ Wenden Sie die Daten Bank Sicherheitsarchitektur von SQL Server auf Ihre R-und python-Lösungen an.
+ Nutzen Sie SQL Server Infrastruktur und administrative Unterstützung für Ihre benutzerdefinierten Lösungen.

## <a name="quickstarts"></a>Schnellstarts

Beginnen Sie hier, um zu erfahren, wie Sie r oder python aus T-SQL ausführen und ihren R-und Python-Code für eine SQL-Produktionsumgebung operationalisieren.

+ [Python: Ausführen von Python mit T-SQL](run-python-using-t-sql.md)
+ [R Hallo Welt in R und SQL](rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R Behandeln von Eingaben und Ausgaben](rtsql-working-with-inputs-and-outputs.md)
+ [R Verarbeiten von Datentypen und Objekten](rtsql-r-and-sql-data-types-and-data-objects.md)
+ [R Verwenden von R-Funktionen](rtsql-using-r-functions-with-sql-server-data.md)
+ [R Erstellen eines Vorhersagemodells](rtsql-create-a-predictive-model-r.md)
+ [R Vorhersagen und zeichnen aus dem Modell](rtsql-predict-and-plot-from-model.md)

## <a name="tutorials"></a>Lernprogramme

Erstellen Sie Ihre erste Umgebung mit R und Python und T-SQL, indem Sie sich näher mit den Microsoft-Paketen und spezielleren Vorgängen befassen, wie z. b. der Umstellung von lokalen zu remotecomputekontexten.

+ [Python-Tutorials](sql-server-python-tutorials.md)
+ [R-Tutorials](sql-server-r-tutorials.md)

<a name ="bkmk_samples"></a>

## <a name="samples"></a>Proben

Diese Beispiele und Demos, die vom SQL Server und R Server Entwicklungsteam bereitgestellt werden, stellen Möglichkeiten hervor, wie Sie Embedded Analytics in realen Anwendungen verwenden können.

| Link | Beschreibung | 
|------|-------------|
| [Durchführen von Customer Clustering mithilfe von R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Verwenden Sie nicht überwachtes Lernen, um Kunden anhand von Vertriebs Daten zu segmentieren. In diesem Beispiel wird der skalierbare rxkmeans-Algorithmus von Microsoft R verwendet, um das Clustering-Modell zu erstellen. |
| [Ausführen von Customer Clustering mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Erfahren Sie, wie Sie den kmeans-Algorithmus verwenden, um nicht überwachte Clustering von Kunden auszuführen. In diesem Beispiel wird die Python-Sprache in der-Datenbank verwendet.| SQL Server 2017 |
| [Erstellen eines Vorhersagemodells mithilfe von R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Erfahren Sie, wie ein Ski-vermietungsgeschäft Machine Learning verwenden könnte, um zukünftige Vermietungen vorherzusagen, die dem Geschäftsplan und den Mitarbeitern helfen, zukünftige Anforderungen zu erfüllen. In diesem Beispiel werden die Microsoft-Algorithmen zum Erstellen von logistischen Regressions-und Entscheidungsstruktur Modellen verwendet. | 
| [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Erstellen Sie die Skiverleih-Analyse Anwendung mithilfe von Python, um zukünftige Anforderungen zu planen. In diesem Beispiel wird die neue Python-Bibliothek **revoscalepy**verwendet, um ein lineares Regressionsmodell zu erstellen. | 

<a name="bkmk_solutions"></a>

## <a name="solution-templates"></a>Lösungs Vorlagen

Das Microsoft Data Science-Team hat anpassbare Lösungs Vorlagen bereitgestellt, die für den Einstieg in Lösungen für gängige Szenarien verwendet werden können. Jede Lösung ist auf eine bestimmte Aufgabe oder ein branchenproblem zugeschnitten. Die meisten Lösungen sind so konzipiert, dass Sie entweder in SQL Server oder in einer cloudumgebung (z. b. Azure Machine Learning) ausgeführt werden. Andere Lösungen können unter Linux oder in Spark-oder Hadoop-Clustern mithilfe von Microsoft R Server oder Machine Learning Server ausgeführt werden.

Der gesamte Code wird zusammen mit Anweisungen zum trainieren und Bereitstellen eines Modells zur Bewertung mithilfe SQL Server gespeicherter Prozeduren bereitgestellt.

+ [Betrugserkennung](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [Vorhersage der Kundenabwanderung](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [Vorbeugende Wartung](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Vorhersagen der Krankenhaus Länge des Aufenthalts](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

