---
title: sys. server_principals (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_principals
- sys.server_principals_TSQL
- sys.server_principals
- server_principals_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_principals catalog view
ms.assetid: c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 822d0663d13e4ad03c852758e97277e6711af0bd
ms.sourcegitcommit: 8515bb2021cfbc7791318527b8554654203db4ad
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2020
ms.locfileid: "86091882"
---
# <a name="sysserver_principals-transact-sql"></a>sys.server_principals (Transact-SQL)
[!INCLUDE [sql-asdbmi-pdw](../../includes/applies-to-version/sql-asdbmi-pdw.md)]

  Enthält eine Zeile für jeden Prinzipal auf Serverebene.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name des Prinzipals. Ist innerhalb eines Servers eindeutig.|  
|**principal_id**|**int**|Die ID des Prinzipals. Ist innerhalb eines Servers eindeutig.|  
|**sid**|**varbinary(85)**|Sicherheitsbezeichner (SID, Security-IDentifier) des Prinzipals. Bei einem Windows-Prinzipal entspricht dies Windows SID.|  
|**type**|**char (1)**|Prinzipaltyp:<br /><br /> S = SQL-Anmeldename<br /><br /> U = Windows-Anmeldename<br /><br /> G = Windows-Gruppe<br /><br /> R = Serverrolle<br /><br /> C = Einem Zertifikat zugeordneter Anmeldename<br /><br /> K = Einem asymmetrischen Schlüssel zugeordneter Anmeldename|  
|**type_desc**|**nvarchar(60)**|Beschreibung des Prinzipaltyps:<br /><br /> SQL_LOGIN<br /><br /> WINDOWS_LOGIN<br /><br /> WINDOWS_GROUP<br /><br /> SERVER_ROLE<br /><br /> CERTIFICATE_MAPPED_LOGIN<br /><br /> ASYMMETRIC_KEY_MAPPED_LOGIN|  
|**is_disabled**|**int**|1 = Anmeldename ist deaktiviert.|  
|**create_date**|**datetime**|Der Zeitpunkt, zu dem der Prinzipal erstellt wurde.|  
|**modify_date**|**datetime**|Zeitpunkt, zu dem die Prinzipaldefinition zuletzt geändert wurde.|  
|**default_database_name**|**sysname**|Standarddatenbank für diesen Prinzipal.|  
|**default_language_name**|**sysname**|Standardsprache für diesen Prinzipal.|  
|**credential_id**|**int**|ID von Anmeldeinformationen, die diesem Prinzipal zugeordnet sind. Falls diesem Prinzipal keine Anmeldeinformationen zugeordnet sind, ist credential_id gleich NULL.|  
|**owning_principal_id**|**int**|Die **principal_id** des Besitzers einer Server Rolle. NULL, wenn der Prinzipal keine Serverrolle ist.|  
|**is_fixed_role**|**bit**|Gibt 1 zurück, wenn der Prinzipal eine der integrierten Server Rollen mit Fixed-Berechtigungen ist. Weitere Informationen finden Sie unter [Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md).|  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer kann seinen eigenen Anmeldenamen, die Systemanmeldenamen und die festen Serverrollen anzeigen. Zum Anzeigen anderer Anmeldenamen ist ALTER ANY LOGIN oder eine Berechtigung für den Anmeldenamen erforderlich. Zum Anzeigen benutzerdefinierter Serverrollen ist ALTER ANY SERVER ROLE oder die Mitgliedschaft in der Rolle erforderlich.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
 Mit der folgenden Abfrage werden die Berechtigungen aufgelistet, die Serverprinzipalen ausdrücklich gewährt oder verweigert wurden.  
  
> [!IMPORTANT]  
>  Die Berechtigungen fester Server Rollen (außer Public) werden in sys. server_permissions nicht angezeigt. Daher können Serverprinzipale über zusätzliche Berechtigungen verfügen, die hier nicht aufgeführt werden.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pe.state_desc, pe.permission_name   
FROM sys.server_principals AS pr   
JOIN sys.server_permissions AS pe   
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Berechtigungshierarchie &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
  
  
