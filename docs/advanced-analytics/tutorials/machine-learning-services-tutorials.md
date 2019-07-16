---
title: 'SQL Server R und Python-Tutorials: SQL Server-Machine Learning'
description: Beispiele und Tutorials für R und Python-Skripts in SQL Server-Machine Learning-Dienste.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 8c8e8ad13ddc34148f1718b7843e00545cd758c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962099"
---
# <a name="sql-server-machine-learning-tutorials-in-r-and-python"></a>SQL Server-Machine Learning-Tutorials, in R und Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel bietet eine umfassende Liste der Tutorials und Codebeispiele zur Machine learning-Funktionen von [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) oder [SQL Server 2017-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md). 

+ Schnellstarts verwenden integrierte oder keine Daten für schnelle Auswertung mit möglichst geringem Aufwand.
+ Tutorials machen, Sie sich mit Weitere Aufgaben, größeren Datasets und länger erläuterungen.
+ Beispiele und Lösungen sind für Entwickler bevorzugen, mit Code zu beginnen, arbeiten Sie sich mit Konzepten und Lektionen, um Wissenslücken zu füllen.

Sie erfahren, wie mit R und Python-Bibliotheken mit residenten relationalen Daten in den gleichen operativen Kontext, wie Sie mit SQL Server gespeicherte Prozeduren zum Ausführen und Bereitstellen von benutzerdefiniertem Code und das Aufrufen von der Microsoft R und Python-Bibliotheken für Hochleistungs-Daten Science und Machine learning-Aufgaben.

Überprüfen Sie als ersten Schritt, grundlegende Konzepte, Sichern von Microsoft R und Python-Integration mit SQL Server.

## <a name="concepts"></a>Konzepte

In-Database-Analyse bezieht sich auf systemeigene Unterstützung für R und Python in SQL Server, bei der Installation von SQL Server Machine Learning Services oder SQL Server 2016 R Services (nur R) als Add-on für die Datenbank-Engine. Integration von R und Python enthält basisverteilungen Open Source- und Microsoft-spezifische Bibliotheken für die leistungsstarke Analysen.

Führt von einem eigenständigen Architektur den Code als externer Prozess, in das Feld, um die Integrität der Datenbank-Engine zu erhalten. Zugriff auf alle Daten und Sicherheit ist jedoch über SQL Server-Datenbankrollen und Berechtigungen, mit denen bedeutet, dass jede Anwendung mit Zugriff auf SQL Server können das R- und Python-Skript zugreifen, wenn Sie als eine gespeicherte Prozedur, bereitstellen oder serialisieren und speichern ein trainiertes Modells mit einer SQL Server-Datenbank.

Wichtige Unterschiede zwischen R und Python-Unterstützung in SQL Server und die entsprechende sprachunterstützung in andere Microsoft-Produkte und Dienste umfassen:

+ Die Möglichkeit, "Package"-Code in gespeicherten Prozeduren oder als binären Modelle.
+ Schreiben Sie Code, der die Microsoft R und Python-Bibliotheken, die lokal mit den SQL Server-Programmdateien installiert aufruft.
+ Wenden Sie SQL Server Datenbank-Sicherheitsarchitektur, auf Ihre Lösungen für R und Python.
+ Nutzen Sie SQL Server-Infrastruktur und administrative Unterstützung für Ihren benutzerdefinierten Lösungen.

## <a name="quickstarts"></a>Schnellstarts

Beginnen Sie hier Informationen zum Ausführen von R- oder Python und T-SQL und zum operationalisieren von R und Python Code für eine SQL-produktionsumgebung.

+ [Python: Führen Sie Python mit T-SQL](run-python-using-t-sql.md)
+ [R: Hallo-Welt in R und SQL](rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R: Verarbeiten von Eingaben und Ausgaben](rtsql-working-with-inputs-and-outputs.md)
+ [R: Behandeln von Datentypen und Objekte](rtsql-r-and-sql-data-types-and-data-objects.md)
+ [R: Verwenden von R-Funktionen](rtsql-using-r-functions-with-sql-server-data.md)
+ [R: Erstellen eines Vorhersagemodells](rtsql-create-a-predictive-model-r.md)
+ [R: Vorhersagen und zeichnen ausgehend vom Modell](rtsql-predict-and-plot-from-model.md)

## <a name="tutorials"></a>Lernprogramme

Erstellen Sie auf noch keine Erfahrung mit R und Python und T-SQL, indem ein genauerer Blick auf Microsoft-Pakete und spezialisiertere Operationen wie z. B. das Verschieben von lokalen nach remotecomputekontexte.

+ [Python-Tutorials](sql-server-python-tutorials.md)
+ [R-tutorials](sql-server-r-tutorials.md)

<a name ="bkmk_samples"></a>

## <a name="samples"></a>Proben

Markieren Sie diese Beispiele und Demos, die vom SQL Server und R Server-Entwicklungsteam bereitgestellte Methoden, mit denen Sie eingebettete Analysen in realen Anwendungen verwenden können.

| Link | Beschreibung | 
|------|-------------|
| [Führen Sie Kunden mit R und SQL Server-clustering](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Verwenden Sie unbeaufsichtigtes lernen zum Segmentieren von Kunden anhand der Umsatzdaten. In diesem Beispiel verwendet den skalierbaren k-Means-Algorithmus von Microsoft R, um das clustering-Modell zu erstellen. |
| [Ausführen von Kunden mithilfe von Python und SQL Server-clustering](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Erfahren Sie, wie Sie mit der k-Means-Algorithmus zum Ausführen von nicht überwachten Gruppieren von Kunden. Dieses Beispiel verwendet die Python-Sprache in der Datenbank.| SQL Server 2017 |
| [Erstellen eines Vorhersagemodells mit R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Erfahren Sie, wie ein skiverleih Machine learning, um zukünftige verleihe vorherzusagen, wodurch die Business-Plan und die Mitarbeiter, von der zukünftigen Nachfrage zu begegnen verwenden kann. Dieses Beispiel verwendet die Microsoft-Algorithmen zum Erstellen von logistischen Regression und entscheidungsstrukturmodelle. | 
| [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Die Ski Mietwagen-Analyse-Anwendung mithilfe von Python, zur Unterstützung der Planung für die zukünftige Nachfrage zu erstellen. Dieses Beispiel verwendet die neue Python-Bibliothek **Revoscalepy**, um ein lineares Regressionsmodell zu erstellen. | 

<a name="bkmk_solutions"></a>

## <a name="solution-templates"></a>Lösungsvorlagen

Das Microsoft Data Science-Team hat anpassbare Vorlagen bereitgestellt, die zum Beschleunigen von Lösungen für häufige Szenarien verwendet werden kann. Jede Lösung ist auf einem bestimmten Task oder Branche Problem zugeschnitten. Die meisten Lösungen dienen zum Ausführen von in SQL Server oder in einer Cloudumgebung wie Azure Machine Learning. Andere Lösungen können unter Linux oder in Spark oder Hadoop-Clustern mithilfe von Microsoft R Server oder Machine Learning Server ausführen.

Der gesamte Code bereitgestellt sowie Anweisungen zum Trainieren und Bereitstellen eines Modells für die Bewertung mithilfe von SQL Server gespeicherte Prozeduren.

+ [Betrugserkennung](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [Vorhersage der Kundenabwanderung](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [Vorbeugende Wartung](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Prognostizieren der Länge der Krankenhaus der Aufenthaltsdauer](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

