---
title: Übersicht über SQL-Tools
description: SQL-Tools für Abfragen und Verwaltung für SQL Server, Azure SQL (Azure SQL-Datenbank, verwaltete Azure SQL-Instanz, SQL-VMs) und Azure SQL Data Warehouse.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/06/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: f4aaea790cf1e308b0675792b110ed129a55ed97
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "76516261"
---
# <a name="sql-tools-overview"></a>Übersicht über SQL-Tools

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Zum Verwalten Ihrer Datenbank benötigen Sie ein Tool. Unabhängig davon, ob Ihre Datenbanken in der Cloud, unter Windows, unter macOS oder unter [Linux](../linux/sql-server-linux-overview.md) ausgeführt werden – Ihr Tool muss nicht auf derselben Plattform ausgeführt werden wie die Datenbank.

Sehen Sie sich die Links zu den verschiedenen SQL-Tools in den folgenden Tabellen an.

> [!Note]
> Informationen zum Herunterladen von SQL Server finden Sie unter [Installieren von SQL Server](../database-engine/install-windows/install-sql-server.md).

## <a name="recommended-tools"></a>Empfohlene Tools

Die folgenden Tools stellen eine grafische Benutzeroberfläche (Graphical User Interface, GUI) bereit.

| Tool | Beschreibung | Betriebssystem |
|:--|:--|:--|
| [ **![Bild für ADS](../tools/media/overview-sql-tools/azure-data-studio.svg)</br></br>Azure Data Studio**](../azure-data-studio/download.md) | Ein einfacher Editor, in dem Sie SQL-Abfragen bedarfsgesteuert ausführen und Ergebnisse im Text-, JSON- oder Excel-Format anzeigen und speichern können. Bearbeiten Sie Daten, organisieren Sie Ihre bevorzugten Datenbankverbindungen und durchsuchen Sie Datenbankobjekte in einem vertrauten Objektbrowser. | **Windows</br>macOS</br>Linux** |
| [ **![Bild für SSMS](../tools/media/overview-sql-tools/ssms.svg)</br></br>SQL Server Management Studio (SSMS)** ](../ssms/download-sql-server-management-studio-ssms.md) | Verwalten Sie eine SQL Server-Instanz oder -Datenbank mit vollständiger GUI-Unterstützung. Sie können auf alle Komponenten von SQL Server, Azure SQL-Datenbank und SQL Data Warehouse zugreifen und diese konfigurieren, verwalten und entwickeln. SSMS bietet ein einzelnes, umfassendes Hilfsprogramm, das eine Vielzahl grafischer Tools mit einer Reihe von Skript-Editoren mit großem Funktionsumfang kombiniert, um Entwicklern und Datenbankadministratoren mit unterschiedlichem Kenntnisstand den Zugriff auf SQL zu ermöglichen. | **Windows** |
| [ **![Bild für SSDT](../tools/media/overview-sql-tools/ssdt.svg)</br>SQL Server Data Tools (SSDT)** ](../ssdt/download-sql-server-data-tools-ssdt.md) | Ein modernes Entwicklungstool für die Erstellung von relationalen SQL Server-Datenbanken, Azure SQL-Datenbanken, Analysis Services-Datenmodellen (AS), Integration Services-Paketen (IS) und Reporting Services-Berichten (RS). Mit SSDT können Sie alle Arten von SQL Server-Inhalten genauso einfach entwerfen und bereitstellen wie eine Anwendung in **[Visual Studio](https://visualstudio.microsoft.com/downloads/)** . | **Windows** |
| [ **![Bild für VS Code](../tools/media/overview-sql-tools/visual-studio-code.svg)</br></br>Visual Studio Code**](https://code.visualstudio.com/) | Die **[mssql-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)** für Visual Studio Code ist die offizielle SQL Server-Erweiterung, die Verbindungen mit SQL Server unterstützt und umfassende Bearbeitungsfunktionen für T-SQL in Visual Studio Code bietet. Schreiben Sie T-SQL-Skripts in einem einfachen Editor. | **Windows</br>macOS</br>Linux** |

## <a name="command-line-tools"></a>Befehlszeilentools

Die folgenden Tools sind Befehlszeilentools.

| Tool | Beschreibung | Betriebssystem |
|:--|:--|:--|
|[**mssql-cli (Vorschauversion)** ](mssql-cli.md)|**mssql-cli** ist ein interaktives Befehlszeilentool zum Abfragen von SQL Server. Dieses Befehlszeilentool bietet zudem IntelliSense, Syntaxmarkierung und vieles mehr für SQL Server-Abfragen. | **Windows</br>macOS</br>Linux** |
| [**sqlpackage**](sqlpackage.md) |**sqlpackage** ist ein Befehlszeilen-Hilfsprogramm, das verschiedene Aufgaben bei der Datenbankentwicklung automatisiert. |**Windows</br>macOS</br>Linux** |
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** stellt Cmdlets für die Arbeit mit SQL bereit. | **Windows</br>macOS</br>Linux** |
| [**sqlcmd**](sqlcmd-utility.md) |Mit dem Hilfsprogramm **sqlcmd** können Sie Transact-SQL-Anweisungen, Systemprozeduren und Skriptdateien an der Eingabeaufforderung eingeben. | **Windows</br>macOS</br>Linux** |
|[**bcp**](bcp-utility.md)|Mit dem Hilfsprogramm **bcp** (**B**ulk **C**opy **P**rogram) werden Daten per Massenvorgang zwischen einer Instanz von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und einer Datendatei in einem benutzerdefinierten Format kopiert.| **Windows</br>macOS</br>Linux** |
|[**mssql-scripter (Vorschau)** ](https://github.com/Microsoft/mssql-scripter) | **mssql-scripter** ist eine Befehlszeilen-Benutzeroberfläche zur Skripterstellung für SQL Server-Datenbanken, die auf verschiedenen Plattformen ausgeführt werden kann. | **Windows</br>macOS</br>Linux** |
|[**mssql-conf**](../linux/sql-server-linux-configure-mssql-conf.md) | **mssql-conf** dient zur Konfiguration von SQL Server unter Linux. | **Linux** |

## <a name="migration-and-other-tools"></a>Migrationstools und andere Tools

Mit diesen Tools können Sie SQL-Datenbanken migrieren, konfigurieren und weitere Features bereitstellen.

| Tool | Beschreibung |
|:--|:--|
| **[Konfigurations-Manager](../tools/configuration-manager/sql-server-configuration-manager-help.md)** | Verwenden Sie den SQL Server-Konfigurations-Manager zum Konfigurieren von SQL Server-Diensten und Netzwerkkonnektivität. Der Konfigurations-Manager wird unter Windows ausgeführt.|
| **[SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md)** | Verwenden Sie SQL Server Migration Assistant zur Automatisierung der Datenbankmigration von Microsoft Access, DB2, MySQL, Oracle und Sybase zu SQL Server.|
| **[Assistent für Datenbankexperimente](../dea/database-experimentation-assistant-overview.md)** | Verwenden Sie den Assistenten für Datenbankexperimente, um eine SQL-Zielversion für eine bestimmte Workload zu evaluieren. |
| **[Distributed Replay](../tools/distributed-replay/install-distributed-replay-overview.md)** | Das Distributed Replay-Feature hilft Ihnen beim Bewerten der Auswirkungen zukünftiger SQL Server-Upgrades. Sie können Distributed Replay auch verwenden, um die Auswirkungen von Hardware- und Betriebssystemupgrades sowie von SQL Server-Optimierungen zu bewerten. |
| **[ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)** | Das Hilfsprogramm „ssbdiagnose“ meldet Probleme bei Service Broker-Konversationen oder der Konfiguration von Service Broker-Diensten. |

Wenn Sie andere Tools suchen, die auf dieser Seite nicht erwähnt werden, finden Sie weitere Informationen unter [SQL-Befehlszeilen-Hilfsprogramme](command-prompt-utility-reference-database-engine.md).