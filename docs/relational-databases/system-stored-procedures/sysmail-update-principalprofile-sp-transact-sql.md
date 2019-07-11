---
title: Sysmail_update_principalprofile_sp (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: fc6e973b71b16817f3e3533544102bfeba3caeb4
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793056"
---
# <a name="sysmailupdateprincipalprofilesp-transact-sql"></a>sysmail_update_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aktualisiert die Informationen über eine Zuordnung zwischen einem Prinzipal und einem Profil.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_update_principalprofile_sp { @principal_id = principal_id | @principal_name = 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    [ @is_default = ] 'is_default'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @principal_id = ] principal_id` Die ID des Datenbankbenutzers oder der Rolle in der **Msdb** -Datenbank für die Zuordnung zu ändern. *principal_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @principal_name = ] 'principal_name'` Der Name des Datenbankbenutzers oder der Rolle in der **Msdb** -Datenbank für die Zuordnung zu aktualisieren. *principal_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es kann entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @profile_id = ] profile_id` Die Id des Profils für die Zuordnung, die geändert werden soll. *profile_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
`[ @profile_name = ] 'profile_name'` Der Name des Profils für die Zuordnung, die geändert werden soll. *profile_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
`[ @is_default = ] 'is_default'` Ist, gibt an, ob dieses Profil das Standardprofil für den Datenbankbenutzer ist. Ein Datenbankbenutzer kann nur ein Standardprofil besitzen. *is_default* ist vom Datentyp **bit**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser gespeicherten Prozedur wird festgelegt, ob das angegebene Profil das Standardprofil für den Datenbankbenutzer ist. Ein Datenbankbenutzer kann nur ein privates Standardprofil besitzen.  
  
 Wenn der Prinzipalname für die Zuordnung auf **public** festgelegt ist oder die Prinzipal-ID für die Zuordnung den Wert **0**hat, wird das öffentliche Profil von dieser gespeicherten Prozedur geändert. Es kann nur ein öffentliches Standardprofil vorhanden sein.  
  
 Wenn  **\@Is_default** ist "**1**" und der Prinzipal mehreren Profilen zugeordnet ist, wird das angegebene Profil als Standardprofil für den Prinzipal. Das zuvor als Standardprofil verwendete Profil ist dem Prinzipal weiter zugeordnet, es ist jedoch nicht mehr als Standardprofil festgelegt.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail Configuration Objects](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Datenbank-e-Mails gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
