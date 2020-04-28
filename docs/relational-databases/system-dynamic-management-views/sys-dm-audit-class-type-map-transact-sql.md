---
title: sys. dm_audit_class_type_map (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_audit_class_type_map
- sys.dm_audit_class_type_map_TSQL
- dm_audit_class_type_map
- dm_audit_class_type_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_audit_class_type_map dynamic management view
ms.assetid: e10b5431-1bb0-47ca-8fd0-c04bd73a4410
author: stevestein
ms.author: sstein
ms.openlocfilehash: ae1c39d5c3ddc36f4ca3007cf9e17c2543055b85
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68099200"
---
# <a name="sysdm_audit_class_type_map-transact-sql"></a>sys.dm_audit_class_type_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Gibt eine Tabelle zurück, die das Feld class_type im Überwachungsprotokoll dem Feld class_desc in sys.dm_audit_actions zuordnet. Weitere Informationen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Überwachung finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**class_type**|**char (2)**|Der Klassentyp der überwachten Entität. Wird dem class_type zugeordnet, der in das Überwachungs Protokoll geschrieben und von der **get_audit_file ()** -Funktion zurückgegeben wird. Lässt keine NULL-Werte zu.|  
|**class_type_desc**|**nvarchar(120)**|Der Name der überwachbaren Entität. Lässt keine NULL-Werte zu.|  
|**securable_class_desc**|**nvarchar(120)**|Das sicherungsfähige Objekt, das dem überwachten class_type zugeordnet ist. Ist NULL, wenn class_type keinem sicherungsfähigen Objekt zugeordnet ist. Kann zu class_desc in sys.dm_audit_actions in Beziehung gesetzt werden.|  
  
## <a name="permissions"></a>Berechtigungen  
 Prinzipale müssen über **SELECT** -Berechtigung verfügen. Standardmäßig wird der Gruppe Public dies gewährt.  
  
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
 [sys. dm_audit_class_type_map](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
