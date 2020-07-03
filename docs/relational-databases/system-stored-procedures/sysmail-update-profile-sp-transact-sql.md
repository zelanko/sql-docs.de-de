---
title: sysmail_update_profile_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_profile_sp
- sysmail_update_profile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_profile_sp
ms.assetid: eaedf7ce-a8d5-4ab9-99e0-d77d5be19e90
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c795b604538a26fc7602ea245bd4d1d8c9c52d33
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890809"
---
# <a name="sysmail_update_profile_sp-transact-sql"></a>sysmail_update_profile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Beschreibung oder den Namen eines Datenbank-E-Mail-Profils.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_update_profile_sp [ [ @profile_id = ] profile_id , ] [ [ @profile_name = ] 'profile_name' , ]  
    [ [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_id = ] profile_id`Die zu Aktualisier gende Profil-ID. *profile_id* ist vom Datentyp **int**und hat den Standardwert NULL. Mindestens eine *profile_id* oder *profile_name* muss angegeben werden. Werden beide Werte angegeben, wird der Name des Profils geändert.  
  
`[ @profile_name = ] 'profile_name'`Der Name des zu aktualisierenden Profils oder der neue Name für das Profil. *profile_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Mindestens eine *profile_id* oder *profile_name* muss angegeben werden. Werden beide Werte angegeben, wird der Name des Profils geändert.  
  
`[ @description = ] 'description'`Die neue Beschreibung für das Profil. die *Beschreibung* ist vom Datentyp **nvarchar (256)** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Wenn sowohl die Profil-ID als auch der Profilname angegeben werden, wird der Name des Profils zum bereitgestellten Namen geändert und die Beschreibung des Profils aktualisiert. Wenn nur eins dieser Argumente bereitgestellt wird, wird die Beschreibung des Profils aktualisiert.  
  
 Die gespeicherte Prozedur **sysmail_update_profile_sp** wird in der **msdb** -Datenbank gespeichert und befindet sich im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 **A. Ändern der Beschreibung eines Profils**  
  
 Im folgenden Beispiel wird die Beschreibung für das Profil `AdventureWorks Administrator` in der **msdb** -Datenbank geändert.  
  
```  
EXECUTE msdb.dbo.sysmail_update_profile_sp  
    @profile_name = 'AdventureWorks Administrator'  
    ,@description = 'Administrative mail profile.';  
```  
  
 **B. Ändern des Namens und der Beschreibung eines Profils**  
  
 Im folgenden Beispiel wird der Name und die Beschreibung des Profils mit der Profil-ID `750` geändert.  
  
```  
EXECUTE msdb.dbo.sysmail_update_profile_sp  
    @profile_id = 750  
    ,@profile_name = 'Operator'  
    ,@description = 'Profile to send alert e-mail to operators.';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Konfigurationsobjekte Datenbank-E-Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Erstellen eines Datenbank-E-Mail Kontos](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
