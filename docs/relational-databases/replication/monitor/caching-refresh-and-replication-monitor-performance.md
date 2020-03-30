---
title: Zwischenspeichern, Aktualisieren und Leistung des Replikationsmonitors
description: In diesem Artikel erfahren Sie, wie Sie in SQL Server Management Studio (SSMS) im Replikationsmonitor zwischenspeichern, aktualisieren und die Leistung optimieren.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- cache [SQL Server], replication
- Replication Monitor, caching
- refreshing data
- Replication Monitor, refreshing
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 45cad9f38fadd8280b6cb155c0e44643448ac4bf
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "76286348"
---
# <a name="caching-refresh-and-replication-monitor-performance"></a>Zwischenspeichern, Aktualisieren und Leistung des Replikationsmonitors
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Der Replikationsmonitor von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dient der effizienten Überwachung einer großen Zahl von Computern in einem Produktionssystem. Die Abfragen, mit denen der Replikationsmonitor Berechnungen ausführt und Daten erfasst, werden zwischengespeichert und regelmäßig aktualisiert. Das Zwischenspeichern verringert die Zahl der Abfragen und Berechnungen, die erforderlich sind, wenn Sie verschiedene Seiten im Replikationsmonitor anzeigen, und ermöglicht es, den Umfang der Überwachungen für mehrere Benutzer optimal anzupassen.  
  
 Die Aktualisierung des Cache wird durch einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agentauftrag ausgeführt: **Aktualisierung für die Replikationsüberwachung**. Der Auftrag wird fortlaufend ausgeführt. Der Zeitplan für die Aktualisierung des Cache hängt von einer bestimmten Wartedauer nach der vorhergehenden Aktualisierung ab:  
  
-   Wenn seit dem letzten Erstellen des Cache Änderungen des Agent-Verlaufs stattgefunden haben, beträgt die Wartezeit mindestens 4 Sekunden oder die Zeitspanne, die das Erstellen des vorherigen Cache gedauert hat.  
  
-   Wenn seit dem letzten Erstellen des Cache keine Änderungen des Agent-Verlaufs stattgefunden haben (es könnten andere Änderungen eingetreten sein), beträgt die Wartezeit maximal 30 Sekunden oder die Zeitspanne, die das Erstellen des vorherigen Cache gedauert hat.  
  
## <a name="refreshing-the-replication-monitor-user-interface"></a>Aktualisieren der Benutzeroberfläche des Replikationsmonitors  
 Die Benutzeroberfläche des Replikationsmonitors kann folgendermaßen aktualisiert werden:  
  
-   Das Fenster des Replikationsmonitors (einschließlich aller Registerkarten) wird standardmäßig alle fünf Sekunden automatisch aktualisiert. Das automatische Aktualisieren erzwingt keine Aktualisierung des Cache. Die Benutzeroberfläche zeigt die aktuellste Version der Daten aus dem Cache an. Sie können die Aktualisierungsrate für alle Fenster anpassen, die mit einem Verleger zusammenhängen, indem Sie die Einstellungen für den Verleger bearbeiten. Sie können die automatischen Aktualisierungen für einen Verleger auch deaktivieren.  
  
-   Die im Replikationsmonitor gestarteten Detailfenster werden nicht standardmäßig automatisch aktualisiert, ausgenommen Fenster, die mit einem gerade synchronisierten Merge-Abonnement zusammenhängen. Wenn Sie das automatische Aktualisieren von Detailfenstern angeben, werden die Fenster nach demselben Zeitplan aktualisiert wie das Hauptfenster des Replikationsmonitors.  
  
-   Sie können alle Fenster manuell aktualisieren. Drücken Sie dazu F5, oder klicken Sie mit der rechten Maustaste auf einen Knoten in der Struktur des Replikationsmonitors, und klicken Sie dann auf **Aktualisieren**. Das manuelle Aktualisieren erzwingt eine Aktualisierung des Cache.  
  
 Weitere Informationen finden Sie unter [Aktualisieren von Daten im Replikationsmonitor](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md).  
  
## <a name="performance-considerations"></a>Überlegungen zur Leistung  
 Der Replikationsmonitor ist zwar für ein effizientes Ausführen ausgelegt, jedoch sollten Sie Folgendes beachten:  
  
-   Legen Sie bei einer großen Zahl von Veröffentlichungen oder Abonnements einen Zeitplan fest, nach dem die Benutzeroberfläche weniger häufig automatisch aktualisiert wird.  
  
-   Vermeiden Sie das gleichzeitige Ausführen mehrerer Instanzen des Replikationsmonitors.  
  
-   Vermeiden Sie es, eine große Zahl von Verteilern zu registrieren und festzulegen, dass der Replikationsmonitor zu allen automatisch eine Verbindung herstellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Aufträgen zur Replikationswartung &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)   
 [Überwachen der Replikation](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
