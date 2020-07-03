---
title: sysmail_help_principalprofile_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_principalprofile_sp_TSQL
- sysmail_help_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_principalprofile_sp
ms.assetid: 0cfd6464-09c7-4f03-9d25-58001c096a9e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 024eec5c9e74eb48ac57dcf16a40a7783d79f5b3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890894"
---
# <a name="sysmail_help_principalprofile_sp-transact-sql"></a>sysmail_help_principalprofile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Führt Informationen zu Zuordnungen zwischen Datenbank-E-Mail-Profilen und Datenbankprinzipalen auf.  
  
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_help_principalprofile_sp [ {   [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ]  
    [ [ , ] {   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @principal_id = ] principal_id`Die ID des Daten Bank Benutzers oder der Daten Bank Rolle in der **msdb** -Datenbank für die Zuordnung, die aufgelistet werden soll. *principal_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es kann entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @principal_name = ] 'principal_name'`Der Name des Daten Bank Benutzers oder der Daten Bank Rolle in der **msdb** -Datenbank für die Zuordnung, die aufgelistet werden soll. *principal_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es kann entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @profile_id = ] profile_id`Die ID des Profils für die Zuordnung, die aufgelistet werden soll. *profile_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es können entweder *profile_id* oder *profile_name* angegeben werden.  
  
`[ @profile_name = ] 'profile_name'`Der Name des Profils für die Zuordnung, die aufgelistet werden soll. *profile_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es können entweder *profile_id* oder *profile_name* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Gibt ein Resultset zurück, das die in der folgenden Tabelle aufgelisteten Spalten enthält.  
  
||||  
|-|-|-|  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|**principal_id**|**int**|Die ID des Datenbankbenutzers.|  
|**principal_name**|**sysname**|Der Name des Datenbankbenutzers.|  
|**profile_id**|**int**|Die ID des Datenbank-E-Mail-Profils.|  
|**profile_name**|**sysname**|Der Name des Datenbank-E-Mail-Profils.|  
|**is_default**|**bit**|Das Flag, das besagt, ob es sich bei dem Profil um das Standardprofil des Benutzers handelt.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn **sysmail_help_principalprofile_sp** ohne Parameter aufgerufen wird, listet das zurückgegebene Resultset alle Zuordnungen in der Instanz von auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Andernfalls enthält das Resultset Informationen zu Zuordnungen, die mit den bereitgestellten Parametern übereinstimmen. So listet beispielsweise die Prozedur alle Zuordnungen für ein Profil auf, wenn der Profilname bereitgestellt wird.  
  
 **sysmail_help_principalprofile_sp** befindet sich in der **msdb** -Datenbank und befindet sich im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-information-for-a-specific-association"></a>A. Auflisten von Informationen für eine bestimmte Zuordnung  
 Im folgenden Beispiel werden die Informationen für alle Zuordnungen zwischen dem Profil `AdventureWorks Administrator` und dem Prinzipal `ApplicationLogin` in der `msdb`-Datenbank aufgelistet.  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp  
    @principal_name = 'danw',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 Es folgt ein Beispielresultset, das auf Zeilenlänge umformatiert wurde.  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
5            danw               9           AdventureWorks Administrator   1  
```  
  
### <a name="b-listing-information-for-all-associations"></a>B. Auflisten von Informationen für alle Zuordnungen  
 Im folgenden Beispiel werden die Informationen für alle Zuordnungen in der Instanz aufgelistet.  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp ;  
```  
  
 Es folgt ein Beispielresultset, das auf Zeilenlänge umformatiert wurde.  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
6            terrid             3           Product Update Profile         1  
5            danw               9           AdventureWorks Administrator   1  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
