---
title: Feature Regeln (Upgrade) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 653b15db-a984-4b4b-b224-81b0285b099b
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eb47e8f74b54daef890940587f8b0544a1795361
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060857"
---
# <a name="feature-rules-upgrade"></a>Funktionsregeln (Upgrade)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup überprüft die Computerkonfiguration, bevor der Setupvorgang abgeschlossen wird. Beim Setup von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchsucht das System den Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert wird. Außerdem wird nach Bedingungen gesucht, die ein erfolgreiches Durchführen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setups verhindern. Bevor Setup den Upgrade-Assistenten startet, wird der Status jedes Elements abgerufen. SCC vergleicht dann das Ergebnis mit den erforderlichen Bedingungen und gibt Anweisungen zum Entfernen der Blockierungsprobleme.  
  
 Die Systemkonfigurationsprüfung generiert einen Bericht, der eine kurze Beschreibung für jede ausgeführte Regel sowie den Ausführungsstatus enthält. Der Bericht der systemkonfigurationsprüfung befindet sich unter "% ProgramFiles%"\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< jjjjmmtt_hhmm >\\.  
  
 Bevor Sie Setup ausführen, lesen Sie die folgenden Themen:  
  
1.  [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Von den SQL Server 2014-Editionen unterstützte Funktionen](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Lokale Sprachversionen in SQL Server](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Weitere Referenzen:  
  
1.  [Unterstützte Versions- und Editionsupgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Vor dem Installieren des Failoverclusterings](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Installationsregeln](../../../2014/sql-server/install/install-rules.md)  
  
  