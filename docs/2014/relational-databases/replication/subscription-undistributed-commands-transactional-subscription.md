---
title: Abonnement, nicht verteilte Befehle (Transaktionsabonnement, SqlServer 2005 und höher) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 88124bde6d1f8b54a875f1c30076408dc24fcc2c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238712"
---
# <a name="subscription-undistributed-commands-transactional-subscription-sql-server-2005-and-later"></a>Abonnement, Nicht verteilte Befehle (Transaktionsabonnement, SQL Server 2005 und höher)
  Mithilfe der Registerkarte **Nicht verteilte Befehle** können Sie Informationen zur Anzahl der Befehle in der Verteilungsdatenbank anzeigen, die nicht an den ausgewählten Abonnenten übermittelt wurden, sowie die geschätzte Zeit zur Übermittlung dieser Befehle. Weitere Informationen zum Anzeigen der Befehle in der Verteilungsdatenbank finden Sie unter [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql).  
  
## <a name="options"></a>Tastatur  
 **Anzahl von Befehlen in der Verteilungsdatenbank, die darauf warten, auf diesen Abonnenten angewendet zu werden**  
 Die Anzahl von Befehlen in der Verteilungsdatenbank, die nicht an den ausgewählten Abonnenten übermittelt wurden. Ein Befehl besteht aus einer Transact-SQL-DML-Anweisung (Data Manipulation Language, Datenbearbeitungssprache) oder einer DDL-Anweisung (Data Definition Language, Datendefinitionssprache).  
  
 **Geschätzte Zeit, um diese Befehle anzuwenden, basierend auf der früheren Leistung**  
 Die geschätzte Zeitdauer für die Übermittlung von Befehlen an den Abonnenten. Wenn dieser Wert größer ist, als die zum Generieren und Anwenden einer Momentaufnahme auf den Abonnenten erforderliche Zeit, sollten Sie eine erneute Initialisierung des Abonnenten in Betracht ziehen. Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
