---
title: Verwalten des Arbeitsspeichers für In-Memory-OLTP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d82f21fa-6be1-4723-a72e-f2526fafd1b6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6f7b32b9e3d87c783efe2a064714454c50a886c6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214250"
---
# <a name="managing-memory-for-in-memory-oltp"></a>Verwalten des Arbeitsspeichers für In-Memory OLTP
  Speicheroptimierte Tabellen benötigen ausreichend verfügbaren Arbeitsspeicher, um alle Zeilen und Indizes im Arbeitsspeicher ablegen zu können. Da Arbeitsspeicher nicht unbegrenzt verfügbar ist, sollten Sie die Arbeitsspeichernutzung in Ihrem System kennen und effizient verwalten. Die Themen in diesem Abschnitt behandeln allgemeine Szenarien zur Speichernutzung und -verwaltung.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Abschnitt|Description|  
|-------------|-----------------|  
|[Schätzen der Arbeitsspeicheranforderungen speicheroptimierter Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md)|Erläutert, wie die Arbeitsspeicheranforderungen einer Tabelle geschätzt werden.|  
|[Binden einer Datenbank mit speicheroptimierten Tabellen an einen Ressourcenpool](../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)|Exemplarische Vorgehensweise, in der das Binden einer Datenbank an einen Ressourcenpool schrittweise erläutert wird.|  
|[Überwachung und Fehlerbehebung für die Arbeitsspeicherauslastung](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)|Tools, die zur Überwachung der Arbeitsspeichernutzung verwendet werden können. Zusätzlich werden Probleme bei zu hoher Speicherauslastung behandelt.|  
|[Beheben von OOM-Problemen (nicht genügend Arbeitsspeicher)](../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md)|Schritte zum Beheben von OOM-Situationen (Out of Memory, nicht genügend Arbeitsspeicher).|  
|[Wiederherstellen einer Datenbank und Binden der Datenbank an einen Ressourcenpool](../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md)|Schritte, durch die eine [!INCLUDE[hek_2](../includes/hek-2-md.md)] -Datenbank wiederhergestellt und an einen benannten Ressourcenpool gebunden wird.|  
|[In-Memory OLTP-Garbage Collection](../relational-databases/in-memory-oltp/in-memory-oltp-garbage-collection.md)|Grundlegendes zur Funktionsweise der Garbage Collection bei gelöschten Zeilen.|  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
