---
title: SQL Server, Broker-Aktivierung-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7799c0ebb5dce481da8257bf74700d2fe40caeee
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43816296"
---
# <a name="sql-server-broker-activation-object"></a>SQL Server, Broker-Aktivierung-Objekt
  Das Leistungsobjekt **SQLServer:Broker-Aktivierung** enthält Leistungsindikatoren, die Informationen über gespeicherte Aktivierungsprozeduren übermitteln. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
|SQL Server, Broker-Aktivierungsindikatoren|Description|  
|-------------------------------------------|-----------------|  
|**Aufruf von gespeicherten Prozeduren/Sekunde**|Dieser Indikator übermittelt die Gesamtzahl der gespeicherten Aktivierungsprozeduren, die pro Sekunde von allen Warteschlangenüberwachungen der Instanz aufgerufen wurden.|  
|**Taskgrenze erreicht**|Dieser Indikator übermittelt, wie oft eine Warteschlangenüberwachung insgesamt einen neuen Task gestartet hätte, wenn nicht bereits die maximal für die Warteschlange zulässige Anzahl Tasks ausgeführt würde.|  
|**Erreichte Taskgrenze/Sekunde**|Dieser Indikator übermittelt, wie oft pro Sekunde eine Warteschlangenüberwachung einen neuen Task gestartet hätte, wenn nicht bereits die maximal für die Warteschlange zulässige Anzahl Tasks ausgeführt würde.|  
|**Abgebrochene Tasks/Sekunde**|Dieser Indikator übermittelt die Anzahl der gespeicherten Aktivierungsprozeduraufgaben, die mit einem Fehler beendet oder wegen eines Fehlers beim Empfangen von Nachrichten über eine Warteschlangenüberwachung abgebrochen wurden.|  
|**Ausgeführte Tasks**|Dieser Indikator übermittelt die Anzahl der gespeicherten Aktivierungsprozeduren, die zurzeit ausgeführt werden.|  
|**Gestartete Tasks/Sekunde**|Dieser Indikator übermittelt die Anzahl der gespeicherten Aktivierungsprozeduren, die von allen Warteschlangenüberwachungen der Instanz pro Sekunde gestartet wurden.|  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql)   
 [sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
