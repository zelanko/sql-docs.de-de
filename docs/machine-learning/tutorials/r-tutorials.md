---
title: R-Tutorials
titleSuffix: SQL machine learning
description: In diesem Artikel werden die R-Tutorials für SQL Machine Learning aufgeführt. Erfahren Sie, wie Sie Skripts ausführen und Machine Learning-Modelle erstellen.
ms.prod: sql
ms.technology: machine-learning
ms.topic: tutorial
author: cawrites
ms.author: chadam
ms.reviewer: garye, davidph
ms.date: 05/04/2020
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 63c271c4e1d59c9446495607b42b0b5ad13ea246
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606922"
---
# <a name="r-tutorials-for-sql-machine-learning"></a>R-Turorials für SQL Machine Learning

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
In diesem Artikel werden die R-Tutorials und -Schnellstarts für [Machine Learning Services in SQL Server](../sql-server-machine-learning-services.md) und in [Big Data-Clustern](../../big-data-cluster/machine-learning-services.md) beschrieben.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
In diesem Artikel werden die R-Tutorials und -Schnellstarts für [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) beschrieben.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
In diesem Artikel werden die R-Tutorials und -Schnellstarts für [SQL Server 2016 R Services](../r/sql-server-r-services.md) beschrieben.
::: moniker-end

<a name="bkmk_sqltutorials"></a>

## <a name="r-tutorials"></a>R-Tutorials

| Lernprogramm | BESCHREIBUNG |
|------|-------------|
| [Vorhersagen für einen Skiverleih mit Entscheidungsstruktur](r-predictive-model-introduction.md) | Verwenden Sie R und ein Entscheidungsstrukturmodell, um die Anzahl zukünftiger Skivermietungen vorherzusagen. Bereiten Sie mithilfe von Notebooks in Azure Data Studio Daten vor und trainieren Sie das Modell, und verwenden Sie T-SQL für die Modellimplementierung. |
| [Kategorisierung von Kunden mit K-Means-Clustering](r-clustering-model-introduction.md) | Verwenden Sie R, um ein K-Means-Clusteringmodell zum Kategorisieren von Kunden zu entwickeln und bereitzustellen. Bereiten Sie mithilfe von Notebooks in Azure Data Studio Daten vor und trainieren Sie das Modell, und verwenden Sie T-SQL für die Modellimplementierung. |
| [Datenbankinterne R-Analysen für Data Scientists](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | In diesem Tutorial wird R-Entwicklern, für die SQL Server noch Neuland ist, erklärt, wie allgemeine Data Science-Aufgaben in SQL Server ausgeführt werden. Laden und Visualisieren Sie Daten, trainieren und speichern Sie ein Modell in SQL Server, und verwenden Sie es für Vorhersageanalysen. |
| [Datenbankinterne R-Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Erstellen Sie eine vollständige R-Lösung mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Tools. Konzentriert sich auf das Verschieben einer Lösung in die Produktionsumgebung. Sie erfahren, wie Sie R-Code in einer gespeicherten Prozedur umschließen können, ein R-Modell in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank speichern können und parametrisierte Aufrufe des R-Modells für die Vorhersage durchführen können. |

## <a name="r-quickstarts"></a>R-Schnellstarts

Wenn SQL Machine Learning noch Neuland für Sie ist, können Sie auch die R-Schnellstarts ausprobieren.

| Schnellstart | BESCHREIBUNG |
|-|-|
| [Ausführen einfacher R-Skripts mit SQL Server Machine Learning Services](quickstart-r-create-script.md) | Erfahren Sie mehr über die Grundlagen zum Aufrufen von R in T-SQL mithilfe von [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Datenstrukturen und -objekte, die R verwenden](quickstart-r-data-types-and-objects.md) | Dieser Schnellstart zeigt, wie mithilfe von R Datenstrukturen verarbeitet werden. |
| [Erstellen und Bewerten eines Vorhersagemodells in R](quickstart-r-data-types-and-objects.md) | Hier sehen Sie, wie ein R-Modell erstellt, trainiert und verwendet wird, um Vorhersagen aus neuen Daten zu treffen. |

## <a name="next-steps"></a>Nächste Schritte

Weitere technische Details zu R in SQL Server finden Sie unter [R-Spracherweiterung in SQL Server](../concepts/extension-r.md).
