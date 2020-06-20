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
ms.openlocfilehash: 031fedc4af4b058704cef1da8df846397b235305
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065141"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a>Durchführen eines Upgrades aller Zielserver vor dem Upgrade des Masterservers
  Führen Sie vor dem Upgrade des Masterservers ein Upgrade aller Computer aus, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführen und als Zielserver konfiguriert sind.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>BESCHREIBUNG  
 Um die Verwaltung in Multiserverumgebungen zu automatisieren, benötigen Sie mindestens einen Masterserver und mindestens einen Zielserver. Ein Masterserver verteilt Aufträge an die Zielserver und empfängt Ereignisse von ihnen. Auf dem Masterserver ist zudem die zentrale Kopie der Auftragsdefinitionen für Aufträge gespeichert, die auf Zielservern ausgeführt werden.  
  
 Wenn der aktuelle Server als Masterserver konfiguriert ist, führen Sie zuerst ein Upgrade aller Zielserver durch, bevor Sie den Masterserver aktualisieren.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Wenn Sie vor dem Upgrade des Masterservers nicht alle Zielserver aktualisieren können, müssen Sie alle Zielserver austragen und nach dem Upgrade wieder eintragen.  
  
 Weitere Informationen finden Sie in den Themen "Automatisieren der Verwaltung in einem Unternehmen", "Vorgehensweise: Austragen eines Zielservers bei einem Masterserver", und "Vorgehensweise: Eintragen eines Zielservers als Masterserver" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent Upgradeprobleme](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)   
 [Probleme beim Aktualisieren des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
