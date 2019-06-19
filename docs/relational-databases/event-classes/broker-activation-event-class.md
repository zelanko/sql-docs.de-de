---
title: Broker:Activation (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 71f3b7d8dd6f5e52cf37582c1a6d1fc974c48c48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66265569"
---
# <a name="brokeractivation-event-class"></a>Broker:Activation (Ereignisklasse)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert ein **Broker:Activation** -Ereignis, wenn eine Warteschlangenüberwachung eine gespeicherte Aktivierungsprozedur startet oder eine QUEUE_ACTIVATION-Benachrichtigung sendet oder wenn eine gespeicherte Aktivierungsprozedur, die von einer Warteschlangenüberwachung gestartet wurde, beendet wird.  
  
## <a name="brokeractivation-event-class-data-columns"></a>Datenspalten der Broker:Activation-Ereignisklasse  
  
|Datenspalte|Typ|und Beschreibung|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ClientProcessID**|**ssNoversion**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|**DatabaseID**|**ssNoversion**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database*-Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**EventClass**|**ssNoversion**|Der Typ der aufgezeichneten Ereignisklasse. Immer **163** für **Broker:Activation**.|27|Nein|  
|**EventSequence**|**ssNoversion**|Die Sequenznummer für dieses Ereignis.|51|Nein|  
|**EventSubClass**|**nvarchar**|Die spezielle Aktion, die von diesem Ereignis gemeldet wird. Einer der folgenden Werte:<br /><br /> **Gestartet**:   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat eine gespeicherte Aktivierungsprozedur gestartet.<br /><br /> **Beendet**:  Die gespeicherte Aktivierungsprozedur wurde normal beendet.<br /><br /> **Abgebrochen**:   Die gespeicherte Aktivierungsprozedur wurde mit einem Fehler beendet.|21|Nein|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**IntegerData**|**ssNoversion**|Die Anzahl der in dieser Warteschlange aktiven Aufgaben.|25|Nein|  
|**IsSystem**|**ssNoversion**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Nein|  
|**LoginSid**|**image**|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|**nvarchar**|Die Windows-Domäne, der der Benutzer angehört.|7|Ja|  
|**NTUserName**|**nvarchar**|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Ja|  
|**ObjectID**|**ssNoversion**|Die diesem Ereignis zugeordnete Warteschlange.|22|Nein|  
|**ServerName**|**nvarchar**|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SPID**|**ssNoversion**|Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.|12|Ja|  
|**StartTime**|**datetime**|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.|14|Ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Nein|  
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
