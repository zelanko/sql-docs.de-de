---
title: Unterstützte Versions- und Editionsupgrades in SQL Server 2019
description: In diesem Artikel finden Sie Informationen zu den unterstützten Versions- und Editionsupgrades in SQL Server 2019.
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server], adding to existing installations
- versions [SQL Server], upgrading
- upgrading SQL Server, upgrades supported
- cross-language support
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
author: cawrites
ms.author: chadam
monikerRange: '>=sql-server-2017'
ms.openlocfilehash: 6b92acc4dbf0b7b9418e382019f48ec1d1c6a36a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97463561"
---
# <a name="supported-version--edition-upgrades-sql-server-2019"></a>Unterstützte Versions- und Editionsupgrades in SQL Server 2019

[!INCLUDE [SQL Server -Windows Only](../../includes/applies-to-version/sql-windows-only.md)]
  
  Sie können ein Upgrade von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[sssql16-md](../../includes/sssql16-md.md)]und [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]ausführen. In diesem Artikel werden die unterstützten Upgradepfade von diesen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Versionen sowie die unterstützten Editionsupgrades für [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] aufgeführt.  
  
## <a name="pre-upgrade-checklist"></a>Prüfliste vor dem Upgrade  

- Bevor eine Edition von [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] auf eine andere Edition aktualisiert wird, sollten Sie überprüfen, ob die derzeit verwendete Funktionalität in der Edition, die Ziel des Upgrades ist, unterstützt wird.  
- Überprüfen Sie die unterstützte [Hard- und Software](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md).
- Aktivieren Sie vor dem Upgrade auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Windows-Authentifizierung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent, und überprüfen Sie die erforderliche Standardkonfiguration. Dabei muss das Konto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts Mitglied der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Gruppe der Systemadministratoren sein.
- Um auf [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]aktualisieren zu können, müssen Sie ein unterstütztes Betriebssystem ausführen. Weitere Informationen finden Sie unter [Hardware- und Softwareanforderungen für die Installation von SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md).  
- Das Upgrade wird blockiert, wenn noch ein Neustart aussteht.  
- Das Upgrade wird blockiert, wenn der Windows Installer-Dienst nicht ausgeführt wird.

## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien

- Versionsübergreifende Instanzen von [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] werden nicht unterstützt. Die Versionsnummern der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Komponenten innerhalb einer Instanz von [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] müssen identisch sein.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] ist nur für 64-Bit-Plattformen verfügbar. Ein plattformübergreifendes Upgrade wird nicht unterstützt. Sie können keine 32-Bit-Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup auf systemeigenes 64-Bit aktualisieren. Sie können jedoch Datenbanken von einer 32-Bit-Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sichern oder trennen und sie in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (64-Bit) wiederherstellen oder anfügen, wenn die Datenbanken nicht in der Replikation veröffentlicht sind. Sie müssen alle Anmeldenamen und anderen Benutzerobjekte in den Systemdatenbanken „master“, „msdb“ und „model“ wiederherstellen.  
  
- Sie können während des Upgrades der vorhandenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]keine neuen Funktionen hinzufügen. Nachdem Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] aktualisiert haben, können Sie Funktionen mit dem [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]-Setup hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Funktionen zu einer Instanz von SQL Server 40 (Setup)](./add-features-to-an-instance-of-sql-server-setup.md).  
 
## <a name="upgrades-from-earlier-versions-to-sssqlv15-md"></a>Upgrades von früheren Versionen auf [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]  
 
[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] unterstützt ein Upgrade von folgenden Versionen von SQL Server:

