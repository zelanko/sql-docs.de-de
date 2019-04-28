---
title: dm_pdw_exec_requests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 72c449ee83798a99109029fc2d0b91e2b8c1e2b6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62691326"
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu Anforderungen, die alle zurzeit oder zuletzt im aktiven [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Sie enthält eine Zeile für jede Anforderung bzw. die Abfrage.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Der Schlüssel für diese Sicht. Eindeutige numerische ID der Anforderung zugeordnet ist.|Für alle Anforderungen im System eindeutig.|  
|session_id|**nvarchar(32)**|Eindeutige numerische ID in Zusammenhang mit der Sitzung, in der diese Abfrage ausgeführt wurde. Finden Sie unter [dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|Aktuellen Status der Anforderung.|'Running', 'Suspended', 'Completed', 'Canceled', 'Failed'.|  
|submit_time|**datetime**|Zeit mit der die Anforderung gesendet wurde für die Ausführung.|Gültige **"DateTime"** kleiner oder gleich der aktuellen Uhrzeit und Start_time.|  
|start_time|**datetime**|Zeitpunkt, an dem die anforderungsausführung gestartet wurde.|NULL für Anforderungen in der Warteschlange. andernfalls, gültige **"DateTime"** kleiner oder gleich der aktuellen Zeit.|  
|end_compile_time|**datetime**|Zeitpunkt, an dem das Modul abgeschlossen Kompilieren die Anforderung.|NULL für Anforderungen, die noch nicht kompiliert wurden. andernfalls ein gültiger **"DateTime"** Start_time kleiner und kleiner als oder gleich der aktuellen Zeit.|
|end_time|**datetime**|Zeitpunkt, an dem die anforderungsausführung abgeschlossen, Fehler, oder wurde abgebrochen.|NULL für in der Warteschlange oder aktiven Anforderungen. andernfalls, eine gültige **"DateTime"** kleiner oder gleich der aktuellen Zeit.|  
|total_elapsed_time|**int**|Bei der Ausführung verstrichene Zeit seit Beginn die Anforderung, in Millisekunden.|Zwischen 0 und der Unterschied zwischen Start_time "und" End_time.</br></br> Wenn Total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, weiterhin Total_elapsed_time der maximale Wert sein. Diese Bedingung generiert die Warnung "der maximale Wert überschritten wurde."</br></br> Der maximale Wert in Millisekunden ist identisch mit rund 24,8 Tage.|  
|Bezeichnung|**nvarchar(255)**|Optionale Bezeichnung-Zeichenfolge, die einige Anweisungen SELECT-Abfrage zugeordnet.|Eine beliebige Zeichenfolge mit "a – Z", "A – Z", "0-9,"_".|  
|error_id|**nvarchar(36)**|Eindeutige ID des Fehlers der Anforderung zugeordnet ist, falls vorhanden.|Finden Sie unter [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); auf NULL festgelegt werden, wenn kein Fehler aufgetreten ist.|  
|database_id|**int**|Der Bezeichner der Datenbank, die durch explizite Kontext (z. B. Verwendung DB_X) verwendet.|Finden Sie unter-ID in [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|Befehl|**nvarchar(4000)**|Enthält den vollständigen Text der Anforderung durch den Benutzer gesendet.|Alle gültigen Abfrage oder einen Anforderung-Text. Abfragen, die länger als 4.000 Byte sind, werden abgeschnitten.|  
|resource_class|**nvarchar(20)**|Die Ressourcenklasse für diese Anforderung. Finden Sie im Zusammenhang **Concurrency_slots_used** in [sys.dm_pdw_resource_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).  Weitere Informationen zu Ressourcenklassen, finden Sie unter [ressourcenverwaltung Ressourcenklassen und workloadverwaltung](https://docs.microsoft.com/azure/sql-data-warehouse/resource-classes-for-workload-management) |Statische Ressourcenklassen</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Dynamische Ressourcenklassen</br>"Smallrc"</br>MediumRC</br>LargeRC</br>XLargeRC|
|Wichtigkeit (Workload-Klassifizierung ist für die Vorschau für SQL Data Warehouse Gen2 verfügbar. Die Klassifizierung für die Workloadverwaltung und Workloadpriorität (Vorschauversion) ist für Builds mit einem Veröffentlichungsdatum ab dem 09. April 2019 verfügbar.  Builds mit einem früheren Veröffentlichungsdatum sollten nicht für das Testen der Workloadverwaltung verwendet werden.  Um festzustellen, ob der Build workloadverwaltung fähig ist, führen Sie select @@version beim Verbinden mit Ihrer SQL Data Warehouse-Instanz.)|**nvarchar(32)**|Die Bedeutung die Anforderung festlegen eingereicht wurde. Anforderungen mit einer niedrigeren Wichtigkeit werden in der Warteschlange unterbrochenen Zustand verbleiben, wenn höhere Wichtigkeit-Anforderungen gesendet werden.  Anforderungen und einer höheren Priorität werden vor niedriger Wichtigkeit Anforderungen ausgeführt werden, die zuvor gesendet wurden.  Weitere Informationen zu Wichtigkeit, finden Sie unter [Workload Wichtigkeit](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-workload-importance).  |NULL</br>low</br>below_normal</br>Normal (Standard)</br>above_normal</br>high|
  
 Informationen, die maximale Anzahl Zeilen, die von dieser Sicht beibehalten können, finden Sie im Abschnitt "Metadaten" in der [Kapazitätsgrenzen](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) Thema.   
  
## <a name="permissions"></a>Berechtigungen

 Erfordert die VIEW SERVER STATE-Berechtigung.  
  
## <a name="security"></a>Sicherheit

 dm_pdw_exec_requests nicht Abfrageergebnisse entsprechend datenbankspezifischen Berechtigungen zu filtern. Anmeldungen mit VIEW SERVER STATE-Berechtigung können die Ergebnisse Abfrageergebnisse für alle Datenbanken abrufen  
  
>[!WARNING]  
>Angreifer können dm_pdw_exec_requests für das Abrufen von Informationen über bestimmte Datenbankobjekte, indem Sie einfache Maßnahmen handeln, VIEW SERVER STATE-Berechtigung und ohne eine datenbankspezifische-Berechtigung.  
  
## <a name="see-also"></a>Siehe auch

 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md) 
