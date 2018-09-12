---
title: SQLServer, Broker und DBM-Transport-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Broker / DBM Transport object
- SQLServer:Broker/DBM Transport
ms.assetid: eddb60b6-20a9-416c-adf3-4bc1687944fa
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 817d965a1f3ec36088dcecc80e5018be8aa6368a
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818306"
---
# <a name="sql-server-broker-and-dbm-transport-object"></a>SQL Server, Broker und DBM-Transport-Objekt
  Das **Broker/DBM-Transport** -Leistungsobjekt enthält Leistungsindikatoren, die Netzwerkinformationen für Service Broker und die Datenbankspiegelung melden. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
|SQL Server, Broker/DBM-Transport-Leistungsindikator|Description|  
|------------------------------------------------|-----------------|  
|**Aktuelle Bytes für E/A-Empfangsvorgänge**|Dieser Leistungsindikator gibt die Anzahl der Bytes an, die von den aktuell ausgeführten Transportempfangsvorgängen gelesen werden müssen.|  
|**Aktuelle Bytes für E/A-Sendungen**|Dieser Leistungsindikator gibt die Anzahl der Bytes in Nachrichtenfragmenten an, die aktuell über das Netzwerk gesendet werden.|  
|**Aktuelle Nachrichtenfragmente für E/A-Sendungen**|Dieser Leistungsindikator gibt die Gesamtanzahl der Nachrichtenfragmente an, die über das Netzwerk gesendet werden.|  
|**P1-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 1 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**P2-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 2 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**P3-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 3 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**P4-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 4 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**P5-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 5 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**P6-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 6 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**P7-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 7 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**P8-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 8 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**P9-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 9 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**P10-Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente mit Priorität 10 an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**Message Fragment durchschn. Größe**|Dieser Leistungsindikator gibt die durchschnittliche Größe der Nachrichtenfragmente an, die über das Netzwerk gesendet werden.|  
|**Nachrichtenfragmente gesendet/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente aller Prioritäten an, die pro Sekunde über das Netzwerk gesendet werden.|  
|**Nachrichtenfragmente empfangen/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente an, die pro Sekunde über das Netzwerk empfangen werden.|  
|**Durchschn. Größe von empfangenen Nachrichtenfragmenten**|Dieser Leistungsindikator gibt die durchschnittliche Größe der Nachrichtenfragmente an, die über das Netzwerk empfangen wurden.|  
|**Anzahl der geöffneten Verbindungen**|Dieser Leistungsindikator gibt die Anzahl der Netzwerkverbindungen an, die Service Broker aktuell geöffnet hat.|  
|**Ausstehende Bytes für E/A-Empfangsvorgänge**|Dieser Leistungsindikator gibt die Anzahl der Bytes an, die in Nachrichtenfragmenten enthalten sind, die zwar über das Netzwerk empfangen, jedoch noch nicht in einer Warteschlange gespeichert oder verworfen wurden.|  
|**Ausstehende Bytes für E/A-Sendevorgänge**|Dieser Leistungsindikator gibt die Gesamtanzahl der Bytes in Nachrichtenfragmenten an, die für das Senden über das Netzwerk bereit sind.|  
|**Ausstehende Nachrichtenfragmente für E/A-Empfangsvorgänge**|Dieser Leistungsindikator gibt die Anzahl der Nachrichtenfragmente an, die zwar über das Netzwerk empfangen, jedoch noch nicht in einer Warteschlange gespeichert oder verworfen wurden.|  
|**Ausstehende Nachrichtenfragmente für E/A-Sendevorgänge**|Dieser Leistungsindikator gibt die Gesamtanzahl der Nachrichtenfragmente an, die für das Senden über das Netzwerk bereit sind.|  
|**Bytes von E/A-Empfangsvorgängen gesamt**|Dieser Leistungsindikator gibt die Gesamtanzahl der über das Netzwerk von Service Broker- und Datenbankspiegelungs-Endpunkten empfangenen Bytes an.|  
|**Bytes von E/A-Empfangsvorgängen/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der pro Sekunde über das Netzwerk von Service Broker- und Datenbankspiegelungs-Endpunkten empfangenen Bytes an.|  
|**Durchschn. Länge von E/A-Empfangsvorgängen**|Dieser Leistungsindikator gibt die durchschnittliche Anzahl der Bytes für einen Transportempfangsvorgang an.|  
|**Empfangen von e/a pro Sekunde**|Dieser Leistungsindikator gibt die Anzahl der E/A-Transportempfangsvorgänge pro Sekunde an, die die Service Broker- bzw. DBM-Transportschicht abgeschlossen hat. Beachten Sie, dass ein Transportempfangsvorgang mehrere Nachrichtenfragmente enthalten kann.|  
|**Bytes von E/A-Sendungen gesamt**|Dieser Leistungsindikator gibt die Gesamtanzahl der von Service Broker- und Datenbankspiegelungs-Endpunkten über das Netzwerk gesendeten Bytes an.|  
|**Bytes von E/A-Sendungen/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der von Service Broker- und Datenbankspiegelungs-Endpunkten über das Netzwerk gesendeten Bytes pro Sekunde an.|  
|**Durchschn. E/A-Sendelänge**|Dieser Leistungsindikator gibt die durchschnittliche Größe in Byte für jeden Transportsendevorgang an. Beachten Sie, dass ein Transportsendevorgang mehrere Nachrichtenfragmente enthalten kann.|  
|**E/A-Sendungen/Sekunde**|Dieser Leistungsindikator gibt die Anzahl der E/A-Transportsendevorgänge pro Sekunde an, die abgeschlossen wurden. Beachten Sie, dass ein Transportsendevorgang mehrere Nachrichtenfragmente enthalten kann.|  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_broker_forwarded_messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-forwarded-messages-transact-sql)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
