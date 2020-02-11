---
title: Broker:Forwarded Message Dropped-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Forwarded Message Dropped event class
ms.assetid: ec242d0b-77b0-45f5-8b12-186a14b173a8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bf6e9bb278417d69be0ec0a99cb1c47d88ffddff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62664026"
---
# <a name="brokerforwarded-message-dropped-event-class"></a>Broker:Forwarded Message Dropped-Ereignisklasse
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert ein Broker:Forwarded Message Dropped-Ereignis, wenn Service Broker eine Nachricht löscht, die eigentlich weitergeleitet werden sollte.  
  
## <a name="brokerforwarded-message-dropped-event-class-data-columns"></a>Datenspalten der Broker:Forwarded Message Dropped-Ereignisklasse  
  
|Datenspalte|type|BESCHREIBUNG|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|BigintData1|`bigint`|Nachrichtensequenznummer.|52|Nein|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database*-Anweisung ausgegeben wurde. 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die Server Name-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Der Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|DBUserName|`nvarchar`|Der Brokerinstanzbezeichner, vom dem diese Nachricht stammt.|40|Nein|  
|Fehler|`int`|Die Nachrichten-ID-Nummer in sys.messages für den Text des Ereignisses.|31|Nein|  
|EventClass|`int`|Der Typ der aufgezeichneten Ereignisklasse. Für Broker:Forwarded Message Dropped lautet der Typ immer 191.|27|Nein|  
|EventSequence|`int`|Die Sequenznummer für dieses Ereignis.|51|Nein|  
|FileName|`nvarchar`|Name des Diensts, an den die Nachricht gerichtet ist.|36|Nein|  
|GUID|`uniqueidentifier`|Die Konversations-ID des Dialogs. Dieser Bezeichner wird als Teil der Nachricht übertragen und von beiden Seiten der Konversation gemeinsam verwendet.|54|Nein|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IndexID|`int`|Die Anzahl der für die weitergeleitete Nachricht verbleibenden Hops.|24|Nein|  
|IntegerData|`int`|Die Fragmentnummer der weitergeleiteten Nachricht.|25|Nein|  
|LoginSid|`image`|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|NTDomainName|`nvarchar`|Die Windows-Domäne, der der Benutzer angehört.|7|Ja|  
|NTUserName|`nvarchar`|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Ja|  
|ObjectId|`int`|Der Gültigkeitsdauerwert der weitergeleiteten Nachricht.|22|Nein|  
|ObjectName|`nvarchar`|Nachrichten-ID der weitergeleiteten Nachricht.|34|Nein|  
|OwnerName|`nvarchar`|Der Brokerinstanzbezeichner für das Ziel der Nachricht.|37|Nein|  
|RoleName|`nvarchar`|Die Rolle des Konversationshandles. Enthält einen der folgenden Werte:<br /><br /> Initiator. Dieser Broker hat die Konversation initiiert.<br /><br /> Ziel. Der Broker ist das Ziel der Konversation.|38|Nein|  
|Servername|`nvarchar`|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|severity|`int`|Schweregradnummer für den Text im Ereignis.|29|Nein|  
|SPID|`int`|Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.|12|Ja|  
|StartTime|`datetime`|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.|14|Ja|  
|State|`int`|Gibt den Standort im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Quellcode an, der das Ereignis erstellt hat. Jeder Ort, von dem aus dieses Ereignis ggf. erstellt werden kann, besitzt einen anderen Statuscode. Der Microsoft Software Service kann mithilfe dieses Statuscodes herausfinden, wo das Ereignis generiert wurde.|30|Nein|  
|Erfolg|`int`|Die Zeitdauer, für die die Nachricht gültig war. Wenn dieser Wert größer oder gleich der Gültigkeitsdauer ist, wird die Nachricht gelöscht.|23|Nein|  
|TargetLoginName|`nvarchar`|Die Netzwerkadresse, an die die Nachricht weitergeleitet werden soll.|42|Nein|  
|TargetUserName|`nvarchar`|Der Name des initiierenden Diensts für die Nachricht.|11,9|Nein|  
|TextData|`ntext`|Beschreibung des Grundes, aus dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Nachricht gelöscht hat.|1|Ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Nein|  
  
 Die TextData-Spalte dieses Ereignisses enthält eine Beschreibung des Grundes, aus dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Nachricht gelöscht hat.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
