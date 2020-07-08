---
title: sys. dm_db_rda_schema_update_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_schema_update_status
- sys.dm_db_rda_schema_update_status_TSQL
- dm_db_rda_schema_update_status
- dm_db_rda_schema_update_status_TSQL
helpviewer_keywords:
- sys.dm_db_rda_schema_update_status dynamic management view
ms.assetid: 364e3caa-a7c6-4be5-a029-0b19da34de3e
author: pmasl
ms.author: pelopes
ms.openlocfilehash: b74f408bdb2be61076d5034478dc6743259fed6a
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053646"
---
# <a name="stretch-database---sysdm_db_rda_schema_update_status"></a>Stretch Database-sys. dm_db_rda_schema_update_status
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Enthält eine Zeile für jeden Schema Aktualisierungs Task für das Remote Datenarchiv der einzelnen Stretch-aktivierten Tabellen in der aktuellen Datenbank. Tasks werden durch ihre Aufgaben-IDs identifiziert.  
  
 **dm_db_rda_schema_update_status** ist auf den aktuellen Daten Bank Kontext beschränkt. Stellen Sie sicher, dass Sie sich im Daten Bank Kontext der Stretch-aktivierten Tabelle befinden, für die Sie den Status des Schema Updates anzeigen möchten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Die ID der lokalen Stretch-aktivierten Tabelle, deren Remote Datenarchiv-Schema aktualisiert wird.|  
|**database_id**|**int**|Die ID der Datenbank, die die lokale Stretch-aktivierte Tabelle enthält.|  
|**task_id**|**bigint**|Die ID des Remote-Datenarchiv-Schema Aktualisierungs Tasks.|  
|**task_type**|**int**|Der Typ der Remote Datenarchiv-Schema Aktualisierungs Aufgabe.|  
|**task_type_desc**|**nvarchar**|Die Beschreibung des Typs der Aufgabe zum Aktualisieren des Schemas für Remote Datenarchive.|  
|**task_state**|**int**|Der Status der Aufgabe zum Aktualisieren des Schemas für das Remote Datenarchiv.|  
|**task_state_des**|**nvarchar**|Die Beschreibung des Zustands der Aufgabe zum Aktualisieren des Schemas für das Remote Datenarchiv.|  
|**start_time_utc**|**datetime**|Die UTC-Zeit, zu der das Update des Remote Datenarchiv-Schemas gestartet wurde.|  
|**end_time_utc**|**datetime**|Die UTC-Zeit, zu der das Update des Remote Datenarchiv-Schemas abgeschlossen wurde.|  
|**error_number**|**int**|Wenn die Aktualisierung des Remote Datenarchiv-Schemas fehlschlägt, wird die Fehlernummer des aufgetretenen Fehlers angezeigt. andernfalls NULL.|  
|**error_severity**|**int**|Wenn die Aktualisierung des Remote Datenarchiv-Schemas fehlschlägt, wird der Schweregrad des aufgetretenen Fehlers verursacht. andernfalls NULL.|  
|**error_state**|**int**|Wenn bei der Aktualisierung des Remote Datenarchiv-Schemas ein Fehler auftritt, wird der Status des aufgetretenen Fehlers angezeigt. andernfalls NULL. Der ERROR_STATE gibt die Bedingung oder den Speicherort an, an dem der Fehler aufgetreten ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
