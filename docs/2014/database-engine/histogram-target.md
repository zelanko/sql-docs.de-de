---
title: Histogrammziel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bucketing target [SQL Server extended events]
- event bucketing target
- targets [SQL Server extended events], bucketing
ms.assetid: 2ea39141-7eb0-4c74-abf8-114c2c106a19
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dcee8251ba073d87f94fc4be18bc6e77c6113361
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147594"
---
# <a name="histogram-target"></a>Histogrammziel
  Das Histogrammziel fasst Ereignisse eines bestimmten Ereignistyps auf Grundlage von Ereignisdaten zusammen. Die Gruppierungen von Ereignissen werden anhand einer bestimmten Ereignisspalte oder Aktion gezählt. Mit dem Histogrammziel können Sie Leistungsprobleme diagnostizieren. Durch Identifizieren der am häufigsten eintretenden Ereignisse können Sie relevante Bereiche ausmachen, die auf mögliche Ursachen eines Leistungsproblems hindeuten.  
  
 In der folgenden Tabelle werden die verfügbaren Optionen zum Konfigurieren des Histogrammziels beschrieben.  
  
|Option|Zulässige Werte|Description|  
|------------|--------------------|-----------------|  
|slots|Ein ganzzahliger Wert. Dieser Wert ist optional.|Ein vom Benutzer angegebener Wert, der die maximale Anzahl von Gruppierungen angibt, die beizubehalten sind. Wenn dieser Wert erreicht wird, werden neue Ereignisse, die nicht zu vorhandenen Gruppen gehören, ignoriert.<br /><br /> Beachten Sie, dass die Slotnummer zur Leistungsverbesserung auf die nächste Potenz von 2 aufgerundet wird.|  
|filtering_event_name|Ein beliebiges Ereignis in der Sitzung für erweiterte Ereignisse. Dieser Wert ist optional.|Ein vom Benutzer angegebener Wert, mit dem eine Klasse von Ereignissen identifiziert wird. Nur Instanzen des angegebenen Ereignisses werden Buckets zugeordnet. Alle anderen Ereignisse werden ignoriert.<br /><br /> Wenn Sie diesen Wert angeben, müssen Sie folgendes Format verwenden: *Paketname*.*Ereignisname*. Beispiel: `'sqlserver.checkpoint_end'`. Sie können den Paketnamen mit der folgenden Abfrage ermitteln:<br /><br /> SELECT p.name, se.event_name<br />VON dm_xe_session_events se<br />Verknüpfen von dm_xe_packages p<br />ON Se_event_package_guid = p.guid<br />ORDER BY p.name, se.event_name<br /><br /> <br /><br /> Wenn Sie den Wert filtering_event_name nicht angeben, muss source_type auf 1 (den Standardwert) festgelegt werden.|  
|source_type|Der Typ des Objekts, auf dem der Bucket basiert. Dieser Wert ist optional. Wenn er nicht angegeben wird, wird 1 als Standardwert verwendet.|Kann einen der folgenden Werte aufweisen:<br /><br /> 0 für ein Ereignis<br /><br /> 1 für eine Aktion|  
|Quelle|Ereignisspalte oder Aktionsname.|Die Ereignisspalte oder der Aktionsname, die bzw. der als Datenquelle verwendet wird.<br /><br /> Wenn Sie für source eine Ereignisspalte angeben, müssen Sie eine Spalte aus dem Ereignis angeben, das für den Wert filtering_event_name verwendet wird. Sie können mögliche Spalten mithilfe der folgenden Abfrage identifizieren:<br /><br /> SELECT Name FROM dm_xe_object_columns<br />WHERE Object_name = "\<Ereignisname >'<br />UND Column_type! = "Readonly"<br /><br /> Wenn Sie für source eine Ereignisspalte angeben, müssen Sie den Paketnamen nicht im Wert source angeben.<br /><br /> Wenn Sie für source einen Aktionsnamen angeben, müssen Sie eine der konfigurierten Aktionen verwenden, die für die Auflistung in der Ereignissitzung konfiguriert ist, für die dieses Ziel verwendet wird. Mögliche Werte für den Aktionsnamen können Sie ermitteln, indem Sie die action_name-Spalte der sys.dm_xe_sesssion_event_actions-Sicht abfragen.<br /><br /> Wenn Sie einen Aktionsnamen als Datenquelle verwenden, müssen Sie den source-Wert im Format *Paketname*.*Aktionsname*angeben.|  
  
 Im folgenden Beispiel wird das Erfassen von Daten mit dem Histogrammziel auf abstrakter Ebene veranschaulicht. In diesem Beispiel soll das Histogrammziel zum Zählen der Anzahl der eingetretenen Wartevorgänge je Wartevorgangstyp verwendet werden. Geben Sie dazu beim Definieren des Histogrammziels die folgenden Optionen an:  
  
