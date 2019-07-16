---
title: Sp_helpuser (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpuser
- sp_helpuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpuser
ms.assetid: 9c70b41d-ef4c-43df-92da-bd534c287ca1
author: stevestein
ms.author: sstein
ms.openlocfilehash: a170c5e43329d90a4977db12a98bd9d2e556e91d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048160"
---
# <a name="sphelpuser-transact-sql"></a>sp_helpuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen zu Prinzipalen auf Datenbankebene in der aktuellen Datenbank bereit.  
  
> [!IMPORTANT]  
>  **Sp_helpuser** gibt keine Informationen zu sicherungsfähigen Elementen, die in eingeführt wurden zurück [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Verwendung [Sys. database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpuser [ [ @name_in_db = ] 'security_account' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name_in_db = ] 'security_account'` Ist der Name des Datenbankbenutzers oder der Datenbankrolle in der aktuellen Datenbank. *Security_account* muss in der aktuellen Datenbank vorhanden sein. *Security_account* ist **Sysname**, hat den Standardwert NULL. Wenn *Security_account* nicht angegeben ist, **Sp_helpuser** gibt Informationen zu allen datenbankprinzipalen zurück.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Die folgende Tabelle zeigt das Resultset, wenn weder ein Benutzerkonto noch ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder für die Windows-Benutzer angegeben wird *Security_account*.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**UserName**|**sysname**|Benutzer in der aktuellen Datenbank.|  
|**RoleName**|**sysname**|Rollen, zu denen **Benutzername** gehört.|  
|**LoginName**|**sysname**|Anmeldename des **Benutzername**.|  
|**DefDBName**|**sysname**|Standarddatenbank von **Benutzername**.|  
|**DefSchemaName**|**sysname**|Standardschema des Datenbankbenutzers.|  
|**UserID**|**smallint**|ID des **Benutzername** in der aktuellen Datenbank.|  
|**SID**|**smallint**|Sicherheits-ID (SID) des Benutzers.|  
  
 Die folgende Tabelle zeigt, wie das Resultset aussieht, wenn kein Benutzerkonto angegeben ist und Aliase in der aktuellen Datenbank vorhanden sind.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Anmeldenamen, die mithilfe eines Alias mit Benutzern in der aktuellen Datenbank verknüpft sind.|  
|**UserNameAliasedTo**|**sysname**|Benutzername in der aktuellen Datenbank, mit dem der Anmeldename mithilfe eines Alias verknüpft ist.|  
  
 Die folgende Tabelle zeigt das Resultset, wenn für eine Rolle angegeben wird *Security_account*.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**Rollenname**|**sysname**|Name der Rolle in der aktuellen Datenbank.|  
|**Role_id**|**smallint**|Rollen-ID für die Rolle in der aktuellen Datenbank.|  
|**Users_in_role**|**sysname**|Mitglied der Rolle in der aktuellen Datenbank.|  
|**Benutzer-ID**|**smallint**|Benutzer-ID für das Rollenmitglied.|  
  
## <a name="remarks"></a>Hinweise  
 Um Informationen zur Mitgliedschaft von Datenbankrollen anzuzeigen, verwenden Sie [database_role_members](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md). Um Informationen zur Mitgliedschaft in Serverrollen anzuzeigen, verwenden [Sys. server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md), und verwenden, um Informationen auf Serverebene anzuzeigen [Sys. server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
 Die zurückgegebenen Informationen unterliegen den Einschränkungen, die für den Zugriff auf Metadaten gelten. Entitäten, für die der Prinzipal keine Berechtigungen besitzt, werden nicht angezeigt. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-all-users"></a>A. Auflisten aller Benutzer  
 Im folgenden Beispiel werden alle Benutzer in der aktuellen Datenbank aufgelistet.  
  
```  
EXEC sp_helpuser;  
```  
  
### <a name="b-listing-information-for-a-single-user"></a>B. Auflisten von Informationen für einen einzelnen Benutzer  
 Im folgenden Beispiel werden Informationen zum Datenbankbesitzer (`dbo`) aufgelistet.  
  
```  
EXEC sp_helpuser 'dbo';  
```  
  
### <a name="c-listing-information-for-a-database-role"></a>C. Auflisten von Informationen für eine Datenbankrolle  
 Im folgenden Beispiel werden Informationen zur festen Datenbankrolle `db_securityadmin` aufgelistet.  
  
```  
EXEC sp_helpuser 'db_securityadmin';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
  
