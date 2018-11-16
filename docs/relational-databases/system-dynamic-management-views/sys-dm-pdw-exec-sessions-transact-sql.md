---
title: dm_pdw_exec_sessions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31c262b3-7e4d-44c4-af71-aaef0fd1a980
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: dade699d433ce2b7ab95d3f09f370adedc8bcf2e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664059"
---
# <a name="sysdmpdwexecsessions-transact-sql"></a>dm_pdw_exec_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen Sitzungen auf dem Gerät zurzeit oder zuletzt geöffnet. Sie enthält eine Zeile für jede Sitzung.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|session_id|**nvarchar(32)**|Die Id des die aktuelle Abfrage oder der letzten Abfrage ausführen (wenn die Sitzung beendet wird, und zum Zeitpunkt der Beendigung die Abfrage ausgeführt wurde). Der Schlüssel für diese Sicht.|Für alle Sitzungen im System eindeutig.|  
|status|**nvarchar(10)**|Für die aktuellen Sitzungen identifiziert, ob die Sitzung derzeit aktiv oder im Leerlauf befindet. Für die vergangenen Sitzungen die Sitzung, die Status angezeigt werden kann geschlossen oder abgebrochen wird (wenn die Sitzung zwangsweise geschlossen wurde).|'AKTIV","GESCHLOSSEN","IM LEERLAUF', BEENDET' '|  
|request_id|**nvarchar(32)**|Die Id der aktuellen Abfrage oder des letzten Abfrage, die ausgeführt werden soll.|Für alle Anforderungen im System eindeutig. NULL, wenn keine ausgeführt wurde.|  
|security_id|**varbinary(85)**|Sicherheits-ID des Prinzipals die-Sitzung ausführt.||  
|login_name|**nvarchar(128)**|Der Anmeldename, der der Prinzipal, der die Sitzung ausgeführt werden soll.|Eine beliebige Zeichenfolge, die Benutzer-Namenskonventionen entsprechen.|  
|login_time|**datetime**|Datum und Uhrzeit, an dem der Benutzer angemeldet, und dieser Sitzung erstellt wurde.|Gültige **"DateTime"** vor der aktuellen Zeit.|  
|query_count|**int**|Erfasst die Anzahl der Abfragen/BeschreibungDiese-Sitzung wurde seit der Erstellung ausgeführt werden.|Größer als oder gleich 0.|  
|is_transactional|**bit**|Zeichnet auf, ob eine Sitzung derzeit innerhalb einer Transaktion befindet.|für automatische Commits 0, 1 für transaktionale.|  
|Client-ID|**nvarchar(255)**|Zeichnet Clientinformationen für die Sitzung.|Eine beliebige gültige Zeichenfolge.|  
|App-Name|**nvarchar(255)**|Erfasst Informationen zum Anwendungsnamen im Rahmen des Verbindungsprozesses optional festlegen.|Eine beliebige gültige Zeichenfolge.|  
|sql_spid|**int**|Die ID der SPID. Verwenden der `session_id` in dieser Sitzung. Verwenden der `sql_spid` Spalte hinzufügen **sys.dm_pdw_nodes_exec_sessions**.<br /><br /> **\*\* Warnung \* \***  enthält diese Spalte geschlossene SPIDs.||  
  
 Informationen, die maximale Anzahl Zeilen, die von dieser Sicht beibehalten können, finden Sie im Abschnitt "maximale Systemwerte anzeigen" in der [Mindest- und Höchstwerte (SQL Server PDW)](https://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9) Thema.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
