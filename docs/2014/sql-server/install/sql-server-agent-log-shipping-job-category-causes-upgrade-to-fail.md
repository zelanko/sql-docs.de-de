---
title: SQL Server-Agent-Protokollversand Auftragskategorie verursacht Fehler beim Upgrade | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47d7d5024d234478b8b54e3c05b3c22335758782
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059288"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>Fehler beim Upgrade der Auftragskategorie für den SQL Server-Agent-Protokollversand
  Der Upgradevorgang schlägt fehl, wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agentauftragskategorie mit dem Namen Protokollversand vorhanden ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>Description  
 Es ist eine Systemauftragskategorie mit dem Namen Protokollversand vorhanden. Wenn eine zu aktualisierende Installation bereits eine von einem Benutzer erstellte Auftragskategorie mit dem Namen Protokollversand enthält, müssen Sie die Auftragskategorie vor dem Upgrade umbenennen. Andernfalls schlägt der Upgradevorgang fehl.  
  
## <a name="see-also"></a>Siehe auch  
 [Protokollversand wird nach dem Upgrade nicht ausgeführt.](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [Beim Upgrade wird das Benutzerproxykonto von SQL Server-Agents in das temporäre ' UpgradedProxyAccount ' geändert.](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [SQL Server-Agent-Upgradeprobleme](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  