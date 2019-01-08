---
title: SQL Server 2017-Python-Tutorial-Übersicht – SQL Server-Machine Learning
description: Einführung in die Python-Lernprogramme für SQL Server 2017-in-Database-Analyse.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9101471c53ea1e253f7a6eb13e0c2cb2bc137ed3
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046460"
---
# <a name="sql-server-2017-python-tutorials"></a>SQL Server 2017-Python-tutorials
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Python-Tutorials für in-Database-Analyse auf [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md). 

+ Erfahren Sie, wie Sie umschließen und führen Python-Code in gespeicherten Prozeduren.
+ Serialisieren und Speichern von Python-basierte Modelle in SQL Server-Datenbanken.
+ Informationen Sie zu lokalen und remote computekontexte und wann sie zu verwenden.
+ Untersuchen Sie die Microsoft-Python-Module für Data Science und Machine learning-Aufgaben.

<a name="bkmk_pythontutorials"></a>

## <a name="python-quickstarts-and-tutorials"></a>Python-Schnellstarts und tutorials

| Link | Description |
|------|-------------|
| [Schnellstart: "Hello World"-Python-Skript in SQL Server](quickstart-r-run-using-tsql.md) | Enthält die Grundlagen zum Aufrufen von Python in T-SQL. |
| [Schnellstart: Erstellen Sie, Trainieren Sie und verwenden Sie ein Python-Modell mit gespeicherten Prozeduren in SQL Server](quickstart-python-train-score-in-tsql.md) | Erläutert die Funktionsweise der Einbettung von Python-Code in einer gespeicherten Prozedur, die Bereitstellung von Eingaben und Ausführung einer gespeicherten Prozedur. |
| [Tutorial: Erstellen eines Modells mithilfe von revoscalepy](use-python-revoscalepy-to-create-model.md) | Veranschaulicht, wie zum Ausführen von Code über ein remote Python Terminal mithilfe von SQL Server-computekontext. Sie sollten etwas mit Python-Tools und Umgebungen vertraut sein. Ist Beispielcode bereitgestellt, die ein Modell mithilfe erstellt **RxLinMod**, aus dem neuen **Revoscalepy** Bibliothek. |
| [Tutorial: Erfahren Sie mehr in-Database Python Analytics für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md) | Diese exemplarische End-to-End-Vorgehensweise wird veranschaulicht, wie zum Erstellen einer vollständigen Python-Lösung mithilfe von gespeicherten T-SQL-Prozeduren. Alle Python-Code ist enthalten.|

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Codebeispiele

Markieren Sie diese Beispiele und Demos, die von der SQL Server-Entwicklungsteam bereitgestellte Methoden, mit denen Sie eingebettete Analysen in realen Anwendungen verwenden können.

| Link | Description |
|------|-------------|
| [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Erfahren Sie, wie ein skiverleih Machine learning, um zukünftige verleihe vorherzusagen, wodurch die Business-Plan und die Mitarbeiter, von der zukünftigen Nachfrage zu begegnen verwenden kann. |
| [Ausführen von Kunden mithilfe von Python und SQL Server-clustering](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Erfahren Sie, wie Sie mit der k-Means-Algorithmus zum Ausführen von nicht überwachten Gruppieren von Kunden. |

## <a name="see-also"></a>Siehe auch

+ [Python-Erweiterung für SQL Server](../concepts/extension-python.md)
+ [SQL Server Machine Learning Services-Lernprogramme](machine-learning-services-tutorials.md)
