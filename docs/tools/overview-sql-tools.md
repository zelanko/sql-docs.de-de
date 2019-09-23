---
title: SQL-Abfrage-und-Verwaltungs Tools für SQL Server, Azure SQL (Azure SQL-Datenbanken, verwaltete Azure SQL-Instanzen, virtuelle SQL-Computer) und Azure SQL-Data Warehouse | Microsoft-Dokumentation
description: SQL-Abfrage-und-Verwaltungs Tools für SQL Server, Azure SQL (Azure SQL-Datenbank, verwaltete Azure SQL-Instanz, virtuelle SQL-Computer) und Azure SQL-Data Warehouse
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 09/11/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 9c5262dfc610e62f0782b0cc6c8fe523d94d0730
ms.sourcegitcommit: c0fd28306a3b42895c2ab673734fbae2b56f9291
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096876"
---
# <a name="sql-query-and-management-tools-for-sql-server"></a>SQL-Abfrage-und-Verwaltungs Tools für SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Zum Verwalten (Abfragen, überwachen usw.) Ihrer Datenbank benötigen Sie ein Tool. Während Ihre Datenbanken in der Cloud, unter Windows oder [Linux](../linux/sql-server-linux-overview.md)ausgeführt werden können, muss das Tool nicht auf derselben Plattform wie die Datenbank ausgeführt werden.

