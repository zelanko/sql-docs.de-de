---
title: Was ist SQL Server Machine Learning Services (Python und R)?
titleSuffix: ''
description: Machine Learning Services ist ein Feature in SQL Server, das die Möglichkeit bietet, Python- und R-Skripts mit relationalen Daten auszuführen. Sie können Open-Source-Pakete und -Frameworks und die Microsoft Python- und R-Pakete für Predictive Analytics und Machine Learning verwenden. Die Skripts werden in der Datenbank ausgeführt, ohne dass Daten aus SQL Server oder über das Netzwerk verschoben werden. In diesem Artikel werden die Grundlagen von SQL Server Machine Learning Services erläutert.
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/06/2020
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a94a3aea418a4c404b568fe6df7af701bc46de34
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285904"
---
# <a name="what-is-sql-server-machine-learning-services-python-and-r"></a>Was ist SQL Server Machine Learning Services (Python und R)?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Machine Learning Services ist ein Feature in SQL Server, das die Möglichkeit bietet, Python- und R-Skripts mit relationalen Daten auszuführen. Sie können Open-Source-Pakete und -Frameworks und die [Microsoft Python- und R-Pakete](#packages) für Predictive Analytics und Machine Learning verwenden. Die Skripts werden in der Datenbank ausgeführt, ohne dass Daten aus SQL Server oder über das Netzwerk verschoben werden. In diesem Artikel werden die Grundlagen von SQL Server Machine Learning Services erläutert.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Informationen zum Ausführen von Java in SQL Server finden Sie in der Dokumentation zu [Spracherweiterungen](../language-extensions/language-extensions-overview.md).
::: moniker-end

## <a name="what-is-machine-learning-services"></a>Was ist Machine Learning Services?

Mit SQL Server Machine Learning Services können Sie Python- und R-Skripts in einer Datenbank ausführen. Sie können das Feature verwenden, um Daten vorzubereiten und zu bereinigen, Features zu entwickeln und Machine Learning-Modelle in einer Datenbank zu trainieren, auszuwerten und bereitzustellen. Mit dem Feature können Sie Skripts ausführen, in denen sich die Daten befinden. Die Übertragung der Daten über das Netzwerk auf einen anderen Server entfällt.

In Machine Learning Services sind Basisverteilungen von R und Python enthalten. Neben den Microsoft-Paketen [revoscalepy](python/ref-py-revoscalepy.md) und [microsoftml](python/ref-py-microsoftml.md) für Python und [RevoScaleR](r/ref-r-revoscaler.md), [MicrosoftML](r/ref-r-microsoftml.md), [olapR](r/ref-r-olapr.md) und [sqlrutils](r/ref-r-sqlrutils.md) für R können Sie Open-Source-Pakete und -Frameworks wie PyTorch, TensorFlow und scikit-learn installieren und verwenden.

Zum Ausführen von Python- und R-Skripts in SQL Server wird von Machine Learning Services ein Erweiterbarkeitsframework verwendet. Weitere Informationen zur Funktionsweise finden Sie unter:

+ [Erweiterbarkeitsframework](concepts/extensibility-framework.md)
+ [Python-Erweiterung](concepts/extension-python.md)
+ [R-Erweiterung](concepts/extension-r.md)

## <a name="what-can-i-do-with-machine-learning-services"></a>Welche Möglichkeiten bietet Machine Learning Services?

Mit Machine Learning Services können Sie Machine Learning- und Deep Learning-Modelle in SQL Server erstellen und trainieren. Sie können auch vorhandene Modelle für Machine Learning Services bereitstellen und relationale Daten für Vorhersagen verwenden.

Hier finden Sie einige Beispiele für die Art von Vorhersagen, für die Sie SQL Server-Machine Learning Services verwenden können:

