---
title: Unterstützte Versions- und Editionsupgrades in SQL Server 2016 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server], adding to existing installations
- versions [SQL Server], upgrading
- upgrading SQL Server, upgrades supported
- cross-language support
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4a245aab71292e1482bd5a17bd32a27bded640ab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62775220"
---
# <a name="supported-version-and-edition-upgrades"></a>Unterstützte Versions- und Editionsupgrades
  Sie können ein Upgrade von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]und [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]ausführen. In diesem Thema werden die unterstützten Upgradepfade von diesen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Versionen sowie die unterstützten Editionsupgrades für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]aufgeführt.  
  
## <a name="pre-upgrade-checklist"></a>Prüfliste vor dem Upgrade  
  
-   Bevor eine Edition von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] auf eine andere Edition aktualisiert wird, sollten Sie überprüfen, ob die derzeit verwendete Funktionalität in der Edition, die Ziel des Upgrades ist, unterstützt wird.  
  
-   Aktivieren Sie vor dem Upgrade auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Windows-Authentifizierung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent, und überprüfen Sie die erforderliche Standardkonfiguration. Dabei muss das Konto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts Mitglied der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Gruppe der Systemadministratoren sein.  
  
-   Um auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]aktualisieren zu können, müssen Sie ein unterstütztes Betriebssystem ausführen. Weitere Informationen finden Sie unter [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Das Upgrade wird blockiert, wenn noch ein Neustart aussteht.  
  
-   Das Upgrade wird blockiert, wenn der Windows Installer-Dienst nicht ausgeführt wird.  
  
## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien  
  
-   Versionsübergreifende Instanzen von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] werden nicht unterstützt. Die Versionsnummern der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]- und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten innerhalb einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]müssen identisch sein.  
  
-   Ein plattformübergreifendes Upgrade wird nicht unterstützt. Sie können keine 32-Bit-Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup auf systemeigenes 64-Bit aktualisieren. Sie können jedoch Datenbanken von einer 32-Bit-Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sichern oder trennen und sie in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (64-Bit) wiederherstellen oder anfügen, wenn die Datenbanken nicht in der Replikation veröffentlicht sind. Sie müssen alle Anmeldenamen und anderen Benutzerobjekte in den Systemdatenbanken „master“, „msdb“ und „model“ wiederherstellen.  
  
-   Sie können während des Upgrades der vorhandenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]keine neuen Funktionen hinzufügen. Nachdem Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aktualisiert haben, können Sie Funktionen mit dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Setup hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Funktionen zu einer Instanz von SQL Server 2014 &#40;Setup&#41;](add-features-to-an-instance-of-sql-server-setup.md).  
  
-   Failovercluster werden im WOW-Modus nicht unterstützt.  
  
-   Upgrades von einer Evaluation Edition einer früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version werden nicht unterstützt.  
  
## <a name="upgrades-from-earlier-versions-to-sssql14"></a>Upgrades von früheren Versionen auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
> [!NOTE]  
>  Die Unterstützung für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] wird im nächsten Abschnitt "[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Unterstützung für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]" ausführlich erläutert.  
  
-   32-Bit-Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf dem 32-Bit-Subsystem (WOW64) eines 64-Bit-Servers aktualisiert werden.  
  
-   64-Bit-Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können nur auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 64-Bit-Server aktualisiert werden.  
  
> [!NOTE]  
>  Wenn Sie von einer früheren Version der [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise-Edition auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisieren, wählen Sie zwischen "Enterprise Edition: Core-basierte Lizenzierung" und "Enterprise Edition" aus. Diese Enterprise Editionen unterscheiden sich nur im Hinblick auf den Lizenzierungsmodus und die maximale Anzahl unterstützter Cores. Weitere Informationen finden Sie unter [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterstützt ein Upgrade von folgenden Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 oder höher  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 oder höher  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 oder höher  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 oder höher  
  
 In der nachfolgenden Tabelle sind die unterstützten Szenarien für das Upgrade von früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]aufgeführt.  
  
|Upgrade von|Unterstützter Upgradepfad|  
|------------------|----------------------------|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Enterprise|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Developer|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Entwickler|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Standard|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Workgroup|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Express,<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Express with Tools und<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Express with Advanced Services|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Enterprise|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Developer|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Entwickler|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Standard|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Small Business|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Web|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Workgroup|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Express,<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Express with Tools und<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Express with Advanced Services|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Datacenter|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Enterprise|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Developer|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Entwickler|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Small Business|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Standard|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Web|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Workgroup|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Express,<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Express with Tools und<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Express with Advanced Services|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Enterprise|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Developer|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Entwickler|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Standard|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Web|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Express,<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Express with Tools und<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Express Management Studio und<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Express with Advanced Services|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Business Intelligence|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
  
### <a name="sssql14-support-for-ssversion2005"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]-Unterstützung für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
 In diesem Abschnitt wird die [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Unterstützung für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]erläutert. In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]können Sie die folgenden Schritte ausführen:  
  
