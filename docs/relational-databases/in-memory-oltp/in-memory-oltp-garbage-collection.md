---
title: In-Memory OLTP-Garbage Collection | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Garbage Collection in In-Memory-OLTP auf SQL Server. Wenn eine inaktive Transaktion eine Zeile löscht, wird diese der Garbage Collection überstellt.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 940140a7-4785-46fc-8bf4-151435dccd3c
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 92a1137dd1fa20ad2a6748be9309d812fdfc38f6
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91866753"
---
# <a name="in-memory-oltp-garbage-collection"></a>In-Memory OLTP-Garbage Collection
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Eine Datenzeile wird als veraltet betrachtet, wenn sie durch eine nicht mehr aktive Transaktion gelöscht wurde. Eine veraltete Zeile kann durch die Garbage Collection bereinigt werden. Die Garbage Collection in [!INCLUDE[hek_2](../../includes/hek-2-md.md)]weist die folgenden Merkmale auf:  
  
-   Nicht blockierend. Die Garbage Collection erfolgt über einen längeren Zeitraum und wirkt sich nur minimal auf die Arbeitsauslastung aus.  
  
-   Kooperativ. Benutzertransaktionen nehmen über den GC-Hauptthread an der Garbage Collection teil.  
  
-   Effizient. Benutzertransaktionen löschen die Verknüpfungen veralteter Zeilen aus dem verwendeten Zugriffspfad (dem Index). Dadurch wird der erforderliche Aufwand bei der endgültigen Entfernung der Zeile verringert.  
  
-   Reaktionsschnell. Hohe Arbeitsspeicherauslastung führt zu aggressiver Garbage Collection.  
  
-   Skalierbar. Nach dem Commit übernehmen Benutzertransaktionen einen Teil der Garbage Collection. Je höher die Transaktionsaktivität, umso mehr werden Verknüpfungen veralteter Zeilen von den Transaktionen entfernt.  
  
 Die Garbage Collection wird vom GC-Hauptthread gesteuert. Dieser GC-Hauptthread wird einmal pro Minute ausgeführt oder wenn die Anzahl der Transaktionen, für die ein Commit ausgeführt wurde, einen internen Schwellenwert überschreitet. Aufgaben der Garbage Collection:  
  
-   Identifizieren der Transaktionen, durch die eine Reihe von Zeilen gelöscht oder aktualisiert wurden und für die vor der ältesten aktiven Transaktion ein Commit ausgeführt wurde.  
  
-   Identifizieren von Zeilenversionen, die durch diese alten Transaktionen erstellt wurden.  
  
-   Gruppieren alter Zeilen in einer oder mehrere Einheiten von jeweils 16 Zeilen. Dadurch wird die Arbeitslast der Garbage Collection auf kleinere Einheiten verteilt.  
  
-   Verschieben dieser Arbeitseinheiten in die Warteschlange der Garbage Collection (eine für jedes Zeitplanungsmodul). Ausführliche Informationen finden Sie in den Garbage Collector-DMVs: [sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql.md), [sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql.md) und [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md).  
  
 Nachdem für eine Benutzertransaktion ein Commit ausgeführt wurde, identifiziert sie alle Elemente in der Warteschlange, die dem Zeitplanungsmodul zugeordnet sind, in dem sie ausgeführt wurde, und gibt dann den Arbeitsspeicher frei. Wenn die Garbage Collection-Warteschlange im Zeitplanungsmodul leer ist, wird nach einer nicht leeren Warteschlange im aktuellen NUMA-Knoten gesucht. Bei einer geringen Transaktionsaktivität und nicht ausreichendem Arbeitsspeicher kann der Garbage Collector-Hauptthread auf GC-Zeilen aus einer beliebigen Warteschlange zugreifen. Wenn beispielsweise nach dem Löschen einer großen Anzahl von Zeilen keine Transaktionsaktivität erfolgt und kein Engpass bei der Arbeitsspeicherverfügbarkeit besteht, werden die gelöschten Zeilen erst wieder durch die Garbage Collection bereinigt, wenn die Transaktionsaktivität fortgesetzt wird bzw. nicht mehr genügend Arbeitsspeicher zur Verfügung steht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten des Arbeitsspeichers für In-Memory-OLTP](/previous-versions/sql/sql-server-2016/dn465872(v=sql.130))  
  
