---
title: Der Protokoll Versand wird nach dem Upgrade nicht ausgeführt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 952a47eaa2028819908ef7e93326c31a289a0cc2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093982"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a>Protokollversand wird nach Update nicht ausgeführt
  Der Upgrade Advisor hat festgestellt, dass Sie den Protokollversand verwenden. Der Protokollversand in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ist nicht mit dem Protokollversand in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] kompatibel und kann nicht direkt aktualisiert werden. Konfigurieren Sie nach dem Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]den Protokollversand mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mithilfe gespeicherter Prozeduren neu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent Protokoll Versand-Auftrags Kategorie bewirkt, dass das Upgrade fehlschlägt](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [Beim Upgrade wird das SQL Server-Agent Benutzer Proxy Konto in das temporäre UpgradedProxyAccount geändert.](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
