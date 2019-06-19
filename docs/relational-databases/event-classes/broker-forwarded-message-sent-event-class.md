---
title: Broker:Forwarded Message Sent-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Broker:Forwarded Message Sent event class
ms.assetid: d0ef74d9-a4ef-4918-aa21-6b267e85569f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 35e9be1d5a1a3e8861866bd565f36854def1bb54
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66265515"
---
# <a name="brokerforwarded-message-sent-event-class"></a>Broker:Forwarded Message Sent-Ereignisklasse

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert ein Broker:Forwarded Message Sent-Ereignis, wenn Service Broker eine Nachricht weiterleitet.  
  
## <a name="brokerforwarded-message-sent-event-class-data-columns"></a>Datenspalten der Broker:Forwarded Message Sent-Ereignisklasse  
  
|Datenspalte|Typ|und Beschreibung|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|**nvarchar**|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|BigintData1|**bigint**|Nachrichtensequenznummer.|52|Nein|  
|ClientProcessID|**ssNoversion**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|DatabaseID|**ssNoversion**|Die ID der Datenbank, die durch die USE *Datenbank* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *Datenbank*-Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die Server Name-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DBUserName|**nvarchar**|Die Brokerinstanz-ID für den Dienst, vom dem die Nachricht stammt.|40|Nein|  
|EventClass|**ssNoversion**|Der Typ der aufgezeichneten Ereignisklasse. Immer 139 für Broker:Forwarded Message Sent.|27|Nein|  
|EventSequence|**ssNoversion**|Die Sequenznummer für dieses Ereignis.|51|Nein|  
|FileName|**nvarchar**|Name des Diensts, an den die Nachricht gerichtet ist.|36|Nein|  
|GUID|**uniqueidentifier**|Die Konversations-ID des Dialogs. Dieser Bezeichner wird als Teil der Nachricht übertragen und von beiden Seiten der Konversation gemeinsam verwendet.|54|Nein|  
|HostName|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IndexID|**ssNoversion**|Die Anzahl der für die weitergeleitete Nachricht verbleibenden Hops.|24|Nein|  
|IntegerData|**ssNoversion**|Die Fragmentnummer der weitergeleiteten Nachricht.|25|Nein|  
|IsSystem|**ssNoversion**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Nein|  
|LoginSid|**image**|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|NTDomainName|**nvarchar**|Die Windows-Domäne, der der Benutzer angehört.|7|Ja|  
|NTUserName|**nvarchar**|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Ja|  
|ObjectID|**ssNoversion**|Der Gültigkeitsdauerwert für die weitergeleitete Nachricht, als die Nachricht weitergeleitet wurde.|22|Nein|  
|ObjectName|**nvarchar**|Nachrichten-ID der weitergeleiteten Nachricht.|34|Nein|  
|OwnerName|**nvarchar**|Der Brokerbezeichner, an den die Nachricht weitergeleitet wird.|37|Nein|  
|RoleName|**nvarchar**|Die Rolle des Konversationshandles. Gültige Werte sind:<br /><br /> Initiator. Dieser Broker hat die Konversation initiiert.<br /><br /> Ziel. Der Broker ist das Ziel der Konversation.|38|Nein|  
|ServerName|**nvarchar**|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SPID|**ssNoversion**|Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.|12|Ja|  
|StartTime|**datetime**|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.|14|Ja|  
|Success|**ssNoversion**|Die Zeitspanne, die für den Weiterleitungsvorgang benötigt wurde.|23|Nein|  
|TargetLoginName|**nvarchar**|Die Netzwerkadresse, an die diese Instanz die Nachricht gesendet hat. Beachten Sie, dass sich diese Adresse vom endgültigen Ziel der Nachricht unterscheiden kann.|42|Nein|  
|TargetUserName|**nvarchar**|Der Name des initiierenden Diensts für die Nachricht.|39|Nein|  
|TransactionID|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Nein|  
  
  
