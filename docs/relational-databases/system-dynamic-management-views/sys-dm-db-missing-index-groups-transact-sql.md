---
title: sys. dm_db_missing_index_groups (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c92162cb78043b078e38dac63e22a3ca3267251c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828077"
---
# <a name="sysdm_db_missing_index_groups-transact-sql"></a>sys.dm_db_missing_index_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Diese DMV gibt Informationen zu Indizes zurück, die in einer bestimmten Indexgruppe fehlen, ausgenommen räumliche Indizes. 
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, dass diese Informationen verfügbar gemacht werden, wird jede Zeile, die Daten enthält, die nicht zum verbundenen Mandanten gehören, herausgefiltert.  
   
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**index_group_handle**|**int**|Identifiziert eine Gruppe fehlender Indizes.|  
|**index_handle**|**int**|Identifiziert einen fehlenden Index, der zu der durch **index_group_handle** angegebenen Gruppe gehört.<br /><br /> Eine Indexgruppe enthält nur einen Index.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die von **sys.dm_db_missing_index_groups** zurückgegebenen Informationen werden aktualisiert, wenn eine Abfrage vom Abfrageoptimierer optimiert wird, und sind nicht persistent. Informationen zu fehlenden Indizes werden nur bis zum Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufbewahrt. Datenbankadministratoren sollten regelmäßig Sicherungskopien der Informationen zu fehlenden Indizes erstellen, wenn Sie sie nach dem Wiederverwenden des Servers beibehalten möchten.  
  
 Keine Spalte des Ausgaberesultsets stellt einen Schlüssel dar, gemeinsam bilden sie jedoch einen Indexschlüssel.  

  >[!NOTE]
  >Das Resultset für diese DMV ist auf 600 Zeilen beschränkt. Jede Zeile enthält einen fehlenden Index. Wenn Sie über mehr als 600 fehlende Indizes verfügen, sollten Sie die vorhandenen fehlenden Indizes ansprechen, damit Sie die neueren Indizes anzeigen können.
  
## <a name="permissions"></a>Berechtigungen  
 Zum Abfragen dieser dynamischen Verwaltungssicht muss den Benutzern die VIEW SERVER STATE-Berechtigung oder eine Berechtigung, die die VIEW SERVER STATE-Berechtigung impliziert, erteilt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_db_missing_index_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys. dm_db_missing_index_details &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys. dm_db_missing_index_group_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
