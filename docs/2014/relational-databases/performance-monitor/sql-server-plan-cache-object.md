---
title: SQL Server, Plancache-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Plan Cache object
- SQLServer:Plan Cache
ms.assetid: 225e2b02-8d2f-4f29-9eba-f5847c36ea99
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ff1acb1fb3af2708b14b31eeb82aa0989685630c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68210816"
---
# <a name="sql-server-plan-cache-object"></a>SQL Server, Plancache-Objekt
  Das **Plancache** -Objekt stellt Indikatoren bereit, mit denen überwacht werden kann, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Arbeitsspeicher zum Speichern von Objekten verwendet, z. B. gespeicherten Prozeduren, Ad-hoc-Anweisungen, vorbereiteten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen sowie Triggern. Es können mehrere Instanzen des **Plancache** -Objekts gleichzeitig überwacht werden, wobei jede Instanz einen unterschiedlichen Typ von zu überwachendem Plan darstellt.  
  
 In dieser Tabelle werden die **SQLServer:Plancache**Leistungsindikatoren beschrieben.  
  
|SQL Server, Plancache-Leistungsindikatoren|BESCHREIBUNG|  
|------------------------------------|-----------------|  
|**Cachetrefferquote**|Das Verhältnis zwischen Cachetreffern und -suchvorgängen.|  
|**Cacheobjektzähler**|Anzahl der Cacheobjekte im Cache.|  
|**Cacheseiten**|Anzahl der von Cacheobjekten verwendeten 8-KB-Seiten.|  
|**Verwendete Cacheobjekte**|Anzahl der verwendeten Cacheobjekte.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Plancache-Instanz|BESCHREIBUNG|  
|-------------------------|-----------------|  
|**_Total**|Informationen zu allen Typen von Cacheinstanzen.|  
|**Sql-Pläne**|Abfragepläne, die von einer Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage, einschließlich automatisch parametrisierten Abfragen, oder durch [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen generiert wurden, die mit **sp_prepare** oder **sp_cursorprepare**vorbereitet wurden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichert die Pläne für Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen für die spätere Wiederverwendung zwischen, wenn die identische [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung später ausgeführt wird. Vom Benutzer parametrisierte Abfragen (selbst wenn sie nicht ausdrücklich vorbereitet sind) werden ebenfalls mit Prepared SQL Plans überwacht.|  
|**Objektpläne**|Abfragepläne, die durch Erstellen von gespeicherten Prozeduren, Funktionen oder Triggern generiert wurden.|  
|**Gebundene Strukturen**|Normalisierte Strukturen für Sichten, Regeln, berechnete Spalten und CHECK-Einschränkungen.|  
|**Erweiterte gespeicherte Prozeduren**|Kataloginformationen für erweiterte Prozeduren.|  
|**Temporäre Tabellen & Tabellenvariablen**|Cacheinformationen zu temporären Tabellen und Tabellenvariablen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Server Konfigurationsoptionen für den Server Arbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [SQL Server, Puffer-Manager-Objekt](sql-server-buffer-manager-object.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
