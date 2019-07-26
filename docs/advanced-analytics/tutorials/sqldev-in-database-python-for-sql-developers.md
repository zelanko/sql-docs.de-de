---
title: Tutorial für Daten bankübergreifende python-Analysen für SQL-Entwickler
description: Erfahren Sie, wie Sie Python-Code in SQL Server gespeicherten Prozeduren und T-SQL-Funktionen einbetten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6147c4670dace104c2c33c19e1fd29cbf2d4f2ee
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68468852"
---
# <a name="tutorial-python-data-analytics-for-sql-developers"></a>Tutorial: Python-Datenanalysen für SQL-Entwickler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Tutorial für SQL-Programmierer erfahren Sie mehr über die python-Integration, indem Sie eine Python-basierte Machine Learning-Lösung mithilfe einer [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) -Datenbank auf SQL Server entwickeln und bereitstellen. Sie verwenden T-SQL, SQL Server Management Studio und eine Datenbank-Engine-Instanz mit [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) -und python-Sprachunterstützung.

Dieses Tutorial bietet eine Einführung in Python-Funktionen, die in einem Daten Modellierungs Workflow verwendet werden. Die Schritte umfassen das Durchsuchen von Daten, das entwickeln und Trainieren eines binären Klassifizierungs Modells und die Modell Bereitstellung. Sie verwenden Beispiel Daten aus der New York City Taxi-und der limosinus-Kommission, und das Modell, das Sie erstellen, sagt vorher, ob eine Fahrt wahrscheinlich zu einem Trinkgeld führt, basierend auf der Tageszeit, der Entfernung und der Pick-up-Position. 

Der gesamte Python-Code, der in diesem Tutorial verwendet wird, ist in gespeicherten Prozeduren umschließt, die Sie in Management Studio erstellen und ausführen.

> [!NOTE]
> Dieses Tutorial ist in R und Python verfügbar. Informationen zur r-Version finden Sie unter [Daten Bank Analysen für r-Entwickler](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Übersicht

Der Prozess des Erstellens einer Machine Learning-Lösung ist eine komplexe Lösung, die mehrere Tools umfassen kann, sowie die Koordination von Fachleuten in mehreren Phasen:

+ Abrufen und Bereinigen von Daten
+ Untersuchen der Daten und entwickeln von Features für die Modellierung
+ trainieren und Optimieren des Modells
+ Bereitstellung in der Produktion

Die Entwicklung und das Testen des tatsächlichen Codes erfolgt am besten mithilfe einer dedizierten Entwicklungsumgebung. Nachdem das Skript vollständig getestet wurde, können Sie es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jedoch problemlos mithilfe [!INCLUDE[tsql](../../includes/tsql-md.md)] von gespeicherten Prozeduren in der vertrauten Umgebung [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]von bereitstellen. Das Umpacken von externem Code in gespeicherten Prozeduren ist der primäre Mechanismus zum operationalisieren von Code in SQL Server.

Egal, ob Sie ein SQL-Programmierer sind, der noch nicht mit python vertraut ist, oder ein python SQL Server-Entwickler, der für SQL neu ist, in diesem mehrteiligen Tutorial wird ein typischer Workflow für die Durchführung von datenbankübergreifenden Analysen mit python 

+ [Lektion 1: Untersuchen und Visualisieren von Daten mithilfe von python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Lektion 2: Erstellen von Datenfunktionen mithilfe von benutzerdefinierten SQL-Funktionen](sqldev-py4-create-data-features-using-t-sql.md)

+ [Lektion 3: Trainieren und Speichern eines python-Modells mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Lektion 4: Vorhersagen potenzieller Ergebnisse mithilfe eines python-Modells in einer gespeicherten Prozedur](sqldev-py6-operationalize-the-model.md)

Nachdem das Modell in der Datenbank gespeichert wurde, können Sie das Modell für Vorhersagen aus [!INCLUDE[tsql](../../includes/tsql-md.md)] mithilfe von gespeicherten Prozeduren abrufen.

## <a name="prerequisites"></a>Vorraussetzungen

+ [SQL Server 2017 Machine Learning Services mit python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Berechtigungen](../security/user-permission.md)

+ [NYC Taxi Demo-Datenbank](demo-data-nyctaxi-in-sql.md)

Alle Tasks können mithilfe [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherter Prozeduren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]ausgeführt werden.

In diesem Tutorial wird davon ausgegangen, dass Sie mit grundlegenden Daten Bank Vorgängen wie dem Erstellen von Datenbanken und Tabellen, dem Importieren von Daten und dem Schreiben Es wird davon ausgegangen, dass Sie python nicht kennen. Daher wird der gesamte Python-Code bereitgestellt. 

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Untersuchen und Visualisieren von Daten mithilfe von python](sqldev-py3-explore-and-visualize-the-data.md)
