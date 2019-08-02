---
title: Übersicht über SQL Server 2017 python-Tutorial
description: Einführung in die Python-Tutorials für die 2017 SQL Server der Datenbankanalyse in der Datenbank.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 65dd2197d9fb079da116908871d931ad19370cf5
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714771"
---
# <a name="sql-server-2017-python-tutorials"></a>Python-Tutorials zu SQL Server 2017
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die Python-Tutorials für Daten bankübergreifende Analysen auf [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)beschrieben. 

+ Erfahren Sie, wie Sie Python-Code in gespeicherten Prozeduren Verpacken und ausführen.
+ Serialisieren und speichern Sie python-basierte Modelle in SQL Server Datenbanken.
+ Erfahren Sie mehr über Remote-und lokale computekontexte und wann diese verwendet werden sollen.
+ Erkunden Sie die Microsoft Python-Module für Data Science und Machine Learning-Aufgaben.

<a name="bkmk_pythontutorials"></a>

## <a name="python-quickstarts-and-tutorials"></a>Python-Schnellstarts und Tutorials

| Link | Beschreibung |
|------|-------------|
| [Schnellstart: "Hello World"-Python-Skript in SQL Server](quickstart-python-run-using-t-sql.md) | Erfahren Sie mehr über die Grundlagen zum Abrufen von python in T-SQL. |
| [Schnellstart: Erstellen, trainieren und Verwenden eines python-Modells mit gespeicherten Prozeduren in SQL Server](quickstart-python-train-score-in-tsql.md) | Erläutert die Mechanismen zum Einbetten von Python-Code in einer gespeicherten Prozedur, zum Bereitstellen von Eingaben und zum Ausführen der gespeicherten Prozedur. |
| [Tutorial: Erstellen eines Modells mithilfe von revoscalepy](use-python-revoscalepy-to-create-model.md) | Veranschaulicht, wie mithilfe SQL Server computekontexts Code von einem Python-Remote Terminal aus ausgeführt wird. Sie sollten mit python-Tools und-Umgebungen vertraut sein. In der neuen **revoscalepy** -Bibliothek wird ein Beispielcode bereitgestellt, der mithilfe von **rxlinmod**ein Modell erstellt. |
| [Tutorial: Erlernen von in-Database-python-Analysen für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md) | In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine komplette python-Lösung mit gespeicherten T-SQL-Prozeduren aufbauen. Der gesamte Python-Code ist enthalten.|

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Codebeispiele

Diese Beispiele und Demos vom SQL Server-Entwicklungsteam veranschaulichen Möglichkeiten, wie Sie Embedded Analytics in realen Anwendungen verwenden können.

| Link | Beschreibung |
|------|-------------|
| [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Erfahren Sie, wie ein Ski-vermietungsgeschäft Machine Learning verwenden könnte, um zukünftige Vermietungen vorherzusagen, die dem Geschäftsplan und den Mitarbeitern helfen, zukünftige Anforderungen zu erfüllen. |
| [Ausführen von Customer Clustering mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Erfahren Sie, wie Sie den kmeans-Algorithmus verwenden, um nicht überwachte Clustering von Kunden auszuführen. |

## <a name="see-also"></a>Siehe auch

+ [Python-Erweiterung zu SQL Server](../concepts/extension-python.md)
+ [SQL Server Machine Learning Services Tutorials](machine-learning-services-tutorials.md)
