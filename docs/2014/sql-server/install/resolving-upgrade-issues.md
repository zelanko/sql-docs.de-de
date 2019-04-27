---
title: Beheben von Upgradeproblemen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bad975eb6b2b2645cb31b075089c02be735b1d88
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62753322"
---
# <a name="resolving-upgrade-issues"></a>Beheben von Upgradeproblemen
  Die Themen in diesem Abschnitt beschreiben sowohl Upgradeprobleme, die erkannt werden können, als auch solche, die nicht erkannt werden können. Beide wirken sich möglicherweise beim Upgrade oder zu einem späteren Zeitpunkt aus. Die Probleme sind nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten organisiert.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aktuelle Upgradeprobleme](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [Probleme beim Upgrade der Datenbank-Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [Probleme beim Upgrade der Volltextsuche](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [Probleme beim Replikationsupgrade](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [Probleme beim Upgrade des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>Probleme, die ein Upgrade verhindern  
 Einige Konfigurationen oder Einstellungen in einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können ein Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verhindern. Wenn das Setup solche Probleme bei der Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erkennt, hält es den Upgradeprozess an und fordert Sie auf, den Upgrade Advisor auszuführen und blockierende Probleme zu beseitigen.  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 Wenn die folgenden Tasks im [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Upgradebericht enthalten sind, müssen Sie die erforderlichen Aktionen durchführen, bevor Sie ein Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vornehmen.  
  
-   [Trennen der Datenbank-ID 32767](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [Umbenennen von Anmeldeinformationen, die mit Namen fester Serverrollen identisch sind](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [Umbenennen des Benutzers in „sys“](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [Verwenden von „sp_rename“ zum Umbenennen doppelter Indexnamen](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
