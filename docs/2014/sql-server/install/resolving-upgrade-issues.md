---
title: Beheben von Upgradeproblemen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6072fb3c1d52048832bd6d07f34828c84eb2d491
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059503"
---
# <a name="resolving-upgrade-issues"></a>Beheben von Upgradeproblemen
  Die Themen in diesem Abschnitt beschreiben sowohl Upgradeprobleme, die erkannt werden können, als auch solche, die nicht erkannt werden können. Beide wirken sich möglicherweise beim Upgrade oder zu einem späteren Zeitpunkt aus. Die Probleme sind nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten organisiert.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aktuelle Upgradeprobleme](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [Probleme beim Upgrade der Volltextsuche](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [Beim Replikationsupgrade](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [SQL Server-Agent-Upgradeprobleme](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>Probleme, die ein Upgrade verhindern  
 Einige Konfigurationen oder Einstellungen in einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können ein Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verhindern. Wenn das Setup solche Probleme bei der Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erkennt, hält es den Upgradeprozess an und fordert Sie auf, den Upgrade Advisor auszuführen und blockierende Probleme zu beseitigen.  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 Wenn die folgenden Tasks im [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Upgradebericht enthalten sind, müssen Sie die erforderlichen Aktionen durchführen, bevor Sie ein Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vornehmen.  
  
-   [Datenbank-ID 32767 trennen](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [Umbenennen von Anmeldungen, die mit Namen fester Serverrollen](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [Umbenennen von Benutzer ' sys '](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [Verwenden Sie Sp_rename, benennen Sie die doppelten Indexnamen](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
