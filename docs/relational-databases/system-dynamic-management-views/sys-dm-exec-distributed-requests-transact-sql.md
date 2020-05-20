---
title: sys. dm_exec_distributed_requests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_REQUESTS
- DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- sys.dm_exec_distributed_sql_requests management view
- PolyBase
- dm_exec_distributed_sql_requests management view
ms.assetid: c041d416-d8c6-435e-a563-6a310abd33e3
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 52a1ee453d0a516bc2dc1fd42dcd4439272d844c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821150"
---
# <a name="sysdm_exec_distributed_requests-transact-sql"></a>sys. dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen Anforderungen, die derzeit oder vor kurzem in polybase-Abfragen aktiv sind. Es wird eine Zeile pro Anforderung/Abfrage aufgelistet.  
  
 Basierend auf der Sitzungs-und Anforderungs-ID kann ein Benutzer dann die tatsächlich für die Ausführung generierten Anforderungen über sys. dm_exec_distributed_requests abrufen. Beispielsweise wird eine Abfrage, die reguläre SQL-Tabellen und externe SQL-Tabellen enthält, in verschiedene Anweisungen/Anforderungen zerlegt, die auf den verschiedenen Computeknoten ausgeführt werden. Zum Nachverfolgen der verteilten Schritte auf allen Computeknoten führen wir eine "globale" Ausführungs-ID ein, die verwendet werden kann, um alle Vorgänge auf den Computeknoten zu verfolgen, die einer bestimmten Anforderung bzw. einem Operator zugeordnet sind.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Der Schlüssel für diese Ansicht. Eindeutige numerische ID, die der Anforderung zugeordnet ist.|Eindeutig für alle Anforderungen im System.|  
|execution_id|**nvarchar (32**|Eindeutige numerische ID, die der Sitzung zugeordnet ist, in der die Abfrage ausgeführt wurde.||  
|status|**nvarchar (32**|Aktueller Status der Anforderung.|"Pending", "autorisieren", "acquiresystemresources", "Initialisieren", "Plan", "", "", "", "...", "" wird ausgeführt "," abgebrochen "," abgeschlossen "," failed "," abgebrochen ".|  
|error_id|**nvarchar (36)**|Eindeutige ID des Fehlers, der der Anforderung zugeordnet ist, sofern vorhanden.|Auf NULL festgelegt, wenn kein Fehler aufgetreten ist.|  
|start_time|**datetime**|Der Zeitpunkt, zu dem die Ausführung der Anforderung gestartet wurde.|0 bei Anforderungen in der Warteschlange; Andernfalls ist ein gültiger DateTime-Wert kleiner oder gleich der aktuellen Zeit.|  
|end_time|**datetime**|Der Zeitpunkt, zu dem die Engine das Kompilieren der Anforderung abgeschlossen hat.|NULL für Warteschlangen-oder aktive Anforderungen; andernfalls ein gültiger DateTime-Wert, der kleiner oder gleich der aktuellen Zeit ist.|  
|total_elapsed_time|**int**|Verstrichene Zeit seit dem Start der Anforderung in Millisekunden.|Zwischen 0 und dem Unterschied zwischen start_time und end_time. Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, ist total_elapsed_time weiterhin der Höchstwert. Mit dieser Bedingung wird die Warnung "der Höchstwert wurde überschritten" generiert. Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei polybase mit dynamischen Verwaltungs Sichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
