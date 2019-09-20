---
title: Was ist SQL Server 2016 R Services?
titleSuffix: ''
description: R Services ist ein Feature in SQL Server 2016, das die Möglichkeit bietet, R-Skripts mit relationalen Daten auszuführen. Sie können Open-Source-Pakete und-Frameworks sowie die Microsoft R-Pakete für Predictive Analytics und Machine Learning verwenden. Die Skripts werden in der Datenbank ausgeführt, ohne dass Daten aus SQL Server oder über das Netzwerk verschoben werden. In diesem Artikel werden die Grundlagen von SQL Server R Services erläutert.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/12/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 99aba9748e7ee6d53aabb18919324243740d996a
ms.sourcegitcommit: 1661c3e1bb38ed12f8485c3860fc2d2b97dd2c9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71149929"
---
# <a name="what-is-sql-server-2016-r-services"></a>Was ist SQL Server 2016 R Services?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

R Services ist ein Feature in SQL Server 2016, das die Möglichkeit bietet, R-Skripts mit relationalen Daten auszuführen. Sie können Open-Source-Pakete und-Frameworks sowie die [Microsoft R-Pakete](#packages) für Predictive Analytics und Machine Learning verwenden. Die Skripts werden in der Datenbank ausgeführt, ohne dass Daten aus SQL Server oder über das Netzwerk verschoben werden. In diesem Artikel werden die Grundlagen von SQL Server R Services erläutert.

> [!Note]
> R Services wurde in SQL Server 2017 und höher in [Machine Learning Services](../what-is-sql-server-machine-learning.md) umbenannt und unterstützt sowohl python als auch R.

## <a name="what-is-r-services"></a>Was sind R Services?

Mit SQL Server R Services können Sie R-Skripts in der-Datenbank ausführen. Sie können Sie verwenden, um Daten vorzubereiten und zu bereinigen, Featureentwicklung durchzuführen und Machine Learning-Modelle in einer Datenbank zu trainieren, auszuwerten und bereitzustellen. Die Funktion führt Ihre Skripts aus, in denen sich die Daten befinden, und die Übertragung der Daten über das Netzwerk auf einen anderen Server entfällt.

Basis Verteilungen von r sind in r Services enthalten. Open-Source-Pakete und-Frameworks können zusätzlich zu den Microsoft-Paketen [revoscaler](../r/ref-r-revoscaler.md), [microsoftml](../r/ref-r-microsoftml.md), [olapr]. verwendet werden. /r/Ref-r-olapr.MD) und [sqlrutils](../r/ref-r-sqlrutils.md) für r.

R Services verwendet ein Erweiterbarkeits Framework, um R-Skripts in SQL Server auszuführen. Weitere Informationen finden Sie hier:

+ [Erweiterbarkeits Framework](../concepts/extensibility-framework.md)
+ [R-Erweiterung](../concepts/extension-r.md)

## <a name="what-can-i-do-with-r-services"></a>Was kann ich mit R Services tun?

Sie können R Services verwenden, um Machine Learning-und Deep Learning-Modelle in SQL Server zu erstellen und zu trainieren. Sie können auch vorhandene Modelle für R-Dienste bereitstellen und relationale Daten für Vorhersagen verwenden.

Beispiele für die Art von Vorhersagen, die Sie für SQL Server R Services verwenden können, sind:

|||
|-|-|
|Klassifizierung/Kategorisierung|Automatisches Aufteilen von Kundenfeedback in positive und negative Kategorien|
|Regression/Vorhersage von kontinuierlichen Werten|Vorhersagen des Preis von Häusern basierend auf Größe und Standort|
|Erkennung von Anomalien|Erkennen betrügerischer Banktransaktionen |
|Empfehlungen|Produkte vorschlagen, die Online-Einkäufer basierend auf Ihren vorherigen Käufen erwerben können|

### <a name="how-to-execute-r-scripts"></a>Ausführen von R-Skripts

Es gibt zwei Möglichkeiten zum Ausführen von r-Skripts in r Services:

+ Die gängigste Methode ist die Verwendung der gespeicherten T-SQL-Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Sie können auch Ihren bevorzugten R-Client verwenden und Skripts schreiben, die die Ausführung (als *remotecomputekontext*bezeichnet) per Push auf eine Remote SQL Server überführen. Weitere Informationen finden [Sie unter Einrichten einer Data Science-Client-R-Entwicklung](../r/set-up-a-data-science-client.md) .

