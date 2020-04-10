---
title: 'Tutorial zu R und Transact-SQL: Entwickeln eines Modells'
description: Hier erfahren Sie, wie Sie Code der Programmiersprache R in gespeicherte SQL Server-Prozeduren und T-SQL-Funktionen einbetten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9669b2c38d2e8b571ef7e519100b13cf5a63a10d
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81115983"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>Tutorial: R-Datenanalysen für SQL-Entwickler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Tutorial für SQL-Programmierer erfahren Sie, wie Sie R durch Erstellen und Bereitstellen einer R-basierten Machine Learning-Lösung mithilfe der Datenbank [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) in SQL Server integrieren. Sie verwenden T-SQL, SQL Server Management Studio und eine Datenbank-Engine-Instanz mit [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) und Unterstützung der R-Programmiersprache.

Dieses Tutorial bietet eine Einführung in R-Funktionen, die in einem Workflow für Datenmodellierung verwendet werden. Dies beinhaltet das Durchsuchen von Daten, das Entwickeln und Trainieren eines binären Klassifizierungsmodells sowie die Modellimplementierung. Mit dem Modell, das Sie erstellen, soll vorhergesagt werden, ob eine Fahrt (basierend auf der Tageszeit, der zurückgelegten Strecke und der Abholadresse) zur Gabe von Trinkgeld führt. 

Der gesamte in diesem Tutorial verwendete R-Code wird in gespeicherte Prozeduren eingebunden, die Sie in Management Studio erstellen und ausführen.

## <a name="background-for-sql-developers"></a>Hintergrund für SQL-Entwickler

Der Erstellungsprozess einer Machine Learning-Lösung ist komplex und kann den Einsatz mehrerer Tools sowie die phasenübergreifende Koordinierung von Experten bei folgenden Schritten erfordern:

+ Abrufen und Bereinigen von Daten
+ Untersuchen der Daten und Entwickeln von Modellierungsfunktionen
+ Trainieren und Optimieren des Modells
+ Bereitstellen in der Produktion

Die Entwicklung und das Testen des eigentlichen Codes werden am besten in einer dedizierten R-Entwicklungsumgebung durchgeführt. Nachdem das Skript vollständig getestet wurde, können Sie es jedoch problemlos in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren in der vertrauten Umgebung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] bereitstellen.

Dieses mehrteilige Tutorial stellt eine Einführung in einen typischen Workflow für die Migration von „fertiggestelltem R-Code“ zu SQL Server dar. 

- [Lektion 1: Durchsuchen und Visualisieren von Datenform und -verteilung durch Aufrufen von R-Funktionen in gespeicherten Prozeduren](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Lektion 2: Erstellen von Datenfunktionen mithilfe von R in T-SQL-Funktionen](sqldev-create-data-features-using-t-sql.md)
  
- [Lektion 3: Trainieren und Speichern eines R-Modells mithilfe von Funktionen und gespeicherten Prozeduren](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Lektion 4: Vorhersagen potenzieller Ergebnisse mithilfe eines R-Modells in einer gespeicherten Prozedur](../tutorials/sqldev-operationalize-the-model.md)

Rufen Sie das Modell nach dem Speichern in der Datenbank für Vorhersagen aus [!INCLUDE[tsql](../../includes/tsql-md.md)] mithilfe von gespeicherten Prozeduren auf.

## <a name="prerequisites"></a>Voraussetzungen

Alle Aufgaben können mithilfe von gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ausgeführt werden.

Für dieses Tutorial sollten Sie sich mit grundlegenden Datenbankvorgängen auskennen, wie z. B. dem Erstellen von Datenbanken und Tabellen, dem Importieren von Daten und dem Schreiben von SQL-Abfragen. Kenntnisse im Umgang mit R sind nicht erforderlich. Daher wird der gesamte R-Code bereitgestellt. 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) oder [SQL Server Machine Learning Services mit aktiviertem R](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [R-Bibliotheken](../package-management/r-package-information.md)

+ [Berechtigungen](../security/user-permission.md)

+ [Demodatenbank für Taxifahrten in New York City](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Untersuchen und Visualisieren von Daten mithilfe von R-Funktionen in gespeicherten Prozeduren](../tutorials/sqldev-explore-and-visualize-the-data.md)
