---
title: Beim Upgrade wird das Benutzerproxykonto von SQL Server-Agent in das temporäre ' UpgradedProxyAccount ' geändert | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6e08ed37f94a60e1727dfcd006de7faff0545a23
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160790"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a>Beim Upgrade wird das Benutzerproxykonto des SQL Server-Agents in das temporäre 'UpgradedProxyAccount' geändert.
  Datenbankwartungspläne, bei denen der Protokollversand aktiviert ist, werden nach dem Upgrade nicht aktiviert.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt einen neuen Satz Protokollversandfunktionen bereit, die nicht direkt kompatibel mit Datenbankwartungsplänen sind.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-Benutzer mit Datenbankwartungsplänen, die Protokollversandfunktionen enthalten, müssen den Protokollversand mit den neuen Funktionen konfigurieren. Weitere Informationen finden Sie, wenn Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation nach "Protokollversand" suchen.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent Auftragskategorie Log Protokollversand beim Upgrade zur Folge](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [Protokollversand wird nach Update nicht ausgeführt](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  
