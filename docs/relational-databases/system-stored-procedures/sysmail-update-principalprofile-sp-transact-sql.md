---
title: sysmail_update_principalprofile_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_principalprofile_sp
- sysmail_update_principalprofile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_principalprofile_sp
ms.assetid: 9fe96e9a-4758-4e4a-baee-3e1217c4426c
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1f488c50518f0a1dd06d72532f1e9edad865e26a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783670"
---
# <a name="sysmail_update_principalprofile_sp-transact-sql"></a>sysmail_update_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Aktualisiert die Informationen über eine Zuordnung zwischen einem Prinzipal und einem Profil.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_update_principalprofile_sp { @principal_id = principal_id | @principal_name = 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    [ @is_default = ] 'is_default'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @principal_id = ] principal_id`Die ID des Daten Bank Benutzers oder der Daten Bank Rolle in der **msdb** -Datenbank für die Zuordnung, die geändert werden soll. *principal_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @principal_name = ] 'principal_name'`Der Name des Daten Bank Benutzers oder der Daten Bank Rolle in der **msdb** -Datenbank für die zu aktualisierenden Zuordnung. *principal_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es kann entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @profile_id = ] profile_id`Die ID des Profils für die Zuordnung, die geändert werden soll. *profile_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
`[ @profile_name = ] 'profile_name'`Der Name des Profils für die Zuordnung, die geändert werden soll. *profile_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
`[ @is_default = ] 'is_default'`Gibt an, ob dieses Profil das Standardprofil für den Datenbankbenutzer ist. Ein Datenbankbenutzer kann nur ein Standardprofil besitzen. *is_default* ist vom Datentyp **bit**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Mit dieser gespeicherten Prozedur wird festgelegt, ob das angegebene Profil das Standardprofil für den Datenbankbenutzer ist. Ein Datenbankbenutzer kann nur ein privates Standardprofil besitzen.  
  
 Wenn der Prinzipalname für die Zuordnung auf **public** festgelegt ist oder die Prinzipal-ID für die Zuordnung den Wert **0**hat, wird das öffentliche Profil von dieser gespeicherten Prozedur geändert. Es kann nur ein öffentliches Standardprofil vorhanden sein.  
  
 Wenn ** \@ is_default** den Wert "**1**" hat und der Prinzipal mehr als einem Profil zugeordnet ist, wird das angegebene Profil zum Standardprofil für den Prinzipal. Das zuvor als Standardprofil verwendete Profil ist dem Prinzipal weiter zugeordnet, es ist jedoch nicht mehr als Standardprofil festgelegt.  
  
 Die gespeicherte Prozedur **sysmail_update_principalprofile_sp** wird in der **msdb** -Datenbank gespeichert und befindet sich im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 **A. Festlegen eines Profils als öffentliches Standardprofil für eine Datenbank**  
  
 Im folgenden Beispiel wird das Profil `General Use Profile` als öffentliches Standardprofil für Benutzer in der **msdb** -Datenbank festgelegt.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'General Use Profile',  
    @is_default = '1';  
```  
  
 **B. Festlegen eines Profils als privates Standardprofil für einen Benutzer**  
  
 Im folgenden Beispiel wird das Profil `AdventureWorks Administrator` als Standardprofil für den Prinzipal `ApplicationUser` in der **msdb** -Datenbank festgelegt. Das Profil muss dem Prinzipal bereits zugeordnet sein. Das zuvor als Standardprofil verwendete Profil ist dem Prinzipal weiter zugeordnet, es ist jedoch nicht mehr als Standardprofil festgelegt.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator',  
    @is_default = '1' ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Konfigurationsobjekte Datenbank-E-Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
