---
title: Tutorial für datenbankinterne Analysen mit R – SQL Server-Machine Learning
description: Informationen Sie zum Einbetten von R programming Language-Code in SQL Server gespeicherte Prozeduren und T-SQL-Funktionen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8d3235c585d3ea56a64776fde841ccc6d71b1a4d
ms.sourcegitcommit: 2e8783e6bedd9597207180941be978f65c2c2a2d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2019
ms.locfileid: "54405600"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>Lernprogramm: R-Data-Analysen für SQL-Entwickler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Tutorial für die SQL-Programmierer erfahren Sie mehr über R-Integration durch die Erstellung und Bereitstellung einer R-basierte-Machine learning-Lösung mit einem [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) Datenbank auf SQL Server. Verwenden Sie T-SQL und SQL Server Management Studio eine Datenbank-Engine-Instanz mit [Machine Learning-Dienste] ([Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) und die R-sprachunterstützung

Dieses Tutorial führt Sie in R-Funktionen, die in einem Workflow der Modellierung verwendet. Schritte schließen das Durchsuchen von Daten, erstellen und Trainieren ein binärklassifizierungsmodell für und Bereitstellung eines Modells. Das Modell, das Sie erstellen vorhersagt, ob eine Fahrt wahrscheinlich zu einer QuickInfo, die basierend auf dem der Tag, Wegstrecke und einstiegsort ist. 

Alle in diesem Tutorial verwendeten R-Code ist eingeschlossen in gespeicherten Prozeduren, die Sie erstellen, und führen Sie in Management Studio.

## <a name="background-for-sql-developers"></a>Hintergrund für SQL-Entwickler

Der Prozess der Erstellung einer Machine Learning-Lösung ist ein komplexes, die mehrere Tools und die Koordination von Experten in mehreren Phasen umfassen können:

+ Abrufen und Bereinigen von Daten
+ Untersuchen der Daten und Erstellen von Features, die für die Modellierung hilfreich.
+ Trainieren und Optimieren des Modells
+ Bereitstellung in der Produktion

Entwickeln und Testen von den eigentlichen Code erfolgt am besten das über eine dedizierte R-Entwicklungsumgebung. Allerdings nachdem das Skript vollständig getestet ist, können Sie ganz einfach bereitstellen damit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren in der vertrauten Umgebung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Der Zweck dieses mehrteilige Tutorial bietet eine Einführung in ein typischer Workflow für die Migration von "Fertig R-Code" für SQL Server. 

- [Lektion 1: Untersuchen und Visualisieren von Daten-Shapes und die Verteilung durch Aufrufen von R-Funktionen in gespeicherten Prozeduren](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Lektion 2: Erstellen von Datenfunktionen mit R in T-SQL-Funktionen](sqldev-create-data-features-using-t-sql.md)
  
- [Lektion 3: Trainieren und Speichern eines R-Modells mithilfe von Funktionen und gespeicherten Prozeduren](sqldev-train-and-save-a-model-using-t-sql.md)
  
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