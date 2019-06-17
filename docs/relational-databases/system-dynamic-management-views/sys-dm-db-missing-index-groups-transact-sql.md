---
title: Sys. dm_db_missing_index_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_groups
- sys.dm_db_missing_index_groups_TSQL
- dm_db_missing_index_groups
- dm_db_missing_index_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_missing_index_groups dynamic management view
- missing indexes feature [SQL Server], sys.dm_db_missing_index_groups dynamic management view
ms.assetid: 9cc00acd-d83d-49f8-be72-5b2aebed246b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f205632359b7bd40f446ced41cccdf43e984709b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62507788"
---
# <a name="sysdmdbmissingindexgroups-transact-sql"></a>sys.dm_db_missing_index_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Diese DMV gibt Informationen zu Indizes, die einer bestimmten Index Gruppe angehören, mit Ausnahme von räumlichen Indizes fehlen. 
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, diese Informationen bereitstellen, wird jede Zeile, die Daten enthält, die zum verbundenen Mandanten gehören nicht herausgefiltert.  
   
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**index_group_handle**|**int**|Identifiziert eine Gruppe fehlender Indizes.|  
|**index_handle**|**int**|Identifiziert einen fehlenden Index, zu der angegebenen Gruppe gehört **Index_group_handle**.<br /><br /> Eine Indexgruppe enthält nur einen Index.|  
  
## <a name="remarks"></a>Hinweise  
 Informationen, die vom **Sys. dm_db_missing_index_groups** wird aktualisiert, wenn eine Abfrage vom Abfrageoptimierer optimiert wird, und wird nicht beibehalten. Informationen zu fehlenden Indizes werden nur bis zum Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufbewahrt. Datenbankadministratoren sollten regelmäßig Sicherungskopien der Informationen zu fehlenden Indizes erstellen, wenn Sie sie nach dem Wiederverwenden des Servers beibehalten möchten.  
  
 Keine Spalte des Ausgaberesultsets stellt einen Schlüssel dar, gemeinsam bilden sie jedoch einen Indexschlüssel.  

  >[!NOTE]
  >Das Resultset für diese DMV wird auf 600 Zeilen beschränkt. Jede Zeile enthält einen fehlenden Index. Wenn Sie mehr als 600 fehlende Indizes verfügen, sollten Sie die vorhandenen fehlende Indizes behandeln, damit Sie Sie dann die neuere anzeigen können.
  
## <a name="permissions"></a>Berechtigungen  
 Zum Abfragen dieser dynamischen Verwaltungssicht muss den Benutzern die VIEW SERVER STATE-Berechtigung oder eine Berechtigung, die die VIEW SERVER STATE-Berechtigung impliziert, erteilt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
