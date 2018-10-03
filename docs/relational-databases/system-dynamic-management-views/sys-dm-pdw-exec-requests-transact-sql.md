---
title: dm_pdw_exec_requests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c2a1978aeea7ec69ea45bc088bbdff432de3c9f4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621868"
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu Anforderungen, die alle zurzeit oder zuletzt im aktiven [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Sie enthält eine Zeile für jede Anforderung bzw. die Abfrage.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Der Schlüssel für diese Sicht. Eindeutige numerische Id der Anforderung zugeordnet ist.|Für alle Anforderungen im System eindeutig.|  
|session_id|**nvarchar(32)**|Eindeutige numerische Id in Zusammenhang mit der Sitzung, in der diese Abfrage ausgeführt wurde. Finden Sie unter [dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|Aktuellen Status der Anforderung.|"Wird ausgeführt", "Angehalten", "Abgeschlossen", "Abgebrochen", "Failed".|  
|submit_time|**datetime**|Zeit mit der die Anforderung gesendet wurde für die Ausführung.|Gültige **"DateTime"** kleiner oder gleich der aktuellen Uhrzeit und Start_time.|  
|start_time|**datetime**|Zeitpunkt, an dem die anforderungsausführung gestartet wurde.|NULL für Anforderungen in der Warteschlange. andernfalls, gültige **"DateTime"** kleiner oder gleich der aktuellen Zeit.|  
|end_compile_time|**datetime**|Zeitpunkt, an dem das Modul abgeschlossen Kompilieren die Anforderung.|NULL für Anforderungen, die noch nicht kompiliert wurden. andernfalls ein gültiger **"DateTime"** Start_time kleiner und kleiner als oder gleich der aktuellen Zeit.|
|end_time|**datetime**|Zeitpunkt, an dem die anforderungsausführung abgeschlossen, Fehler, oder wurde abgebrochen.|NULL für in der Warteschlange oder aktiven Anforderungen. andernfalls, eine gültige **"DateTime"** kleiner oder gleich der aktuellen Zeit.|  
|total_elapsed_time|**int**|Bei der Ausführung verstrichene Zeit seit Beginn die Anforderung, in Millisekunden.|Zwischen 0 und der Unterschied zwischen Start_time "und" End_time.<br /><br /> Wenn Total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, weiterhin Total_elapsed_time der maximale Wert sein. Diese Bedingung generiert die Warnung "der maximale Wert überschritten wurde."<br /><br /> Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
|Bezeichnung|**nvarchar(255)**|Optionale Bezeichnung-Zeichenfolge, die einige Anweisungen SELECT-Abfrage zugeordnet.|Eine beliebige Zeichenfolge mit "a – Z", "A – Z", "0-9,"_".|  
|error_id|**nvarchar(36)**|Eindeutige Id des Fehlers der Anforderung zugeordnet ist, falls vorhanden.|Finden Sie unter [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); auf NULL festgelegt werden, wenn kein Fehler aufgetreten ist.|  
|database_id|**int**|Der Bezeichner der Datenbank, die durch explizite Kontext (z. B. Verwendung DB_X) verwendet.|Finden Sie unter-Id in [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|Befehl|**nvarchar(4000)**|Enthält den vollständigen Text der Anforderung durch den Benutzer gesendet.|Alle gültigen Abfrage oder einen Anforderung-Text. Abfragen, die länger als 4.000 Byte sind, werden abgeschnitten.|  
|resource_class|**nvarchar(20)**|Die Ressourcenklasse für diese Anforderung. Finden Sie im Zusammenhang **Concurrency_slots_used** in [sys.dm_pdw_resource_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).|"Smallrc"<br /><br /> "Mediumrc"<br /><br /> "Largerc"<br /><br /> "Xlargerc"|  
  
 Informationen zu den maximalen Zeilen, die von dieser Sicht beibehalten, finden Sie unter "Minimum und Maximum Values" in der [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung.  
  
## <a name="security"></a>Security  
 dm_pdw_exec_requests filtert die Ergebnisse der Abfrage entsprechend datenbankspezifischen Berechtigungen nicht. Anmeldungen mit VIEW SERVER STATE-Berechtigung können die Ergebnisse Abfrageergebnisse für alle Datenbanken abrufen  
  
> [!WARNING]  
>  Angreifer können dm_pdw_exec_requests für das Abrufen von Informationen über bestimmte Datenbankobjekte, indem Sie einfache Maßnahmen handeln, VIEW SERVER STATE-Berechtigung und ohne eine datenbankspezifische-Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
