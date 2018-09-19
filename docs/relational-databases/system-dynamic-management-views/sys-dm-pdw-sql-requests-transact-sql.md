---
title: Sys. dm_pdw_sql_requests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 44e19609-902c-46cf-acdf-19ea75011365
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1647424ce9350cbd7f7d591b510799e12d03f3a2
ms.sourcegitcommit: b8e2e3e6e04368aac54100c403cc15fd4e4ec13a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45563487"
---
# <a name="sysdmpdwsqlrequests-transact-sql"></a>Sys. dm_pdw_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen über alle Verteilungen von SQL Server-Abfrage als Teil eines SQL-Schritts in der Abfrage.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Eindeutiger Bezeichner der Abfrage zu der diese SQL-Abfrage-Distribution gehört.<br /><br /> Anforderungs-ID, Step_index und Distribution_id bilden den Schlüssel für diese Ansicht ein.|Finden Sie im Anforderungs-ID [dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Der Index des abfrageschritts, die diesem Verteilungspunkt gehört.<br /><br /> Anforderungs-ID, Step_index und Distribution_id bilden den Schlüssel für diese Ansicht ein.|Finden Sie unter Step_index in [dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|pdw_node_id|**int**|Eindeutiger Bezeichner des Knotens, auf denen diese Verteilung für die Abfrage ausgeführt wird.|Finden Sie unter Node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**int**|Eindeutiger Bezeichner der Verteilung auf der diese Abfrage Verteilung ausgeführt wird.<br /><br /> Anforderungs-ID, Step_index und Distribution_id bilden den Schlüssel für diese Ansicht ein.|Finden Sie unter Distribution_id in [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md). Legen Sie auf-1 für Anforderungen, die im Knotenbereich nicht den Verteilungsbereich ausgeführt.|  
|status|**nvarchar(32)**|Aktuelle Status der Verteilung von Abfragen.|Ausstehend "" "ausführen", "Fehler", "abgebrochen", "abgeschlossen", wurde abgebrochen, CancelSubmitted|  
|error_id|**nvarchar(36)**|Eindeutiger Bezeichner des Fehlers diese Verteilung von Abfragen, ggf. zugeordnet.|Finden Sie unter Fehler-ID in [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Auf NULL festgelegt, wenn kein Fehler aufgetreten ist.|  
|start_time|**datetime**|Zeit, die mit der Verteilung Ausführung gestartet wurde.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich Start_time des abfrageschritts gehört dieser Verteilung von Abfragen|  
|end_time|**datetime**|Zeitpunkt, an dem diese Verteilung von Abfragen die Ausführung abgeschlossen, wurde abgebrochen oder fehlerhaft.|Größer oder gleich der Startzeit oder auf NULL festgelegt werden, wenn die Verteilung von Abfragen laufende oder in der Warteschlange ist.|  
|total_elapsed_time|**int**|Stellt die Zeit, die die Verteilung für die Abfrage, die in Millisekunden ausgeführt wurde.|Größer oder gleich 0. Das Delta der Start_time gleich und End_time abgeschlossen, Fehler, oder Verteilungen der Abfrage abgebrochen.<br /><br /> Wenn Total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, weiterhin Total_elapsed_time der maximale Wert sein. Diese Bedingung generiert die Warnung "der maximale Wert überschritten wurde."<br /><br /> Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
|row_count|**bigint**|Anzahl der Zeilen geändert oder von dieser Verteilung von Abfragen gelesen werden.|-1 für Vorgänge, die nicht ändern oder Daten, z. B. CREATE TABLE und DROP TABLE zurück.|  
|spid|**int**|Sitzungs-Id für die Verteilung von Abfragen mit SQL Server-Instanz.||  
|Befehl|**nvarchar(4000)**|Die Volltext-Befehl für diese Verteilung von Abfragen.|Eine beliebige gültige Abfrage oder einen Anforderung-Zeichenfolge.|  
  
 Informationen, die maximale Anzahl Zeilen, die von dieser Sicht beibehalten können, finden Sie im Abschnitt "maximale Systemwerte anzeigen" in der [Mindest- und Höchstwerte (SQL Server PDW)](http://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9) Thema.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
