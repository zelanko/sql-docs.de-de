---
title: Datenbankdateien und Dateigruppen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], files
- filegroups [SQL Server]
- transaction logs [SQL Server], about
- transaction logs [SQL Server], files
- .mdf files
- data files [SQL Server]
- default filegroups
- files [SQL Server], about files and filegroups
- secondary files [SQL Server]
- log files [SQL Server]
- .ndf files
- files [SQL Server]
- .ldf files
- database files [SQL Server]
- databases [SQL Server], filegroups
- filegroups [SQL Server], types
- primary filegroups [SQL Server]
- user-defined filegroups [SQL Server]
- filegroups [SQL Server], about filegroups
- primary files [SQL Server]
- file types [SQL Server]
ms.assetid: 9ca11918-480d-4838-9198-cec221ef6ad0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3d75dee637a5579ca3f189e14333fbf9356623d0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52790112"
---
# <a name="database-files-and-filegroups"></a>Datenbankdateien und Dateigruppen
  Jede [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank verfügt über mindestens zwei Betriebssystemdateien: eine Datendatei und eine Protokolldatei. Datendateien enthalten Daten und Objekte wie z. B. Tabellen, Indizes, gespeicherte Prozeduren und Sichten. Protokolldateien enthalten die Informationen, die zum Wiederherstellen aller Transaktionen in der Datenbank erforderlich sind. Datendateien können für die Zuordnung und Verwaltung in Dateigruppen zusammengefasst werden.  
  
## <a name="database-files"></a>Datenbankdateien  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken verwenden drei Arten von Dateien, wie in der folgenden Tabelle gezeigt wird.  
  
|Datei|Description|  
|----------|-----------------|  
|Primär|Die primäre Datendatei enthält die Startinformationen für die Datenbank und verweist auf die anderen Dateien in der Datenbank. Benutzerdaten und -objekte können in dieser Datei oder in sekundären Datendateien gespeichert werden. Jede Datenbank verfügt über eine primäre Datendatei. Die empfohlene Dateinamenerweiterung für primäre Datendateien ist MDF.|  
|Secondary|Sekundäre Datendateien sind optional, benutzerdefiniert und speichern Benutzerdaten. Sekundäre Dateien können verwendet werden, um Daten auf mehrere Datenträger zu verteilen, indem jede Datei auf einem anderen Datenträger gespeichert wird. Wenn eine Datenbank die maximal zulässige Größe für eine einzige Datei überschreitet, haben Sie zudem die Möglichkeit, sekundäre Datendateien zu verwenden, sodass die Datenbank weiter vergrößert werden kann.<br /><br /> Die empfohlene Dateinamenerweiterung für sekundäre Datendateien ist NDF.|  
|Transaktionsprotokoll|Die Transaktionsprotokolldateien speichern die Protokollinformationen, die zum Wiederherstellen der Datenbank verwendet werden. Für jede Datenbank muss mindestens eine Protokolldatei vorhanden sein. Die empfohlene Dateinamenerweiterung für Transaktionsprotokolle ist LDF.|  
  
 Sie können z. B. eine einfache Datenbank ( **Sales** ), die eine primäre Datei umfasst, die alle Daten und Objekte enthält, und eine Protokolldatei erstellen, die die Transaktionsprotokollinformationen enthält. Es kann auch eine komplexere Datenbank namens **Orders** erstellt werden, die eine primäre Datei und fünf sekundäre Dateien enthält. Die Daten und Objekte in der Datenbank verteilen sich auf alle sechs Dateien, und die vier Protokolldateien enthalten die Transaktionsprotokollinformationen.  
  
 Standardmäßig werden die Daten und Transaktionsprotokolle auf dem gleichen Laufwerk und im gleichen Pfad gespeichert. Dadurch werden auch Systeme mit nur einem Datenträger berücksichtigt. Diese Vorgehensweise ist für Produktionsumgebungen jedoch  möglicherweise nicht optimal. Es wird empfohlen, Daten und Protokolldateien auf verschiedenen Datenträgern zu speichern.  
  
## <a name="filegroups"></a>Dateigruppen  
 Jede Datenbank besitzt eine primäre Dateigruppe. Diese Dateigruppe enthält die primäre Datendatei sowie ggf. alle sekundären Dateien, die nicht in anderen Dateigruppen gespeichert werden. Benutzerdefinierte Dateigruppen können erstellt werden, um Datendateien zum Zweck der Verwaltung, Datenzuordnung und -verteilung zu Gruppen zusammenzufassen.  
  
 Es können z. B. drei Dateien (Data1.ndf, Data2.ndf und Data3.ndf) auf drei unterschiedlichen Datenträgern erstellt und der **fgroup1**-Dateigruppe zugewiesen werden. Anschließend kann eine Tabelle speziell für die **fgroup1**-Dateigruppe erstellt werden. Abfragen nach Daten in der Tabelle werden über alle drei Datenträger verteilt, wodurch die Leistung gesteigert wird. Dieselbe Leistungssteigerung kann auch durch die Verwendung einer einzigen Datei erzielt werden, wenn diese auf einem RAID-Stripeset (Redundant Array of Independent Disks; redundantes Datenträgerarray) erstellt wird. Dateien und Dateigruppen ermöglichen Ihnen jedoch das problemlose Hinzufügen neuer Dateien zu neuen Datenträgern.  
  
 Alle Datendateien werden in den Dateigruppen gespeichert, die in der folgenden Tabelle aufgeführt werden.  
  
|Dateigruppe|Description|  
|---------------|-----------------|  
|Primär|Die Dateigruppe, die die primäre Datei enthält. Alle Systemtabellen werden der primären Dateigruppe zugewiesen.|  
|Benutzerdefinierte Dateigruppe|Jede Dateigruppe, die eigens durch den Benutzer erstellt wird, wenn dieser die Datenbank erstmals erstellt oder zu einem späteren Zeitpunkt ändert.|  
  
### <a name="default-filegroup"></a>Standarddateigruppe  
 Wenn Objekte in der Datenbank ohne Angabe einer Dateigruppe erstellt werden, werden sie der Standarddateigruppe zugewiesen. Zu jedem Zeitpunkt wird genau eine Dateigruppe zur Standarddateigruppe erklärt. Die Dateien in der Standarddateigruppe müssen groß genug sein, um alle neuen Objekte aufnehmen zu können, die nicht anderen Dateigruppen zugeordnet werden.  
  
 Die PRIMARY-Dateigruppe stellt die Standarddateigruppe dar, sofern diese nicht mithilfe der ALTER DATABASE-Anweisung geändert wird. Systemobjekte und -tabellen sind weiterhin der Dateigruppe PRIMARY (primäre Dateigruppe) und nicht der neuen Standarddateigruppe zugeordnet.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
 [ALTER DATABASE-Optionen für Dateien und Dateigruppen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)  
  
  
