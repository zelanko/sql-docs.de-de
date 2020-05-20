---
title: sp_helpuser (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9e186b87680ec0592f5c69ee5659c3b9c74f680b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826048"
---
# <a name="sp_helpuser-transact-sql"></a>sp_helpuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen zu Prinzipalen auf Datenbankebene in der aktuellen Datenbank bereit.  
  
> [!IMPORTANT]  
>  **sp_helpuser** gibt keine Informationen zu Sicherungs fähigen Elementen zurück, die in eingeführt wurden [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] . Verwenden Sie stattdessen [sys. database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpuser [ [ @name_in_db = ] 'security_account' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name_in_db = ] 'security_account'`Der Name des Daten Bank Benutzers oder der Daten Bank Rolle in der aktuellen Datenbank. *security_account* muss in der aktuellen Datenbank vorhanden sein. *security_account* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *security_account* nicht angegeben ist, gibt **sp_helpuser** Informationen zu allen Daten Bank Prinzipale zurück.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 In der folgenden Tabelle wird das Resultset angezeigt, wenn für security_account weder ein Benutzerkonto noch ein- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder ein Windows-Benutzer *security_account*angegeben ist.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**User**|**sysname**|Benutzer in der aktuellen Datenbank.|  
|**RoleName**|**sysname**|Rollen, zu denen der **Benutzername** gehört.|  
|**LoginName**|**sysname**|Anmelde **Name des Benutzernamens**.|  
|**DefDBName**|**sysname**|Standarddatenbank des **Benutzernamens**.|  
|**DefSchemaName**|**sysname**|Standardschema des Datenbankbenutzers.|  
|**UserID**|**smallint**|ID des **Benutzernamens** in der aktuellen Datenbank.|  
|**SID**|**smallint**|Sicherheits-ID (SID) des Benutzers.|  
  
 Die folgende Tabelle zeigt, wie das Resultset aussieht, wenn kein Benutzerkonto angegeben ist und Aliase in der aktuellen Datenbank vorhanden sind.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Anmeldenamen, die mithilfe eines Alias mit Benutzern in der aktuellen Datenbank verknüpft sind.|  
|**UserNameAliasedTo**|**sysname**|Benutzername in der aktuellen Datenbank, mit dem der Anmeldename mithilfe eines Alias verknüpft ist.|  
  
 In der folgenden Tabelle wird das Resultset angezeigt, wenn eine Rolle für *security_account*angegeben wird.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Role_name**|**sysname**|Name der Rolle in der aktuellen Datenbank.|  
|**Role_id**|**smallint**|Rollen-ID für die Rolle in der aktuellen Datenbank.|  
|**Users_in_role**|**sysname**|Mitglied der Rolle in der aktuellen Datenbank.|  
|**UserID**|**smallint**|Benutzer-ID für das Rollenmitglied.|  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie [sys. database_role_members](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md), um Informationen zur Mitgliedschaft in Daten bankrollen anzuzeigen. Um Informationen zu Server Rollen Mitgliedern anzuzeigen, verwenden Sie [sys. server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md), und um Informationen über Prinzipale auf Serverebene anzuzeigen, verwenden Sie [sys. server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
 Die zurückgegebenen Informationen unterliegen den Einschränkungen, die für den Zugriff auf Metadaten gelten. Entitäten, für die der Prinzipal keine Berechtigungen besitzt, werden nicht angezeigt.  Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys. database_principals &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys. database_role_members &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys. server_principals &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
  
