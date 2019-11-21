---
title: R-Tutorials
description: Einführung in die Tutorials der Programmiersprache R für datenbankinterne SQL Server-Analysen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7c71ebfbda37e66050f868fa7676d0247e84840e
ms.sourcegitcommit: add39e028e919df7d801e8b6bb4f8ac877e60e17
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74119229"
---
# <a name="sql-server-r-language-tutorials"></a>Tutorials für die Programmiersprache R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die Tutorials für die Programmiersprache R für datenbankinterne Analysen in [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) oder [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) beschrieben.

+ Erfahren Sie, wie Sie R-Code in gespeicherten Prozeduren umschließen und ausführen.
+ Serialisieren und speichern Sie R-basierte Modelle in SQL Server-Datenbanken.
+ Erfahren Sie mehr über lokale und Remotecomputekontexte und wann diese verwendet werden.
+ Erkunden Sie die Microsoft-R-Bibliotheken für Data Science- und Machine Learning-Aufgaben.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>Schnellstarts und Tutorials für R

| Link | und Beschreibung |
|------|-------------|
| [Schnellstart: Erstellen und Ausführen einfacher R-Skripts](quickstart-r-create-script.md) | Der erste von mehreren Schnellstarts, wobei dieser die grundlegende Syntax zum Aufrufen einer R-Funktion mit einem T-SQL-Abfrage-Editor wie SQL Server Management Studio veranschaulicht. |
| [Tutorial: Datenbankinterne R-Analysen für Data Scientists](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | In diesem Tutorial wird R-Entwicklern, für die SQL Server noch Neuland ist, erklärt, wie allgemeine Data Science-Aufgaben in SQL Server ausgeführt werden. Laden und Visualisieren Sie Daten, trainieren und speichern Sie ein Modell in SQL Server, und verwenden Sie es für Vorhersageanalysen. |
| [Tutorial: Datenbankinterne R-Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Erstellen Sie eine vollständige R-Lösung mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Tools. Konzentriert sich auf das Verschieben einer Lösung in die Produktionsumgebung. Sie erfahren, wie Sie R-Code in einer gespeicherten Prozedur umschließen können, ein R-Modell in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank speichern können und parametrisierte Aufrufe des R-Modells für die Vorhersage durchführen können. |
| [Tutorial: Ausführliche Informationen zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Sie erfahren auch, wie Sie die Funktionen in den RevoScaleR-Paketen verwenden. Verschieben Sie Daten zwischen R und SQL Server, und wechseln Sie Computekontexte passend zu einer bestimmten Aufgabe. Erstellen Sie Modelle und Diagramme, und verschieben Sie diese zwischen Ihrer Entwicklungsumgebung und dem Datenbankserver. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Codebeispiele

| Link | und Beschreibung |
|------|-------------|
| [Build a predictive model using R and SQL Server (Erstellen eines Vorhersagemodells mithilfe von R und SQL Server)](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Erfahren Sie, wie ein Skiverleih Machine Learning einsetzen könnte, um zukünftige Verleihe vorherzusagen. Dies hilft dem Geschäft und den Mitarbeitern, der zukünftigen Nachfrage zu begegnen. |
| [Perform customer clustering using R and SQL Server (Durchführen von Kundenclustering mithilfe von R und SQL Server)](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Segmentieren Sie Kunden anhand von Vertriebsdaten durch unüberwachtes Lernen. |

## <a name="see-also"></a>Siehe auch

+ [R-Erweiterung in SQL Server](../concepts/extension-r.md)
+ [Tutorials zu SQL Server Machine Learning Services](machine-learning-services-tutorials.md)

