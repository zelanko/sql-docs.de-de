---
title: Sp_attachsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_attachsubscription
- sp_attachsubscription_TSQL
helpviewer_keywords:
- sp_attachsubscription
ms.assetid: b9bbda36-a46a-4327-a01e-9cd632e4791b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d9f144d9d896fb75af5f59850c249b9044d1b781
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046152"
---
# <a name="spattachsubscription-transact-sql"></a>sp_attachsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt eine vorhandene Abonnementdatenbank an einen beliebigen Abonnenten an. Diese gespeicherte Prozedur wird beim neuen Abonnenten für die master-Datenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Diese Funktion wurde als veraltet markiert und wird in einer zukünftigen Version entfernt. Diese Funktion sollte bei neuen Entwicklungen nicht verwendet werden. Für Mergeveröffentlichungen, die mithilfe von parametrisierten Filtern partitioniert werden, ist es empfehlenswert, die neuen Funktionen von partitionierten Momentaufnahmen zu verwenden. Diese vereinfachen die Initialisierung zahlreicher Abonnements. Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). Für nicht partitionierte Veröffentlichungen können Sie ein Abonnement mit einer Sicherung initialisieren. Weitere Informationen finden Sie unter [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)initialisiert wird.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_attachsubscription [ @dbname = ] 'dbname'  
        , [ @filename = ] 'filename'  
    [ , [ @subscriber_security_mode = ] 'subscriber_security_mode' ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @db_master_key_password = ] 'db_master_key_password' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'dbname'` Ist die Zeichenfolge, die die Ziel-Abonnementdatenbank namentlich angibt. *Dbname* ist **Sysname**, hat keinen Standardwert.  
  
`[ @filename = ] 'filename'` Der Name und physische Speicherort der primären MDF-Datei (**master** Datendatei). *FileName* ist **nvarchar(260)** , hat keinen Standardwert.  
  
`[ @subscriber_security_mode = ] 'subscriber_security_mode'` Ist der Sicherheitsmodus des Abonnenten beim Herstellen einer Verbindung an einen Abonnenten, bei der Synchronisierung verwendet. *Subscriber_security_mode* ist **Int**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Die Windows-Authentifizierung muss verwendet werden. Wenn *Subscriber_security_mode* nicht **1** (Windows-Authentifizierung), wird ein Fehler zurückgegeben.  
  
`[ @subscriber_login = ] 'subscriber_login'` Ist der Anmeldename des Abonnenten beim Herstellen einer Verbindung an einen Abonnenten, bei der Synchronisierung verwendet. *Subscriber_login* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird nur aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Wenn *Subscriber_security_mode* nicht **1** und *Subscriber_login* wird angegeben, wird ein Fehler zurückgegeben.  
  
`[ @subscriber_password = ] 'subscriber_password'` Ist das Kennwort des Abonnenten. *Subscriber_password* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird nur aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Wenn *Subscriber_security_mode* nicht **1** und *Subscriber_password* wird angegeben, wird ein Fehler zurückgegeben.  
  
`[ @distributor_security_mode = ] distributor_security_mode` Ist der Sicherheitsmodus, verwenden Sie beim Herstellen einer Verbindung mit einem Verteiler, bei der Synchronisierung. *Distributor_security_mode* ist **Int**, hat den Standardwert **0**. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. **1** gibt die Windows-Authentifizierung. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` Ist der Anmeldename des Verteilers beim Verbinden mit einem Verteiler, bei der Synchronisierung verwendet. *Distributor_login* ist erforderlich, wenn *Distributor_security_mode* nastaven NA hodnotu **0**. *Distributor_login* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @distributor_password = ] 'distributor_password'` Ist das Verteilerkennwort. *Distributor_password* ist erforderlich, wenn *Distributor_security_mode* nastaven NA hodnotu **0**. *Distributor_password* ist **Sysname**, hat den Standardwert NULL. Der Wert des *Distributor_password* muss weniger als 120 Unicode-Zeichen sein.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Ist der Sicherheitsmodus, verwenden Sie beim Herstellen einer Verbindung mit einem Verleger, bei der Synchronisierung. *Publisher_security_mode* ist **Int**, hat den Standardwert **1**. Wenn **0**, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. Wenn **1**, gibt die Windows-Authentifizierung. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Ist die Anmeldung beim Herstellen einer Verbindung mit einem Verleger, bei der Synchronisierung verwendet. *Publisher_login* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @publisher_password = ] 'publisher_password'` Das Kennwort wird verwendet werden, wenn eine Verbindung mit dem Verleger herstellen. *Publisher_password* ist **Sysname**, hat den Standardwert NULL. Der Wert des *Publisher_password* muss weniger als 120 Unicode-Zeichen sein.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @job_login = ] 'job_login'` Ist der Anmeldename für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_login* ist **nvarchar(257)** , hat keinen Standardwert. Das Windows-Konto wird stets für Agent-Verbindungen mit dem Verteiler verwendet.  
  
`[ @job_password = ] 'job_password'` Ist das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_password* ist **Sysname**, hat keinen Standardwert. Der Wert des *Job_password* muss weniger als 120 Unicode-Zeichen sein.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @db_master_key_password = ] 'db_master_key_password'` Ist das Kennwort von einer benutzerdefinierten Datenbank-Hauptschlüssel. *Db_master_key_password* ist **nvarchar(524)** , hat den Standardwert NULL. Wenn *Db_master_key_password* nicht angegeben ist, wird eine vorhandene Datenbank-Hauptschlüssel gelöscht und neu erstellt werden.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_attachsubscription** wird in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
 Ein Abonnement kann nicht an die Veröffentlichung angefügt werden, wenn die Aufbewahrungsdauer der Veröffentlichung abgelaufen ist. Wenn ein Abonnement mit einer abgelaufenen Aufbewahrungsdauer angegeben wird, tritt ein Fehler auf, wenn das Abonnement angefügt wird oder wenn es erstmalig synchronisiert wird. Veröffentlichungen mit einer Aufbewahrungsdauer von **0** (laufen nie ab) werden ignoriert.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_attachsubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
