---
title: FT:Crawl Aborted-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Crawl Aborted event class
ms.assetid: eead8ea6-5051-4689-ab30-4dfbfda01fb9
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ecf13efc4b4beefd1983b76619eb03eeac7cb8bc
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43058178"
---
# <a name="ftcrawl-aborted-event-class"></a>FT:Crawl Aborted (Ereignisklasse)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die **FT:Crawl Aborted** -Ereignisklasse zeigt eine Ausnahme während einer Volltextdurchforstung an. Der Fehler führt normalerweise dazu, dass die Volltextdurchforstung beendet wird. Ausführlichere Fehlerinformationen finden Sie im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Ereignisprotokoll oder im Durchforstungsprotokoll.  
  
## <a name="ftcrawl-aborted-event-class-data-columns"></a>Datenspalten der FT:Crawl Aborted-Ereignisklasse  
  
|Datenspaltenname|Datentyp|und Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID der Datenbank, in der die Volltextdurchforstung ausgeführt wird. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|**Fehler**|**int**|Fehlernummer eines bestimmten Ereignisses. Dies ist häufig die in der **sysmessages** -Tabelle gespeicherte Fehlernummer.|31|Benutzerkontensteuerung|  
|**EventClass**|**int**|Ereignistyp = 157.|27|nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Benutzerkontensteuerung|  
|**ObjectID**|**int**|Vom System zugewiesene ID des Objekts, für das die Volltextdurchforstung ausgeführt wird, wenn der Fehler auftritt.|22|Benutzerkontensteuerung|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|**Status**|**int**|Gleichbedeutend mit einem Fehlerzustandscode.|30|Benutzerkontensteuerung|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
