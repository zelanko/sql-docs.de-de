---
title: sysmail_add_profile_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_profile_sp_TSQL
- sysmail_add_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profile_sp
ms.assetid: a828e55c-633a-41cf-9769-a0698b446e6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a4bd7f90688d61f9ecee487d553393e38bed82e3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "70211282"
---
# <a name="sysmail_add_profile_sp-transact-sql"></a>sysmail_add_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Erstellt ein neues Profil für Datenbank-E-Mail.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_add_profile_sp [ @profile_name = ] 'profile_name'  
    [ , [ @description = ] 'description' ]  
    [ , [ @profile_id = ] new_profile_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_name = ] 'profile\_name'`Der Name des neuen Profils. *profile_name* ist vom Datentyp **sysname**und hat keinen Standardwert.  
 
   > [!NOTE]
   > Der Name des Profils, der den SQL-Agent von Azure SQL verwaltete Instanz verwendet, muss aufgerufen werden **AzureManagedInstance_dbmail_profile**
  
`[ @description = ] 'description'`Die optionale Beschreibung für das neue Profil. die *Beschreibung* ist vom Datentyp **nvarchar (256)** und hat keinen Standardwert.  
  
`[ @profile_id = ] _new\_profile\_id OUTPUT`Gibt die ID für das neue Profil zurück. *new_profile_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Datenbank-E-Mail-Profil kann eine beliebige Anzahl von Datenbank-E-Mail-Konten enthalten. Gespeicherte Prozeduren von Datenbank-E-Mail können nach dem Profilnamen oder der von dieser Prozedur generierten Profil-ID auf ein Profil verweisen. Weitere Informationen zum Hinzufügen eines Kontos zu einem Profil finden Sie unter [sysmail_add_profileaccount_sp &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md).  
  
 Der Profilname und die Beschreibung können mit der gespeicherten Prozedur **sysmail_update_profile_sp**geändert werden, während die Profil-ID für die Lebensdauer des Profils konstant bleibt.  
  
 Der Profilname muss für Microsoft [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] eindeutig sein. Andernfalls wird von der gespeicherten Prozedur ein Fehler zurückgegeben.  
  
 Die gespeicherte Prozedur **sysmail_add_profile_sp** wird in der **msdb** -Datenbank gespeichert und befindet sich im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 **A. Erstellen eines neuen Profils**  
  
 Im folgenden Beispiel wird ein neues Datenbank-E-Mail-Profil mit dem Namen `AdventureWorks Administrator` erstellt.  
  
```  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.' ;  
```  
  
 **B. Erstellen eines neuen Profils und Speichern der Profil-ID in einer Variablen**  
  
 Im folgenden Beispiel wird ein neues Datenbank-E-Mail-Profil mit dem Namen `AdventureWorks Administrator` erstellt. Im folgenden Beispiel wird die Profil-ID in der Variablen `@profileId` gespeichert, und es wird ein Resultset mit der Profil-ID für das neue Profil zurückgegeben.  
  
```  
DECLARE @profileId INT ;  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.',  
       @profile_id = @profileId OUTPUT ;  
  
SELECT @profileId ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Erstellen eines Datenbank-E-Mail Kontos](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Konfigurationsobjekte Datenbank-E-Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
