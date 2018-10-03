---
title: Weitere Upgradeprobleme bei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- system tables [SQL Server], replication
- passwords [SQL Server replication]
- versions [SQL Server replication]
- connections [SQL Server replication]
- scripts [SQL Server replication]
- ActiveX controls [SQL Server replication]
ms.assetid: 8a5e74be-4992-4f17-b20c-c3dce8f49329
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5ffde063d94f0e08ea0e82e6b5998a6d23cfaac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200730"
---
# <a name="other-replication-upgrade-issues"></a>Weitere Probleme beim Replikationsupgrade
  In diesem Thema werden einige Upgradeprobleme erläutert, die nicht von Upgrade Advisor gemeldet werden.  
  
## <a name="versions-supported"></a>Unterstützte Versionen  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unterstützt das Aktualisieren replizierter Datenbanken aus früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Während des Upgrades eines Knotens müssen die auf anderen Knoten ausgeführten Aktivitäten nicht beendet werden. Stellen Sie sicher, dass die Regeln, die im Hinblick auf die in einer Topologie unterstützten Versionen gelten, eingehalten werden.  
  
 Bei einer Replikation mit unterschiedlichen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist der verfügbare Funktionsumfang häufig auf die Funktionen der frühesten verwendeten Version begrenzt.  
  
> [!NOTE]  
>  Da das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicherformat für Datenträger in 64-Bit- und in 32-Bit-Umgebungen übereinstimmt, können für eine Replikationstopologie Serverinstanzen, die in einer 32-Bit-Umgebung ausgeführt werden, mit Serverinstanzen, die in einer 64-Bit-Umgebung ausgeführt werden, kombiniert werden.  
  
 Bei allen Replikationstypen darf auf dem Verteiler keine frühere Version ausgeführt werden als auf dem Verleger. (Häufig handelt es sich bei Verteiler und Verleger um dieselbe Instanz.)  
  
 Bei einer Transaktionsreplikation kann auf dem Abonnenten einer Transaktionsveröffentlichung eine Version verwendet werden, die sich um höchstens zwei Versionen von der Verlegerversion unterscheidet.  
  
 Bei einer Mergereplikation ist auf dem Abonnenten einer Mergeveröffentlichung jede Version zulässig, die nicht höher als die des Verlegers ist.  
  
## <a name="merge-replication-batches-changes"></a>Batchänderungen bei der Mergereplikation  
 Vom Merge-Agent vorgenommene Änderungen werden zur Leistungsverbesserung in Batches gesammelt. Daher können in einer einzelnen Anweisung mehrere Zeilen eingefügt, aktualisiert oder gelöscht werden. Wenn veröffentlichte Tabellen in den Veröffentlichungs- und Abonnementdatenbanken Trigger enthalten, müssen diese mehrzeilige Einfüge-, Update- und Löschvorgänge verarbeiten können. Weitere Informationen finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation unter "Trigger bei mehrzeiligen Operationen".  
  
## <a name="activex-control-changes"></a>Änderungen von ActiveX-Steuerelementen  
 Die folgenden Änderungen wurden für ActiveX-Replikationssteuerelemente vorgenommen:  
  
-   Alle ActiveX-Steuerelemente sind als unsicher für die Skripterstellung und für die Initialisierung gekennzeichnet.  
  
-   Das ActiveX-Steuerelement für Momentaufnahmen wurde entfernt. Sie können Momentaufnahmen mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder programmgesteuert mit gespeicherten Replikationsprozeduren erstellen und verwalten. Weitere Informationen finden Sie in der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]-Onlinedokumentation unter "Vorgehensweise: Erstellen und Anwenden der Anfangsmomentaufnahme ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])" und unter "Vorgehensweise: Erstellen der Anfangsmomentaufnahme (Replikationsprogrammierung mit Transact-SQL)".  
  
-   Das ActiveX-Verteilungssteuerelement und das ActiveX-Mergesteuerelement wurden als veraltete markiert. Ähnliche Funktionalität wird mit Replikationsverwaltungsobjekten (RMO) für verwaltete Codeanwendungen bereitgestellt. Weitere Informationen finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation unter "Synchronisieren von Abonnements (RMO-Programmierung)".  
  
## <a name="see-also"></a>Siehe auch  
 [Probleme beim Replikationsupgrade](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
