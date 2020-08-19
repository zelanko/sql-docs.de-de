---
description: sysmail_delete_principalprofile_sp (Transact-SQL)
title: sysmail_delete_principalprofile_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_principalprofile_sp_TSQL
- sysmail_delete_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_principalprofile_sp
ms.assetid: 8fc14700-e17a-4073-9a96-7fc23e775c69
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1cf4424f440ff8d03aa63933dbc4e661556e2106
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419304"
---
# <a name="sysmail_delete_principalprofile_sp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt für einen Datenbankbenutzer oder eine Rolle die Berechtigung zum Verwenden eines öffentlichen oder privaten Datenbank-E-Mail-Profils.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @principal_id = ] principal_id` Die ID des Daten Bank Benutzers oder der Daten Bank Rolle in der **msdb** -Datenbank für die Zuordnung, die gelöscht werden soll. *principal_id* ist vom Datentyp **int**und hat den Standardwert NULL. Um ein öffentliches Profil in einem privaten Profil zu erstellen, geben Sie die Prinzipal-ID **0** oder den Prinzipal Namen **' Public '** an. Es muss entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @principal_name = ] 'principal_name'` Der Name des Daten Bank Benutzers oder der Daten Bank Rolle in der **msdb** -Datenbank für die Zuordnung, die gelöscht werden soll. *principal_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Um ein öffentliches Profil in einem privaten Profil zu erstellen, geben Sie die Prinzipal-ID **0** oder den Prinzipal Namen **' Public '** an. Es muss entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @profile_id = ] profile_id` Die ID des Profils für die Zuordnung, die gelöscht werden soll. *profile_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
`[ @profile_name = ] 'profile_name'` Der Name des Profils für die Zuordnung, die gelöscht werden soll. *profile_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie ein öffentliches Profil in ein privates Profil erstellen möchten, geben Sie **"Public"** als Prinzipal Namen oder " **0** " für die Prinzipal-ID an.  
  
 Gehen Sie vorsichtig vor, wenn Sie für einen Benutzer die Berechtigungen für das private Standardprofil entfernen oder das öffentliche Standardprofil entfernen. Wenn kein Standardprofil verfügbar ist, ist für **sp_send_dbmail** der Name eines Profils als Argument erforderlich. Daher kann das Entfernen eines Standard Profils dazu führen, dass Aufrufe von **sp_send_dbmail** fehlschlagen. Weitere Informationen finden Sie unter [sp_send_dbmail &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 Die gespeicherte Prozedur **sysmail_delete_principalprofile_sp** wird in der **msdb** -Datenbank gespeichert und befindet sich im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie die Zuordnung zwischen dem Profil " **AdventureWorks Administrator** " und dem Anmelde Namen **ApplicationUser** in der **msdb** -Datenbank gelöscht wird.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Konfigurationsobjekte Datenbank-E-Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
