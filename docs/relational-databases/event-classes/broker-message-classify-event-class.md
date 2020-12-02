---
description: Broker:Message Classify-Ereignisklasse
title: Broker:Message Classify-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Broker:Message Classify event class
ms.assetid: e51f3351-1239-4c41-b87c-1dd86968e027
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7e5e8e0bc84e26798716ba1635580b81dbfc08c8
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96126687"
---
# <a name="brokermessage-classify-event-class"></a>Broker:Message Classify-Ereignisklasse

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert ein **Broker:Message Classify**-Ereignis, wenn Service Broker das Routing für eine Nachricht bestimmt.  
  
## <a name="brokermessage-classify-event-class-data-columns"></a>Datenspalten der Broker:Message Classify-Ereignisklasse  
  
|Datenspalte|Datentyp|BESCHREIBUNG|Spaltennummer|Filterbar|  
|-----------------|---------------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**EventClass**|**int**|Der Typ der aufgezeichneten Ereignisklasse. Für **Broker:Message Classify** lautet der Typ immer **141**.|27|Nein|  
|**EventSequence**|**int**|Die Sequenznummer für dieses Ereignis.|51|Nein|  
|**EventSubClass**|**nvarchar**|Der Typ der Ereignisunterklasse, der weitere Informationen zu jeder Ereignisklasse liefert. Diese Spalte kann die folgenden Werte enthalten:<br /><br /> **Lokal**: Die ausgewählte Route hat die Adresse LOCAL.<br /><br /> **Remote**: Die ausgewählte Route hat eine andere Adresse als LOCAL.<br /><br /> **Verzögert**: Die Nachricht wird verzögert, weil die Weiterleitung deaktiviert ist oder keine entsprechende Route vorhanden ist.|21|Ja|  
|**FileName**|**nvarchar**|Der Dienstname, an den die Nachricht weitergeleitet wird.|36|Nein|  
|**GUID**|**uniqueidentifier**|Die Konversations-ID des Dialogs. Dieser Bezeichner wird als Teil der Nachricht übertragen und von beiden Seiten der Konversation gemeinsam verwendet.|54|Nein|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Nein|  
|**LoginSid**|**image**|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|**nvarchar**|Die Windows-Domäne, der der Benutzer angehört.|7|Ja|  
|**NTUserName**|**nvarchar**|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Ja|  
|**OwnerName**|**nvarchar**|Der Brokerbezeichner, an den die Nachricht weitergeleitet wird.|37|Nein|  
|**RoleName**|**nvarchar**|Gibt an, ob die Nachricht aus dem Netzwerk empfangen wurde oder ob sie aus dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz stammt.|38|Nein|  
|**ServerName**|**nvarchar**|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SPID**|**int**|Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.|12|Ja|  
|**Startzeit**|**datetime**|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.|14|Ja|  
|**TargetUserName**|**nvarchar**|Die Netzwerkadresse des nächsten Hopbrokers.|39|Nein|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
