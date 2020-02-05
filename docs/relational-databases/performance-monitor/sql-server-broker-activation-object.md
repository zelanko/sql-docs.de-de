---
title: SQL Server, Broker-Aktivierung-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 364fd8e037e2c09afa16294e75096993f861ca20
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "67987153"
---
# <a name="sql-server-broker-activation-object"></a>SQL Server, Broker-Aktivierung-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das Leistungsobjekt **SQLServer:Broker-Aktivierung** enthält Leistungsindikatoren, die Informationen über gespeicherte Aktivierungsprozeduren übermitteln. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
|SQL Server, Broker-Aktivierungsindikatoren|BESCHREIBUNG|  
|-------------------------------------------|-----------------|  
|**Aufruf von gespeicherten Prozeduren/Sekunde**|Dieser Indikator übermittelt die Gesamtzahl der gespeicherten Aktivierungsprozeduren, die pro Sekunde von allen Warteschlangenüberwachungen der Instanz aufgerufen wurden.|  
|**Taskgrenze erreicht**|Dieser Indikator übermittelt, wie oft eine Warteschlangenüberwachung insgesamt einen neuen Task gestartet hätte, wenn nicht bereits die maximal für die Warteschlange zulässige Anzahl Tasks ausgeführt würde.|  
|**Erreichte Taskgrenze/Sekunde**|Dieser Indikator übermittelt, wie oft pro Sekunde eine Warteschlangenüberwachung einen neuen Task gestartet hätte, wenn nicht bereits die maximal für die Warteschlange zulässige Anzahl Tasks ausgeführt würde.|  
|**Abgebrochene Tasks/Sekunde**|Dieser Indikator übermittelt die Anzahl der gespeicherten Aktivierungsprozeduraufgaben, die mit einem Fehler beendet oder wegen eines Fehlers beim Empfangen von Nachrichten über eine Warteschlangenüberwachung abgebrochen wurden.|  
|**Ausgeführte Tasks**|Dieser Indikator übermittelt die Anzahl der gespeicherten Aktivierungsprozeduren, die zurzeit ausgeführt werden.|  
|**Gestartete Tasks/Sekunde**|Dieser Indikator übermittelt die Anzahl der gespeicherten Aktivierungsprozeduren, die von allen Warteschlangenüberwachungen der Instanz pro Sekunde gestartet wurden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql.md)   
 [sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
