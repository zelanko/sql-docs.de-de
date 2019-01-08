---
title: Bitmap Warning-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Bitmap Warning event class
ms.assetid: 5bf9b4e3-0eba-4e67-8ba9-30ca4b48e1d4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 812ba207d699cbbdb2156a4c5f3799cbfa8a74db
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52753412"
---
# <a name="bitmap-warning-event-class"></a>Bitmap Warning-Ereignisklasse
  Mithilfe der **Bitmap Warning** -Ereignisklasse kann die Verwendung von Bitmapfiltern in Abfragen überwacht werden. Die Ereignisunterklasse kann verwendet werden, um zu melden, wenn Bitmapfilter in einer Abfrage deaktiviert wurden.  
  
## <a name="bitmap-warning-event-class-data-columns"></a>Datenspalten der Bitmap Warning-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|**ClientProcessID**|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|**DatabaseID**|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**DatabaseName**|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|**EventClass**|`int`|Ereignistyp = 212.|27|Nein|  
|**EventSequence**|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|**EventSubClass**|`int`|Der Typ der Ereignisunterklasse. 0 = Bitmapfilter ist deaktiviert.|21|Ja|  
|**HostName**|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**IsSystem**|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|**LoginName**|`nvarchar`|Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder Windows-Anmeldeinformationen im Format *DOMAIN\Benutzername*).|11|Ja|  
|**LoginSid**|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|**NTUserName**|`nvarchar`|Windows-Benutzername.|6|Ja|  
|**ObjectID**|`int`|Die Knoten-ID des Stammes vom an der Neupartition beteiligten Hashteam. Entspricht der Knoten-ID im Showplan.|22|Ja|  
|**RequestID**|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|**ServerName**|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SessionLoginName**|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|**StartTime**|`datetime`|Der Zeitpunkt, zu dem das Ereignis begonnen hat (falls verfügbar).|14|Ja|  
|**TransactionID**|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|**XactSequence**|`bigint`|Das Token, das die aktuelle Transaktion beschreibt.|50|Ja|  
  
  
