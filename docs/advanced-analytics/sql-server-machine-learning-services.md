---
title: R und Python Machine learning-Dokumentation – SQL Server Machine Learning Services
description: R und Python in SQL Server, mit integrierter Data Science-Modellierung und Algorithmen für maschinelles Lernen für umfangreiche Analysen von Unternehmensdaten
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: overview
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: cbe617ea7732468732555bf6f0bba8ebaec2c17a
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141379"
---
# <a name="sql-server-machine-learning-services"></a>SQL Server-Machine Learning-Dienste
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

## <a name="sql-server-machine-learning-services-r-and-python-documentation"></a>SQL Server Machine Learning Services (R- und Python)-Dokumentation

Erfahren Sie anhand unserer Schnellstarts, Tutorials und Artikel, wie Sie die externen Bibliotheken von R und Python sowie die Sprachen selbst für residente, relationale Daten verwenden können. R und Python-Bibliotheken in [SQL Server Machine Learning Services](what-is-sql-server-machine-learning.md) gehören basisverteilungen, Data Science-Modelle, Machine Learning-Algorithmen und -Funktionen für die Durchführung von Analysen im größeren Umfang und mit hoher Leistung ohne Übertragen von Daten über das Netzwerk.

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Die Dokumentation in Java finden Sie in der [Dokumentation zu SQL Server-Spracherweiterungen](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview).
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

- [Installieren von Machine Learning-Dienste mit SQL Server](install/sql-machine-learning-services-windows-install.md)

- [Ausführen von R in T-SQL und gespeicherten Prozeduren](tutorials/sqldev-in-database-r-for-sql-developers.md)

- [Verwenden von Embedded Analytics in Python](tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="video-introduction"></a>Einführungsvideo

> [!VIDEO https://www.youtube.com/embed/ACejZ9optCQ]

## <a name="reference"></a>Referenz

| Package | Sprache | Description |
|:--------|:---------|:------------|
| [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) | R | Verteilte und Parallelverarbeitung für R-Aufgaben: Datentransformation, -exploration und -visualisierung, statistische Analysen und Predictive Analytics |
| [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) | R | Für R angepasste Funktionen, die auf den KI-Algorithmen von Microsoft basieren |
| [olapR](/machine-learning-server/r-reference/olapr/olapr) | R | Importiert Daten aus OLAP-Cubes |
| [sqlRUtils](/machine-learning-server/r-reference/sqlrutils/sqlrutils) | R | Hilfsfunktionen zum Kapseln von R und T-SQL |
[revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Python | Verteilte und Parallelverarbeitung für Python-Aufgaben: Datentransformation, -exploration und -visualisierung, statistische Analysen und Predictive Analytics |
| [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Python | Für Python angepasste Funktionen, die auf den KI-Algorithmen von Microsoft basieren |
| &nbsp; | &nbsp; | &nbsp; |
