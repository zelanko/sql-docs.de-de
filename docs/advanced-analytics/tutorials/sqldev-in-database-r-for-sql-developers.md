---
title: Tutorial für datenbankinterne Analysen mit R und SQL Server-Machine Learning | Microsoft-Dokumentation
description: Veranschaulicht, wie Sie R in SQL Server Einbetten von gespeicherten Prozeduren und T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 651e529bf0aa4cd4b4fab7e292e570dbb78e89d5
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461886"
---
# <a name="tutorial-learn-in-database-analytics-using-r-in-sql-server"></a>Tutorial: Erfahren Sie mehr in-Database-Analyse, die mithilfe von R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Tutorial für die SQL-Programmierer erhalten Sie praktische Erfahrungen mit der R-Sprache zum Erstellen und Bereitstellen ein Machine learning Lösung durch das wrapping von R-Code in gespeicherten Prozeduren.

Dieses Lernprogramm verwendet ein bekanntes öffentliches Dataset basierend auf der Fahrten in New York City Taxi. Um den Beispielcode schneller ausgeführt werden soll, haben wir einen repräsentativen Querschnitt von 1 % der Daten erstellt. Sie verwenden diese Daten, um ein binäres klassifizierungsmodell zu erstellen, das vorhersagt, ob eine bestimmte Fahrt ein Trinkgeld oder nicht, erhalten Sie wahrscheinlich basierend auf Spalten wie z. B. den Zeitpunkt der Tag, Entfernung und einstiegsort.

> [!NOTE]
> 
> Die gleiche Projektmappe ist in Python verfügbar. SQL Server 2017 ist erforderlich. Finden Sie unter [datenbankinterne Analysen für Python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Übersicht

Der Prozess zum Erstellen einer End-to-End-Lösung in der Regel besteht aus abrufen und Bereinigen von Daten, Durchsuchen von Daten und Feature-Engineering, Modelltraining und optimieren und schließlich Bereitstellung des Modells in der Produktion. Entwickeln und Testen von den tatsächlichen Code, wird am besten mit einer dedizierten Umgebung ausgeführt. Für R, das kann bedeuten, RStudio oder [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Nachdem die Lösung erstellt wurde, können Sie sie jedoch problemlos für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)] -gespeicherten Prozeduren in der vertrauten Umgebung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]bereitstellen.

- [Richten Sie die NYC Taxi-Datenbank](demo-data-nyctaxi-in-sql.md)

- [Lektion 1: Untersuchen und Visualisieren von Daten-Shapes und die Verteilung durch den Aufruf von R-Funktionen in gespeicherten Prozeduren](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Lektion 2: Erstellen von Datenfunktionen mit R in T-SQL-Funktionen](sqldev-create-data-features-using-t-sql.md)
  
- [Lektion 3: Trainieren Sie und speichern Sie eine R-Modells mithilfe von Funktionen und gespeicherten Prozeduren](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Lektion 4: Wrap R-Code in einer gespeicherten Prozedur für die operationalisierung](../tutorials/sqldev-operationalize-the-model.md). 
  Nachdem das Modell in der Datenbank gespeichert wurde, rufen Sie das Modell für die Vorhersage von [!INCLUDE[tsql](../../includes/tsql-md.md)] mit gespeicherten Prozeduren auf.

## <a name="prerequisites"></a>Erforderliche Komponenten

In diesem Tutorial wird davon ausgegangen, Vertrautheit mit grundlegender Datenbankvorgänge wie das Erstellen von Datenbanken und Tabellen, Importieren von Daten und SQL-Abfragen schreiben. Es wird nicht davon ausgegangen, dass Sie wissen, dass R. Daher wird der gesamte R-Code bereitgestellt. Ein erfahrener SQL-Programmierer können ein angegebenes PowerShell-Skripts, Beispieldaten auf GitHub und [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] für dieses Beispiel erforderlich. 

Vor Beginn des Tutorials an:

- Überprüfen, ob eine konfigurierte Instanz von [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) oder [SQL Server 2017 Machine Learning Services mit R aktiviert](../install/sql-machine-learning-services-windows-install.md#verify-installation). Darüber hinaus [bestätigen, dass Sie die R-Bibliotheken](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).
- Die Anmeldung, die Sie für dieses Tutorial verwenden, benötigen Berechtigungen zum Erstellen von Datenbanken und andere Objekte, zum Hochladen von Daten, auswählen von Daten und Ausführen von gespeicherten Prozeduren.

> [!NOTE]
> Es wird empfohlen, die Sie tun **nicht** verwenden [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] schreiben oder R-Code zu testen. Wenn der Code, den Sie in einer gespeicherten Prozedur einbetten, Probleme aufweist, sind die Informationen, die von der gespeicherten Prozedur zurückgegeben wird in der Regel nicht die Ursache des Fehlers zu ermitteln.
> 
> Für das Debuggen, es wird empfohlen, ein Tool wie z. B. [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], oder RStudio. Die in diesem Tutorial bereitgestellten R-Skripts wurden bereits mit herkömmlichen R-Tools entwickelt und debuggt.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Richten Sie die NYC Taxi-Datenbank](demo-data-nyctaxi-in-sql.md)