---
title: R-Tutorials
description: In diesem Artikel werden die R-Tutorials und -Schnellstarts für SQL Server Machine Learning Services beschrieben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/13/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 952a33eb5a160acae44b5d1ae674c75b8d74cca5
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487285"
---
# <a name="r-tutorials-for-sql-server-machine-learning-services"></a>R-Tutorials für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die R-Tutorials und -Schnellstarts für [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) beschrieben.

+ Erfahren Sie, wie Sie R-Skripts ausführen.
+ Erstellen und trainieren Sie R-Modelle, und stellen Sie diese in SQL Server bereit.
+ Erfahren Sie mehr über lokale und Remotecomputekontexte.
+ Erkunden Sie die Microsoft-R-Pakete für Data Science und Machine Learning.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>Schnellstarts und Tutorials für R

| Link | BESCHREIBUNG |
|------|-------------|
| [Schnellstart: Erstellen und Ausführen einfacher R-Skripts](quickstart-r-create-script.md) | Der erste von mehreren Schnellstarts, wobei dieser die grundlegende Syntax zum Aufrufen einer R-Funktion mit einem T-SQL-Abfrage-Editor wie SQL Server Management Studio veranschaulicht. |
| [Tutorial: Datenbankinterne R-Analysen für Data Scientists](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | In diesem Tutorial wird R-Entwicklern, für die SQL Server noch Neuland ist, erklärt, wie allgemeine Data Science-Aufgaben in SQL Server ausgeführt werden. Laden und Visualisieren Sie Daten, trainieren und speichern Sie ein Modell in SQL Server, und verwenden Sie es für Vorhersageanalysen. |
| [Tutorial: Datenbankinterne R-Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Erstellen Sie eine vollständige R-Lösung mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Tools. Konzentriert sich auf das Verschieben einer Lösung in die Produktionsumgebung. Sie erfahren, wie Sie R-Code in einer gespeicherten Prozedur umschließen können, ein R-Modell in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank speichern können und parametrisierte Aufrufe des R-Modells für die Vorhersage durchführen können. |
| [Tutorial: Ausführliche Informationen zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Sie erfahren auch, wie Sie die Funktionen in den RevoScaleR-Paketen verwenden. Verschieben Sie Daten zwischen R und SQL Server, und wechseln Sie Computekontexte passend zu einer bestimmten Aufgabe. Erstellen Sie Modelle und Diagramme, und verschieben Sie diese zwischen Ihrer Entwicklungsumgebung und dem Datenbankserver. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Codebeispiele

| Link | BESCHREIBUNG |
|------|-------------|
| [Build a predictive model using R and SQL Server (Erstellen eines Vorhersagemodells mithilfe von R und SQL Server)](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Erfahren Sie, wie ein Skiverleih Machine Learning einsetzen könnte, um zukünftige Verleihe vorherzusagen. Dies hilft dem Geschäft und den Mitarbeitern, der zukünftigen Nachfrage zu begegnen. |
| [Perform customer clustering using R and SQL Server (Durchführen von Kundenclustering mithilfe von R und SQL Server)](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Segmentieren Sie Kunden anhand von Vertriebsdaten durch unüberwachtes Lernen. |

## <a name="see-also"></a>Weitere Informationen

+ [R-Erweiterung in SQL Server](../concepts/extension-r.md)