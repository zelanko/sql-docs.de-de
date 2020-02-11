---
title: SQL Server, Broker-Aktivierung-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 59c66bc237b496fd913658f168b7b1c0089fdc00
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250698"
---
# <a name="sql-server-broker-activation-object"></a>SQL Server, Broker-Aktivierung-Objekt
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
 [sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql)   
 [sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
