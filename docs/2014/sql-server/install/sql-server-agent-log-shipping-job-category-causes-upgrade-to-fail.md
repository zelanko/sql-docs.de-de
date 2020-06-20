---
title: SQL Server-Agent Protokoll Versand-Auftrags Kategorie bewirkt, dass das Upgrade fehlschlägt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2f5947e8fc8d459388fe35d86c75666e25b5d907
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036126"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>Fehler beim Upgrade der Auftragskategorie für den SQL Server-Agent-Protokollversand
  Der Upgradevorgang schlägt fehl, wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agentauftragskategorie mit dem Namen Protokollversand vorhanden ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>BESCHREIBUNG  
 Es ist eine Systemauftragskategorie mit dem Namen Protokollversand vorhanden. Wenn eine zu aktualisierende Installation bereits eine von einem Benutzer erstellte Auftragskategorie mit dem Namen Protokollversand enthält, müssen Sie die Auftragskategorie vor dem Upgrade umbenennen. Andernfalls schlägt der Upgradevorgang fehl.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Der Protokoll Versand wird nach dem Upgrade nicht ausgeführt.](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [Beim Upgrade wird das SQL Server-Agent Benutzer Proxy Konto in das temporäre UpgradedProxyAccount geändert.](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Probleme beim Aktualisieren des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
