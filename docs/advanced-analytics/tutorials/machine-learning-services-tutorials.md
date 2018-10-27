---
title: SQL Server Machine Learning-Services-Tutorials | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/22/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 08528f3459022bdcb97b97e22d6f6c474c31a715
ms.sourcegitcommit: eddf8cede905d2adb3468d00220a347acd31ae8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "49960744"
---
# <a name="tutorials-for-sql-server-machine-learning-services"></a>Tutorials für SQL Server-Machine Learning-Dienste
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel enthält eine umfassende Liste der Lernprogramme, Demos und Beispielanwendungen, die Machine Learning-Features in SQL Server 2016 oder SQL Server 2017 zu verwenden. Beginnen Sie hier, um erfahren von T-SQL R oder Python ausführen, wie Sie mit der lokalen und remote computekontexte und zum operationalisieren von R und Python Code für eine SQL-produktionsumgebung.

+ [Python-Tutorials](../tutorials/sql-server-python-tutorials.md)

+ [R-tutorials](../tutorials/sql-server-r-tutorials.md)

## <a name ="bkmk_samples"></a>R und Python-Beispiele

Markieren Sie diese Beispiele und Demos, die vom SQL Server und R Server-Entwicklungsteam bereitgestellte Methoden, mit denen Sie eingebettete Analysen in realen Anwendungen verwenden können.

| Link | Description | Gilt für |
|------|-------------|------------|
| [Führen Sie Kunden mit R und SQL Server-clustering](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Verwenden Sie unbeaufsichtigtes lernen zum Segmentieren von Kunden anhand der Umsatzdaten. In diesem Beispiel verwendet den skalierbaren k-Means-Algorithmus von Microsoft R, um das clustering-Modell zu erstellen. | SQLServer 2016 oder SQLServer 2017 |
| [Ausführen von Kunden mithilfe von Python und SQL Server-clustering](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Erfahren Sie, wie Sie mit der k-Means-Algorithmus zum Ausführen von nicht überwachten Gruppieren von Kunden. Dieses Beispiel verwendet die Python-Sprache in der Datenbank.| SQL Server 2017 |
| [Erstellen eines Vorhersagemodells mit R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Erfahren Sie, wie ein skiverleih Machine learning, um zukünftige verleihe vorherzusagen, wodurch die Business-Plan und die Mitarbeiter, von der zukünftigen Nachfrage zu begegnen verwenden kann. Dieses Beispiel verwendet die Microsoft-Algorithmen zum Erstellen von logistischen Regression und entscheidungsstrukturmodelle. | SQLServer 2016 oder SQLServer 2017 |
| [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Die Ski Mietwagen-Analyse-Anwendung mithilfe von Python, zur Unterstützung der Planung für die zukünftige Nachfrage zu erstellen. Dieses Beispiel verwendet die neue Python-Bibliothek **Revoscalepy**, um ein lineares Regressionsmodell zu erstellen. | SQL Server 2017 |
| [Verwenden von Tableau mit SQL Server Machine Learning Services](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/) | Soziale medienanalyse und Tableau Diagramme erstellen, mit SQL Server und R. | SQLServer 2016 oder SQLServer 2017 |

## <a name="bkmk_solutions"></a>Lösungsvorlagen

Das Microsoft Data Science-Team hat anpassbare Vorlagen bereitgestellt, die zum Beschleunigen von Lösungen für häufige Szenarien verwendet werden kann. Jede Lösung ist auf einem bestimmten Task oder Branche Problem zugeschnitten. Die meisten Lösungen dienen zum Ausführen von in SQL Server oder in einer Cloudumgebung wie Azure Machine Learning. Andere Lösungen können unter Linux oder in Spark oder Hadoop-Clustern mithilfe von Microsoft R Server oder Machine Learning Server ausführen.

Der gesamte Code bereitgestellt sowie Anweisungen zum Trainieren und Bereitstellen eines Modells für die Bewertung mithilfe von SQL Server gespeicherte Prozeduren.

+ [Betrugserkennung](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [Vorhersage der Kundenabwanderung](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [Vorbeugende Wartung](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Prognostizieren der Länge der Krankenhaus der Aufenthaltsdauer](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

Weitere Informationen finden Sie unter [Machine Learning Templates with SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/) (Machine Learning-Vorlagen mit SQL Server 2016 R Services).

## <a name="recommended-reading"></a>Empfohlene Literatur

+ [Warum erstellen wir es?](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/01/10/sql-server-r-services-why-did-we-build-it/)

    Was verbirgt sich hinter R Services? Dieser Artikel aus der Entwicklung und PM-Teams, die den Ursprung und Ziele des SQL Server R Services erläutert.

+ [Anhand von Tutorials und Beispieldaten für Microsoft R](https://docs.microsoft.com/machine-learning-server/r/tutorial-introduction)

    Informationen Sie zu Microsoft R und was in dieser Sammlung von schnellen Lernprogrammen das RevoScaleR-Paket bietet. Erfahren Sie, wie R-Code einmal schreiben und bereitstellen, mithilfe von RevoScaleR-Datenquellen und remotecomputekontexte.

+ [Erste Schritte mit MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)

  Erfahren Sie, wie Sie mit den neuen Algorithmen in des MicrosoftML-Pakets für erweiterte Modellierung und skalierbare Datentransformationen, die für mehrere computekontexte optimiert.
