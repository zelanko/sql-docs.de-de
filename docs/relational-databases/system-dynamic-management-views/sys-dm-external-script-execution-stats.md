---
title: dm_external_script_execution_stats | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/28/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_execution_stats
- sys.dm_external_script_execution_stats_TSQL
- dm_external_script_execution_stats
- dm_external_script_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_execution_stats dynamic management view
ms.assetid: 2e99f026-ceb2-42a2-a549-c71d31ed0cf4
author: HeidiSteen
ms.author: heidist
manager: cgronlund
ms.openlocfilehash: 8bdbaf1fdb0fb0c27127611ace0fac00d861838f
ms.sourcegitcommit: c2322c1a1dca33b47601eb06c4b2331b603829f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50743135"
---
# <a name="sysdmexternalscriptexecutionstats"></a>sys.dm_external_script_execution_stats
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Gibt eine Zeile für jeden Typ von externer Skriptanforderung zurück. Die externen Skriptanforderungen werden nach der unterstützten externen Skriptsprache gruppiert. Für jede externe Skriptfunktion wird eine Zeile generiert. Beliebige externe Skriptfunktionen werden nicht aufgezeichnet, sofern sie nicht von einem übergeordneten Prozess wie `rxExec`gesendet werden.
  
> [!NOTE]  
> Diese dynamische verwaltungssicht (DMV) ist verfügbar, nur dann, wenn Sie installiert und aktiviert die Funktion, die Ausführung des externen Skripts unterstützt haben. Weitere Informationen finden Sie unter [R Services in SQL Server 2016](../../advanced-analytics/r/sql-server-r-services.md) und [Machine Learning-Diensten (R, Python) in SQL Server 2017](../../advanced-analytics/what-is-sql-server-machine-learning.md).  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|language|**nvarchar**|Name der registrierten externen Skriptsprache. Jedes externe Skript muss die Sprache in der Skriptanforderung angeben, um das zugehörige Startprogramm zu starten. |  
|counter_name|**nvarchar**|Name einer registrierten externen Skriptfunktion. Lässt keine NULL-Werte zu.|  
|counter_value|**integer**|Gesamtanzahl der Instanzen, die von der registrierten externen Skriptfunktion auf dem Server aufgerufen wurden. Dieser Wert ist kumulativ und beginnt mit dem Zeitpunkt, zu dem das Feature auf der Instanz installiert wurde. Der Wert kann nicht zurückgesetzt werden.|  

  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
> [!NOTE]  
>  Benutzer, die externe Skripts ausführen, müssen die zusätzliche Berechtigung EXECUTE ANY EXTERNAL SCRIPT haben, aber diese dynamische Verwaltungssicht kann von Administratoren ohne diese Berechtigung verwendet werden. 
  
## <a name="remarks"></a>Hinweise  
  Diese dynamische Verwaltungssicht wird für die interne Telemetrie bereitgestellt, um die Gesamtauslastung des neuen Features zur externen Skriptausführung in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] zu überwachen. Der Telemetriedienst wird mit Launchpad gestartet und inkrementiert jedes Mal einen datenträgerbasierten Zähler, wenn eine registrierte externe Skriptfunktion aufgerufen wird.

Leistungsindikatoren sind im Allgemeinen nur so lange gültig, wie der Prozess aktiv ist, der sie generiert hat. Daher kann eine Abfrage für eine DMV keine ausführlichen Daten für Dienste anzeigen, die beendet wurden. Z. B. wenn ein Startprogramm für ein externes Skript ausführt und sehr schnell abschließt, kann eine konventionelle DMV keine Daten angezeigt.

Daher bleiben die von der DMV verfolgten Leistungsindikatoren aktiv und der Status für „sys.dm_external_script_requests“ wird beibehalten, indem Schreibvorgänge auf den Datenträger verwendet werden, auch wenn die Instanz heruntergefahren wird.

   
  
### <a name="counter-values"></a>Werte von Leistungsindikatoren
In SQL Server 2016 ist die einzige externe Sprache unterstützt R und die externen skriptanforderungen werden von verarbeitet [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. Klicken Sie in SQL Server 2017 R und Python sind unterstützte externe Sprachen, und die externen skriptanforderungen werden verarbeitet, indem [!INCLUDE[rsql_productname_md](../../includes/rsql-productnamenew-md.md)].

Für R verfolgt diese DMV die Anzahl der R-Aufrufe, die vorgenommen werden, auf einer Instanz. Wenn `rxLinMod` z. B. parallel aufgerufen und ausgeführt wird, wird der Leistungsindikator um 1 erhöht.
 
Für die Sprache R stellen die im Feld *counter_name* angezeigten Leistungsindikatorwerte die Namen von registrierten ScaleR-Funktionen dar. Die Werte im Feld *counter_value* stellen die kumulierte Anzahl von Instanzen für die bestimmte ScaleR-Funktion dar. 

Für Python verfolgt diese DMV die Anzahl der Python-Aufrufe, die vorgenommen werden, auf einer Instanz.

Die Zählung beginnt, wenn das Feature für die Instanz installiert und aktiviert wird und bleibt kumulativ, bis die Datei, die den Status verwaltet, von einem Administrator gelöscht oder überschrieben wird. Daher ist es im Allgemeinen nicht möglich, die Werte in *counter_value*zurückzusetzen. Zum Überwachen der Nutzung nach Sitzung, Kalenderzeiten oder anderen Intervallen wird empfohlen, dass Sie die Leistungsindikatoren in einer Tabelle erfassen.

### <a name="registration-of-external-script-functions-in-r"></a>Registrierung externer Skriptfunktionen in R

R unterstützt beliebige Skripts und die R-Community stellt viele Tausende Pakete, die jeweils über eigene Funktionen und Methoden. Diese DMV überwacht jedoch nur die ScaleR-Funktionen, die mit SQL Server-R Services installiert sind.

Die Registrierung dieser Funktionen wird beim Installieren des Features durchgeführt, und registrierte Funktionen können nicht hinzugefügt oder gelöscht werden.

## <a name="examples"></a>Beispiele  
  
### <a name="viewing-the-number-of-r-scripts-run-on-the-server"></a>Anzeigen der Anzahl der auf dem Server ausgeführten R-Skripts  
 Im folgenden Beispiel wird die kumulative Anzahl von externen Skriptausführungen für die R-Sprache angezeigt.  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'R';
```  

### <a name="viewing-the-number-of-python-scripts-run-on-the-server"></a>Anzeigen der Anzahl von Python Ausführen von Skripts auf dem server  
 Das folgende Beispiel zeigt die kumulierte Anzahl von externen skriptausführungen für die Python-Sprache.  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'Python';
```  

  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten und -funktionen im Zusammenhang mit der Ausführung &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md) 
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

