---
title: 'SQL Server R Übersicht über das Tutorial: SQL Server-Machine Learning'
description: Einführung in die R-Sprache-Tutorials für SQL Server in-Database-Analyse.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4353d50ecfd8aac3ada1c71baf1be78f13c51b11
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596531"
---
# <a name="sql-server-r-language-tutorials"></a>Tutorials für SQL Server R-Sprache
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die R-Sprache-Tutorials für in-Database-Analyse auf [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) oder [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md).

+ Erfahren Sie, wie Sie umschließen und führen R-Code in gespeicherten Prozeduren.
+ Serialisieren Sie und speichern Sie R-basierte Modelle in SQL Server-Datenbanken.
+ Informationen Sie zu lokalen und remote computekontexte und wann sie zu verwenden.
+ Untersuchen Sie die Microsoft R-Bibliotheken für Data Science und Machine learning-Aufgaben.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>R-Schnellstarts und tutorials

| Link | Description |
|------|-------------|
| [Schnellstart: Verwenden von R in T-SQL](rtsql-using-r-code-in-transact-sql-quickstart.md) | Die erste von mehreren Schnellstarts, mit der in diesem Beispiel veranschaulicht die grundlegende Syntax zum Aufrufen einer R-Funktion, die mit einem T-SQL-Abfrage-Editor wie z. B. SQL Server Management Studio. |
| [Tutorial: Erfahren Sie in der Datenbank-R-Analysen für Datenanalysten](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | Für R-Entwickler mit Erfahrung mit SQL Server, in diesem Tutorial wird erläutert, wie Sie führen allgemeine Data Science-Aufgaben in SQL Server. Laden und Visualisieren von Daten, Trainieren und Speichern eines Modells zu SQL Server, und verwenden Sie das Modell für predictive Analytics. |
| [Tutorial: Erfahren Sie mehr in-Database R Analytics für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Erstellen und bereitstellen, nur über eine vollständige R-Lösung [!INCLUDE[tsql](../../includes/tsql-md.md)] Tools. Konzentriert sich auf eine Lösung in die Produktion überführen. Sie erfahren, wie Sie R-Code in einer gespeicherten Prozedur umschließen können, ein R-Modell in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank speichern können und parametrisierte Aufrufe des R-Modells für die Vorhersage durchführen können. |
| [Tutorial: Tieferer Einblick in RevoScalepR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Erfahren Sie, wie Sie die Funktionen in der RevoScaleR-Pakete verwenden. Verschieben von Daten zwischen R und SQL Server und Switches compute-Kontexte, um einen bestimmten Task angepasst. Erstellen von Modellen und Diagrammen, und verschieben diese zwischen Ihrer Entwicklungsumgebung und dem Datenbankserver. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Codebeispiele

| Link | Description |
|------|-------------|
| [Erstellen eines Vorhersagemodells mit R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Erfahren Sie, wie ein skiverleih Machine learning, um zukünftige verleihe vorherzusagen, wodurch die Business-Plan und die Mitarbeiter, von der zukünftigen Nachfrage zu begegnen verwenden kann. |
| [Führen Sie Kunden mit R und SQL Server-clustering](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Verwenden Sie unbeaufsichtigtes lernen zum Segmentieren von Kunden anhand der Umsatzdaten. |

## <a name="see-also"></a>Siehe auch

+ [R-Erweiterung für SQL Server](../concepts/extension-r.md)
+ [SQL Server Machine Learning Services-Lernprogramme](machine-learning-services-tutorials.md)

