---
title: Abonnement, nicht verteilte Befehle (Transaktionsabonnement, SqlServer 2005 und höher) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a1f957c417c5c63766dfbffa923edd6935d1eb5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63151482"
---
# <a name="subscription-undistributed-commands-transactional-subscription-sql-server-2005-and-later"></a>Abonnement, Nicht verteilte Befehle (Transaktionsabonnement, SQL Server 2005 und höher)
  Mithilfe der Registerkarte **Nicht verteilte Befehle** können Sie Informationen zur Anzahl der Befehle in der Verteilungsdatenbank anzeigen, die nicht an den ausgewählten Abonnenten übermittelt wurden, sowie die geschätzte Zeit zur Übermittlung dieser Befehle. Weitere Informationen zum Anzeigen der Befehle in der Verteilungsdatenbank finden Sie unter [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql).  
  
## <a name="options"></a>Optionen  
 **Anzahl von Befehlen in der Verteilungsdatenbank, die darauf warten, auf diesen Abonnenten angewendet zu werden**  
 Die Anzahl von Befehlen in der Verteilungsdatenbank, die nicht an den ausgewählten Abonnenten übermittelt wurden. Ein Befehl besteht aus einer Transact-SQL-DML-Anweisung (Data Manipulation Language, Datenbearbeitungssprache) oder einer DDL-Anweisung (Data Definition Language, Datendefinitionssprache).  
  
 **Geschätzte Zeit, um diese Befehle anzuwenden, basierend auf der früheren Leistung**  
 Die geschätzte Zeitdauer für die Übermittlung von Befehlen an den Abonnenten. Wenn dieser Wert größer ist, als die zum Generieren und Anwenden einer Momentaufnahme auf den Abonnenten erforderliche Zeit, sollten Sie eine erneute Initialisierung des Abonnenten in Betracht ziehen. Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
