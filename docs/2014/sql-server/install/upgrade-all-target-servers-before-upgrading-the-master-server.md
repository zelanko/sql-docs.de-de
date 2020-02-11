---
title: Aktualisieren aller Zielserver vor dem Upgrade des Master Servers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b6e08a384e20d64a7002171059db0d35dfd94a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091465"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a>Durchführen eines Upgrades aller Zielserver vor dem Upgrade des Masterservers
  Führen Sie vor dem Upgrade des Masterservers ein Upgrade aller Computer aus, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführen und als Zielserver konfiguriert sind.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Büros  
  
## <a name="description"></a>BESCHREIBUNG  
 Um die Verwaltung in Multiserverumgebungen zu automatisieren, benötigen Sie mindestens einen Masterserver und mindestens einen Zielserver. Ein Masterserver verteilt Aufträge an die Zielserver und empfängt Ereignisse von ihnen. Auf dem Masterserver ist zudem die zentrale Kopie der Auftragsdefinitionen für Aufträge gespeichert, die auf Zielservern ausgeführt werden.  
  
 Wenn der aktuelle Server als Masterserver konfiguriert ist, führen Sie zuerst ein Upgrade aller Zielserver durch, bevor Sie den Masterserver aktualisieren.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Wenn Sie vor dem Upgrade des Masterservers nicht alle Zielserver aktualisieren können, müssen Sie alle Zielserver austragen und nach dem Upgrade wieder eintragen.  
  
 Weitere Informationen finden Sie in den Themen "Automatisieren der Verwaltung in einem Unternehmen", "Vorgehensweise: Austragen eines Zielservers bei einem Masterserver", und "Vorgehensweise: Eintragen eines Zielservers als Masterserver" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent Upgradeprobleme](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)   
 [Probleme beim Aktualisieren des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
