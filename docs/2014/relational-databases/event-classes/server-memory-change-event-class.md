---
title: Server Memory Change-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Server Memory Change event class
ms.assetid: c9836484-39c5-4a89-b080-3567783b6fff
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 358d468c900d367496cd904b4f401b0948af0853
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044155"
---
# <a name="server-memory-change-event-class"></a>Server Memory Change-Ereignisklasse
  Die **Server Memory Change** -Ereignisklasse tritt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf, wenn die Speicherauslastung um 1 Megabyte (MB) oder 5% des maximalen Server Arbeitsspeichers (je nachdem, welcher Wert größer ist) gestiegen oder gesunken ist.  
  
## <a name="server-memory-change-event-class-data-columns"></a>Datenspalten der Server Memory Change-Ereignisklasse  
  
|Datenspaltenname|Datentyp|BESCHREIBUNG|Column ID|Ja|  
|----------------------|---------------|-----------------|---------------|---------|  
|**EventClass**|**int**|Ereignistyp = 81.|27|Nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|**EventSubClass**|**int**|Der Typ der Ereignisunterklasse.<br /><br /> 1 = Arbeitsspeichervergrößerung<br /><br /> 2 = Arbeitsspeicherverringerung|21|Ja|  
|**IntegerData**|**int**|Neue Arbeitsspeichergröße in MB|25|Ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|**RequestId**|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|**Servername**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**Ausführen**|**nvarchar**|Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. b. mithilfe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Login1 eine Verbindung mit herstellen und eine Anweisung als Login2 ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|**TransactionId**|**BIGINT**|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|**Xactsequence**|**BIGINT**|Das Token, das die aktuelle Transaktion beschreibt.|50|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Serverkonfigurationsoptionen für den Serverarbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
