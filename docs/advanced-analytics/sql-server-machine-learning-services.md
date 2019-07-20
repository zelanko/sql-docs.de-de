---
title: Dokumentation zu R und python Machine Learning
description: R und Python in SQL Server, mit integrierter Data Science-Modellierung und Algorithmen für maschinelles Lernen für umfangreiche Analysen von Unternehmensdaten
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 8eb391ac4b64c93de255214d748c77f44dccb1b3
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344742"
---
# <a name="sql-server-machine-learning-services"></a>SQL Server-Machine Learning-Dienste
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

## <a name="sql-server-machine-learning-services-r-and-python-documentation"></a>Dokumentation zu SQL Server Machine Learning Services (R und python)

Erfahren Sie anhand unserer Schnellstarts, Tutorials und Artikel, wie Sie die externen Bibliotheken von R und Python sowie die Sprachen selbst für residente, relationale Daten verwenden können. R-und python-Bibliotheken in [SQL Server Machine Learning Services](what-is-sql-server-machine-learning.md) Basis Verteilungen, Data Science Modelle, Machine Learning-Algorithmen und Funktionen für die Bedarfs gesteuerte Durchführung von Hochleistungsanalysen, ohne dass Daten übertragen werden müssen. Netzwerk.

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Die Dokumentation zu Java finden Sie in der [Dokumentation zur SQL Server-Spracherweiterungen](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview).
::: moniker-end

|   |   |
|---|:--|
| ![R-Logo](media/index/logo_r.png) | Open Source-R wurde um [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) und KI-Algorithmen von Microsoft in [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) erweitert. Diese Bibliotheken ermöglichen Ihnen Vorhersagen und Vorhersagemodelle, statistische Analysen, Visualisierungen und umfangreiche Datenbearbeitung.<br/>Die Integration von R wurde mit [SQL Server 2016](install/sql-r-services-windows-install.md) eingeführt und ist auch in [SQL Server 2017](install/sql-machine-learning-services-windows-install.md) verfügbar. |
| ![Python-Logo](media/index/logo_python.png) | Python-Entwickler können die Microsoft-Bibliotheken [revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) und [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) für Predictive Analytics und umfangreiches maschinelles Lernen verwenden. Mit Anaconda und Python 3.5 kompatible Bibliotheken entsprechen der Baselineverteilung.<br/>Die Integration von Python wurde mit [SQL Server 2017](install/sql-machine-learning-services-windows-install.md) eingeführt. |
| &nbsp; | &nbsp; |

## <a name="5-minute-quickstarts"></a>5-minütige Schnellstarts

- [Erstellen eines Vorhersagemodells in R](tutorials/rtsql-create-a-predictive-model-r.md)

- [Vorhersagen und Zeichnen aus dem Modell mit R](tutorials/rtsql-predict-and-plot-from-model.md)

## <a name="step-by-step-tutorials"></a>Schritt-für-Schritt-Tutorials

- [Installieren von Machine Learning Services in SQL Server](install/sql-machine-learning-services-windows-install.md)

- [Ausführen von R in T-SQL und gespeicherten Prozeduren](tutorials/sqldev-in-database-r-for-sql-developers.md)

- [Verwenden von Embedded Analytics in Python](tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="video-introduction"></a>Einführungsvideo

> [!VIDEO https://www.youtube.com/embed/ACejZ9optCQ]

## <a name="reference"></a>Referenz

| Package | Sprache | Beschreibung |
|:--------|:---------|:------------|
| [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) | R | Verteilte und Parallelverarbeitung für R-Aufgaben: Datentransformation, -exploration und -visualisierung, statistische Analysen und Predictive Analytics |
| [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) | R | Für R angepasste Funktionen, die auf den KI-Algorithmen von Microsoft basieren |
| [olapR](/machine-learning-server/r-reference/olapr/olapr) | R | Importiert Daten aus OLAP-Cubes |
| [sqlRUtils](/machine-learning-server/r-reference/sqlrutils/sqlrutils) | R | Hilfsfunktionen zum Kapseln von R und T-SQL |
[revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Python | Verteilte und Parallelverarbeitung für Python-Aufgaben: Datentransformation, -exploration und -visualisierung, statistische Analysen und Predictive Analytics |
| [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Python | Für Python angepasste Funktionen, die auf den KI-Algorithmen von Microsoft basieren |
| &nbsp; | &nbsp; | &nbsp; |
