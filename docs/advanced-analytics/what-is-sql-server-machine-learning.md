---
title: Was ist SQL Server Machine Learning Services (python und R)?
titleSuffix: ''
description: Machine Learning Services ist eine Funktion in SQL Server, die die Möglichkeit bietet, Python-und R-Skripts mit relationalen Daten auszuführen. Sie können Open-Source-Pakete und-Frameworks sowie die Microsoft python-und R-Pakete für Predictive Analytics und Machine Learning verwenden. Die Skripts werden in der Datenbank ausgeführt, ohne dass Daten aus SQL Server oder über das Netzwerk verschoben werden. In diesem Artikel werden die Grundlagen der SQL Server Machine Learning Services erläutert.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/07/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4a1a9a3b0f712458466051ce2c67c0a725ef0a76
ms.sourcegitcommit: 12b7e3447ca2154ec2782fddcf207b903f82c2c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957441"
---
# <a name="what-is-sql-server-machine-learning-services-python-and-r"></a>Was ist SQL Server Machine Learning Services (python und R)?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Machine Learning Services ist eine Funktion in SQL Server, die die Möglichkeit bietet, Python-und R-Skripts mit relationalen Daten auszuführen. Sie können Open-Source-Pakete und-Frameworks sowie die [Microsoft python-und R-Pakete](#packages) für Predictive Analytics und Machine Learning verwenden. Die Skripts werden in der Datenbank ausgeführt, ohne dass Daten aus SQL Server oder über das Netzwerk verschoben werden. In diesem Artikel werden die Grundlagen der SQL Server Machine Learning Services erläutert.

In Azure SQL-Datenbank befindet sich [Machine Learning Services](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview) zurzeit in der öffentlichen Vorschau.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Informationen zum Ausführen von Java in SQL Server finden Sie in der [Dokumentation zu Spracherweiterungen](../language-extensions/language-extensions-overview.md).
::: moniker-end

## <a name="what-is-machine-learning-services"></a>Was ist Machine Learning Services?

Mit SQL Server Machine Learning Services können Sie python-und R-Skripts in der-Datenbank ausführen. Sie können Sie verwenden, um Daten vorzubereiten und zu bereinigen, Featureentwicklung durchzuführen und Machine Learning-Modelle in einer Datenbank zu trainieren, auszuwerten und bereitzustellen. Die Funktion führt Ihre Skripts aus, in denen sich die Daten befinden, und die Übertragung der Daten über das Netzwerk auf einen anderen Server entfällt.

Basis Verteilungen von Python und R sind in Machine Learning Services enthalten. Sie können Open-Source-Pakete und-Frameworks, wie z. b. pytorch, tensorflow und scikit-Learn, zusätzlich zu den Microsoft-Paketen [revoscalepy](python/ref-py-revoscalepy.md) und [microsoftml](python/ref-py-microsoftml.md) für python und [revoscaler](r/ref-r-revoscaler.md), [microsoftml](r/ref-r-microsoftml.md), [olapr verwenden. ](r/ref-r-olapr.md)und [sqlrutils](r/ref-r-sqlrutils.md) für R.

Machine Learning Services verwendet ein Erweiterbarkeits Framework, um Python-und R-Skripts in SQL Server auszuführen. Weitere Informationen finden Sie hier:

+ [Erweiterbarkeits Framework](concepts/extensibility-framework.md)
+ [Python-Erweiterung](concepts/extension-python.md)
+ [R-Erweiterung](concepts/extension-r.md)

## <a name="what-can-i-do-with-machine-learning-services"></a>Was kann ich mit Machine Learning Services tun?

Mit Machine Learning Services können Sie Machine Learning-und Deep Learning-Modelle in SQL Server erstellen und trainieren. Sie können auch vorhandene Modelle bereitstellen, um die relationalen Daten für Vorhersagen zu Machine Learning Services und zu verwenden.

Beispiele für die Art von Vorhersagen, die Sie für SQL Server Machine Learning Services verwenden können, sind:

|||
|-|-|
|Klassifizierung/Kategorisierung|Automatisches Aufteilen von Kundenfeedback in positive und negative Kategorien|
|Regression/Vorhersage von kontinuierlichen Werten|Vorhersagen des Preis von Häusern basierend auf Größe und Standort|
|Erkennung von Anomalien|Erkennen betrügerischer Banktransaktionen |
|Empfehlungen|Produkte vorschlagen, die Online-Einkäufer basierend auf Ihren vorherigen Käufen erwerben können|

### <a name="how-to-execute-python-and-r-scripts"></a>Ausführen von Python-und R-Skripts

Es gibt zwei Möglichkeiten, um Python-und R-Skripts in Machine Learning Services auszuführen:

