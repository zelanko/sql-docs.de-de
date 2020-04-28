---
title: sys. server_file_audits (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_file_audits_TSQL
- sys.server_file_audits_TSQL
- sys.server_file_audits
- server_file_audits
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_file_audits catalog view
ms.assetid: 553288a0-be57-4d79-ae53-b7cbd065e127
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7b3ed8e08d333c4aed2576154c645a0050ebf4df
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68133134"
---
# <a name="sysserver_file_audits-transact-sql"></a>sys.server_file_audits (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält erweiterte Informationen über den Datei Überwachungstyp in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Überwachung auf einer Serverinstanz. Weitere Informationen finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|audit_id|**int**|Die ID der Überwachung.|  
|Name|**sysname**|Der Name der Überwachung.|  
|audit_guid|**uniqueidentifier**|GUID der Überwachung.|  
|create_date|**datetime**|Das UTC-Datum, an dem die Dateiüberwachung erstellt wurde.|  
|modify_date|**DataTime**|Das UTC-Datum, an dem die Dateiüberwachung zuletzt geändert wurde.|  
|principal_id|**int**|Die ID des Besitzers der Überwachung, wie sie auf dem Server registriert wurde.|  
|type|**char (2)**|Überwachungstyp:<br /><br /> 0 = NT-Sicherheitsereignisprotokoll<br /><br /> 1 = NT-Anwendungsereignisprotokoll<br /><br /> 2 = Datei auf Dateisystem|  
|type_desc|**nvarchar(60)**|Beschreibung des Überwachungstyps.|  
|on_failure|**tinyint**|Bei Fehlerbedingung:<br /><br /> 0 = Weiter<br /><br /> 1 = Serverinstanz herunterfahren<br /><br /> 2 = Fehler bei Vorgang|  
|on_failure_desc|**nvarchar(60)**|Bei einem Fehler schreiben Sie folgendermaßen einen Aktionseintrag:<br /><br /> CONTINUE<br /><br /> SHUTDOWN SERVER INSTANCE<br /><br /> FAIL OPERATION|  
|is_state_enabled|**tinyint**|0 = Deaktiviert<br /><br /> 1 = Aktiviert|  
|queue_delay|**int**|Vorgeschlagene maximale Wartezeit in Millisekunden, bevor auf den Datenträger geschrieben wird. Wenn 0, garantiert die Überwachung einen Schreibvorgang, bevor das Ereignis fortgesetzt werden kann.|  
|predicate|**nvarchar (8000)**|Prädikatausdruck, der auf das Ereignis angewendet wird.|  
|max_file_size|**bigint**|Maximale Größe der Überwachungsdatei in MB:<br /><br /> 0 = Unbegrenzt/Nicht anwendbar auf den ausgewählten Überwachungstyp.|  
|max_rollover_files|**int**|Maximale Anzahl von Dateien zur Verwendung mit der Rolloveroption.|  
|max_files|**int**|Maximale Anzahl von Dateien zur Verwendung ohne die Rolloveroption.|  
|reserved_disk_space|**int**|Pro Datei zu reservierender Speicherplatz.|  
|log_file_path|**nvarchar(260)**|Pfad zum Speicherort der Überwachung. Dateipfad für Dateiüberwachung, Anwendungsprotokollpfad für Anwendungsprotokollüberwachung.|  
|log_file_name|**nvarchar(260)**|Basisname für die in CREATE AUDIT DDL angegebene Protokolldatei. Der base_log_name Datei wird eine inkrementelle Zahl als Suffix hinzugefügt, um den Namen der Protokolldatei zu erstellen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Prinzipale mit der Berechtigung **Alter any Server Audit** oder **View any Definition** haben Zugriff auf diese Katalog Sicht. Außerdem darf dem Prinzipal die **View any Definition** -Berechtigung nicht verweigert werden.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
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
 [sys. server_file_audits (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys. server_audit_specifications &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys. database_audit_specifications &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys. database_audit_specification_details &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys. dm_server_audit_status &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys. dm_audit_actions &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys. dm_audit_class_type_map &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
