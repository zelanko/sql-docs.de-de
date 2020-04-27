---
title: Broker:Corrupted Message-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Corrupted Message event class
ms.assetid: 084bf198-2138-438e-bdc7-4ff1e04300f7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a49f10826496e9e8fea46b1846b74535a173f821
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62664085"
---
# <a name="brokercorrupted-message-event-class"></a>Broker:Corrupted Message-Ereignisklasse
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt ein **Broker:Corrupted Message** -Ereignis, wenn Service Broker eine beschädigte Nachricht empfängt.  
  
## <a name="brokercorrupted-message-event-class-data-columns"></a>Datenspalten der Broker:Corrupted Message-Ereignisklasse  
  
|Datenspalte|type|BESCHREIBUNG|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|**BigintData1**|**bigint**|Die Sequenznummer dieser Nachricht.|52|Nein|  
|**BinaryData**|**image**|Der Nachrichtentext der Nachricht.|2|Ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**Fehler**|**int**|Die Nachrichten-ID-Nummer in **sys.messages** für den Text des Ereignisses.|31|Nein|  
|**EventClass**|**int**|Der Typ der aufgezeichneten Ereignisklasse. Für **Broker:Corrupted Message** lautet der Typ immer **161**.|27|Nein|  
|**EventSequence**|**int**|Die Sequenznummer für dieses Ereignis.|51|Nein|  
|**FileName**|**nvarchar**|Die Netzwerkadresse des Remoteendpunktes.|36|Nein|  
|**GUID**|**uniqueidentifier**|Die Konversations-ID der Konversation, zu der die beschädigte Nachricht gehört. Dieser Bezeichner wird als Teil der Nachricht übertragen und von beiden Seiten der Konversation gemeinsam verwendet.|54|Nein|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**IntegerData**|**int**|Die Fragmentnummer dieser Nachricht.|25|Ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Nein|  
|**LoginSid**|**image**|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|**nvarchar**|Die Windows-Domäne, der der Benutzer angehört.|7|Ja|  
|**NTUserName**|**nvarchar**|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Ja|  
|**ObjectName**|**nvarchar**|Der Dienstname der anderen Seite der Konversation und die Verbindungszeichenfolge, die die Remotedatenbank verwendet hat, um eine Verbindung mit dieser Datenbank herzustellen.|34|Nein|  
|**RoleName**|**nvarchar**|Die Rolle des Endpunktes, der diese Nachricht empfängt. Einer der folgenden Werte:<br /><br /> **Initiator**:<br />                  Der empfangende Endpunkt ist der Initiator der Konversation.<br /><br /> **Ziel**:<br />                  Der empfangende Endpunkt ist das Ziel der Konversation.|38|Nein|  
|**ServerName**|**nvarchar**|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**Schweregrad**|**int**|Wenn ein Fehler bewirkt hat, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Nachricht gelöscht hat, der Schweregrad des Fehlers.|29|Nein|  
|**SPID**|**int**|Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.|12|Ja|  
|**StartTime**|**datetime**|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.|14|Ja|  
|**State**|**int**|Gibt den Standort im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Quellcode an, der das Ereignis erstellt hat. Jeder Ort, von dem aus dieses Ereignis ggf. erstellt werden kann, besitzt einen anderen Statuscode. Der Microsoft Software Service kann mithilfe dieses Statuscodes herausfinden, wo das Ereignis generiert wurde.|30|Nein|  
|**TextData**|**ntext**|Beschreibung der erkannten Beschädigung|1|Ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Nein|  
  
 Die **TextData** -Spalte dieses Ereignisses enthält eine Nachricht, die das Problem mit der Nachricht beschreibt.  
  
  
