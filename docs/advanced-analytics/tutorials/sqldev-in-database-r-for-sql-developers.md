---
title: Tutorial für datenbankinterne Analysen mit R und SQL Server-Machine Learning | Microsoft-Dokumentation
description: Informationen Sie zum Einbetten von R programming Language-Code in SQL Server gespeicherte Prozeduren und T-SQL-Funktionen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 80c4d39e87984b022340079be4d944ed6ad963e3
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030647"
---
# <a name="tutorial-in-database-r-analytics-for-sql-developers"></a>Tutorial: In-Database R Analytics für SQL-Entwickler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Tutorial für die SQL-Programmierer erfahren Sie mehr über R-Integration durch die Erstellung und Bereitstellung einer R-basierte-Machine learning-Lösung mit einem [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) Datenbank auf SQL Server. 

Dieses Tutorial führt Sie in R-Funktionen, die in einem Workflow der Modellierung verwendet. Schritte schließen das Durchsuchen von Daten, erstellen und Trainieren ein binärklassifizierungsmodell für und Bereitstellung eines Modells. Verwenden Sie Beispieldaten aus der New York City Taxi und Limosine Kommission und das Modell, das Sie erstellen vorhersagt, ob eine Fahrt wahrscheinlich zu einer QuickInfo, die basierend auf dem der Tag, Wegstrecke und einstiegsort ist. Alle in diesem Tutorial verwendeten R-Code ist eingeschlossen in gespeicherten Prozeduren, die Sie erstellen, und führen Sie in Management Studio.


> [!NOTE]
> 
> Dieses Tutorial ist in R und Python verfügbar. Die Python-Version finden Sie unter [datenbankinterne Analysen für Python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md).

## <a name="overview"></a>Übersicht

Der Prozess der Erstellung einer Machine Learning-Lösung ist ein komplexes, die mehrere Tools und die Koordination von Experten in mehreren Phasen umfassen können:

+ Abrufen und Bereinigen von Daten
+ Untersuchen der Daten und Erstellen von Features, die für die Modellierung hilfreich.
+ Trainieren und Optimieren des Modells
+ Bereitstellung in der Produktion

Entwickeln und Testen von den tatsächlichen Code, wird am besten mit einer dedizierten Umgebung ausgeführt. Allerdings nachdem das Skript vollständig getestet ist, können Sie ganz einfach bereitstellen damit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren in der vertrauten Umgebung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Führt, ob Sie ein SQL-Programmierer, die keine Erfahrung mit R, oder ein R-Entwickler, die noch nicht mit SQL, diesem mehrteiligen Tutorial wird einen typischen Workflow für die Durchführung von in-Database-Analyse mit R und SQL Server. 

- [Lektion 1: Untersuchen und Visualisieren von Daten-Shapes und die Verteilung durch den Aufruf von R-Funktionen in gespeicherten Prozeduren](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Lektion 2: Erstellen von Datenfunktionen mit R in T-SQL-Funktionen](sqldev-create-data-features-using-t-sql.md)
  
- [Lektion 3: Trainieren Sie und speichern Sie eine R-Modells mithilfe von Funktionen und gespeicherten Prozeduren](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Lektion 4: Vorhersagen von möglichen Ergebnissen, die mithilfe eines R-Modells in einer gespeicherten Prozedur](../tutorials/sqldev-operationalize-the-model.md)

Nachdem das Modell in der Datenbank gespeichert wurde, rufen Sie das Modell für Vorhersagen [!INCLUDE[tsql](../../includes/tsql-md.md)] mit gespeicherten Prozeduren.

## <a name="prerequisites"></a>Erforderliche Komponenten

Alle Vorgänge erfolgen mit [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

In diesem Tutorial wird davon ausgegangen, Vertrautheit mit grundlegender Datenbankvorgänge wie das Erstellen von Datenbanken und Tabellen, Importieren von Daten und SQL-Abfragen schreiben. Es wird nicht davon ausgegangen, dass Sie wissen, dass R. Daher wird der gesamte R-Code bereitgestellt. 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) oder [SQL Server 2017 Machine Learning Services mit R aktiviert](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [R-Bibliotheken](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)

+ [Berechtigungen](../security/user-permission.md)

+ [NYC Taxi-Demo-Datenbank](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Richten Sie die NYC Taxi-Datenbank](demo-data-nyctaxi-in-sql.md)