---
title: sys. dm_pdw_exec_sessions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/22/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31c262b3-7e4d-44c4-af71-aaef0fd1a980
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3e5e3982f0e8a2470878e06cded3f814871cc0aa
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197084"
---
# <a name="sysdm_pdw_exec_sessions-transact-sql"></a>sys. dm_pdw_exec_sessions (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält Informationen zu allen Sitzungen, die aktuell oder zuletzt auf dem Gerät geöffnet sind. Es wird eine Zeile pro Sitzung aufgelistet.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|session_id|**nvarchar(32)**|Die ID der aktuellen Abfrage oder der letzten Abfrage Ausführung (wenn die Sitzung beendet wird und die Abfrage zum Zeitpunkt der Beendigung ausgeführt wurde). Der Schlüssel für diese Ansicht.|Eindeutig in allen Sitzungen im System.|  
|status|**nvarchar (10)**|Gibt bei aktuellen Sitzungen an, ob die Sitzung zurzeit aktiv ist oder sich im Leerlauf befindet. Für vergangene Sitzungen wird der Sitzungs Status möglicherweise als geschlossen oder abgebrochen angezeigt (wenn die Sitzung zwangsweise geschlossen wurde).|"Active", "Closed", "idle", "beendet"|  
|request_id|**nvarchar(32)**|Die ID der aktuellen Abfrage oder der letzten Abfrage.|Eindeutig für alle Anforderungen im System. NULL, wenn kein Wert ausgeführt wurde.|  
|security_id|**varbinary(85)**|Sicherheits-ID des Prinzipals, der die Sitzung ausgeführt hat.||  
|login_name|**nvarchar(128)**|Der Anmelde Name des Prinzipals, der die Sitzung ausgeführt hat.|Eine beliebige Zeichenfolge, die den Benennungs Konventionen für Benutzer entspricht.|  
|login_time|**datetime**|Datum und Uhrzeit, zu denen der Benutzer angemeldet und diese Sitzung erstellt wurde.|Gültiger **DateTime** -Wert vor der aktuellen Uhrzeit.|  
|query_count|**int**|Erfasst die Anzahl der Abfragen/Anforderer, die diese Sitzung seit der Erstellung ausgeführt hat.|Größer oder gleich 0 (null).|  
|is_transactional|**bit**|Erfasst, ob sich eine Sitzung derzeit in einer Transaktion befindet oder nicht.|0 für automatischen Commit, 1 für transaktional.|  
|client_id|**nvarchar(255)**|Erfasst Client Informationen für die Sitzung.|Eine beliebige gültige Zeichenfolge.|  
|app_name|**nvarchar(255)**|Erfasst Informationen zu Anwendungsnamen, die optional als Teil des Verbindungsprozesses festgelegt werden.|Eine beliebige gültige Zeichenfolge.|  
|sql_spid|**int**|Die ID-Nummer der SPID. Verwenden Sie `session_id` diese Sitzung. Verwenden Sie die- `sql_spid` Spalte, um mit **sys. dm_pdw_nodes_exec_sessions**zu verknüpfen.<br /><br /> Warnung in dieser Spalte sind geschlossene SPIDs enthalten. ** \* \* \* \* **||  
  
 Informationen über die maximale Anzahl von Zeilen, die in dieser Sicht beibehalten werden, finden Sie im Abschnitt "Metadaten" im Thema [Kapazitäts Limits](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
