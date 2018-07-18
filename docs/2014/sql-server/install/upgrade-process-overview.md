---
title: Übersicht über den Upgradeprozess | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
- Upgrade Advisor [SQL Server], process description
- SQL Server Upgrade Advisor, process description
- upgrade process [Upgrade Advisor]
ms.assetid: f77ffbab-a195-4124-acce-9c538f7ca9ce
caps.latest.revision: 39
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cb54124a1646b65632a74db6d8c4cc9630e30046
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288256"
---
# <a name="upgrade-process-overview"></a>Übersicht über den Upgradeprozess
  Dieses Thema bietet Informationen zu bewährten Methoden für den Upgrade Advisor von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sowie eine Zusammenfassung des empfohlenen Prozesses für das Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="upgrade-process"></a>Upgradeprozess  
 Server, auf denen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ausgeführt wird, können auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aktualisiert werden. Manche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten können direkt aktualisiert werden, während andere migriert und wieder andere durch neue Komponenten ersetzt werden müssen. Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) werden z. B. die Data Transformation Services (DTS) abgelöst, und DTS wird in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nicht mehr unterstützt. Beim Erstellen Ihres Upgradeplans kann es erforderlich sein, die Aktualisierung Ihrer aktuellen DTS-Pakete auf [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Pakete zu planen.  
  
 Mit dem Upgrade Advisor können Sie aktuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationen, -Komponenten und zugehörige Dateien auswerten, um bekannte Probleme zu identifizieren, die sowohl während als auch nach dem Upgrade auf oder der Migration zu [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Probleme verursachen. Nur einige dieser bekannten Probleme blockieren den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aktualisieren. Im Bericht des Upgrade Advisors werden diese Probleme als Upgrade Blocker identifiziert. Wenn Sie die Upgrade Blocker vor dem Ausführen von Setup nicht beseitigen, wird [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Setup beendet. Außerdem wird die Ausführung des Upgrade Advisors empfohlen, um die spezifischen Probleme zu identifizieren, die das Upgrade blockieren.  
  
 Als bewährte Methode vor dem Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] empfiehlt es sich, eine Sicherungskopie der Daten und Systemeinstellungen zu erstellen und die strategischen Schritte auszuführen, die in den für Ihr Unternehmen definierten Betriebsrichtlinien beschrieben sind. Führen Sie die folgenden Schritte aus, um das Upgrade auszuführen:  
  
1.  Informieren Sie sich unter [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
2.  Erstellen Sie eine Sicherungskopie der Daten und Systemeinstellungen.  
  
3.  Führen Sie den Upgrade Advisor aus.  
  
     Der Upgrade Advisor nimmt keine Änderungen an den Daten oder Einstellungen auf dem Computer vor.  
  
4.  Überprüfen Sie die im Bericht des Upgrade Advisors angegebenen Probleme.  
  
5.  Beheben Sie alle Blockierungsprobleme, die eine Aktualisierung auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verhindern würden.  
  
6.  Beheben Sie alle weiteren Probleme vor dem Upgrade.  
  
7.  Führen Sie den Upgrade Advisor aus, um zu überprüfen, ob alle bekannten Probleme behoben wurden.  
  
8.  Führen Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup aus.  
  
9. Beheben Sie alle Probleme nach dem Upgrade sowie alle Migrationsprobleme.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Upgrade Advisor &#40;-Benutzeroberfläche&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [Verwenden von Berichten](../../../2014/sql-server/install/using-reports.md)   
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
