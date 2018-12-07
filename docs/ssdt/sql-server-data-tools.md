---
title: SQL Server Data Tools | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.errortask.generichelp
ms.assetid: 5f08f15a-851d-4026-a557-28b3c6492efe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 77d24c998c17e9fb265defa252b37b955e451bda
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52414667"
---
# <a name="sql-server-data-tools"></a>SQL Server Datatools
SQL Server Data Tools (SSDT) ermöglichen durch die Einführung eines universellen deklarativen Modells, das sämtliche Phasen der Datenbankentwicklung in Visual Studio umfasst, eine neue Art der Datenbankentwicklung. Mit den Transact\-SQL-Entwurfsfunktionen von SSDT können Sie Datenbanken erstellen, debuggen, verwalten und umgestalten. Dies gilt unabhängig davon, ob Sie mit einem Datenbankprojekt oder direkt mit einer verbundenen lokalen oder nicht lokalen Datenbankinstanz arbeiten.  
  
Entwickler haben Zugriff auf vertraute Visual Studio-Tools für die Datenbankentwicklung. Die Tools umfassen: Codenavigation, IntelliSense, Sprachunterstützung entsprechend den verfügbaren Funktionen für C# und Visual Basic, plattformspezifische Überprüfung, Debugging und deklaratives Bearbeiten im Transact\-SQL-Editor. SSDT bietet außerdem einen visuellen Tabellen-Designer zum Erstellen und Bearbeiten von Tabellen in Datenbankprojekten oder verbundene Datenbankinstanzen. Während Sie in einer teambasierten Umgebung an den Datenbankprojekten arbeiten, können Sie die Versionskontrolle für alle Dateien nutzen. Sie können das Projekt auf allen unterstützten SQL-Plattformen veröffentlichen, einschließlich SQL-Datenbank und SQL Server. Die Plattformüberprüfungsfunktion von SSDT stellt sicher, dass die Skripts ordnungsgemäß auf dem von Ihnen festgelegten Ziel ausgeführt werden.  
  
Der SQL Server-Objekt-Explorer in Visual Studio bietet eine Ansicht Ihrer Datenbankobjekte ähnlich der in SQL Server Management Studio. Mit dem SQL Server-Objekt-Explorer können Sie einfache Datenbankverwaltungs- und Entwurfsarbeiten ausführen. Sie können auch auf einfache Weise Tabellen, gespeicherte Prozeduren, Typen und Funktionen erstellen, bearbeiten, umbenennen und löschen. Darüber hinaus ist es über Kontextmenüs möglich, direkt über den SQL Server-Objekt-Explorer Tabellendaten zu bearbeiten, Schemas zu vergleichen oder Abfragen auszuführen.  
  
In den folgenden Themen und Abschnitten wird erläutert, wie SSDT zur Datenbankentwicklung beiträgt. Anhand exemplarischer Vorgehensweisen werden Sie durch die Schritte zur Fertigstellung des Datenbankprojekts geführt. Diese im Stil eines Lernprogramms beschriebenen und nacheinander ausgeführten Aufgaben sind im Kontext von Northwind Traders angesiedelt, einer fiktiven, weltweit tätigen Import- und Exportfirma für Lebensmittel und Feinkost.  
  
|Themen/Abschnitt|und Beschreibung|  
|-------------------|---------------|  
|[Projektorientierte Offlinedatenbankentwicklung](../ssdt/project-oriented-offline-database-development.md)|In den Themen dieses Abschnitts werden die SQL Server Data Tools-Funktionen zum Erstellen, Debuggen und Veröffentlichen von Datenbankprojekten beschrieben.|  
|[Projektorientierte Datenbankentwicklung mit Befehlszeilentools](../ssdt/project-oriented-database-development-using-command-line-tools.md)|In den Themen dieses Abschnitts werden die Befehlszeilentools beschrieben, die eine Reihe von Szenarien für die projektorientierte Datenbankentwicklung ermöglichen.|  
|[Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md)|In den Themen dieses Abschnitts werden die SQL Server Data Tools-Funktionen zum Entwerfen und Abfragen einer verbundenen Datenbank beschrieben.|  
|[Vergleichen und Synchronisieren von Daten in einer oder mehreren Tabellen anhand von Daten aus einer Verweisdatenbank](../ssdt/compare-and-synchronize-data-in-tables-with-data-in-reference-database.md)|Erörtert die Möglichkeiten zum Vergleich von Daten in einer Quelldatenbank und einer Zieldatenbank, gibt die Werte an, die übereinstimmen sollen, und aktualisiert dann das Ziel, um die Datenbanken zu synchronisieren, oder exportiert das Aktualisierungsskript in den Transact\-SQL-Editor oder eine Datei.|  
|[Verwenden des Transact-SQL-Editors zum Bearbeiten und Ausführen von Skripts](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)|In den Themen dieses Abschnitts wird die Verwendung des Transact\-SQL-Editors beschrieben, der vielfältige Funktionen zum Bearbeiten und Debuggen von Skripts bereitstellt.|  
|[Verwalten von Tabellen, Beziehungen und Beheben von Fehlern](../ssdt/manage-tables-relationships-and-fix-errors.md)|Anhand der Themen in diesem Abschnitt wird beschrieben, wie Sie:<br /><br />– den neuen Tabellen-Designer verwenden, um Tabellen zu entwerfen und Tabellenbeziehungen zu verwalten.<br />– allgemeine Syntax- oder Semantikfehler beheben.|  
|[Überprüfen des Datenbankcodes mithilfe von SQL Server-Komponententests](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)|Erläutert die Verwendung von SQL Server-Komponententests, um einen Baselinezustand für die Datenbank festzulegen und anschließend alle nachfolgenden Änderungen zu überprüfen, die an Datenbankobjekten vorgenommen werden.|  
|[Erweitern der Datenbankfunktionen](../ssdt/extending-the-database-features.md)|Mithilfe von Funktionserweiterungen können Sie Funktionen, wie etwa Komponententests und Datenbankcodeanalyse, selbst erweitern.|  
|[Erforderliche Berechtigungen für SQL Server Data Tools](../ssdt/required-permissions-for-sql-server-data-tools.md)|Behandelt die erforderliche Zugriffsberechtigung für die Verwendung von SQL Server Data Tools.|  
|[DAC-Frameworkkompatibilität](../ssdt/dac-framework-compatibility.md)|Beschreibt Kompatibilitätsprobleme mit dem DAC-Framework.|  
  

  
