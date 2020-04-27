---
title: Beheben von Upgradeproblemen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
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
ms.openlocfilehash: 85de606ecea93aba80714d4266e9897dd856879f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092502"
---
# <a name="resolving-upgrade-issues"></a>Beheben von Upgradeproblemen
  Die Themen in diesem Abschnitt beschreiben sowohl Upgradeprobleme, die erkannt werden können, als auch solche, die nicht erkannt werden können. Beide wirken sich möglicherweise beim Upgrade oder zu einem späteren Zeitpunkt aus. Die Probleme sind nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten organisiert.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aktuelle Upgradeprobleme](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [Probleme beim Upgrade der Datenbank-Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [Probleme beim Upgrade der Volltextsuche](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [Probleme beim Replikationsupgrade](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [Reporting Services Upgradeprobleme &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [Probleme beim Aktualisieren des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>Probleme, die ein Upgrade verhindern  
 Einige Konfigurationen oder Einstellungen in einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können ein Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verhindern. Wenn das Setup solche Probleme bei der Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erkennt, hält es den Upgradeprozess an und fordert Sie auf, den Upgrade Advisor auszuführen und blockierende Probleme zu beseitigen.  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 Wenn die folgenden Tasks im [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Upgradebericht enthalten sind, müssen Sie die erforderlichen Aktionen durchführen, bevor Sie ein Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vornehmen.  
  
-   [Datenbank-ID 32767 trennen](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [Umbenennen von Anmeldungen, die mit Namen fester Serverrollen identisch sind](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [Benennen Sie den Benutzer 'sys' um](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [Verwenden Sie bei doppelten Indexnamen 'sp_rename' zum Umbenennen](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
