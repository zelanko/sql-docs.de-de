---
title: Übersicht über SQL Server R-Tutorial
description: Einführung in die Lernprogramme der Programmiersprache R für SQL Server in-Database-Analysen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fc0cde616bc03be4a984d8de518770b490e4a89a
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199344"
---
# <a name="sql-server-r-language-tutorials"></a>Lernprogramme für die SQL Server R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die Lernprogramme für r-Sprache für Daten bankübergreifende Analysen in [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) oder [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)beschrieben.

+ Erfahren Sie, wie Sie R-Code in gespeicherten Prozeduren Verpacken und ausführen.
+ Serialisieren und speichern Sie r-basierte Modelle in SQL Server Datenbanken.
+ Erfahren Sie mehr über Remote-und lokale computekontexte und wann diese verwendet werden sollen.
+ Erkunden Sie die Microsoft R-Bibliotheken für Data Science-und Machine Learning-Aufgaben.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>R-Schnellstarts und Tutorials

| Link | Beschreibung |
|------|-------------|
| [Schnellstart: Einfache R-Skripts erstellen und ausführen](quickstart-r-create-script.md) | Der erste von mehreren Schnellstarts zeigt die grundlegende Syntax zum Aufrufen einer R-Funktion mithilfe eines T-SQL-Abfrage-Editors, z. b. SQL Server Management Studio. |
| [Tutorial: Erlernen von Daten Bank basierter R-Analysen für Datenanalysten](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | Für R-Entwickler, die neu in SQL Server sind, wird in diesem Tutorial erläutert, wie allgemeine Data Science Aufgaben in SQL Server ausgeführt werden. Laden und visualisieren Sie Daten, trainieren Sie ein Modell, und speichern Sie es in SQL Server, und verwenden Sie das Modell für die Predictive Analytics. |
| [Tutorial: Erlernen von Daten Bank basierter R-Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Erstellen Sie eine komplette R-Lösung, und stellen [!INCLUDE[tsql](../../includes/tsql-md.md)] Sie Sie mithilfe von Tools bereit. Konzentriert sich auf das Verschieben einer Lösung in die Produktion. Sie erfahren, wie Sie R-Code in einer gespeicherten Prozedur umschließen können, ein R-Modell in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank speichern können und parametrisierte Aufrufe des R-Modells für die Vorhersage durchführen können. |
| [Tutorial: Ausführliche Informationen zum revoscalepr](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Erfahren Sie, wie Sie die Funktionen in den revoscaler-Paketen verwenden. Verschieben von Daten zwischen R und SQL Server und Umschalten von computekontexten an eine bestimmte Aufgabe. Erstellen Sie Modelle und Diagramme, und verschieben Sie Sie zwischen Ihrer Entwicklungsumgebung und dem Datenbankserver. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Codebeispiele

| Link | Beschreibung |
|------|-------------|
| [Erstellen eines Vorhersagemodells mithilfe von R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Erfahren Sie, wie ein Ski-vermietungsgeschäft Machine Learning verwenden könnte, um zukünftige Vermietungen vorherzusagen, die dem Geschäftsplan und den Mitarbeitern helfen, zukünftige Anforderungen zu erfüllen. |
| [Durchführen von Customer Clustering mithilfe von R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Verwenden Sie nicht überwachtes Lernen, um Kunden anhand von Vertriebs Daten zu segmentieren. |

## <a name="see-also"></a>Siehe auch

+ [R-Erweiterung zu SQL Server](../concepts/extension-r.md)
+ [SQL Server Machine Learning Services Tutorials](machine-learning-services-tutorials.md)

