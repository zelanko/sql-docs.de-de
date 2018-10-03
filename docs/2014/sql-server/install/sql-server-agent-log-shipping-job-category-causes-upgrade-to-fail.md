---
title: SQL Server-Agent-Protokollversand Auftragskategorie bewirkt, dass beim Upgrade zur Folge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 61b488250267e497541f15033b347074648d3c9d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086150"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>Fehler beim Upgrade der Auftragskategorie für den SQL Server-Agent-Protokollversand
  Der Upgradevorgang schlägt fehl, wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agentauftragskategorie mit dem Namen Protokollversand vorhanden ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>Description  
 Es ist eine Systemauftragskategorie mit dem Namen Protokollversand vorhanden. Wenn eine zu aktualisierende Installation bereits eine von einem Benutzer erstellte Auftragskategorie mit dem Namen Protokollversand enthält, müssen Sie die Auftragskategorie vor dem Upgrade umbenennen. Andernfalls schlägt der Upgradevorgang fehl.  
  
## <a name="see-also"></a>Siehe auch  
 [Der Protokollversand wird nach dem Upgrade nicht ausgeführt.](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [Beim Upgrade wird das Benutzerproxykonto von SQL Server-Agent in das temporäre ' UpgradedProxyAccount ' geändert.](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Probleme beim Upgrade des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
