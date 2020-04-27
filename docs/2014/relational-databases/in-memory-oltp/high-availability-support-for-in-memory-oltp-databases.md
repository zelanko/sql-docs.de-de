---
title: Unterstützung für Hochverfügbarkeit für In-Memory OLTP-Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2113a916-3b1e-496c-8650-7f495e492510
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 37c719beb625a533c2d8f279a8500365c4786c05
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62990584"
---
# <a name="high-availability-support-for-in-memory-oltp-databases"></a>Unterstützung für Hochverfügbarkeit für In-Memory OLTP-Datenbanken
  Datenbanken mit speicheroptimierten Tabellen mit bzw. ohne systemeigene kompilierte gespeicherte Prozeduren werden mit AlwaysOn-Verfügbarkeitsgruppen vollständig unterstützt.  Es gibt keinen Unterschied in Konfiguration und Unterstützung zwischen Datenbanken mit [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Objekten und solchen ohne diese Objekte.  
  
## <a name="alwayson-availability-groups-and-in-memory-oltp-databases"></a>AlwaysOn-Verfügbarkeitsgruppen und In-Memory OLTP-Datenbanken  
 Die Konfiguration von Datenbanken mit [!INCLUDE[hek_2](../../includes/hek-2-md.md)] -Komponenten ermöglicht Folgendes:  
  
-   **Vollständig integriertes Verfahren**   
    Sie können Ihre Datenbanken mit speicheroptimierten Tabellen unter Verwendung des gleichen Assistenten mit der gleichen Ebene der Unterstützung für synchrone und asynchrone sekundäre Replikate konfigurieren. Darüber hinaus erfolgt die Systemüberwachung über das vertraute AlwaysOn-Dashboard in SQL Server Management Studio.  
  
-   **Vergleichbare Failoverzeit**   
    Sekundäre Replikate behalten den im Speicher enthaltenen Status der dauerhaften speicheroptimierten Tabellen. Beim automatischen oder erzwungenen Failover ist die Failoverzeit auf dem neuen primären Replikat mit der für datenträgerbasierte Tabellen vergleichbar, da keine Wiederherstellung notwendig ist. Speicheroptimierte Tabellen, die als SCHEMA_ONLY erstellt wurden, werden in dieser Konfiguration unterstützt. Änderungen an diesen Tabellen werden jedoch nicht protokolliert. Deshalb sind in diesen Tabellen keine Daten auf dem sekundären Replikat vorhanden.  
  
-   **Lesbare sekundäre Datenbank**   
    Sie können auf speicheroptimierte Tabellen auf dem sekundären Replikat zugreifen und sie abfragen, wenn es für Lesezugriff konfiguriert ist. Weitere Informationen finden Sie unter [Aktive sekundäre Replikate: Lesbare sekundäre Replikate (AlwaysOn-Verfügbarkeitsgruppen)](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
## <a name="failover-clustering-instance-fci-and-in-memory-oltp-databases"></a>Failoverclustering-Instanz (FCI) und In-Memory OLTP-Datenbanken  
 Um in einer Konfiguration mit freigegebenem Speicher Hochverfügbarkeit zu erreichen, können Sie das Failoverclustering für Instanzen mit mindestens einer Datenbank mit speicheroptimierten Tabellen einrichten. Beim Einrichten einer FCI müssen Sie die folgenden Faktoren berücksichtigen:  
  
-   **Wiederherstellungszeit Ziel**   
    Die Failoverzeit wird wahrscheinlich höher sein, da speicheroptimierte Tabellen in den Arbeitsspeicher geladen werden müssen, bevor die Datenbank verfügbar gemacht wird.  
  
-   **Tabellen SCHEMA_ONLY**   
    Beachten Sie, dass SCHEMA_ONLY-Tabellen nach dem Failover ohne Zeilen, also leer sind. Dies ist so von der Anwendung definiert. Es ist genau das gleiche Verhalten wie beim Neustart einer [!INCLUDE[hek_2](../../includes/hek-2-md.md)] -Datenbank mit SCHEMA_ONLY-Tabellen.  
  
## <a name="support-for-transaction-replication-in-in-memory-oltp"></a>Unterstützung für Transaktionsreplikation in In-Memory OLTP  
 Die Tabellen, die als Transaktionsreplikationsabonnenten fungieren, können (mit Ausnahme der Peer-zu-Peer-Transaktionsreplikation) als speicheroptimierte Tabellen konfiguriert werden. Andere Replikationskonfigurationen sind mit speicheroptimierten Tabellen nicht kompatibel.  Weitere Informationen finden Sie unter [Replikation mit Abonnenten von speicheroptimierten Tabellen](../replication/replication-to-memory-optimized-table-subscribers.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Aktive sekundäre Replikate: lesbare sekundäre Replikate &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [Replikation mit Abonnenten von speicheroptimierten Tabellen](../replication/replication-to-memory-optimized-table-subscribers.md)  
  
  
