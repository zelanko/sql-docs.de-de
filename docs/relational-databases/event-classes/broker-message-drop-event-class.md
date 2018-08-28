---
title: Broker:Message Undeliverable-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Broker:Message Undeliverable event class
ms.assetid: f532b7c9-ca34-4bac-8dc3-53f9895fd6af
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dc8a55215281ee56e6a4797b7f3268f0544e92f4
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43088886"
---
# <a name="brokermessage-undeliverable-event-class"></a>Broker:Message Undeliverable-Ereignisklasse
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert ein **Broker:Message Undeliverable**-Ereignis, wenn Service Broker eine empfangene Nachricht nicht beibehalten kann, die an einen Dienst in dieser Instanz weitergeleitet werden sollte. Informationen über Nachrichten, die weitergeleitet werden sollten, finden Sie unter [Broker:Forwarded Message Dropped (Ereignisklasse)](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md).  
  
## <a name="brokermessage-undeliverable-event-class-data-columns"></a>Broker:Message Undeliverable-Ereignisklasse – Datenspalten  
  
|Datenspalte|Typ|und Beschreibung|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Benutzerkontensteuerung|  
|**BigintData1**|**bigint**|Die Sequenznummer der unzustellbaren Nachricht.|52|nein|  
|**BigintData2**|**bigint**|Die Sequenznummer der Nachricht, die zuletzt erfolgreich bestätigt wurde.|53|nein|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Benutzerkontensteuerung|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|**Fehler**|**int**|Die Nachrichten-ID-Nummer in **sys.messages** für den Text des Ereignisses.|31|nein|  
|**EventClass**|**int**|Der Typ der aufgezeichneten Ereignisklasse. Für **Broker:MessageUndeliverable** lautet der Typ immer **160**.|27|nein|  
|**EventSequence**|**int**|Die Sequenznummer für dieses Ereignis.|51|nein|  
|**EventSubClass**|**nvarchar**|Gibt an, ob die unzustellbare Nachricht eine sequenzierte Nachricht war. Einer von zwei Werten:<br /><br /> **Sequenced Message**. Die unzustellbare Nachricht war eine sequenzierte Nachricht.<br /><br /> **Nicht sequenzierte Nachricht**. Die unzustellbare Nachricht war keine sequenzierte Nachricht.|21|Benutzerkontensteuerung|  
|**GUID**|**uniqueidentifier**|Die Konversations-ID der Konversation, zu der die unzustellbare Nachricht gehört. Dieser Bezeichner wird als Teil der Nachricht übertragen und von beiden Seiten der Konversation gemeinsam verwendet.|54|nein|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|**IntegerData**|**int**|Die Fragmentnummer der unzustellbaren Nachricht.|25|nein|  
|**IntegerData2**|**int**|Die Nachrichtenfragmentnummer, die die unzustellbare Nachricht bestätigen sollte.|55|nein|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|nein|  
|**LoginName**|**nvarchar**|Der Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder Windows-Anmeldeinformationen im Format DOMAIN\Username).|11|nein|  
|**LoginSid**|**image**|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|**NTDomainName**|**nvarchar**|Die Windows-Domäne, der der Benutzer angehört.|7|Benutzerkontensteuerung|  
|**NTUserName**|**nvarchar**|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Benutzerkontensteuerung|  
|**ObjectName**|**nvarchar**|Das Konversationshandle des Dialogs.|34|nein|  
|**RoleName**|**nvarchar**|Die Rolle des Konversationshandles. Dabei handelt es sich um **initiator** oder **target**.|38|nein|  
|**ServerName**|**nvarchar**|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**Severity**|**int**|Schweregradnummer für den Text im Ereignis.|29|nein|  
|**SPID**|**int**|Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.|12|Benutzerkontensteuerung|  
|**StartTime**|**datetime**|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.|14|Benutzerkontensteuerung|  
|**Status**|**int**|Gibt den Standort im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Quellcode an, der das Ereignis erstellt hat. Jeder Ort, von dem aus dieses Ereignis ggf. erstellt werden kann, besitzt einen anderen Statuscode. Der Microsoft Software Service kann anhand dieses Statuscodes ermitteln, wo das Ereignis erstellt wurde.|30|nein|  
|**TextData**|**ntext**|Der Grund, aus dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Nachricht nicht übermitteln konnte.|1|Benutzerkontensteuerung|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|nein|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