<a name="packages"></a>

## <a name="r-packages"></a>R-Pakete

Zusätzlich zu den Unternehmens Paketen von Microsoft können Sie auch Open-Source-Pakete und-Frameworks verwenden. Die häufigsten Open Source-r-Pakete werden in r Services vorinstalliert. Die folgenden R-Pakete von Microsoft sind ebenfalls enthalten:

| Package | Beschreibung |
|-|-|
| [RevoScaleR](../r/ref-r-revoscaler.md) | Das primäre Paket für skalierbare R. Daten Transformationen und-Manipulation, statistische Zusammenfassung, Visualisierung und viele Modellierungs Formen. Außerdem verteilen Funktionen in diesem Paket Arbeits Auslastungen für die parallele Verarbeitung automatisch auf verfügbare Kerne. |
| [Microsoftml (R)](../r/ref-r-microsoftml.md) | Fügt Machine Learning-Algorithmen hinzu, um benutzerdefinierte Modelle für die Textanalyse, die Bildanalyse und die Stimmungs Analyse zu erstellen. |
| [olapR](../r/ref-r-olapr.md) | R-Funktionen, die für MDX-Abfragen für einen SQL Server Analysis Services OLAP-Cube verwendet werden. |
| [sqlrutils](../r/ref-r-sqlrutils.md) | Ein Mechanismus zur Verwendung von R-Skripts in einer gespeicherten T-SQL-Prozedur, Registrieren dieser gespeicherten Prozedur bei einer Datenbank und Ausführen der gespeicherten Prozedur aus einer [R-Entwicklungsumgebung](../r/set-up-a-data-science-client.md). |
| [Microsoft R Open](https://mran.microsoft.com/rro) | Microsoft r Open (MRO) ist die verbesserte Verteilung von R von Microsoft. Es handelt sich um eine umfassende Open Source-Plattform für statistische Analysen und Data Science. Es basiert auf und 100%, die mit R kompatibel sind, und bietet zusätzliche Funktionen für eine verbesserte Leistung und Reproduzierbarkeit. |

## <a name="how-do-i-get-started-with-rservices"></a>Gewusst wie Sie die ersten Schritte mit rservices aus?

1. [Installieren von SQL Server 2016 R-Diensten](../install/sql-r-services-windows-install.md)

1. Konfigurieren Sie Ihre Entwicklungs Tools. Sie können Folgendes verwenden:

    + [Azure Data Studio](../../azure-data-studio/what-is.md) oder [SQL Server Management Studio (SSMS)](../../ssms/sql-server-management-studio-ssms.md) , um T-SQL und die gespeicherte Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) zum Ausführen Ihres R-Skripts zu verwenden.
    + R auf einem eigenen Entwicklungs Laptop oder einer Arbeitsstation, um Skripts auszuführen. Sie können Daten entweder lokal abrufen oder die Ausführung per Push Remote an SQL Server mit [revoscaler](../r/ref-r-revoscaler.md)überwachen. Weitere Informationen finden [Sie unter Einrichten einer Data Science-Client-R-Entwicklung](../r/set-up-a-data-science-client.md) .

1. Schreiben Ihres ersten R-Skripts

    + Schnellstart: [Einfache R-Skripts in SQL Server erstellen und ausführen](../tutorials/quickstart-r-create-script.md)
    + Schnellstart: [Erstellen und Trainieren eines Vorhersagemodells in R](../tutorials/quickstart-r-train-score-model.md)
    + Tutorial: [Verwenden von R in T-SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md): Durchsuchen von Daten, Ausführen von Featureentwicklung, trainieren und Bereitstellen von Modellen und Treffen von Vorhersagen (fünf teilige Reihe)
    + Tutorial: [Verwenden von r Services in r-Tools](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md): Durchsuchen von Daten, Erstellen von Diagrammen und Diagrammen, Ausführen von Featureentwicklung, trainieren und Bereitstellen von Modellen und Treffen von Vorhersagen (sechs teilige Reihe)

## <a name="next-steps"></a>Nächste Schritte

+ [Installieren von SQL Server 2016 R-Diensten](../install/sql-r-services-windows-install.md)
+ [Einrichten eines Data Science-Clients für die R-Entwicklung](../r/set-up-a-data-science-client.md)