+ Die gängigste Methode ist die Verwendung der gespeicherten T-SQL-Prozedur [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Sie können auch Ihren bevorzugten python-oder R-Client verwenden und Skripts schreiben, die die Ausführung (alsremotecomputekontext bezeichnet) auf eine Remote SQL Server überführen. Weitere Informationen finden Sie unter Einrichten eines Data Science Clients für die [Python-Entwicklung](python/setup-python-client-tools-sql.md) und [R-Entwicklung](r/set-up-a-data-science-client.md) .

<a name="packages"></a>

## <a name="python-and-r-packages"></a>Python-und R-Pakete

Zusätzlich zu den Unternehmens Paketen von Microsoft können Sie auch Open-Source-Pakete und-Frameworks verwenden. Die häufigsten Open-Source-python-und R-Pakete sind in Machine Learning Services vorinstalliert. Die folgenden python-und R-Pakete von Microsoft sind ebenfalls enthalten:

| Sprache | Package | Beschreibung |
|-|-|-|
| Python | [revoscalepy](python/ref-py-revoscalepy.md) | Das primäre Paket für skalierbare python. Daten Transformationen und-Bearbeitung, statistische Zusammenfassung, Visualisierung und viele Formen der Modellierung. Außerdem verteilen Funktionen in diesem Paket Arbeits Auslastungen für die parallele Verarbeitung automatisch auf verfügbare Kerne. |
| Python | [microsoftml](python/ref-py-microsoftml.md) | Fügt Machine Learning-Algorithmen hinzu, um benutzerdefinierte Modelle für die Textanalyse, die Bildanalyse und die Stimmungs Analyse zu erstellen. | 
| R | [RevoScaleR](r/ref-r-revoscaler.md) | Das primäre Paket für skalierbare R. Daten Transformationen und-Manipulation, statistische Zusammenfassung, Visualisierung und viele Modellierungs Formen. Außerdem verteilen Funktionen in diesem Paket Arbeits Auslastungen für die parallele Verarbeitung automatisch auf verfügbare Kerne. |
| R | [Microsoftml (R)](r/ref-r-microsoftml.md) | Fügt Machine Learning-Algorithmen hinzu, um benutzerdefinierte Modelle für die Textanalyse, die Bildanalyse und die Stimmungs Analyse zu erstellen. |
| R | [olapR](r/ref-r-olapr.md) | R-Funktionen, die für MDX-Abfragen für einen SQL Server Analysis Services OLAP-Cube verwendet werden. |
| R | [sqlrutils](r/ref-r-sqlrutils.md) | Ein Mechanismus zur Verwendung von R-Skripts in einer gespeicherten T-SQL-Prozedur, Registrieren dieser gespeicherten Prozedur bei einer Datenbank und Ausführen der gespeicherten Prozedur aus einer [R-Entwicklungsumgebung](r/set-up-a-data-science-client.md). |
| R | [Microsoft R Open](https://mran.microsoft.com/rro) | Microsoft r Open (MRO) ist die verbesserte Verteilung von R von Microsoft. Es handelt sich um eine umfassende Open Source-Plattform für statistische Analysen und Data Science. Es basiert auf und 100%, die mit R kompatibel sind, und bietet zusätzliche Funktionen für eine verbesserte Leistung und Reproduzierbarkeit. |

## <a name="how-do-i-get-started-with-machine-learning-services"></a>Gewusst wie Sie mit Machine Learning Services beginnen?

1. [Installieren Sie SQL Server Machine Learning Services](install/sql-machine-learning-services-windows-install.md)

1. Konfigurieren Sie Ihre Entwicklungs Tools. Sie können Folgendes verwenden:

    + [Azure Data Studio](../azure-data-studio/what-is.md) oder [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) , um T-SQL und die gespeicherte Prozedur [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) zum Ausführen Ihres python-oder R-Skripts zu verwenden.
    + Python oder R auf Ihrem eigenen Entwicklungs Laptop oder einer Arbeitsstation zum Ausführen von Skripts. Sie können Daten entweder lokal abrufen oder die Ausführung per Push Remote an SQL Server mit [revoscalepy](python/ref-py-revoscalepy.md) und [revoscaler](r/ref-r-revoscaler.md)übermitteln. Weitere Informationen finden Sie unter Einrichten eines Data Science Clients für die [Python-Entwicklung](python/setup-python-client-tools-sql.md) und [R-Entwicklung](r/set-up-a-data-science-client.md) .

1. Schreiben Ihres ersten python-oder R-Skripts

    + Schnellstart: Ausführen eines "Hello World"-Skripts [in python](tutorials/quickstart-python-run-using-t-sql.md) oder [R](tutorials/quickstart-r-run-using-tsql.md)
    + Schnellstart: Erstellen eines Vorhersagemodells [in python](tutorials/quickstart-python-train-score-in-tsql.md) oder [in R](tutorials/quickstart-r-create-predictive-model.md)
    + Tutorial: [Verwenden Sie python in T-SQL](tutorials/sqldev-in-database-python-for-sql-developers.md): Durchsuchen von Daten, Ausführen von Featureentwicklung, trainieren und Bereitstellen von Modellen und Treffen von Vorhersagen (fünf teilige Reihe)
    + Tutorial: [Verwenden von R in T-SQL](tutorials/sqldev-in-database-r-for-sql-developers.md): Durchsuchen von Daten, Ausführen von Featureentwicklung, trainieren und Bereitstellen von Modellen und Treffen von Vorhersagen (fünf teilige Reihe)
    + Tutorial: [Verwenden Sie Machine Learning Services in R-Tools](tutorials/walkthrough-data-science-end-to-end-walkthrough.md): Durchsuchen von Daten, Erstellen von Diagrammen und Diagrammen, Ausführen von Featureentwicklung, trainieren und Bereitstellen von Modellen und Treffen von Vorhersagen (sechs teilige Reihe)

## <a name="next-steps"></a>Nächste Schritte

+ [Installieren Sie SQL Server Machine Learning Services](install/sql-machine-learning-services-windows-install.md)
+ Einrichten eines Data Science Clients für die [Entwicklung von python](python/setup-python-client-tools-sql.md) -und [R-Entwicklung](r/set-up-a-data-science-client.md)
