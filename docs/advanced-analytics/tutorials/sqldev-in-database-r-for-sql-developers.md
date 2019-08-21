---
title: Tutorial für Daten bankübergreifende Analysen mit R
description: Erfahren Sie, wie Sie R-Programmiersprachen Code in SQL Server gespeicherten Prozeduren und T-SQL-Funktionen einbetten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5b2629a50a73208181cc14fd843cd9ab9c0b05df
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69633609"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>Tutorial: R-Datenanalysen für SQL-Entwickler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Tutorial für SQL-Programmierer erfahren Sie mehr über die Integration von r, indem Sie eine r-basierte Machine Learning-Lösung mithilfe einer [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) -Datenbank auf SQL Server aufbauen und bereitstellen. Sie verwenden T-SQL, SQL Server Management Studio und eine Datenbank-Engine-Instanz mit [Machine Learning Services] ([Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) und der R-Sprachunterstützung.

In diesem Tutorial werden die R-Funktionen vorgestellt, die in einem Daten Modellierungs Workflow verwendet werden. Die Schritte umfassen das Durchsuchen von Daten, das entwickeln und Trainieren eines binären Klassifizierungs Modells und die Modell Bereitstellung. Das Modell, das Sie erstellen, sagt vorher, ob eine Fahrt wahrscheinlich zu einem Trinkgeld führt, basierend auf der Tageszeit, der Entfernung und der Pick-up-Position. 

Der gesamte R-Code, der in diesem Tutorial verwendet wird, ist in gespeicherten Prozeduren umschließt, die Sie in Management Studio erstellen und ausführen.

## <a name="background-for-sql-developers"></a>Hintergrund für SQL-Entwickler

Der Prozess des Erstellens einer Machine Learning-Lösung ist eine komplexe Lösung, die mehrere Tools umfassen kann, sowie die Koordination von Fachleuten in mehreren Phasen:

+ Abrufen und Bereinigen von Daten
+ Untersuchen der Daten und entwickeln von Features für die Modellierung
+ trainieren und Optimieren des Modells
+ Bereitstellung in der Produktion

Die Entwicklung und das Testen des tatsächlichen Codes erfolgt am besten über eine dedizierte R-Entwicklungsumgebung. Nachdem das Skript vollständig getestet wurde, können Sie es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jedoch problemlos mithilfe [!INCLUDE[tsql](../../includes/tsql-md.md)] von gespeicherten Prozeduren in der vertrauten Umgebung [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]von bereitstellen.

Der Zweck dieses mehrteiligen Tutorials ist eine Einführung in einen typischen Workflow zum Migrieren von "fertiggestelltes R-Code" zu SQL Server. 

- [Lektion 1: Durch Aufrufen von R-Funktionen in gespeicherten Prozeduren und Visualisieren der Daten Form und-Verteilung](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Lektion 2: Erstellen von Datenfunktionen mithilfe von R in T-SQL-Funktionen](sqldev-create-data-features-using-t-sql.md)
  
- [Lektion 3: Trainieren und Speichern eines R-Modells mithilfe von Funktionen und gespeicherten Prozeduren](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Lektion 4: Vorhersagen potenzieller Ergebnisse mithilfe eines R-Modells in einer gespeicherten Prozedur](../tutorials/sqldev-operationalize-the-model.md)

Nachdem das Modell in der Datenbank gespeichert wurde, müssen Sie das Modell für Vorhersagen [!INCLUDE[tsql](../../includes/tsql-md.md)] aus mithilfe von gespeicherten Prozeduren abrufen.

## <a name="prerequisites"></a>Erforderliche Komponenten

Alle Tasks können mithilfe [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherter Prozeduren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]ausgeführt werden.

In diesem Tutorial wird davon ausgegangen, dass Sie mit grundlegenden Daten Bank Vorgängen wie dem Erstellen von Datenbanken und Tabellen, dem Importieren von Daten und dem Schreiben Es wird davon ausgegangen, dass Sie R nicht kennen. Daher wird der gesamte R-Code bereitgestellt. 

+ [SQL Server 2016 R-Dienste](../install/sql-r-services-windows-install.md#verify-installation) oder [SQL Server Machine Learning Services mit aktiviertem R](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [R-Bibliotheken](../package-management/r-package-information.md)

+ [Berechtigungen](../security/user-permission.md)

+ [NYC Taxi Demo-Datenbank](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Untersuchen und Visualisieren von Daten mit R-Funktionen in gespeicherten Prozeduren](../tutorials/sqldev-explore-and-visualize-the-data.md)
