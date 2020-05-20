---
title: sys. change_tracking_tables (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- change_tracking_tables_TSQL
- sys.change_tracking_tables
- change_tracking_tables
- sys.change_tracking_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], sys.change_tracking_tables
- sys.change_tracking_tables
ms.assetid: 97ec69b6-0d49-4d98-82f0-d3e77ba1ad2b
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c88edbec34a76b585d114c63b411621fd63d70c3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823639"
---
# <a name="change-tracking-catalog-views---syschange_tracking_tables"></a>Änderungsnachverfolgung Katalog Sichten-sys. change_tracking_tables
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Tabelle in der aktuellen Datenbank zurück, für die die Änderungsnachverfolgung aktiviert ist.  
   
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID einer Tabelle, die ein Änderungsjournal aufweist. Die Tabelle kann ein Änderungsjournal aufweisen, auch wenn die Änderungsnachverfolgung zurzeit deaktiviert ist.<br /><br /> Die Tabellen-ID ist innerhalb der Datenbank eindeutig.|  
|is_track_columns_updated_on|**bit**|Aktueller Status der Änderungsnachverfolgung für die Tabelle:<br /><br /> 0 = OFF<br /><br /> 1 = ON|  
|begin_version|**bigint**|Version der Datenbank, als die Änderungsnachverfolgung für die Tabelle begann. Diese Version gibt in der Regel an, wann die Änderungsnachverfolgung aktiviert wurde; dieser Wert wird jedoch zurückgesetzt, wenn die Tabelle abgeschnitten ist.|  
|cleanup_version|**bigint**|Die Version, bis zu der durch ein Cleanup Änderungsnachverfolgungsinformationen möglicherweise gelöscht wurden.|  
|min_valid_version|**bigint**|Minimale gültige Version der Änderungsnachverfolgungsinformationen, die für die Tabelle verfügbar sind.<br /><br /> Beim Abrufen von Änderungen für die Tabelle, die mit dieser Zeile verknüpft ist, muss der Wert für last_sync_version größer oder gleich der in dieser Spalte aufgeführten Version sein. Weitere Informationen finden Sie unter [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md).|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)   
 [Änderungsnachverfolgung Katalog Sichten &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Nachverfolgen von Datenänderungen &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
