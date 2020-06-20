---
title: Ereignis zählerziel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f540f39176ec638cdc9236b315e306ecebfdcb1b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933071"
---
# <a name="event-counter-target"></a>Ereigniszählerziel
  Das Ereigniszählerziel zählt alle Ereignisse, die während einer Sitzung für erweiterte Ereignisse auftreten. Mithilfe des Ereigniszählerziels erhalten Sie Informationen zu Merkmalen der Arbeitsauslastung ohne den Aufwand einer vollständigen Ereignisauflistung. Dieses Ziel verfügt über keine vom Benutzer anpassbaren Parameter.  
  
## <a name="adding-the-target-to-a-session"></a>Hinzufügen des Ziels zu einer Sitzung  
 Wenn Sie das Ereigniszählerziel einer Sitzung für erweiterte Ereignisse hinzufügen möchten, müssen Sie beim Erstellen oder Ändern einer Ereignissitzung die folgende Anweisung einschließen:  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a>Überprüfen der Zielausgabe  
 Um die Ausgabe des Ereigniszählerziels zu überprüfen, verwenden Sie die folgende Abfrage, und ersetzen Sie dabei *Sitzungsname* durch den Namen der Ereignissitzung:  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 Im folgenden Beispiel wird das Ausgabeformat des Ereigniszählerziels veranschaulicht.  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ziele für erweiterte Ereignisse SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys. dm_xe_session_targets &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [Erstellen einer Ereignis Sitzung &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
