---
title: Background Job Error-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Background Job Error event class
ms.assetid: 9e6d2a0e-919d-4fe2-a306-b20b8d41c197
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b95db663ea56f8dd43ed1091169f8117292033c4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63012331"
---
# <a name="background-job-error-event-class"></a>Background Job Error-Ereignisklasse
  Die **Background Job Error** -Ereignisklasse tritt auf, wenn ein Hintergrundauftrag fehlerbedingt beendet wurde. Dieser Zustand erfordert möglicherweise ein Eingreifen des Systemadministrators.  
  
## <a name="background-job-error-event-class-data-columns"></a>Datenspalten der Background Job Error-Ereignisklasse  
  
|Datenspaltenname|Datentyp|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID der durch den Auftrag angegebenen Datenbank. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|**Fehler**|**int**|Fehlernummer des letzten Versuchs (nur bei**EventSubClass** 1).|31|Ja|  
|**EventClass**|**int**|Ereignistyp = 193.|27|Nein|  
|**EventSequence**|**int**|Die Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|**EventSubClass**|**int**|Der Typ der Ereignisunterklasse.<br /><br /> 1 = Hintergrundauftrag nach Fehler vorzeitig beendet.<br /><br /> 2 = Hintergrundauftrag gelöscht - Warteschlange voll.<br /><br /> 3 = Hintergrundauftrag hat einen Fehler zurückgegeben.|21|Ja|  
|**IndexID**|**int**|ID für den Index des Objekts, das von dem Ereignis betroffen ist. Sie können die Index-ID für ein Objekt mithilfe der **indid** -Spalte der **sysindexes** -Systemtabelle ermitteln.|24|Ja|  
|**IntegerData**|**int**|Anzahl der Versuche des Auftrags (nur bei**EventSubClass** 1).|25|Ja|  
|**IntegerData2**|**int**|Auftragssequenznummer.|55|Ja|  
|**ObjectID**|**int**|Vom System zugewiesene ID des Objekts.|22|Ja|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt die Windows-Anmeldenamen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[msCoName](../../includes/msconame-md.md)] an.|64|Ja|  
|**Severity**|**int**|Der Schweregrad des Fehlers beim letzten Versuch (nur bei**EventSubClass** 1).|20|Ja|  
|**StartTime**|**datetime**|Der Zeitpunkt, zu dem der Auftrag erstellt wurde.|14|Ja|  
|**State**|**int**|Der Status des Fehlers beim letzten Versuch (nur bei**EventSubClass** 1).|30|Ja|  
|**TextData**|**ntext**|Die Textbeschreibung des Wertes der Ereignisunterklasse.|1|Ja|  
|**Typ**|**int**|Typ des Auftrags.|57|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Auto Stats-Ereignisklasse](auto-stats-event-class.md)  
  
  
