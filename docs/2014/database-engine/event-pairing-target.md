---
title: Ziel ' Paarbildung ' Event | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- pairing target [SQL Server extended events]
- event pairing target
- targets [SQL Server extended events], pairing target
ms.assetid: 3c87dcfb-543a-4bd8-a73d-1390bdf4ffa3
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7907ec8b5fa2e450a1a9e3e73c82bf8511da64ca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62780411"
---
# <a name="event-pairing-target"></a>Ziel 'Ereignispaarbildung'
  Das Ziel Ereignispaarbildung ordnet zwei Ereignisse mithilfe mindestens einer Datenspalte in jedem Ereignis einander zu. Viele Ereignisse sind einander paarweise zugeordnet, z. B. die Anforderungen zur Einrichtung und Aufhebung einer Sperre. Nachdem eine Ereignissequenz paarweise zugeordnet wurde, werden beide Ereignisse verworfen. Das Verwerfen übereinstimmender Sätze ermöglicht ein problemloses Erkennen von eingerichteten Sperren, die noch nicht aufgehoben wurden.  
  
 Beim Verwenden von Filtern auf Ereignisebene können mithilfe des Ziels Ereignispaarbildung nur die Ereignisse aufgezeichnet werden, die nicht den voreingestellten Kriterien entsprechen.  
  
 Bei Verwendung des Ziels Ereignispaarbildung können Sie zwei Ereignisse auswählen, die einander zugeordnet werden, sowie eine Sequenz von Spalten, für die die Zuordnung ausgeführt wird. Alle Spalten in dieser Sequenz müssen den gleichen Typ aufweisen.  
  
 In der folgenden Tabelle werden die verfügbaren Optionen für das Konfigurieren der Ereignispaarbildung beschrieben.  
  
|Option|Zulässige Werte|Description|  
|------------|--------------------|-----------------|  
|begin_event|Ein beliebiger Ereignisname, der in der aktuellen Sitzung vorhanden ist.|Der Ereignisname, der das Startereignis in einer paarweise zugeordneten Sequenz angibt.|  
|end_event|Ein beliebiger Ereignisname, der in der aktuellen Sitzung vorhanden ist.|Der Ereignisname, der das Endereignis in einer paarweise zugeordneten Sequenz angibt.|  
|begin_matching_columns|Eine durch Trennzeichen getrennte geordnete Liste mit Spaltennamen.|Die Spalten, für die die Zuordnung ausgeführt wird.|  
|end_matching_columns|Eine durch Trennzeichen getrennte geordnete Liste mit Spaltennamen.|Die Spalten, für die die Zuordnung ausgeführt wird.|  
|begin_matching_actions|Eine durch Trennzeichen getrennte, geordnete Liste von Aktionen.|Die Aktionen, für die die Zuordnung ausgeführt wird.|  
|end_matching_actions|Eine durch Trennzeichen getrennte, geordnete Liste von Aktionen.|Die Aktionen, für die die Zuordnung ausgeführt wird.|  
|respond_to_memory_pressure|Einer der folgenden Werte:<br /><br /> 0 = Es erfolgt keine Antwort.<br /><br /> 1 = Der Liste werden keine neuen verwaisten Objekte hinzugefügt, wenn nicht mehr genügend Arbeitsspeicher vorhanden ist.|Die Antwort des Ziels auf Speicherereignisse. Wenn auf 1 festgelegt, ist auf den Server wenig Arbeitsspeicher verfügbar, und nicht paarweise zugeordnete Informationen, die beibehalten wurden, werden entfernt.|  
|max_orphans||Gibt die Gesamtzahl von nicht paarweise zugeordneten Ereignissen an, die im Ziel gesammelt werden. Sobald die Grenze erreicht wird, werden nicht paarweise zugeordnete Ereignisse auf einer FIFO-Basis (First In, First Out) entfernt. Standardeinstellung = 10,000.|  
  
 Alle einem Ereignis zugeordneten Daten werden aufgezeichnet und für zukünftige paarweise Zuordnungen gespeichert. Außerdem werden von Aktionen hinzugefügte Daten gesammelt. Die aufgezeichneten Ereignisdaten werden im Arbeitsspeicher gespeichert und verfügen daher über eine feste Begrenzung. Diese Begrenzung basiert auf Systemkapazität und -aktivität. Statt die maximale Arbeitsspeichermenge als Parameter zu verwenden, wird der verwendete Arbeitsspeicher auf Grundlage der verfügbaren Systemressourcen festgelegt. Wenn keine verfügbar sind, werden nicht paarweise zugeordnete Ereignisse, die behalten wurden, gelöscht. Wenn ein Ereignis nicht paarweise zugeordnet wurde und gelöscht wird, wird das übereinstimmende Ereignis als nicht paarweise zugeordnetes Ereignis angezeigt.  
  
 Das Ziel Ereignispaarbildung serialisiert nicht paarweise zugeordnete Ereignisse in einem XML-Format. Dieses Format entspricht keinem Schema. Das Format enthält nur zwei Elementtypen. Die  **\<nicht paarweise zugeordneten >** Element ist das Stammelement, gefolgt von einem. **\<Ereignis >** -Element für jedes nicht zugeordnete Ereignis, das derzeit nachverfolgt wird. Die  **\<Event >** -Element enthält ein Attribut mit dem Namen des nicht paarweise zugeordneten Ereignisses.  
  
## <a name="adding-the-target-to-a-session"></a>Hinzufügen des Ziels zu einer Sitzung  
 Wenn Sie das Paarvergleichsziel einer Sitzung für erweiterte Ereignisse hinzufügen möchten, müssen Sie beim Erstellen oder Ändern einer Ereignissitzung die folgende Anweisung einschließen:  
  
```  
ADD TARGET package0.pair_matching   
```  
  
 Nach dieser fügen Sie eine SET-Anweisung ein, um die Anfangs- und Endereignisse sowie die zu vergleichenden Aktionen oder Spalten zu definieren. Das folgende Beispiel zeigt Beispielsyntax für den Paarvergleich der Ereignisse sqlserver.lock_acquired und sqlserver.lock_released.  
  
```  
   ( SET begin_event = 'sqlserver.lock_acquired',  
      begin_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
      end_event = 'sqlserver.lock_released',  
      end_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
   respond_to_memory_pressure = 1)  
```  
  
 Weitere Informationen finden Sie unter [Feststellen, welche Abfragen Sperren enthalten](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md).  
  
## <a name="reviewing-the-target-output"></a>Überprüfen der Zielausgabe  
 Sie können die Ausgabe des Paarvergleichsziels mithilfe der folgenden Abfrage überprüfen und dabei *session_name* durch den Namen der Ereignissitzung ersetzen.  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 Im folgenden Beispiel wird das Ausgabeformat des Ziels Ereignispaarbildung veranschaulicht.  
  
```  
<unpaired truncated = "0" matchedCount = "[matched count]" memoryPressureDroppedCount = " [lost count]">  
    <event name  = "[event name]" package = "[package]" id= "[event ID value]" version = "[event version]">  
    <data name = "[column name]">   
    <type name = "[column type]" package = "[type package]" />   
    <value>[column value]</value>  
    <text value>[text value]</text>>  
        </data>  
    </event>  
</unpaired>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ziele für erweiterte Ereignisse von SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
