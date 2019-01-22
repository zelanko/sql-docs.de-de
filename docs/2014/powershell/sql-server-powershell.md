---
title: SQL Server-PowerShell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 89b70725-bbe7-4ffe-a27d-2a40005a97e7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: acfa87245449566c1f91b447910f5194eda192b0
ms.sourcegitcommit: 480961f14405dc0b096aa8009855dc5a2964f177
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2019
ms.locfileid: "54420075"
---
# <a name="sql-server-powershell"></a>SQL Server-PowerShell
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] unterstützt Windows PowerShell, ein leistungsstarkes Skriptshell, mit der Administratoren und Entwickler die Serververwaltung und die Anwendungsbereitstellung automatisieren können. Die Windows PowerShell-Sprache unterstützt komplexere Logik als [!INCLUDE[tsql](../includes/tsql-md.md)] -Skripts und ermöglicht [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Administratoren dadurch die Erstellung stabiler Verwaltungsskripts. Windows PowerShell-Skripts können außerdem dazu verwendet werden, andere [!INCLUDE[msCoName](../includes/msconame-md.md)] -Serverprodukte zu verwalten. So steht Administratoren eine serverübergreifende allgemeine Skriptsprache zur Verfügung.  
  
## <a name="sql-server-powershell-components"></a>SQL Server PowerShell-Komponenten  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stellt das Windows PowerShell-Modul `sqlps` bereit, mit dem die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Komponenten in eine Windows PowerShell 2.0-Umgebung oder ein Windows PowerShell 2.0-Skript importiert werden. Mit dem `sqlps`-Modul werden zwei Windows PowerShell-Snap-Ins geladen, mit denen folgende Elemente implementiert werden können:  
  
-   Ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter, der einen einfachen Navigationsmechanismus aktiviert, der Dateisystempfaden ähnelt. Sie können Dateisystempfaden ähnelnde Pfade erstellen, in denen das Laufwerk einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object-Modell zugeordnet ist, und deren Knoten auf Objektmodellklassen basieren. Sie können dann vertraute Befehle wie **cd** und **dir** verwenden, um auf den Pfaden zu navigieren, auf ähnliche Weise, wie Sie in einem Eingabeaufforderungsfenster in Ordnern navigieren. Mit anderen Befehlen, wie **ren** oder **del**, können Sie Aktionen für die Knoten im Pfad ausführen.  
  
-   Ein Satz von Cmdlets, bei denen es sich um Befehle handelt, mit denen in Windows PowerShell-Skripts eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Aktion angegeben wird. Mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Cmdlets unterstützen Aktionen wie das Ausführen eines **sqlcmd** -Skripts, das [!INCLUDE[tsql](../includes/tsql-md.md)] - oder XQuery-Anweisungen enthält.  
  
 Informationen zu Windows PowerShell finden Sie unter [Erste Schritte mit Windows PowerShell](https://msdn.microsoft.com/library/hh857337.aspx).  
  
## <a name="sql-server-versions"></a>SQL Server-Versionen  
 Die [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] PowerShell-Komponenten können zur Verwaltung von Instanzen von [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] oder höher verwendet werden. Instanzen von [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] müssen SP2 oder höher ausführen. Instanzen von [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] müssen SP4 oder höher ausführen. Wenn die [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] PowerShell-Komponenten mit früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verwendet werden, sind sie auf die in diesen Versionen verfügbaren Funktionen beschränkt.  
  
## <a name="sql-server-powershell-tasks"></a>SQL Server PowerShell-Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt den bevorzugten Mechanismus zum Ausführen der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Komponenten zum Öffnen einer PowerShell-Sitzung und Laden des `sqlps`-Moduls. Das `sqlps`-Modul lädt in den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Anbieter und die Cmdlets und die vom Anbieter und den Cmdlets verwendeten SQL Server Management Object-Assemblys (SMO).|[Importieren des SQLPS-Moduls](../database-engine/import-the-sqlps-module.md)|  
|Beschreibt, wie nur die SMO-Assemblys ohne den Anbieter oder die Cmdlets geladen werden.|[Laden der SMO-Assemblys in Windows PowerShell](load-the-smo-assemblies-in-windows-powershell.md)|  
|Beschreibt, wie eine Windows-PowerShell-Sitzungen durch Rechtsklick auf einen Knoten im **Objekt-Explorer**ausgeführt wird. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Startet eine Windows PowerShell-Sitzung, lädt die `sqlps` -Modul, und legt den Pfad des SQL Server-Anbieters auf das ausgewählte Objekt fest.|[Ausführen von Windows PowerShell über SQL Server Management Studio](run-windows-powershell-from-sql-server-management-studio.md)|  
|Beschreibt, wie Auftragsschritte des SQL Server-Agents erstellt werden, die ein Windows PowerShell-Skript ausführen. Die Aufträge können dann zum Ausführen zu bestimmten Zeitpunkten oder als Reaktion auf Ereignisse geplant werden.|[Ausführen von Windows PowerShell-Schritten in SQL Server-Agent](run-windows-powershell-steps-in-sql-server-agent.md)|  
|Beschreibt, wie der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter zum Navigieren in einer Hierarchie von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekten verwendet wird.|[SQL Server PowerShell-Anbieter](sql-server-powershell-provider.md)|  
|Beschreibt, wie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Cmdlets verwendet werden, die [!INCLUDE[ssDE](../includes/ssde-md.md)] -Aktionen wie Ausführen eines [!INCLUDE[tsql](../includes/tsql-md.md)] -Skripts angeben.|[Verwenden der Datenbank-Engine-Cmdlets](../database-engine/use-the-database-engine-cmdlets.md)|  
|Beschreibt, wie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Begrenzungsbezeichner angegeben werden, die von Windows PowerShell nicht unterstützte Zeichen enthalten.|[SQL Server-Bezeichnern in PowerShell](sql-server-identifiers-in-powershell.md)|  
|Beschreibt, wie SQL Server-Authentifizierungsverbindungen hergestellt werden. Standardmäßig verwenden die SQL Server PowerShell-Komponenten Windows-Authentifizierungsverbindungen mithilfe der Windows-Anmeldeinformationen für den Prozess, der Windows PowerShell ausführt.|[Verwalten der Authentifizierung in PowerShell der Datenbank-Engine](manage-authentication-in-database-engine-powershell.md)|  
|Beschreibt, wie vom SQL Server PowerShell-Anbieter implementierte Variablen verwendet werden, um die Anzahl der bei Verwendung der Windows PowerShell-Befehlszeilenergänzung aufgeführten Objekte zu steuern. Dies ist vor allem beim Arbeiten an Datenbanken mit einer großen Anzahl von Objekten nützlich.|[Verwalten der Befehlszeilenergänzung &#40;SQL Server PowerShell&#41;](manage-tab-completion-sql-server-powershell.md)|  
|Beschreibt, wie mit Get-Help Informationen zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Komponenten in der Windows PowerShell-Umgebung abgerufen werden.|[Aufrufen der SQL Server PowerShell-Hilfe](../database-engine/get-help-sql-server-powershell.md)|  
  
  