- [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 oder höher
- [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP3 oder höher
- [!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] SP2 oder höher
- [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]

In der nachfolgenden Tabelle sind die unterstützten Szenarien für das Upgrade von früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]aufgeführt.  
  
|Upgrade von|Unterstützter Upgradepfad|  
|:------|:------|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Developer|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/>[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Evaluation|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Developer|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Evaluation|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler|
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Developer|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler|  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Evaluation|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler|
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Entwickler|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler|  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Evaluation|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler|
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Release Candidate* |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise |  
|[!INCLUDE[sssqlv15_md](../../includes/sssqlv15-md.md)] Entwickler |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise | 

 \* Microsoft-Unterstützung zum Aktualisieren von Release-Candidate-Software ist speziell für Kunden vorgesehen, die am Early-Adopter-Programm teilgenommen haben.

## <a name="migrate-to-sql-server-2019"></a>Migration zu SQL Server 2019

Sie können Datenbanken aus älteren Versionen migrieren. Sie können Datenbanken beispielsweise von [!INCLUDE [sskilimanjaro-md](../../includes/sskilimanjaro-md.md)] zu SQL Server 2019 migrieren.

Weitere Informationen finden Sie unter [Leitfaden zur Azure-Datenbankmigration](https://datamigration.microsoft.com/scenario/sql-to-sqlserver).

Mithilfe der folgenden Tipps und Tools können Sie die Implementierung der Migration besser planen und implementieren:

- Migrationstools: Die Migration wird durch den [Datenmigrations-Assistenten (DMA)](../../dma/dma-overview.md) unterstützt.
- Sichern und Wiederherstellen: Eine Sicherung von SQL Server 2008 oder SQL Server 2008 R2 kann in SQL Server 2019 wiederhergestellt werden.
- Protokollversand: Der Protokollversand wird unterstützt, wenn auf dem primären Replikat SQL Server 2008 SP3 oder höher oder SQL Server 2008 R2 SP2 und auf dem sekundären Replikat SQL Server 2019 ausgeführt wird. 

   > [!WARNING]
   > Wenn ein automatisches oder manuelles Failover ausgeführt wird und die SQL Server 2019-Instanz das primäre Replikat wird, wird die SQL Server 2008- oder SQL Server 2008 R2-Instanz das sekundäre Replikat und kann keine Änderungen vom primären Replikat empfangen.

- Massenladen: Tabellen können von SQL Server 2008 oder SQL Server 2008 R2 in SQL Server 2019 per Massenvorgang kopiert werden.

## <a name="sssqlv15-md-edition-upgrade"></a>[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Editionsupgrade 

In der folgenden Tabelle sind die unterstützten Szenarien für das Editionsupgrade in [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]aufgeführt.  

Ausführliche Anweisungen zum Ausführen eines Editionsupgrades finden Sie unter [Aktualisieren auf eine andere Edition von SQL Server (Setup)](../../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-setup.md).  
  
|Upgrade von|Upgrade auf|  
|------------------|----------------|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Server+CAL und Core)**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise |  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise Evaluation**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Server+CAL- oder Core-Lizenz) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> Upgrades von Evaluation (kostenlose Edition) auf eine kostenpflichtige Edition werden für eigenständige Installationen, für gruppierte Installationen jedoch nicht unterstützt. Diese Begrenzung gilt nicht für eigenständige Instanzen, die auf einem Failovercluster von Windows installiert sind, der Mitglied einer Verfügbarkeitsgruppe ist. |  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Server+CAL- oder Core-Lizenz)|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Server+CAL- oder Core-Lizenz) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Server+CAL- oder Core-Lizenz) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express*|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Server+CAL- oder Core-Lizenz) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Entwickler <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
  
 Außerdem können Sie ein Editionsupgrade zwischen [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Server+CAL-Lizenz) und [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Core-Lizenz) ausführen:  
  
|Editionsupgrade von|Editionsupgrade auf|  
|--------------------------|------------------------|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Server+CAL-Lizenz)**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Core-Lizenz)|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Core-Lizenz)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (Server+CAL-Lizenz)|  
  
 \* Gilt auch für [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express with Tools und [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express with Advanced Services.  
  
 ** Änderung der Edition einer gruppierten Instanz von [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Limited Die folgenden Szenarien werden bei [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] -Failoverclustern nicht unterstützt:  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise in [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer, Standard oder Evaluation.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer in [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard oder Evaluation.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard in [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation in [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard.  
  
## <a name="see-also"></a>Weitere Informationen  

 [Editionen und unterstützte Funktionen von [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]](../../sql-server/editions-and-components-of-sql-server-version-15.md)

 [Hardware- und Softwareanforderungen für die Installation von SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md)

 [Aktualisieren von SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)