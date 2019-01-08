---
title: Sys.dm_exec_distributed_requests (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 78604c723c4c19e68a6c29fd3113de3d69d36d44
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52532786"
---
# <a name="sysdmexecdistributedrequests-transact-sql"></a>Sys.dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu Anforderungen, die alle zurzeit oder zuletzt in der PolyBase-Abfragen aktiv. Sie enthält eine Zeile für jede Anforderung bzw. die Abfrage.  
  
 Basierend auf der Sitzung und Anforderungs-ID, ein Benutzer kann dann abrufen, die tatsächlichen verteilte Anforderungen generiert, um - die über sys.dm_exec_distributed_requests ausgeführt werden. Beispielsweise wird eine Abfrage, die im Zusammenhang mit regulären SQL und externe SQL-Tabellen in verschiedenen Anweisungen/Anforderungen, die über die verschiedenen Computeknoten ausgeführt zerlegt werden. Um die verteilte Schritte auf allen Computeknoten nachzuverfolgen, führen wir eine 'global' ausführungs-ID, mit dem verfolgen alle Vorgänge auf den Computeknoten, die eine bestimmte Anforderung und Operator bzw. zugeordnet werden kann.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Der Schlüssel für diese Sicht. Eindeutige numerische Id der Anforderung zugeordnet ist.|Für alle Anforderungen im System eindeutig.|  
|execution_id|**Nvarchar (32**|Eindeutige numerische Id in Zusammenhang mit der Sitzung, in der diese Abfrage ausgeführt wurde.||  
|status|**Nvarchar (32**|Aktuellen Status der Anforderung.|"Ausstehend" fehlgeschlagen "Autorisieren", "AcquireSystemResources", "Initialisierung", "Plan", "Analyse", "AquireResources', 'Running', 'Abbrechen', 'Vollständig'," ","Abgebrochen".|  
|error_id|**nvarchar(36)**|Eindeutige Id des Fehlers der Anforderung zugeordnet ist, falls vorhanden.|Auf NULL festgelegt, wenn kein Fehler aufgetreten ist.|  
|start_time|**datetime**|Zeitpunkt, an dem die anforderungsausführung gestartet wurde.|0 für Anforderungen in der Warteschlange andernfalls, gültige DateTime-Wert kleiner oder gleich der aktuellen Zeit.|  
|end_time|**datetime**|Zeitpunkt, an dem das Modul abgeschlossen Kompilieren die Anforderung.|NULL für in der Warteschlange oder aktiven Anforderungen. andernfalls einen gültigen DateTime-Wert kleiner oder gleich der aktuellen Zeit.|  
|total_elapsed_time|**int**|Bei der Ausführung verstrichene Zeit seit Beginn die Anforderung, in Millisekunden.|Zwischen 0 und der Unterschied zwischen Start_time "und" End_time. Wenn Total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, weiterhin Total_elapsed_time der maximale Wert sein. Diese Bedingung generiert die Warnung "der maximale Wert überschritten wurde." Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
  
## <a name="see-also"></a>Siehe auch  
 [PolyBase-Problembehandlung mit dynamischen Verwaltungssichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
