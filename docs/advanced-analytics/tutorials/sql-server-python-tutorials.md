---
title: Python-Tutorials
description: In diesem Artikel werden die Python-Tutorials für SQL Server Machine Learning Services beschrieben. Erfahren Sie, wie Sie python-Skripts ausführen. Erstellen, trainieren und Bereitstellen von python-Modellen, um SQL Server. Erfahren Sie mehr über Remote-und lokale computekontexte. Erkunden Sie die Microsoft Python-Pakete für Data Science und Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 80f714810acd8c04c80fe0b8abe5214a456f6dd6
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199408"
---
# <a name="python-tutorials-for-sql-server-machine-learning-services"></a>Python-Tutorials für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die Python-Tutorials und-Schnellstarts für [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)beschrieben.

+ Erfahren Sie, wie Sie python-Skripts ausführen.
+ Erstellen, trainieren und Bereitstellen von python-Modellen, um SQL Server.
+ Erfahren Sie mehr über Remote-und lokale computekontexte.
+ Erkunden Sie die Microsoft Python-Pakete für Data Science und Machine Learning.

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Python-Tutorials

| Lernprogramm | Beschreibung |
|-|-|
| [Vorhersagen eines Skirental mit linearer Regression](python-ski-rental-linear-regression.md) | Verwenden Sie python und lineare Regression, um die Anzahl der Ski-Vermietungen vorherzusagen. Verwenden Sie Notebooks in Azure Data Studio zum Vorbereiten von Daten und zum Trainieren des Modells und T-SQL für die Modell Bereitstellung. |
| [Kategorisierung von Kunden mithilfe von k-Means-Clustering](python-clustering-model.md) | Verwenden Sie Python, um ein K-Means-Clustering-Modell zum Kategorisieren von Kunden zu entwickeln und bereitzustellen. Verwenden Sie Notebooks in Azure Data Studio zum Vorbereiten von Daten und zum Trainieren des Modells und T-SQL für die Modell Bereitstellung. |
| [Erstellen eines Modells mithilfe von revoscalepy](use-python-revoscalepy-to-create-model.md) | Veranschaulicht, wie Sie Code von einem Python-Remote Client ausführen, indem Sie SQL Server als computekontext verwenden. In diesem Tutorial wird ein Modell mithilfe von **rxlinmod** aus der **revoscalepy** -Bibliothek erstellt. |
| [Python-Datenanalysen für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md) | In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine komplette python-Lösung mithilfe von T-SQL aufbauen. |

## <a name="python-quickstarts"></a>Python-Schnellstarts

Wenn Sie noch nicht mit SQL Server Machine Learning Services vertraut sind, können Sie auch die python-Schnellstarts ausprobieren.

| Schnellstart | Beschreibung |
|-|-|
| [Hallo Welt in Python und SQL Server](quickstart-python-create-script.md) | Erfahren Sie mehr über die Grundlagen zum Abrufen von python in T-SQL mithilfe von [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Verarbeiten von Datentypen und Objekten mithilfe von python in SQL Server](quickstart-python-data-structures.md) | Zeigt, wie SQL Server das python Pandas-Paket verwendet, um Datenstrukturen zu verarbeiten. |
| [Erstellen und bewerten eines Vorhersagemodells in python](quickstart-python-train-score-model.md) | Erläutert, wie ein python-Modell erstellt, trainiert und verwendet wird, um Vorhersagen aus neuen Daten zu treffen. |

## <a name="next-steps"></a>Nächste Schritte

+ [Was ist SQL Server Machine Learning Services (python und R)?](../what-is-sql-server-machine-learning.md)
+ [Python-Erweiterung zu SQL Server](../concepts/extension-python.md)