-   Aktualisieren einer [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Instanz der Datenbank-Engine auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , indem Sie das [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Setup mithilfe des Installations-Assistenten oder von der Eingabeaufforderung ausführen.  
  
-   Anfügen einer [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Datenbank (MDF-/LDF-Dateien) an eine [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]-Instanz der Datenbank-Engine.  
  
-   Wiederherstellen einer [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Datenbank auf einer [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]-Instanz der Datenbank-Engine mithilfe einer Sicherung.  
  
-   Aktualisieren eines [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] -Pakets auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Ausführen von Paketen mithilfe automatischer direkter Upgrades.  
  
-   Aktualisieren von [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] durch Ausführen von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Setup.  
  
-   Sichern eines [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] -Cubes und Wiederherstellen für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
-   Aktualisieren von [!INCLUDE[ssRSversion2005](../../includes/ssrsversion2005-md.md)] auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] durch Ausführen von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Setup.  
  
-   Stellen Sie eine Verbindung zu [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]über [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 2014 her.  
  
 Wenn für eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Datenbank ein Upgrade auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ausgeführt wird, ändern sich der Datenbank-Kompatibilitätsgrad von 90 in 100. (In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]sind gültige Werte für den Datenbank-Kompatibilitäts Grad 100, 110 und 120.) [ALTER DATABASE-Kompatibilitäts Grad &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) erläutert, wie sich die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Änderung des Kompatibilitäts Grad auf Anwendungen auswirken könnte.  
  
 Szenarien, die in der Liste nicht aufgeführt sind, werden nicht unterstützt. Das gilt z. B. für:  
  
-   Installieren von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] auf demselben Computer (parallel).  
  
-   Verwenden einer [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Instanz als Mitglied der Replikationstopologie, die eine [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Instanz umfasst.  
  
-   Konfigurieren der Datenbankspiegelung zwischen [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] - und [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Instanzen.  
  
-   Sichern des Transaktionsprotokolls mit Protokollversand zwischen [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] - und [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Instanzen.  
  
-   Konfigurieren von Verbindungsservern zwischen [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] - und [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Instanzen.  
  
-   Verwalten einer [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Instanz von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio aus.  
  
-   Anfügen eines [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] -Cubes in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio.  
  
-   Herstellen einer Verbindung mit [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio aus.  
  
-   Verwalten eines [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] -Diensts von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio aus.  
  
-   Unterstützung von benutzerdefinierten Integration Services-Drittanbieterkomponenten für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] sowie Ausführen und Upgrade der Komponenten.  
  
## <a name="sssql14-edition-upgrade"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Editionsupgrade  
 In der folgenden Tabelle sind die unterstützten Szenarien für das Editionsupgrade in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]aufgeführt.  
  
 Schritt-für-Schritt-Anweisungen zum Ausführen eines Editions Upgrades finden [Sie unter Aktualisieren auf eine andere Edition von SQL Server 2014 &#40;Setup&#41;](upgrade-to-a-different-edition-of-sql-server-setup.md).  
  
|Upgrade von|Upgrade auf|  
|------------------|----------------|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]Enterprise (Server + CAL und Core) <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Server+CAL- oder Core-Lizenz)|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]Evaluation Enterprise <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Server+CAL- oder Core-Lizenz)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Entwickler<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> Upgrades von Enterprise Evaluation (kostenlose Edition) auf eine kostenpflichtige Edition werden für eigenständige Installationen, für gruppierte Installationen jedoch nicht unterstützt.|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]Standard <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Server+CAL- oder Core-Lizenz)|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]Entwickler <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Server+CAL- oder Core-Lizenz)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Server+CAL- oder Core-Lizenz)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]Express <sup>1</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Server+CAL- oder Core-Lizenz)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Entwickler<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
  
 Außerdem können Sie ein Editionsupgrade zwischen [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Server+CAL-Lizenz) und [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Core-Lizenz) ausführen:  
  
|Editionsupgrade von|Editionsupgrade auf|  
|--------------------------|------------------------|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]Enterprise (Server + CAL-Lizenz) <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Core-Lizenz)|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Core-Lizenz)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Server+CAL-Lizenz)|  
  
 <sup>1</sup> gilt auch für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express with Tools und [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express with Advanced Services.  
  
 <sup>2</sup> das Ändern der Edition eines [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Failoverclusters ist beschränkt. Die folgenden Szenarien werden bei [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Failoverclustern nicht unterstützt:  
  
-   SQL Server 2014 Enterprise auf SQL Server 2014 Developer, Standard oder Enterprise Evaluation.  
  
-   SQL Server 2014 Developer auf SQL Server 2014 Standard oder Enterprise Evaluation.  
  
-   SQL Server 2014 Standard auf SQL Server 2014 Enterprise Evaluation.  
  
-   SQL Server 2014 Enterprise Evaluation auf SQL Server 2014 Standard.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von den-Editionen unterstützte Funktionen SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Hardware-und Software Anforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [Upgrade auf SQL Server 2014](upgrade-sql-server.md)   
 [Verwenden von Upgrade Advisor zur Vorbereitung auf Upgrades](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
  
