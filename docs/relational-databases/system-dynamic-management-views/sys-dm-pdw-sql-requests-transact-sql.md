---
description: sys.dm_pdw_sql_requests (Transact-SQL)
title: sys.dm_pdw_sql_requests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 44e19609-902c-46cf-acdf-19ea75011365
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 360d6c5f5535b0e0702d1c7aede8721f27f88daf
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482485"
---
# <a name="sysdm_pdw_sql_requests-transact-sql"></a>sys.dm_pdw_sql_requests (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält Informationen zu allen SQL Server Abfrage Verteilungen als Teil eines SQL-Schritts in der Abfrage.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Eindeutiger Bezeichner der Abfrage, zu der diese SQL-Abfrage Verteilung gehört.<br /><br /> request_id, step_index und distribution_id bilden den Schlüssel für diese Ansicht.|Weitere Informationen finden Sie unter request_id in [sys.dm_pdw_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Index des Abfrage Schritts, zu dem diese Distribution gehört.<br /><br /> request_id, step_index und distribution_id bilden den Schlüssel für diese Ansicht.|Weitere Informationen finden Sie unter step_index in [sys.dm_pdw_request_steps &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|pdw_node_id|**int**|Eindeutiger Bezeichner des Knotens, auf dem diese Abfrage Verteilung ausgeführt wird.|Weitere Informationen finden Sie unter node_id in [sys.dm_pdw_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**int**|Eindeutiger Bezeichner der Verteilung, für die diese Abfrage Verteilung ausgeführt wird.<br /><br /> request_id, step_index und distribution_id bilden den Schlüssel für diese Ansicht.|Weitere Informationen finden Sie unter distribution_id in [sys.pdw_distributions &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md). Legen Sie für Anforderungen, die im Knotenbereich ausgeführt werden, und nicht für den Verteilungsbereich den Wert-1 fest.|  
|status|**nvarchar(32)**|Aktueller Status der Abfrage Verteilung.|Ausstehend, wird ausgeführt, fehlerhaft, abgebrochen, abgeschlossen, abgebrochen, canceleingereicht|  
|error_id|**nvarchar (36)**|Eindeutiger Bezeichner des Fehlers, der dieser Abfrage Verteilung zugeordnet ist, sofern vorhanden.|Weitere Informationen finden Sie unter error_id in [sys.dm_pdw_errors &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Auf NULL festgelegt, wenn kein Fehler aufgetreten ist.|  
|start_time|**datetime**|Zeitpunkt, zu dem die Ausführung der Abfrage Verteilung gestartet wurde.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich start_time des Abfrage Schritts, zu dem diese Abfrage Verteilung gehört.|  
|end_time|**datetime**|Der Zeitpunkt, zu dem diese Abfrage Verteilung die Ausführung abgeschlossen hat, abgebrochen wurde oder fehlgeschlagen ist.|Die Startzeit ist größer als oder gleich oder auf NULL festgelegt, wenn die Abfrage Verteilung fortlaufend oder in die Warteschlange eingereiht wird.|  
|total_elapsed_time|**int**|Stellt die Zeit in Millisekunden dar, die die Abfrage Verteilung ausgeführt wurde.|Größer oder gleich 0 (null). Entspricht dem Delta von start_time und end_time für abgeschlossene, fehlgeschlagene oder abgebrochene Abfrage Verteilungen.<br /><br /> Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, ist total_elapsed_time weiterhin der Höchstwert. Mit dieser Bedingung wird die Warnung "der Höchstwert wurde überschritten" generiert.<br /><br /> Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
|row_count|**bigint**|Anzahl der von dieser Abfrage Verteilung geänderten oder gelesenen Zeilen.|-1 für Vorgänge, die keine Daten ändern oder zurückgeben, z. b. CREATE TABLE und DROP TABLE.|  
|spid|**int**|Die Sitzungs-ID auf der SQL Server Instanz, die die Abfrage Verteilung ausgeführt hat.||  
|command|**nvarchar(4000)**|Vollständiger Text des Befehls für diese Abfrage Verteilung.|Eine beliebige gültige Abfrage oder Anforderungs Zeichenfolge.|  
  
 Informationen über die maximale Anzahl von Zeilen, die in dieser Sicht beibehalten werden, finden Sie im Abschnitt "Metadaten" im Thema [Kapazitäts Limits](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Azure Synapse Analytics und parallele Data Warehouse dynamische Verwaltungs Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
