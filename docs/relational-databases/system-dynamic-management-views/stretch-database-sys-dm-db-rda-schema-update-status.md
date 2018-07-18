---
title: sys.dm_db_rda_schema_update_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_schema_update_status
- sys.dm_db_rda_schema_update_status_TSQL
- dm_db_rda_schema_update_status
- dm_db_rda_schema_update_status_TSQL
helpviewer_keywords:
- sys.dm_db_rda_schema_update_status dynamic management view
ms.assetid: 364e3caa-a7c6-4be5-a029-0b19da34de3e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbd99f97902dbbd3c097b76b1f119f400f97c6f6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420059"
---
# <a name="stretch-database---sysdmdbrdaschemaupdatestatus"></a>Stretch Database - sys.dm_db_rda_schema_update_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Aufgabe des Schema-Update für das remotedatenarchiv jeder Stretch-aktivierte Tabelle in der aktuellen Datenbank. Aufgaben werden anhand der Task-ID identifiziert.  
  
 **dm_db_rda_schema_update_status** is scoped to the current database context. Stellen Sie sicher, dass Sie im Rahmen der Tabelle mit aktivierter Funktion Stretch-Datenbank sind für das Schema Aktualisierungsstatus anzuzeigen.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Die ID der lokalen Stretch-aktivierte Tabelle, deren remotedatenarchiv Schema, wird aktualisiert.|  
|**database_id**|**int**|Die ID der Datenbank, die lokale Stretch-aktivierte Tabelle enthält.|  
|**task_id**|**bigint**|Die ID des remote Data Archive Schema Update Tasks.|  
|**task_type**|**int**|Der Typ des remote Data Archive Schema Update Tasks.|  
|**task_type_desc**|**nvarchar**|Die Beschreibung des Typs von der remote Data Archive Schemaaufgabe Update.|  
|**task_state**|**int**|Der Status des remote Data Archive Schema Update Tasks.|  
|**task_state_des**|**nvarchar**|Die Beschreibung des Status des remote Data Archive Schema Update Tasks.|  
|**start_time_utc**|**datetime**|Die UTC-Zeit, an der das Schemaupdate Schritte remotedatenarchiv.|  
|**end_time_utc**|**datetime**|Die UTC-Zeit, an der das Schemaupdate remotedatenarchiv, wurde beendet.|  
|**error_number**|**int**|Wenn die Aktualisierung des Schemas remote Data Archive, die Fehlernummer des Fehlers ein Fehler, die aufgetreten sind auftritt; andernfalls Null.|  
|**error_severity**|**int**|Wenn die Aktualisierung des Schemas remote Data Archive, den Schweregrad des Fehlers ein Fehler, die aufgetreten sind auftritt; andernfalls Null.|  
|**error_state**|**int**|Wenn die Aktualisierung des Schemas remote Data Archive, den Status des Fehlers ein Fehler, die aufgetreten sind auftritt; andernfalls Null. Die Error_state gibt an, die Bedingung oder den Speicherort, in dem der Fehler aufgetreten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