Es sind viele Datenbanktools verfügbar. dieser Artikel enthält Beschreibungen und Verweise auf einige der verfügbaren Tools für die Arbeit mit SQL-Datenbanken. Wenn Sie Hilfe bei der Entscheidung benötigen, welches Tool Sie benötigen, finden Sie weitere Informationen unter [welches Tool soll ich verwenden?](#which-tool-should-i-choose).

Wenn Sie weitere Informationen und ein Tool herunterladen möchten, wählen Sie in den folgenden Tabellen die Links in der Spalte Tool aus. Informationen zum Herunterladen SQL Server finden Sie unter [Install SQL Server](../database-engine/install-windows/install-sql-server.md).

## <a name="gui-tools-to-manage-databases"></a>GUI-Tools zum Verwalten von Datenbanken

Die folgenden Tools stellen eine grafische Benutzeroberfläche (GUI) bereit:

| Tool | und Beschreibung | Läuft auf |
|:--|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)]ist ein kostenloses, leichtes Tool zum Verwalten von Datenbanken, wo Sie ausgeführt werden. Diese Vorschauversion bietet Features für die Datenbankverwaltung, einschließlich eines erweiterten Transact-SQL-Editors und anpassbarer Einblicke in den Betriebszustand Ihrer Datenbanken. | **[!INCLUDE[name-sos](../includes/name-sos-short.md)] kann unter Windows, macOS und Linux ausgeführt werden**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Verwenden Sie SQL Server Management Studio (SSMS), um Ihre SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse abzufragen, zu entwerfen und zu verwalten. | **SSMS wird unter Windows ausgeführt**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Verwandeln Sie Visual Studio in eine leistungsstarke Entwicklungsumgebung für SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse.| **SSDT wird unter Windows ausgeführt**.|
| [Visual Studio Code](https://code.visualstudio.com/)| Installieren Sie nach der Installation von Visual Studio Code die [MSSQL-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) zum Entwickeln von Microsoft SQL Server, Azure SQL-Datenbank und SQL Data Warehouse.| **Visual Studio Code kann unter Windows, macOS und Linux**ausgeführt werden.|

## <a name="command-line-tools-to-manage-databases"></a>Befehlszeilen Tools zum Verwalten von Datenbanken

Im folgenden finden Sie die wichtigsten Befehlszeilen Tools:

| Tool | und Beschreibung | Läuft auf |
|:--|:--|:--|
|[**mssql-cli (Vorschauversion)** ](mssql-cli.md)|**MSSQL-CLI** ist ein interaktives Befehlszeilen Tool zum Abfragen von SQL Server. | Windows, macOS und Linux|
| [**sqlpackage**](sqlpackage.md) |**Sqlpackage** ist ein Befehlszeilenprogramm, mit dem mehrere Daten Bank Entwicklungsaufgaben automatisiert werden. die macOS-und Linux-Versionen von Sqlpackage befinden sich derzeit in der Vorschau Phase. | Windows, macOS und Linux|
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** bietet Cmdlets für die Arbeit mit SQL.| Windows, macOS und Linux|
| [**sqlcmd**](sqlcmd-utility.md) |mit dem Hilfsprogramm **sqlcmd** können Sie an der Eingabeaufforderung Transact-SQL-Anweisungen, System Prozeduren und Skriptdateien eingeben. | Windows, macOS und Linux|
|[**bcp**](https://docs.microsoft.com/sql/tools/bcp-utility?view=sql-server-2014)|Mit dem Hilfsprogramm **bcp**(**B**ulk **C**opy **P**rogram) werden Daten per Massenvorgang zwischen einer Instanz von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und einer Datendatei in einem benutzerdefinierten Format kopiert.|Windows, macOS und Linux|
|[**MSSQL-Scripter (Vorschau)** ](https://github.com/Microsoft/mssql-scripter)|**MSSQL-Scripter** ist eine Befehlszeilen Darstellung mit mehreren Plattformen für die Skripterstellung SQL Server-Datenbanken|Windows, macOS und Linux|
|[**mssql-conf**](../linux/sql-server-linux-configure-mssql-conf.md)|**MSSQL-conf** konfiguriert SQL Server, die unter Linux ausgeführt werden.|Linux|

## <a name="which-tool-should-i-choose"></a>Welches Tool sollte ich auswählen?

- Möchten Sie eine SQL Server Instanz oder-Datenbank in einem einfachen Editor unter Windows, Linux oder Mac verwalten? Verwenden Sie in diesem Fall [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md).
- Möchten Sie eine SQL Server-Instanz oder-Datenbank unter Windows mit vollständiger GUI-Unterstützung verwalten? Verwenden Sie in diesem Fall [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).
- Möchten Sie Datenbankcode erstellen oder verwalten, einschließlich Validierung der Kompilierzeit, Umgestaltung und Designer Unterstützung unter Windows? Verwenden Sie in diesem Fall [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md).
- Möchten Sie SQL Server mit einem Befehlszeilen Tool Abfragen, das IntelliSense, Syntax-hoch Beleuchtung und vieles mehr bietet? [MSSQL-CLI](mssql-cli.md) auswählen
- Möchten Sie T-SQL-Skripts in einem einfachen Editor unter Windows, Linux oder Mac schreiben? Wählen Sie [Visual Studio Code](https://code.visualstudio.com/) und die [MSSQL-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) aus.

## <a name="additional-tools"></a>Weitere Tools

| Tool | und Beschreibung |
|:--|:--|
| [Configuration Manager](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Verwenden Sie SQL Server-Konfigurations-Manager, um SQL Server Dienste zu konfigurieren und die Netzwerk Konnektivität zu konfigurieren. Configuration Manager unter Windows ausgeführt|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | Verwenden Sie SQL Server Migration Assistant zur Automatisierung der Datenbankmigration von Microsoft Access, DB2, MySQL, Oracle und Sybase zu SQL Server.|
| [Assistent für Datenbankexperimente](../dea/database-experimentation-assistant-overview.md) | Verwenden Sie Assistent für Datenbankexperimente, um eine Zielversion von SQL für eine bestimmte Arbeitsauslastung auszuwerten. |
| [Distributed Replay](../tools/distributed-replay/install-distributed-replay-overview.md) | Verwenden Sie die Distributed Replay Funktion, um die Auswirkung zukünftiger SQL Server Upgrades zu bewerten. Verwenden Sie Distributed Replay auch, um die Auswirkungen von Hardware-und Betriebssystem Upgrades sowie SQL Server Optimierung zu bewerten. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Das Hilfsprogramm ssbdiagnose meldet Probleme in Service Broker Konversationen oder der Konfiguration von Service Broker Services. |

Weitere Tools, die auf dieser Seite nicht erwähnt werden, finden Sie unter SQL-Eingabeaufforderungs- [Hilfsprogramme](command-prompt-utility-reference-database-engine.md).