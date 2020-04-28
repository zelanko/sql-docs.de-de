---
title: sys. dm_audit_actions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_audit_actions_TSQL
- sys.dm_audit_actions
- dm_audit_actions_TSQL
- dm_audit_actions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_audit_actions dynamic management view
ms.assetid: b987c2b9-998a-4a5f-a82d-280dc6963cbe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e6a6c91cb31c9c3036bc95239f0aff9c75fda7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67936974"
---
# <a name="sysdm_audit_actions-transact-sql"></a>sys.dm_audit_actions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Gibt eine Zeile für jede Überwachungsaktion zurück, die im Überwachungsprotokoll festgehalten werden kann, und für jede Überwachungsaktionsgruppe, die als Teil von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit konfiguriert werden kann. Weitere Informationen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Überwachung finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**action_id**|**varchar(4)**|ID der Überwachungsaktion. Bezieht sich auf den **action_id** Wert, der in jeden Überwachungsdaten Satz geschrieben wird. Lässt NULL-Werte zu. NULL für Überwachungsgruppen.|  
|**action_in_log**|**bit**|Gibt an, ob eine Aktion in ein Überwachungsprotokoll geschrieben werden kann. Die Werte lauten:<br /><br /> 1 = Ja<br /><br /> 0 = Nein|  
|**name**|**sysname**|Name der Überwachungsaktion oder Überwachungsaktionsgruppe. Lässt keine NULL-Werte zu.|  
|**class_desc**|**nvarchar(120)**|Der Name der Objektklasse, für die die Überwachungsaktion gilt. Kann ein beliebiges der Server-, Datenbank- oder Schemabereichsobjekte sein, umfasst jedoch keine Schemaobjekte. Lässt keine NULL-Werte zu.|  
|**parent_class_desc**|**nvarchar(120)**|Name der übergeordneten Klasse für das von class_desc beschriebene Objekt. Ist NULL, wenn class_desc der Server ist.|  
|**covering_parent_action_name**|**nvarchar(120)**|Name der Überwachungsaktion oder Überwachungsgruppe, welche die in dieser Zeile beschriebene Überwachungsaktion enthält. Dies wird verwendet, um eine Hierarchie von Aktionen und Aktionen zur Notfallwiederherstellung zu erstellen. Lässt NULL-Werte zu.|  
|**configuration_level**|**nvarchar (10)**|Zeigt an, dass die in dieser Zeile angegebene Aktion oder Aktionsgruppe auf Gruppen- oder Aktionsebene konfigurierbar ist. Ist NULL, wenn die Aktion nicht konfigurierbar ist.|  
|**containing_group_name**|**nvarchar(120)**|Der Name der Überwachungsgruppe, die die angegebene Aktion enthält. Ist NULL, wenn der Wert von name eine Gruppe ist.|  
  
## <a name="permissions"></a>Berechtigungen  
 Prinzipale müssen über die **Select** -Berechtigung verfügen. Standardmäßig wird der Gruppe Public dies gewährt.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)].  Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create Server Audit &#40;Transact-SQL-&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [Alter Server Audit &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [Drop Server Audit &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Create Server Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [Alter Server Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [Drop Server Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [Create Database Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [Alter Database Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [Drop Database Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [Alter Authorization &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys. fn_get_audit_file &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys. server_audits &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys. server_file_audits &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys. server_audit_specifications &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys. server_audit_specification_details &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys. database_audit_specifications &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys. database_audit_specification_details &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys. dm_server_audit_status &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys. dm_audit_class_type_map &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
