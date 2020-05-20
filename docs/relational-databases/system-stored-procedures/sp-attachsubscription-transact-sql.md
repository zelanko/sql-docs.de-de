---
title: sp_attachsubscription (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c3ac5075f3bedeb889536fe90ebe7f6c4049199a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833449"
---
# <a name="sp_attachsubscription-transact-sql"></a>sp_attachsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Fügt eine vorhandene Abonnementdatenbank an einen beliebigen Abonnenten an. Diese gespeicherte Prozedur wird beim neuen Abonnenten für die master-Datenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Diese Funktion wurde als veraltet markiert und wird in einer zukünftigen Version entfernt. Diese Funktion sollte bei neuen Entwicklungen nicht verwendet werden. Für Mergeveröffentlichungen, die mithilfe von parametrisierten Filtern partitioniert werden, ist es empfehlenswert, die neuen Funktionen von partitionierten Momentaufnahmen zu verwenden. Diese vereinfachen die Initialisierung zahlreicher Abonnements. Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). Für nicht partitionierte Veröffentlichungen können Sie ein Abonnement mit einer Sicherung initialisieren. Weitere Informationen finden Sie unter [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)initialisiert wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @dbname = ] 'dbname'`Die Zeichenfolge, die die Ziel-Abonnement Datenbank anhand des Namens angibt. *dbname* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @filename = ] 'filename'`Der Name und der physische Speicherort der primären MDF-Datei (**Master** Data File). *Dateiname ist vom Datentyp* **nvarchar (260)** und hat keinen Standardwert.  
  
`[ @subscriber_security_mode = ] 'subscriber_security_mode'`Der Sicherheitsmodus des Abonnenten, der bei der Synchronisierung zum Herstellen einer Verbindung mit einem Abonnenten verwendet wird. *subscriber_security_mode* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Die Windows-Authentifizierung muss verwendet werden. Wenn *subscriber_security_mode* nicht **1** (Windows-Authentifizierung) ist, wird ein Fehler zurückgegeben.  
  
`[ @subscriber_login = ] 'subscriber_login'`Der Anmelde Name des Abonnenten, der bei der Synchronisierung zum Herstellen einer Verbindung mit einem Abonnenten verwendet wird. *subscriber_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird nur aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Wenn *subscriber_security_mode* nicht **1** ist und *subscriber_login* angegeben ist, wird ein Fehler zurückgegeben.  
  
`[ @subscriber_password = ] 'subscriber_password'`Das Kennwort des Abonnenten. *subscriber_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird nur aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Wenn *subscriber_security_mode* nicht **1** ist und *subscriber_password* angegeben ist, wird ein Fehler zurückgegeben.  
  
`[ @distributor_security_mode = ] distributor_security_mode`Der Sicherheitsmodus, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verteiler verwendet wird. *distributor_security_mode* ist vom Datentyp **int**und hat den Standardwert **0**. **0** gibt die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung an. **1** gibt die Windows-Authentifizierung an. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'`Der Verteiler Anmelde Name, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verteiler verwendet wird. *distributor_login* ist erforderlich, wenn *distributor_security_mode* auf **0**festgelegt ist. *distributor_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @distributor_password = ] 'distributor_password'`Das Verteiler Kennwort. *distributor_password* ist erforderlich, wenn *distributor_security_mode* auf **0**festgelegt ist. *distributor_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Der Wert von *distributor_password* muss kleiner als 120 Unicode-Zeichen sein.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Der Sicherheitsmodus, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verleger verwendet wird. *publisher_security_mode* ist vom Datentyp **int**und hat den Standardwert **1**. Bei **0**wird die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung angegeben. Wenn der **1**ist, wird die Windows-Authentifizierung angegeben. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Der Anmelde Name, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verleger verwendet wird. *publisher_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @publisher_password = ] 'publisher_password'`Das Kennwort, das beim Herstellen einer Verbindung mit dem Verleger verwendet wird. *publisher_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Der Wert von *publisher_password* muss kleiner als 120 Unicode-Zeichen sein.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @job_login = ] 'job_login'`Der Anmelde Name für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_login* ist vom Datentyp **nvarchar (257)** und hat keinen Standardwert. Das Windows-Konto wird stets für Agent-Verbindungen mit dem Verteiler verwendet.  
  
`[ @job_password = ] 'job_password'`Das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Der Wert von *job_password* muss kleiner als 120 Unicode-Zeichen sein.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @db_master_key_password = ] 'db_master_key_password'`Das Kennwort eines benutzerdefinierten Datenbank-Haupt Schlüssels. *db_master_key_password* ist vom Datentyp **nvarchar (524)** und hat den Standardwert NULL. Wenn *db_master_key_password* nicht angegeben ist, wird ein vorhandener Datenbank-Hauptschlüssel gelöscht und neu erstellt.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_attachsubscription** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
 Ein Abonnement kann nicht an die Veröffentlichung angefügt werden, wenn die Aufbewahrungsdauer der Veröffentlichung abgelaufen ist. Wenn ein Abonnement mit einer abgelaufenen Aufbewahrungsdauer angegeben wird, tritt ein Fehler auf, wenn das Abonnement angefügt wird oder wenn es erstmalig synchronisiert wird. Veröffentlichungen mit einer Beibehaltungs Dauer von **0** (nie ablaufen) werden ignoriert.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_attachsubscription**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