-   filtering_event_name = 'wait_info'  
  
-   source = 'wait_type'  
  
-   source_type = 0 (da "wait_type" eine Ereignisspalte ist)  
  
 Im Beispielszenario werden die folgenden Daten für die wait_type-Quelle aufgezeichnet:  
  
|Ereignisnamensfilter|Quellspaltenwert|  
|--------------------------|-------------------------|  
|wait_info|file_io|  
|wait_info|file_io|  
|wait_info|Netzwerk|  
|wait_info|Netzwerk|  
|wait_info|sleep|  
  
 Die wait_type-Werte werden in drei Slots mit den folgenden Werten und der jeweiligen Slotanzahl kategorisiert:  
  
|value|Slotanzahl|  
|-----------|----------------|  
|file_io|2|  
|Netzwerk|2|  
|sleep|1|  
  
 Das Histogrammziel behält nur Ereignisdaten für die angegebene Quelle bei. In manchen Fällen können die Ereignisdaten zu lang sein. Dann werden sie abgeschnitten. Wenn Ereignisdaten abgeschnitten werden, wird die Anzahl von Bytes aufgezeichnet und als XML-Ausgabe angezeigt.  
  
## <a name="adding-the-target-to-a-session"></a>Hinzufügen des Ziels zu einer Sitzung  
 Um einer Sitzung für erweiterte Ereignisse das Histogrammziel hinzuzufügen, müssen Sie beim Erstellen oder Ändern einer Ereignissitzung je nach gewünschtem Zieltyp eine der beiden folgenden Anweisungen einschließen:  
  
```  
ADD TARGET package0.histogram  
```  
  
 Die verschiedenen Optionen können Sie mithilfe der SET-Anweisung festlegen. Im folgenden Beispiel wird das Hinzufügen des Histogrammziels veranschaulicht, in dem Daten für das Ereignis „sqlserver.checkpoint_end“ erfasst werden.  
  
```  
ADD TARGET package0.histogram  
(SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id')  
```  
  
 Weitere Informationen finden Sie unter [darauf Suchen der Objekte, die über die meisten Sperren](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md), und [Überwachen der Systemaktivität mit erweiterten Ereignissen](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).  
  
## <a name="reviewing-the-target-output"></a>Überprüfen der Zielausgabe  
 Das Histogrammziel serialisiert Daten zu einem aufrufenden Programm oder einer Prozedur im XML-Format. Die Zielausgabe entspricht keinem Schema.  
  
 Sie können die Ausgabe des Histogrammziels mithilfe der folgenden Abfrage überprüfen und dabei *session_name* durch den Namen der Ereignissitzung ersetzen.  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 Im folgenden Beispiel wird das Ausgabeformat des Histogrammziels veranschaulicht.  
  
```  
<Slots truncated = "0" buckets=[count]>  
    <Slot count=[count] trunc=[truncated bytes]>  
        <value>  
        </value>  
    </Slot>  
</Slots>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ziele für erweiterte Ereignisse von SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