|||
|-|-|
|Klassifizierung/Kategorisierung|Automatische Einteilung von Kundenfeedback in positive und negative Kategorien|
|Regression/Vorhersage von kontinuierlichen Werten|Vorhersage des Preises für Häuser basierend auf Größe und Standort|
|Erkennung von Anomalien|Erkennung von betrügerischen Banktransaktionen |
|Empfehlungen|Empfehlung von Produkten anhand bisheriger Anschaffungen, die Onlinekunden gefallen könnten|

### <a name="how-to-execute-python-and-r-scripts"></a>Ausführen von Python- und R-Skripts

Es gibt zwei Möglichkeiten, Python- und R-Skripts in Machine Learning Services auszuführen:

+ Die gängigste Methode ist die Verwendung der gespeicherten T-SQL-Prozedur [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Sie können auch den von Ihnen bevorzugten Python- oder R-Client verwenden und Skripts schreiben, mit denen die Ausführung an einen Remotecomputer mit SQL Server gepusht wird. (Dies wird als *Remotecomputekontext* bezeichnet.) Weitere Informationen finden Sie unter [Einrichten eines Data Science-Clients für die Entwicklung in Python](python/setup-python-client-tools-sql.md) und [Einrichten eines Data Science-Clients für die Entwicklung in R](r/set-up-a-data-science-client.md).

<a name="versions"></a>

## <a name="python-and-r-versions"></a>Python- und R-Versionen

Welche Version von Python und R in Machine Learning Services integriert ist, hängt davon ab, welche Version von SQL Server Sie verwenden. 

| SQL Server-Version | Python-Version | R-Version |
|-|-|-|
| SQL Server 2017 | 3.5.2 | 3.3.3 |
| SQL Server 2019 | 3.7.3 | 3.5.2 |

Die R-Version in SQL Server 2016 finden Sie in [„Was ist SQL Server 2016 R Services?“ im Abschnitt „R-Version“](r/sql-server-r-services.md#version).

<a name="packages"></a>

## <a name="python-and-r-packages"></a>Python- und R-Pakete

Neben den Enterprise-Paketen von Microsoft können Sie auch Open-Source-Pakete und -Frameworks verwenden. Die gängigsten Open-Source-Pakete für Python und R sind in Machine Learning Services bereits vorinstalliert. Zudem sind die folgenden Python- und R-Pakete von Microsoft bereits enthalten:

| Sprache | Paket | BESCHREIBUNG |
|-|-|-|
| Python | [revoscalepy](python/ref-py-revoscalepy.md) | Das primäre Paket mit skalierbaren Python-Funktionen zum Transformieren und Bearbeiten von Daten sowie zum Erstellen von statistischen Übersichten, Visualisierungen und vielen anderen Modellierungsformen. Zudem enthält das Paket zur Parallelverarbeitung Funktionen zum automatischen Verteilen von Workloads auf verfügbare Kerne. |
| Python | [microsoftml](python/ref-py-microsoftml.md) | Stellt Machine Learning-Algorithmen zur Erstellung von benutzerdefinierten Modellen für die Text-, Bild- und Stimmungsanalyse bereit. | 
| R | [RevoScaleR](r/ref-r-revoscaler.md) | Das primäre Paket mit skalierbaren R-Funktionen zum Transformieren und Bearbeiten von Daten sowie zum Erstellen von statistischen Übersichten, Visualisierungen und vielen anderen Modellierungsformen. Zudem enthält das Paket zur Parallelverarbeitung Funktionen zum automatischen Verteilen von Workloads auf verfügbare Kerne. |
| R | [MicrosoftML (R)](r/ref-r-microsoftml.md) | Stellt Machine Learning-Algorithmen zur Erstellung von benutzerdefinierten Modellen für die Text-, Bild- und Stimmungsanalyse bereit. |
| R | [olapR](r/ref-r-olapr.md) | R-Funktionen, die für MDX-Abfragen eines SQL Server Analysis Services-OLAP-Cube verwendet werden können. |
| R | [sqlrutils](r/ref-r-sqlrutils.md) | Ein Mechanismus zur Verwendung von R-Skripts in gespeicherten T-SQL-Prozeduren sowie zum Registrieren dieser gespeicherten Prozeduren bei einer Datenbank und zum Ausführen der gespeicherten Prozeduren über eine [R-Entwicklungsumgebung](r/set-up-a-data-science-client.md). |
| R | [Microsoft R Open](https://mran.microsoft.com/rro) | Bei Microsoft R Open (MRO) handelt es sich um die erweiterte Verteilung von R von Microsoft. Diese umfassende Open-Source-Plattform wird für statistische Analysen und Data Science verwendet. Sie basiert auf R und ist vollständig kompatibel mit R. Zudem beinhaltet sie Funktionen für eine verbesserte Leistung und Reproduzierbarkeit. |

Weitere Informationen zu den in Machine Learning Services installierten Paketen sowie zur Installation anderer Pakete finden Sie unter:

+ [Abrufen von Paketinformationen für Python](package-management/python-package-information.md)
+ [Installieren von Python-Paketen mit sqlmlutils](package-management/install-additional-python-packages-on-sql-server.md)
+ [Abrufen von R-Paketinformationen](package-management/r-package-information.md)
+ [Installieren von neuen R-Paketen mit sqlmlutils](package-management/install-additional-r-packages-on-sql-server.md)

## <a name="how-do-i-get-started-with-machine-learning-services"></a>Erste Schritte mit Machine Learning Services

1. [Installieren von SQL Server-Machine Learning Services](install/sql-machine-learning-services-windows-install.md)

1. Konfigurieren Sie Ihre Entwicklungstools. Verwenden Sie Folgendes:

    + [Azure Data Studio](../azure-data-studio/what-is.md) oder [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) zur Verwendung von T-SQL sowie die gespeicherte Prozedur [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) zur Ausführung Ihres Python- oder R-Skripts.
    + Python oder R auf Ihrem eigenen Entwicklungslaptop oder Ihrer eigenen Entwicklungsarbeitsstation zum Ausführen von Skripts. Mit [revoscalepy](python/ref-py-revoscalepy.md) und [RevoScaleR](r/ref-r-revoscaler.md) können Sie Daten lokal pullen oder die Ausführung remote auf einen Computer mit SQL Server pushen. Weitere Informationen finden Sie unter [Einrichten eines Data Science-Clients für die Entwicklung in Python](python/setup-python-client-tools-sql.md) und [Einrichten eines Data Science-Clients für die Entwicklung in R](r/set-up-a-data-science-client.md).

1. Schreiben des ersten Python- oder R-Skripts

    + Schnellstart: [Ausführen einfacher Python-Skripts mit SQL Server Machine Learning Services](tutorials/quickstart-python-create-script.md)
    + Schnellstart: [Ausführen einfacher R-Skripts mit SQL Server Machine Learning Services](tutorials/quickstart-r-create-script.md)
    + Tutorial: [Verwenden von Python in T-SQL](tutorials/sqldev-in-database-python-for-sql-developers.md): Daten durchsuchen, Features entwickeln, Modelle trainieren und bereitstellen und Vorhersagen treffen (fünfteilige Reihe)
    + Tutorial: [Verwenden von R in T-SQL](tutorials/sqldev-in-database-r-for-sql-developers.md): Daten durchsuchen, Features entwickeln, Modelle trainieren und bereitstellen und Vorhersagen treffen (fünfteilige Reihe)

## <a name="next-steps"></a>Nächste Schritte

+ [Installieren von SQL Server-Machine Learning Services](install/sql-machine-learning-services-windows-install.md)
+ [Einrichten eines Data Science-Clients für die Entwicklung in Python](python/setup-python-client-tools-sql.md) und [Einrichten eines Data Science-Clients für die Entwicklung in R](r/set-up-a-data-science-client.md)
