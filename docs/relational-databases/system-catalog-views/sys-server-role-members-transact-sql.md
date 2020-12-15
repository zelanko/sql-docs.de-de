---
description: sys.server_role_members (Transact-SQL)
title: sys.server_role_members (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_role_members
- sys.server_role_members_TSQL
- server_role_members_TSQL
- sys.server_role_members
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_role_members catalog view
ms.assetid: efa20414-2c6b-45a2-a7a9-60110a24da18
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 84ae7926b44a1f16ba3f9cb4ce34a6e9bda04295
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475111"
---
# <a name="sysserver_role_members-transact-sql"></a>sys.server_role_members (Transact-SQL)
[!INCLUDE [sql-asdbmi-pdw](../../includes/applies-to-version/sql-asdbmi-pdw.md)]

  Gibt eine Zeile für jedes Mitglied jeder festen und benutzerdefinierten Serverrolle zurück.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|Serverprinzipal-ID der Rolle.|  
|**member_principal_id**|**int**|Serverprinzipal-ID des Mitglieds.|  
  
 Verwenden Sie zum Hinzufügen oder Entfernen der Server Rollen Mitgliedschaft die [&#40;Transact-SQL-&#41;Anweisung ALTER Server Role ](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Anmeldungen können Ihre eigene Server Rollen Mitgliedschaft anzeigen und die principal_id der Mitglieder der fixierten Server Rollen anzeigen. Zum Anzeigen aller Serverrollenmitgliedschaften ist die **VIEW DEFINITION ON SERVER ROLE** -Berechtigung oder die Mitgliedschaft in der festen Serverrolle **securityadmin** erforderlich.  
  
 Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Namen und IDs der Rollen und ihrer Mitglieder zurückgegeben.  
  
```  
SELECT sys.server_role_members.role_principal_id, role.name AS RoleName,   
    sys.server_role_members.member_principal_id, member.name AS MemberName  
FROM sys.server_role_members  
JOIN sys.server_principals AS role  
    ON sys.server_role_members.role_principal_id = role.principal_id  
JOIN sys.server_principals AS member  
    ON sys.server_role_members.member_principal_id = member.principal_id;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
