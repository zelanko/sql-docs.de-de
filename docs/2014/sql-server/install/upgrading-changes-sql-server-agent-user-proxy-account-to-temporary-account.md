---
title: Beim Upgrade wird das Benutzerproxykonto von SQL Server-Agents in das temporäre ' UpgradedProxyAccount ' geändert | Microsoft Docs
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
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9bae867b97a9fc63b97506fd8900e68b670b8013
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047301"
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
 [SQL Server-Agent-Auftragskategorie Protokoll Protokollversand Fehler beim upgrade](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [Protokollversand wird nach dem Upgrade nicht ausgeführt.](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  