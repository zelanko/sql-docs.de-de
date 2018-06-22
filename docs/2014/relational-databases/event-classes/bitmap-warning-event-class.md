---
title: Bitmap Warning-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- Bitmap Warning event class
ms.assetid: 5bf9b4e3-0eba-4e67-8ba9-30ca4b48e1d4
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 4989b77f9d551c9c6afacb5e76986c3356a83ee7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060500"
---
# <a name="bitmap-warning-event-class"></a>Bitmap Warning-Ereignisklasse
  Mithilfe der **Bitmap Warning** -Ereignisklasse kann die Verwendung von Bitmapfiltern in Abfragen überwacht werden. Die Ereignisunterklasse kann verwendet werden, um zu melden, wenn Bitmapfilter in einer Abfrage deaktiviert wurden.  
  
## <a name="bitmap-warning-event-class-data-columns"></a>Datenspalten der Bitmap Warning-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|ja|  
|**ClientProcessID**|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|ja|  
|**DatabaseID**|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|ja|  
|**DatabaseName**|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|ja|  
|**EventClass**|`int`|Ereignistyp = 212.|27|nein|  
|**EventSequence**|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|**EventSubClass**|`int`|Der Typ der Ereignisunterklasse. 0 = Bitmapfilter ist deaktiviert.|21|ja|  
|**HostName**|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|ja|  
|**IsSystem**|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|ja|  
|**LoginName**|`nvarchar`|Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder Windows-Anmeldeinformationen im Format *DOMAIN\Benutzername*).|11|ja|  
|**LoginSid**|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|ja|  
|**NTDomainName**|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|ja|  
|**NTUserName**|`nvarchar`|Windows-Benutzername.|6|ja|  
|**ObjectID**|`int`|Die Knoten-ID des Stammes vom an der Neupartition beteiligten Hashteam. Entspricht der Knoten-ID im Showplan.|22|ja|  
|**RequestID**|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|ja|  
|**ServerName**|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**SessionLoginName**|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|ja|  
|**SPID**|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|ja|  
|**StartTime**|`datetime`|Der Zeitpunkt, zu dem das Ereignis begonnen hat (falls verfügbar).|14|ja|  
|**TransactionID**|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|ja|  
|**XactSequence**|`bigint`|Das Token, das die aktuelle Transaktion beschreibt.|50|ja|  
  
  