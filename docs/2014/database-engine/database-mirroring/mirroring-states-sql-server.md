---
title: Spiegelungsstatus (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- PENDING_FAILOVER state
- mirroring states [SQL Server]
- DISCONNECTED state
- SYNCHRONIZING state
- SYNCHRONIZED state
- SUSPENDED state
- database mirroring [SQL Server], states
ms.assetid: 90062917-74f9-471b-b49e-bc153ae1a468
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9e3e3756f65baa7e1b62e3a84ff709a60b9c887b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62754554"
---
# <a name="mirroring-states-sql-server"></a>Spiegelungsstatus (SQL Server)
  Während einer Datenbank-Spiegelungssitzung befindet sich eine Datenbank stets in einem bestimmten Status (dem *Spiegelungsstatus*). Der Status der Datenbank spiegelt den Kommunikationsstatus, den Datenfluss und den Unterschied in den Daten zwischen den Partnern wider. Die Datenbank-Spiegelungssitzung nimmt denselben Status an wie die Prinzipaldatenbank.  
  
 Während der Datenbank-Spiegelungssitzung überwachen sich die Serverinstanzen gegenseitig. Die Partner verwenden den Spiegelungsstatus für die Überwachung der Datenbank. Mit Ausnahme des PENDING_FAILOVER-Status befinden sich die Prinzipal- und die Spiegeldatenbank immer im gleichen Status. Falls ein Zeuge für die Sitzung festgelegt wurde, überwacht jeder Partner den Zeugen mithilfe seines Verbindungsstatus (CONNECTED oder DISCONNECTED).  
  
 Eine Datenbank kann u. a. den folgenden Spiegelungsstatus annehmen:  
  
|Spiegelungsstatus|Description|  
|---------------------|-----------------|  
|SYNCHRONIZING|Der Inhalt der Spiegeldatenbank liegt zeitlich hinter dem Inhalt der Prinzipaldatenbank. Der Prinzipalserver sendet Protokolleinträge an den Spiegelserver, der die Änderungen auf die Spiegeldatenbank anwendet, um ein Rollforward dafür auszuführen.<br /><br /> Beim Start einer Datenbank-Spiegelungssitzung befindet sich die Datenbank im SYNCHRONIZING-Status. Der Prinzipalserver bedient die Datenbank, während der Spiegelserver versucht, dessen Stand zu erreichen.|  
|SYNCHRONIZED|Wenn der Spiegelserver den Prinzipalserver weitgehend eingeholt hat, wechselt der Spiegelungsstatus zu SYNCHRONIZED. Die Datenbank behält diesen Status so lange bei, wie der Prinzipalserver Änderungen an den Spiegelserver sendet und der Spiegelserver Änderungen auf die Spiegeldatenbank anwendet.<br /><br /> Ist die Transaktionssicherheit auf FULL festgelegt, werden sowohl das automatische als auch das manuelle Failover im Status SYNCHRONIZED unterstützt; nach einem Failover kommt es zu keinem Datenverlust.<br /><br /> Ist die Transaktionssicherheit auf OFF festgelegt, kann es auch im Status SYNCHRONIZED zu Datenverlust kommen.|  
|SUSPENDED|Die Spiegelkopie der Datenbank ist nicht verfügbar. Die Prinzipaldatenbank wird ausgeführt, ohne Protokolle an den Spiegelserver zu senden. Diese Bedingung wird als *ungeschützt laufen*bezeichnet. Dies ist der Status nach einem Failover.<br /><br /> Eine Sitzung kann auch aufgrund von Fehlern beim Wiederholen oder wenn der Administrator die Sitzung anhält in den SUSPENDED-Status gelangen.<br /><br /> SUSPENDED ist ein persistenter Status, der das Herunterfahren und Neustarten der Partner überdauert.|  
|PENDING_FAILOVER|Dieser Status ist nur auf dem Prinzipalserver zu finden, wenn ein Failover zwar begonnen hat, der Server jedoch die Rolle eines Spiegels noch nicht übernommen hat.<br /><br /> Nach dem Initiieren des Failovers wechselt die Prinzipaldatenbank in den Status PENDING_FAILOVER, beendet schnell alle Benutzerverbindungen und übernimmt kurz danach die Rolle des Spiegels.|  
|DISCONNECTED|Die Kommunikation des Partners mit dem anderen Partner wurde unterbrochen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
